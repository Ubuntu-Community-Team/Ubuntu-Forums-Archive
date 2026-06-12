---
title: "WUSB600N Help!! Wireless"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by qbanito on 2010-11-11
Hello, well I am a novice in Linux OS, I have a wireless card, it's a Linksys WUSB600N but it doesn't work in Ubuntu 10.10 Desktop Edition, which it is the one I have, 64 bits machine, so I read this [https://help.ubuntu.com/community/Wi...sys%20WUSB600N]("https://help.ubuntu.com/community/WifiDocs/Device/Linksys%20WUSB600N") and I did all the steps,
I downloaded 2010_0915_RT3572_Linux_STA_v2.4.0.2.tar
 but in the last part, sudo make install I got this error 

alain@alain:~/t/2010_0915_RT3572_Linux_STA_v2.4.0.2$ sudo make install
make -C /home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3572sta.ko /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3572sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux'
make: *** [install] Error 2


and in the make part, i cut the whole code:

usb.c:34: note: expected â€˜VOID **â€™ but argument is of type â€˜struct __HTTX_BUFFER **â€™
/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of â€˜RTMPAllocUsbBulkBufStructâ€™ from incompatible pointer type
/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected â€˜VOID **â€™ but argument is of type â€˜struct __TX_BUFFER **â€™
/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of â€˜RTMPAllocUsbBulkBufStructâ€™ from incompatible pointer type
/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected â€˜VOID **â€™ but argument is of type â€˜struct __TX_BUFFER **â€™
/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of â€˜RTMPAllocUsbBulkBufStructâ€™ from incompatible pointer type
/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected â€˜VOID **â€™ but argument is of type â€˜UCHAR **â€™
make[2]: *** [/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/alain/t/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2

so i have no way to get connected to the internet, what is that error cannot stat `rt3572sta.ko': No such file or directory, I think thats why i can make the wireless card work. 
I just dont know what to do :sad:

Thank you

---

### Post by uncaspi on 2010-11-11
rt3572sta.ko is a driver module. Don`t know if this should be in your system or if it is the one you try to compile. Try locate rt3572sta.ko
Compiling could often cause problems due to what version of the compiler you have and the version of the file you try to compile. You could try to upgrade your compiler or get a newer version of the driver source code.

---

### Post by uncaspi on 2010-11-11
Now I have compiled the driver for you. See attachment.
Unpack it and put the file rt3572sta.ko in

/lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/

and type rt3572sta.ko in /etc/modules

You must do it as root.

Reboot and you are ready to go.

---

### Post by qbanito on 2010-11-11
ok, I will try right now

---

### Post by mod-u-lar on 2010-12-05
Does anyone know what reasons there could be that sometimes after boot the driver is not loaded although USB is plugged in? I'm not 100% sure, but I think it's only after total power disconnect of the PC.

response to 
xbmc@MediaPortal:~$ lsusb |grep 1737:0079
Bus 002 Device 002: ID 1737:0079 Linksys 
is positive on the presence of the device but iwconfig tells me that there is no wireless extension available.

Driver is present in /lib/modules/2.6.32-21-generic/kernel/drivers/net/wireless and added in /etc/modules.

As this is an HTPC and disconnected from power together with all the other appliances regularly it's kinda annoying to reinsert the USB when it should be loaded in the first place.

Any ideas to solve this annoyance are welcome.

---

### Post by maruchas on 2010-12-07
> **uncaspi said:**
> Now I have compiled the driver for you. See attachment.
Unpack it and put the file rt3572sta.ko in
 
/lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/
 
and type rt3572sta.ko in /etc/modules
 
You must do it as root.
 
Reboot and you are ready to go.
 
Hi uncaspi, i still have de install problem :s, i even download the rt3572sta.ko file an added to the /lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/ directory also added the line in the modules file.
 
here is mi lines:
 
/home/guillermo/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.c:34: note: expected âVOID **â but argument is of type âUCHAR **â
make[2]: *** [/home/guillermo/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/guillermo/2010_0915_RT3572_Linux_STA_v2.4.0.2/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-23-generic'
make: *** [LINUX] Error 2

 
 
Can you help me??

---

### Post by maruchas on 2010-12-07
> **qbanito said:**
> ok, I will try right now
 
 
qbanito, did you solve the problem??

---

### Post by edentjeh on 2010-12-07
Had the same problem myself yesterday with my wusb600n, i had to do the following to be able to compile the driver (plus all the other usual changes):

in /include/os/rt_linux.h 

I had to change this:

usb_buffer_alloc change it to -> usb_alloc_coherent (should be in line 1077, otherwise search)

usb_buffer_free change it to -> usb_free_coherent (should be in line 1078)

hope it works for you aswell.. !

---

