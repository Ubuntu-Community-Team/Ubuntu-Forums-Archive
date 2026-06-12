---
title: "Lucid Lynx / Sabrent 802.11-N USB 2.0"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by Clyssus on 2010-05-28
](*,)Help! 

I've been using Ubuntu for a while, but I have never tried to set up a wireless device with it... I have no idea where to even begin... I've done a search of the forums but wasn't able to glean much from it... any and all help would be much appreciated!

Danke!

---

### Post by blesbok on 2010-05-28
May I assume you have a wirless LAN card (wifi)?  Your first step is to see if it can be seen.  Use sudo ifconfig .  If something like wlan0 appears, your wireless device is there.  Next, you must find your chipset ID.  Use chipset ID to find a suitable driver. Eg. do the native drivers (those on your system eg. ath5k, ath 9k) work with that chipset?

To determine chipset ID (for PCI slot card): lspci  Look in the output for a device "wireless" or such.  Note number in leftmost column.

lspci -n will give the chipset ID along with that number in previous paragraph.  That's just a start!  All the best further.

---

### Post by Clyssus on 2010-05-28
It's actually a USB 2.0  wifi N, not a pci card. I tried lsusb, this was the result
```
:~$ lsusb
Bus 003 Device 002: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 016: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 012: ID 0bc2:0503 Seagate RSS LLC 
Bus 001 Device 004: ID 058f:6377 Alcor Micro Corp. Multimedia Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
This is it right here:
```
Bus 001 Device 016: ID 148f:3070 Ralink Technology, Corp. 

```

Now what do I do?

The packaging says it supports Linux, the disk that came with it has a .tar.bz2 file on it but I have no clue how to install it...

---

### Post by Clyssus on 2010-05-29
Bump!

---

### Post by blesbok on 2010-05-29
This line seems to be your wireless device: Bus 001 Device 016: ID 148f:3070 Ralink Technology, Corp.  Using lspci -n , you should get the chipset ID appearing in a line with 148f:3070 in it.  Search the net with that chipset ID and your device name and model no eg Sabrent 123XYZ.  Expect to find something like what follows: (by no means a complete installation guide)

That .tar.bz2 file is probably your driver.  You have to unzip it in a directory. Eg. 
```

```
mkdir ~/wirelessdriver 
cp /urlto/filename.tar.bz2  ~/wirelessdriver
cd wirelessdriver
# now unzip the package 
tar xvfz filename.tar.bz2
# change to the new directory that has appeared within wirelessdriver 
cd filename 
sudo make

You may find NetworkManager getting in the way of the driver.  If it happens right-click the network icon and uncheck the boxes you see.

---

### Post by Clyssus on 2010-05-29
```
:~$ lspci -n
00:00.0 0600: 1002:5a33 (rev 01)
00:01.0 0604: 1002:5a3f
00:11.0 0101: 1002:437a (rev 80)
00:12.0 0101: 1002:4379 (rev 80)
00:13.0 0c03: 1002:4374 (rev 80)
00:13.1 0c03: 1002:4375 (rev 80)
00:13.2 0c03: 1002:4373 (rev 80)
00:14.0 0c05: 1002:4372 (rev 82)
00:14.1 0101: 1002:4376 (rev 80)
00:14.2 0403: 1002:437b (rev 01)
00:14.3 0601: 1002:4377 (rev 80)
00:14.4 0604: 1002:4371 (rev 80)
01:05.0 0300: 1002:5a61
02:02.0 0200: 10ec:8139 (rev 10)
02:03.0 0604: 10b5:8112 (rev aa)
02:04.0 0780: 14f1:2f40
03:00.0 0300: 10de:06e4 (rev a1)
```I didn't see "148f:3070" anywhere.

```
:~$ mkdir ~/wirelessdriver
:~$ cp /ultro/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2 ~/wirelessdriver
cp: cannot stat `/ultro/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2': No such file or directory
 
``` Here's what happened when I tried to install the driver.

Not sure what I'm doing wrong.

---

### Post by blesbok on 2010-05-30
Post 6: :
> ~$ lspci -n
that should be lsusb -i, sorry; you *had* said it's usb, not pci.

>  cp: cannot stat `/ultro/': No such file or directory

Bash doesn't see the directory you've given.  That's because bash needs the path to your device eg. cdrom and you've pointed bash to a subdirectory of root called 'ultro'.  Try to find the path to your bz2 file.  Eg.
```
 cd /media; find . -name '2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2' 
``` 

Follow up with a cp command which will read something like
```
 cp /media/inbetweenstuff/2008_0925_RT2870_Linux_STA_v1.4.0.0.tar.bz2 ~/wirelessdriver
```

After you've unzipped the tarball, look for a README file in your new directory  :P

---

### Post by Clyssus on 2010-06-02
```
:~$ lsusb -i
lsusb: invalid option -- 'i'
Usage: lsusb [options]...
List USB devices
  -v, --verbose
      Increase verbosity (show descriptors)
  -s [[bus]:][devnum]
      Show only devices with specified device and/or
      bus numbers (in decimal)
  -d vendor:[product]
      Show only devices with the specified vendor and
      product ID numbers (in hexadecimal)
  -D device
      Selects which device lsusb will examine
  -t
      Dump the physical USB device hierarchy as a tree
  -V, --version
      Show version of program

