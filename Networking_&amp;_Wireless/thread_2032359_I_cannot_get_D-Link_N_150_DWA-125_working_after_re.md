---
title: "I cannot get D-Link N 150 DWA-125 working after reading these forums"
date: 2012-07-23
forum: Networking &amp; Wireless
---

### Post by Chlewey on 2012-07-23
I have a Compaq CQ1115LA with Red Flag Linux preinstalled (which has very little support so I changed to a fresh 64 bit  Ubuntu 12.04... I have no idea who installed Red Flag as HP seems to have no support for them either.)

Then I acquired a D-Link Wireless N 150 USB Adapter.  Accompanying CD only comes with Windows Drivers (and as I soon researched, they will fail with ndiswrapper, so I have not even try them).

I have downloaded the DWA-125 drivers for Linux from the D-Link website: [http://www.dlinkla.com.co/](http://www.dlinkla.com.co/)

As per instructions both with those drivers and several threats in this forums, I removed the rt2800 drivers, reloaded the system and tried to 'make' the installation.

I keep getting a couple of errors in the first make.
```
[COLOR=Gray]oruga@piloto-oruga:~/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0$[/COLOR]  **make**
make -C tools
make[1]: se ingresa al directorio «/home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/tools»
gcc -g bin2h.c -o bin2h
make[1]: se sale del directorio «/home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/tools»
/home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/3.2.0-23-generic/build SUBDIRS=/home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.2.0-23-generic»
  CC [M]  /home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o
/home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c: En la función &#8216;RtmpRaDevCtrlInit&#8217;:
/home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3710:2: error: declaración implícita de la función &#8216;init_MUTEX&#8217; [-Werror=implicit-function-declaration]
/home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3711:2: aviso: se pasa el argumento 2 de &#8216;os_alloc_mem&#8217; desde un tipo de puntero incompatible [activado por defecto]
/home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/include/rtmp.h:5707:13: nota: se esperaba &#8216;UCHAR **&#8217; pero el argumento es de tipo &#8216;UCHAR *&#8217;
cc1: some warnings being treated as errors
make[2]: *** [/home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: se sale del directorio «/usr/src/linux-headers-3.2.0-23-generic»
make: *** [LINUX] Error 2

```Then the 'make install' also fails:

```
[COLOR=Gray]oruga@piloto-oruga:~/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0$ [/COLOR]**sudo make install**
make -C /home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux -f Makefile.6 install
make[1]: se ingresa al directorio «/home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux»
rm -rf /etc/Wireless/RT3070STA
mkdir -p /etc/Wireless/RT3070STA
cp /home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/RT2870STA.dat /etc/Wireless/RT3070STA/.
install -d /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/3.2.0-23-generic/kernel/drivers/net/wireless/
install: no se puede efectuar `stat' sobre «rt3070sta.ko»: No existe el archivo o el directorio
make[1]: *** [install] Error 1
make[1]: se sale del directorio «/home/oruga/Descargas/2009_1204_RT3070_Linux_STA_v2.1.2.0/os/linux»
make: *** [install] Error 2

```I'm clueless on any next step.

From Ralink site I got a RT2870 driver (only one file: rt2870.bin plus the license) but no instructions on how to use it.

---

### Post by chili555 on 2012-07-23
> [COLOR="Red"]2009[/COLOR]_1204_RT3070_Linux_STA_v2.1.2.0I doubt this old-timer is ever going to work on your 3.2.0 kernel. Why didn't the built-in rt2800usb work? May I see:```
lsusb
```

---

### Post by Chlewey on 2012-07-24
> **chili555 said:**
> I doubt this old-timer is ever going to work on your 3.2.0 kernel. Why didn't the built-in rt2800usb work?
I have no idea if it worked.  The wireless USB adapter just didn't plugged and played, but as far as I know it doesn't do it in Windows either.
> **chili555 said:**
> May I see:```
lsusb
``````
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 07d1:3c16 D-Link System DWA-125 Wireless N 150 Adapter(rev.A2) [Ralink RT3070]
Bus 002 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 005 Device 002: ID 0461:0010 Primax Electronics, Ltd 
Bus 005 Device 003: ID 04d8:fe65 Microchip Technology, Inc. 
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90

```

---

### Post by chili555 on 2012-07-24
> The wireless USB adapter just didn't plugged and played, but as far as I know it doesn't do it in Windows either.Is it defective?

Please insert the device and run and post:```
sudo modprobe rt2800usb
dmesg | grep -i rt2
iwconfig
```Thanks.

---

### Post by Chlewey on 2012-07-24
> **chili555 said:**
> Is it defective?
I haven't tried in Windows yet but according to accompanying instructions the driver must be installed first before plugging the Adapter.

> **chili555 said:**
> 
Please insert the device and run and post:```
sudo modprobe rt2800usb
dmesg | grep -i rt2
iwconfig
```Thanks.
I got a fatal error running modprobe but I assume it is because I banned rt2800usb as per instructions to load the supposedly correct driver.

I will unban it and restart after I finish running some other (unrelated) tests.

---

### Post by chili555 on 2012-07-24
If you still get an error, please post it here.

---

### Post by Chlewey on 2012-07-24
Okay, I unbanned rt2800usb and restarted and run the commands.
```
[COLOR=Gray]oruga@piloto-oruga:~$[/COLOR] sudo modprobe rt2800usb
[B]FATAL: Module rt2800usb not found.
[/B][COLOR=Gray]oruga@piloto-oruga:~$[/COLOR] dmesg | grep -i rt2
[COLOR=Gray]oruga@piloto-oruga:~$[/COLOR] iwconfig
[B]lo        no wireless extensions.

eth0      no wireless extensions.[/B]
```
Given that my main issue is not working either (running a Windows app using Wine to connect to a USB port) it seems I will desist trying to solve these issues on Ubuntu and rather buying a Windows license.

Thank you, any how.

---

### Post by Chlewey on 2012-07-25
> **chili555 said:**
> Is it defective?

Please insert the device and run and post:```
sudo modprobe rt2800usb
dmesg | grep -i rt2
iwconfig
```Thanks.
Okay, I reinstalled a 32 bit Ubuntu and now I get this outoput:

```
[COLOR=Gray]oruga@oruga-piloto:~$ [/COLOR]sudo modprobe rt2800usb
[COLOR=Gray]oruga@oruga-piloto:~$ [/COLOR]dmesg | grep -i rt2
[B][   10.650057] Registered led device: rt2800usb-phy0::radio
[   10.650092] Registered led device: rt2800usb-phy0::assoc
[   10.650129] Registered led device: rt2800usb-phy0::quality
[   10.650189] usbcore: registered new interface driver rt2800usb[/B]
[COLOR=Gray]oruga@oruga-piloto:~$[/COLOR] iwconfig
[B]lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.[/B]


```
Which seems probaly okay.  After I finish my other testing I will try to get connection.

---

### Post by chili555 on 2012-07-25
> Which seems probaly okay. It seems *very* OK! I have my fingers and toes crossed.

---

