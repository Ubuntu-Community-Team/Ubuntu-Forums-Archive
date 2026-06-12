---
title: "Asus usb-n13 in ubuntu 10.10 Help"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by roxxar on 2011-02-03
I just recently bought a **Asus usb-n13. **I need help installing the proper driver for my **Asus usb-n13 in ubuntu 10.10**. I currently have the STA wireless driver installed for the integrated wireless driver on my net book. 

Currently the Asus Usb can find network around my house. I know this because when I click on the wifi icon. However, the signal is very weak compared to the integrated wireless driver.. So I believe that I need to install the correct wireless driver. 


I found this while searching for a solution:  
[http://ubuntuforums.org/showthread.php?p=10425685#post10425685](http://ubuntuforums.org/showthread.php?p=10425685#post10425685)

I did what it said, it didnt work. When i do the make command i get this:

root@pc:~# cd '/home/tyler/Desktop/RT3070' 
root@pc:/home/tyler/Desktop/RT3070# sudo gedit os/linux/config.mk
root@pc:/home/tyler/Desktop/RT3070# sudo gedit os/linux/usb_main_dev.c
root@pc:/home/tyler/Desktop/RT3070# make
make -C tools
make[1]: Entering directory `/home/tyler/Desktop/RT3070/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/tyler/Desktop/RT3070/tools'
/home/tyler/Desktop/RT3070/tools/bin2h
cp -f os/linux/Makefile.6 /home/tyler/Desktop/RT3070/os/linux/Makefile
make  -C  /lib/modules/2.6.35-25-generic/build SUBDIRS=/home/tyler/Desktop/RT3070/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-25-generic'
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/crypt_md5.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/mlme.o
/home/tyler/Desktop/RT3070/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/tyler/Desktop/RT3070/os/linux/../../common/mlme.c:4406: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/cmm_wep.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/action.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/cmm_data.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/rtmp_init.o
/home/tyler/Desktop/RT3070/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/tyler/Desktop/RT3070/os/linux/../../common/rtmp_init.c:3710: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/tyler/Desktop/RT3070/include/rtmp.h:5704: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/cmm_aes.o
/home/tyler/Desktop/RT3070/os/linux/../../common/cmm_aes.c: In function ‘AES_GTK_KEY_WRAP’:
/home/tyler/Desktop/RT3070/os/linux/../../common/cmm_aes.c:1338: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/cmm_sync.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/eeprom.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/cmm_info.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/dfs.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/spectrum.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/rt_channel.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/cmm_profile.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/cmm_asic.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../sta/assoc.o
/home/tyler/Desktop/RT3070/os/linux/../../sta/assoc.c: In function ‘wext_notify_event_assoc’:
/home/tyler/Desktop/RT3070/os/linux/../../sta/assoc.c:1401: warning: pointer targets in passing argument 5 of ‘RtmpOSWrielessEventSend’ differ in signedness
/home/tyler/Desktop/RT3070/include/rtmp.h:7048: note: expected ‘PUCHAR’ but argument is of type ‘char *’
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../sta/auth.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../sta/sync.o
/home/tyler/Desktop/RT3070/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/tyler/Desktop/RT3070/os/linux/../../sta/sync.c:657: warning: the frame size of 1252 bytes is larger than 1024 bytes
/home/tyler/Desktop/RT3070/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/tyler/Desktop/RT3070/os/linux/../../sta/sync.c:1435: warning: the frame size of 1312 bytes is larger than 1024 bytes
/home/tyler/Desktop/RT3070/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/tyler/Desktop/RT3070/os/linux/../../sta/sync.c:935: warning: the frame size of 1260 bytes is larger than 1024 bytes
/home/tyler/Desktop/RT3070/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/tyler/Desktop/RT3070/os/linux/../../sta/sync.c:525: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../sta/sanity.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../sta/connect.o
/home/tyler/Desktop/RT3070/os/linux/../../sta/connect.c: In function ‘LinkDown’:
/home/tyler/Desktop/RT3070/os/linux/../../sta/connect.c:1975: warning: unused variable ‘Cancelled’
/home/tyler/Desktop/RT3070/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/tyler/Desktop/RT3070/os/linux/../../sta/connect.c:343: warning: the frame size of 1600 bytes is larger than 1024 bytes
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../sta/wpa.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../os/linux/rt_linux.o
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/rt_linux.c:982: warning: the frame size of 1084 bytes is larger than 1024 bytes
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../os/linux/rt_main_dev.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.o
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwencode’:
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.c:1839: warning: suggest parentheses around operand of ‘!’ or change ‘&’ to ‘&&’ or ‘!’ to ‘~’
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlRF’:
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.c:7179: warning: pointer targets in passing argument 1 of ‘strchr’ differ in signedness
/usr/src/linux-headers-2.6.35-25-generic/arch/x86/include/asm/string_32.h:27: note: expected ‘const char *’ but argument is of type ‘CHAR *’
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.c:7179: warning: pointer targets in assignment differ in signedness
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_iwaplist’:
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.c:1037: warning: the frame size of 1288 bytes is larger than 1024 bytes
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.c: In function ‘rt_ioctl_siwmlme’:
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.c:2321: warning: the frame size of 1584 bytes is larger than 1024 bytes
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlRF’:
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.c:7315: warning: the frame size of 2328 bytes is larger than 1024 bytes
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlE2PROM’:
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.c:7131: warning: the frame size of 1348 bytes is larger than 1024 bytes
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.c: In function ‘RTMPIoctlMAC’:
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/sta_ioctl.c:6933: warning: the frame size of 1344 bytes is larger than 1024 bytes
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/ba_action.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../os/linux/usb_main_dev.o
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/usb_main_dev.c: In function ‘RTUSBWatchDog’:
/home/tyler/Desktop/RT3070/os/linux/../../os/linux/usb_main_dev.c:760: warning: format ‘%d’ expects type ‘int’, but argument 3 has type ‘ULONG’
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../os/linux/rt_usb.o
  CC [M]  /home/tyler/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.o
/home/tyler/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitRecv’:
/home/tyler/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’
/home/tyler/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/tyler/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function ‘usb_buffer_free’
make[2]: *** [/home/tyler/Desktop/RT3070/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/tyler/Desktop/RT3070/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make: *** [LINUX] Error 2
root@pc:/home/tyler/Desktop/RT3070# sudo make install
make -C /home/tyler/Desktop/RT3070/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/tyler/Desktop/RT3070/os/linux'
rm -rf /etc/Wireless/RT3070STA
mkdir /etc/Wireless/RT3070STA
cp /home/tyler/Desktop/RT3070/RT2870STA.dat /etc/Wireless/RT3070STA/.
install -d /lib/modules/2.6.35-25-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3070sta.ko /lib/modules/2.6.35-25-generic/kernel/drivers/net/wireless/
install: cannot stat `rt3070sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/tyler/Desktop/RT3070/os/linux'
make: *** [install] Error 2

---

### Post by roxxar on 2011-02-04
I tried this below:

By default, downloads go to your desktop, so I assume you have  downloaded the file I attached and can see it, the .tar.bz2 file,  sitting on your desktop. Right click it and select 'Extract Here.' A  folder will be created called RT3070_LinuxSTA_V2.3.0.1_20100208.

I am assuming you have the text editor, gedit. If not, in the following  commands, substitute kate, nano or your favorite text editor. Open a  terminal and do: 	Code:
 	cd Desktop/RT3070 
Press the Tab key; the terminal will fill in the details for you,  assuming you have only one RT3070etc. file on your desktop. Now do: 	Code:
 	cp RT2870STA.dat RT3070STA.dat
cp RT2870STACard.dat RT3070STACard.dat
sudo su
make
make install
modprobe rt3070sta
iwconfig 
Plan B: 	Code:
 	cd Desktop/RT3070 
Tab. 	Code:
 	sudo su
make uninstall
depmod -a 
Now trash the first file and download the attached file to your desktop. Right-click and select 'Extract Here.' 	Code:
 	cd ~/Desktop/2009 
Tab. 	Code:
 	gedit os/linux/config.mk 
Find these lines: 	Quote:
 	 	 		 			 				HAS_WPA_SUPPLICANT=n
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n 			 		 	 	 
Change them to =y

Proofread carefully, save and close gedit. 	Code:
 	gedit os/linux/usb_main_dev.c 
At or near line 45, you will find a listing of PCI IDs. Add a new line: 	Quote:
 	 	 		 			 				{USB_DEVICE(0x0B05,0x1784)}, /* Asus 3070 */ 			 		 	 	 
Make doubly sure that the indentation and spacing exactly matches  the existing lines. I did my change at the top. Please see attached.  Proofread carefully, save and close gedit. 	Code:
 	make
make install
modprobe rt3070sta
iwconfig 


I got the error when compiling option B:

make[2]: *** [/home/tyler/Desktop/2009/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/tyler/Desktop/2009/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-25-generic'
make: *** [LINUX] Error 2
tyler@pc:~/Desktop/2009$ make install
make -C /home/tyler/Desktop/2009/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/tyler/Desktop/2009/os/linux'
rm -rf /etc/Wireless/RT3070STA
rm: cannot remove `/etc/Wireless/RT3070STA/RT3070STA.dat': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/tyler/Desktop/2009/os/linux'
make: *** [install] Error 2
tyler@pc:~/Desktop/2009$ modprobe rt3070sta
FATAL: Module rt3070sta not found.

---

### Post by chili555 on 2011-02-04
Please see:  [http://ubuntuforums.org/showthread.php?p=10427107#post10427107](http://ubuntuforums.org/showthread.php?p=10427107#post10427107)

You shouldn't have to compile anything in order to get it working.

---

