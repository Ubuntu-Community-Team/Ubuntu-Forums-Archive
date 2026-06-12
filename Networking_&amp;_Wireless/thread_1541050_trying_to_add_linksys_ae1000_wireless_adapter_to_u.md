---
title: "trying to add linksys ae1000 wireless adapter to ubuntu 10.04"
date: 2010-07-28
forum: Networking &amp; Wireless
---

### Post by rmamrick on 2010-07-28
[SIZE=3][FONT=Times New Roman]My computer has Ubuntu 10.04 LTS loaded. I tried to get my Linksys AE1000 Wireless N adapter to work. I ran lsusb and it gives me a device number (13b1:002f) for linksys. [/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]I started out trying to fix the connectivity with Ndiswrapper 1st. I loaded the ralink driver 3572.. I believe I have Downloaded the latest Linux wireless drivers. I believe I downloaded [Compat-wireless release types]("http://wireless.kernel.org/en/users/Download#Compat-wireless_release_types#Compat-wireless_release_types"). I downloaded the compat wireless tarball, extracted, built, and installed. The following are error messages that I am getting.[/FONT][/SIZE]
 
**_[SIZE=3][FONT=Times New Roman]rick@rick-desktop:~/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1$ make[/FONT][/SIZE]_**
[FONT=Times New Roman][SIZE=3]make -C tools[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]………[/SIZE][/FONT]
**_[SIZE=3][FONT=Times New Roman]make: *** /lib/modules/2.6.32-24-generic-pae/build: No such file or directory. Stop.[/FONT][/SIZE]_**
**_[SIZE=3][FONT=Times New Roman]make: *** [LINUX] Error 2[/FONT][/SIZE]_**
 
 
 
**_[SIZE=3][FONT=Times New Roman]rick@rick-desktop:~/Ralink_RT2870_Linux_STA_v2.4.0.1/2010_0709_RT2870_Linux_STA_v2.4.0.1$ sudo make install[/FONT][/SIZE]_**
[FONT=Times New Roman][SIZE=3]make -C /home/rick/Ralink_RT2870_Linux_STA_v2.4.0.1/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux -f Makefile.6 install[/SIZE][/FONT]
**_[SIZE=3][FONT=Times New Roman]mkdir: cannot create directory `/etc/Wireless': File exists[/FONT][/SIZE]_**
[FONT=Times New Roman][SIZE=3]…[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]install -m 644 -c rt2870sta.ko /lib/modules/2.6.32-24-generic-pae/kernel/drivers/net/wireless/[/SIZE][/FONT]
**_[SIZE=3][FONT=Times New Roman]/sbin/depmod -a 2.6.32-24-generic-pae[/FONT][/SIZE]_**
**_[SIZE=3][FONT=Times New Roman]WARNING: Can't read module /lib/modules/2.6.32-24-generic-pae/updates/dkms/wl.ko: Invalid argument[/FONT][/SIZE]_**
[FONT=Times New Roman][SIZE=3]make[1]: Leaving directory `/home/rick/Ralink_RT2870_Linux_STA_v2.4.0.1/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'[/SIZE][/FONT]
 
 
 
