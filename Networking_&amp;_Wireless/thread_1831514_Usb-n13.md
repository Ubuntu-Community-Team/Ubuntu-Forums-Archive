---
title: "Usb-n13"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by Ciscowolf on 2011-08-23
I am getting this Error code 2 at the end and I am just getting into  linux and so far I am very pleased with it. I just need some help  getting this USB wireless device to work before I can indulge my self  more into Linux

Here is what I am getting on the Terminal. 

kristofer@Cisco-LIN:~$ cd desktop
bash: cd: desktop: No such file or directory
kristofer@Cisco-LIN:~$ cd Desktop
kristofer@Cisco-LIN:~/Desktop$ cd 2009
bash: cd: 2009: No such file or directory
kristofer@Cisco-LIN:~/Desktop$ cd 2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13
kristofer@Cisco-LIN:~/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$ sudo make
[sudo] password for kristofer: 
make -C tools
make[1]: Entering directory `/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools'
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/tools/bin2h
cp -f os/linux/Makefile.6 /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/Makefile
make  -C  /lib/modules/2.6.38-11-generic/build  SUBDIRS=/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic'
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/crypt_md5.o
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.o
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.c:  In function ‘BssTableSetEntry’:
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.c:4002:39:  warning: operation on ‘Tab->BssOverlapNr’ may be undefined
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.c:  In function ‘BssTableSortByRssi’:
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/mlme.c:4406:1:  warning: the frame size of 1576 bytes is larger than 1024 bytes
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_wep.o
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/action.o
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/cmm_data.o
  CC [M]  /home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.o
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.c:  In function ‘RtmpRaDevCtrlInit’:
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.c:3709:2:  error: implicit declaration of function ‘init_MUTEX’
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.c:3710:2:  warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer  type
/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/include/rtmp.h:5687:13:  note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
make[2]: *** [/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/home/kristofer/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [LINUX] Error 2
kristofer@Cisco-LIN:~/Desktop/2009_0811_RT3070_Linux_STA_v2.1.1.0_USB-N13$

---

### Post by chili555 on 2011-08-23
You probably won't need to compile from source code, as fun as that might be. Please run:```
lsusb
```If your device is ID 0b05:1784 ASUSTek Computer, Inc., then only one step is needed. Please see: [https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04](https://help.ubuntu.com/community/WifiDocs/Device/Asus%20USB-N13_Natty%2011.04)

If your device is different, please post your result from:```
lsusb
```

---

### Post by Ciscowolf on 2011-08-23
It is showing the device in the Indicator applet on the top right but it is gray and it sys disabled.

---

### Post by chili555 on 2011-08-23
Let's have a look at:```
rfkill list all
```Thanks.

---

### Post by Ciscowolf on 2011-08-23
kristofer@Cisco-LIN:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
kristofer@Cisco-LIN:~$

---

### Post by chili555 on 2011-08-23
Ahhh, the infamous hp-wmi! Please try:```
sudo rfkill unblock all
rfkill list all
```Do you have a built-in wireless that's not working correctly?

---

### Post by Ciscowolf on 2011-08-23
kristofer@Cisco-LIN:~$ sudo rfkill inblock all
[sudo] password for kristofer: 
Usage:    rfkill [options] command
Options:
    --version    show version (0.4-1 (Ubuntu))
Commands:
    help
    event
    list [IDENTIFIER]
    block IDENTIFIER
    unblock IDENTIFIER
where IDENTIFIER is the index no. of an rfkill switch or one of:
    <idx> all wifi wlan bluetooth uwb ultrawideband wimax wwan gps fm
kristofer@Cisco-LIN:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
kristofer@Cisco-LIN:~$ 


I have a built in Atheros ar5001 but its to much trouble to get working so I decided to get a USB adapter and use that cause it would be a little friendlier to do until I got the build in card working.

---

### Post by Ciscowolf on 2011-08-23
dont look at my post above this . I had a typo lol. it is working now thank you! :]

---

### Post by chili555 on 2011-08-23
You will probably have better luck if you blacklist the built-in:```
sudo su
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist.conf
exit
```If you find that you need to run unblock every time you boot up, we can tweak one file and make it permanent.

---