```This is the results of "lsusb -i", never saw   "148f:3070" .




```
-------@-------:~$ cd /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0
-------@-------:~/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0$ sudo make
[sudo] password for -------: 
make -C tools
make[1]: Entering directory `/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools'
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/Makefile
make  -C  /lib/modules/2.6.32-22-generic/build SUBDIRS=/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/md5.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/mlme.o
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/mlme.c:4259: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_wep.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/action.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.o
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.c: In function ‘RTMP_FillTxBlkInfo’:
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_data.c:713: warning: label ‘FillTxBlkErr’ defined but not used
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_init.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/rtmp_tkip.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_sync.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/eeprom.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_info.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_wpa.o
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_wpa.c: In function ‘AES_GTK_KEY_WRAP’:
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/cmm_wpa.c:836: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/dfs.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../common/spectrum.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/assoc.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/aironet.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/auth.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.o
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c: In function ‘PeerBeacon’:
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c:1393: warning: the frame size of 1312 bytes is larger than 1024 bytes
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtJoinAction’:
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c:934: warning: the frame size of 1252 bytes is larger than 1024 bytes
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c: In function ‘PeerBeaconAtScanAction’:
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c:675: warning: the frame size of 1256 bytes is larger than 1024 bytes
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c: In function ‘MlmeStartReqAction’:
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sync.c:533: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/sanity.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/connect.o
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/connect.c: In function ‘CntlOidScanProc’:
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/connect.c:351: warning: the frame size of 1600 bytes is larger than 1024 bytes
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/wpa.o
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/wpa.c: In function ‘CCKMPRF’:
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../sta/wpa.c:1848: warning: the frame size of 1044 bytes is larger than 1024 bytes
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.o
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.c: In function ‘send_monitor_packets’:
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_linux.c:1043: warning: the frame size of 1084 bytes is larger than 1024 bytes
  CC [M]  /home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c: In function ‘RTMPReadParametersHook’:
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:928: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:929: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:930: error: ‘struct task_struct’ has no member named ‘fsgid’
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:1593: error: ‘struct task_struct’ has no member named ‘fsuid’
/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.c:1594: error: ‘struct task_struct’ has no member named ‘fsgid’
make[2]: *** [/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/home/-------/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make: *** [LINUX] Error 2
-------@-------:~/wirelessdriver/2008_0925_RT2870_Linux_STA_v1.4.0.0$ 

```This is the result of your advice for installation of the tar.bz2 file, there were a couple of errors...

It seems we are getting somewhere though, I appreciate your help!

---

### Post by Clyssus on 2010-06-02
> =======================================================================
Build Instructions:  
====================

1> $tar -xvzf DPB_RT2870_Linux_STA_x.x.x.x.tgz
    go to "./DPB_RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
     set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
     define the linux kernel source include file path LINUX_SRC
     modify to meet your need.

3> In os/linux/config.mk 
    define the GCC and LD of the target machine
    define the compiler flags CFLAGS
    modify to meet your need.
    ** Build for being controlled by NetworkManager or wpa_supplicant wext functions
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
       => #>cd wpa_supplicant-x.x
       => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
    ** Build for being controlled by WpaSupplicant with Ralink Driver
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       => #>cd wpa_supplicant-0.5.7
       => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make
    # compile driver source code
    # To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
      => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
    $/sbin/rmmod rt2870sta
    
=======================================================================Here is the "build" instructions in the readme file... it's all Greek to me... :-k

I figure this may help...

---

### Post by Clyssus on 2010-06-02
What does this mean?
> ```
[LINUX] Error 2

```

---

### Post by Clyssus on 2010-06-03
Bump

---

### Post by Clyssus on 2010-06-04
Anyone?

---

### Post by blesbok on 2010-06-08
Clyssus
There are seven instructions in the README.  After No.1, No.s2&3 required files to be edited *prior* to the make command being given.  Ensure that you do this correctly before issuing "make".

Ah, but you've done that anyway. So you'll first have to uninstall your driver (it will be something like what follows):

```
sudo modprobe -r 2008_0925_RT2870_Linux_STA_v1.4.0.0
  sudo apt-get --purge remove 2008_0925_RT2870_Linux_STA_v1.4.0.0-utils
  sudo rm -r /etc/2008_0925_RT2870_Linux_STA_v1.4.0.0
  sudo rm -r /etc/modprobe.d/2008_0925_RT2870_Linux_STA_v1.4.0.0
```

Try to follow intstr8ctions 2-7. Follow up with ```
lsmod | grep 2870
```  Do search other forums using terms like rt2870. When you feel there should be something to show for your attempts, try: 
```

sudo iwlist wlan0 scan
sudo iwconfig wlan0
```.  

Post the results too.  All the best.

---