**_[SIZE=3][FONT=Times New Roman]rick@rick-desktop:~/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1$ make[/FONT][/SIZE]_**
[FONT=Times New Roman][SIZE=3]make -C tools[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]make[1]: Entering directory `/home/rick/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1/tools'[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]gcc -g bin2h.c -o bin2h[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]…[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/home/rick/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c: In function ‘AES_GTK_KEY_WRAP’:[/SIZE][/FONT]
**_[SIZE=3][FONT=Times New Roman]/home/rick/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c:2265: warning: the frame size of 1100 bytes is larger than 1024 bytes[/FONT][/SIZE]_**
[FONT=Times New Roman][SIZE=3]/home/rick/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux/../../common/crypt_aes.c: In function ‘WscDecryptData’:[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]There are multiple other frame size errors.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]…[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/home/rick/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c: In function ‘RtmpOSNetDevAttach’:[/SIZE][/FONT]
**_[SIZE=3][FONT=Times New Roman]/home/rick/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_linux.c:1731: warning: initialization discards qualifiers from pointer target type[/FONT][/SIZE]_**
**_[SIZE=3][FONT=Times New Roman]CC [M][/FONT][/SIZE]_**
[SIZE=3][FONT=Times New Roman]…[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3]/home/rick/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_main_dev.c: In function ‘MainVirtualIF_close’:[/SIZE][/FONT]
**_[SIZE=3][FONT=Times New Roman]/home/rick/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux/../../os/linux/rt_main_dev.c:117: warning: unused variable ‘Cancelled’[/FONT][/SIZE]_**
[FONT=Times New Roman][SIZE=3]… /home/rick/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o[/SIZE][/FONT]
**_[SIZE=3][FONT=Times New Roman]/home/rick/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:[/FONT][/SIZE]_**
**_[SIZE=3][FONT=Times New Roman]/home/rick/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type[/FONT][/SIZE]_**
**_[SIZE=3][FONT=Times New Roman]/home/rick/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’[/FONT][/SIZE]_**
**_[FONT=Times New Roman][SIZE=3]Multiple similar error and warning messages[/SIZE][/FONT]_**
 
 
 
[FONT=Times New Roman][SIZE=3]rick@rick-desktop:~/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1$ sudo make install[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][sudo] password for rick: [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]make -C /home/rick/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux -f Makefile.6 install[/SIZE][/FONT]
**_[SIZE=3][FONT=Times New Roman]mkdir: cannot create directory `/etc/Wireless': File exists[/FONT][/SIZE]_**
[FONT=Times New Roman][SIZE=3]install -m 644 -c rt3572sta.ko /lib/modules/2.6.32-24-generic-pae/kernel/drivers/net/wireless/[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]/sbin/depmod -a 2.6.32-24-generic-pae[/SIZE][/FONT]
**_[SIZE=3][FONT=Times New Roman]WARNING: Can't read module /lib/modules/2.6.32-24-generic-pae/updates/dkms/wl.ko: Invalid argument[/FONT][/SIZE]_**
[FONT=Times New Roman][SIZE=3]make[1]: Leaving directory `/home/rick/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1/os/linux'[/SIZE][/FONT]
 
 
 
[FONT=Times New Roman][SIZE=3]rick@rick-desktop:~/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1$ sudo modprobe rt2870sta[/SIZE][/FONT]
**_[SIZE=3][FONT=Times New Roman]WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.[/FONT][/SIZE]_**
**_[SIZE=3][FONT=Times New Roman]WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.[/FONT][/SIZE]_**
[FONT=Times New Roman][SIZE=3]Ndiswrapper was removed with synaptic package manager[/SIZE][/FONT]
 
 
[FONT=Times New Roman][SIZE=3]rick@rick-desktop:~/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1$ sudo /etc/init.d/networking restart[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]* Reconfiguring network interfaces... Ignoring unknown interface eth0=eth0.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman][ OK ][/FONT][/SIZE]
 
 
 
[SIZE=3][FONT=Times New Roman]rick@rick-desktop:~/Desktop/2010_0709_RT3572_Linux_STA_v2.4.0.1**_$ iwconfig_**[/FONT][/SIZE]
**_[SIZE=3][FONT=Times New Roman]lo no wireless extensions.[/FONT][/SIZE]_**
 
**_[SIZE=3][FONT=Times New Roman]eth0 no wireless extensions.[/FONT][/SIZE]_**
 
 
 
[SIZE=3][FONT=Times New Roman]rick@rick-desktop**_:~$ dmesg|grep rt28_**[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][ 14.501943] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman][ 14.512544**_] usbcore: registered new interface driver rt2870_**[/FONT][/SIZE]
**_[SIZE=3][FONT=Times New Roman][ 14.634242] Error: Driver 'rt2870' is already registered, aborting...[/FONT][/SIZE]_**
**_[SIZE=3][FONT=Times New Roman][ 14.634291] usbcore: error -16 registering interface driver rt2870[/FONT][/SIZE]_**
[FONT=Times New Roman][SIZE=3]rick@rick-desktop:~$[/SIZE][/FONT]

---

