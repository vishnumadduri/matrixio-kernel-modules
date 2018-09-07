DTC=dtc

obj-m += matrixio-core.o
obj-m += matrixio-uart.o
obj-m += matrixio-everloop.o
obj-m += matrixio-codec.o
obj-m += matrixio-pcm.o
obj-m += matrixio-gpio.o
obj-m += matrixio-env.o
obj-m += matrixio-imu.o
obj-m += matrixio-regmap.o

SRC := $(shell pwd)


all:	matrixio.dtbo
	$(MAKE) -C $(KERNEL_SRC) M=$(SRC) modules

matrixio.dtbo: matrixio-overlay.dts
	$(DTC) -W no-unit_address_vs_reg -@ -I dts -O dtb -o matrixio.dtbo matrixio-overlay.dts


modules_install:
        cp matrixio.dtbo /boot/overlays
	$(MAKE) -C $(KERNEL_SRC) M=$(SRC) modules_install


clean:
	$(MAKE) -C $(KERNEL_SRC) M=$(SRC) clean
	rm -f *.dtbo
