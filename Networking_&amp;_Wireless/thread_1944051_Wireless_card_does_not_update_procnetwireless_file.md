---
title: "Wireless card does not update /proc/net/wireless file"
date: 2012-03-20
forum: Networking &amp; Wireless
---

### Post by Sedio on 2012-03-20
I am creating a program that requires the ability to obtain the link quality (%), noise level, and quality level.  I am attempting to obtain this information by using the wireless tools dev library.  The file '/proc/net/wireless' is empty besides the header part. 
i.e.
```
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
```

From what I understand that file is updated by the wireless driver (if supported) after every packet is received.  The command 'iwconfig' also uses this file to output full information about the wireless card.  Currently when I run the command iwconfig I get the following information:
```
brt@sedio:~$ gedit /proc/net/wireless 
brt@sedio:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth3      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
brt@sedio:~$ 
```

Whereas if the driver supported wireless tool it would output something like this:
```
wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:177  Invalid misc:99   Missed beacon:0
```

As you can see I am missing a lot of information, specifically the link quality which is what I need.

I am using a USB wireless adapter(Alfa AWUS036NEH) which uses a ralink driver (either RT2870 or RT3070).  The information about it is below (let me know if more information is required).
lsusb |grep rt:
```
brt@sedio:~$ lsusb |grep rt
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
brt@sedio:~$ 
```
lsmod |grep rt:
```
brt@sedio:~$ lsmod |grep rt
rt2800usb              22590  0 
rt2800lib              54538  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20830  1 rt2800usb
rt2x00lib              50365  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              462046  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              199630  2 rt2x00lib,mac80211
parport_pc             36962  0 
parport                46562  3 parport_pc,ppdev,lp
brt@sedio:~$ 
```

Previously I was using Ubuntu 11.04 and had fixed this problem.  In 11.04 both the drivers rt2x00lib/rt2x00usb and rt2870sta were automatically installed.  I was able to fix this problem by blacklisting the community created drivers by putting the follow lines in '/etc/modprode.d/blacklist.conf':
```
# Blacklist for rt 2870/3070 drivers
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```

Now that I have upgraded to 11.10 it seems the ralink drivers (rt2870sta) were removed from the OS thus creating my original problem as the community drivers were not allowing me to display the link quality.  Now I could go back and install the ralink 2870sta drivers but I heard they were written badly and don't work especially well.  Is there a way I could fix this without having to install another driver and blacklist the rt2x00 ones?

---

### Post by chili555 on 2012-03-20
> Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22> wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:onI believe you actually have to be connected to an access point for packets to be transmitted, measured, etc. Here is my /proc/net/wireless while connected (and answering this post):> Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
 wlan0: 0000   65.  -45.  -256        0      0      0      0    661        0I doubt the whole rt2870sta vs. rt2800usb nightmare has any bearing on it.

---

### Post by Sedio on 2012-03-20
Sorry I forgot to mention that I am running Ad-hoc mode.  I must have restarted my computer and forgot to change the wireless card's mode before posting this.  Here is the new information.

```
brt@sedio:~$ ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_req=2 ttl=128 time=5.90 ms
64 bytes from 192.168.1.2: icmp_req=3 ttl=128 time=2.15 ms
64 bytes from 192.168.1.2: icmp_req=4 ttl=128 time=2.23 ms
64 bytes from 192.168.1.2: icmp_req=5 ttl=128 time=2.20 ms
^C
--- 192.168.1.2 ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4012ms
rtt min/avg/max/mdev = 2.155/3.126/5.906/1.605 ms
brt@sedio:~$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"Carver"  
          Mode:Ad-Hoc  Frequency:2.422 GHz  Cell: B6:4B:5D:29:3E:6E   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
brt@sedio:~$ 
```

I have another computer connected to the Ad-hoc here and ping it (i.e. the ping to 192.168.1.2) to show it has some connection.  I then run 'iwconfig' which still returns very limited data.  

You are correct that if I connect to a AP it will work correctly but not in Ad-hoc mode.  This worked fine in 11.04 when I was using the rt2x00sta driver.

---

### Post by chili555 on 2012-03-20
Perhaps the updated firmware will help. You seem pretty adept, so I'll assume you can back up the current firmware /lib/firmware/rt2870.bin, install this, unload and reload the driver and test.

If it doesn't help, I'll be happy to assist you to compile rt2870sta; it may or may not help.

---

### Post by Sedio on 2012-03-20
> **chili555 said:**
> You seem pretty adept, so I'll assume you can back up the current firmware /lib/firmware/rt2870.bin, install this, unload and reload the driver and test.

You over estimate my abilities!  I attempted to install the new firmware (with my understanding of how to) and it did not seem to work.  If you could point me in the right direction it would be appreciated.

---

### Post by chili555 on 2012-03-20
Back up the current firmware:```
sudo mv /lib/firmware/rt2870.bin /lib/firmware/rt2870.bak
```Download the file I attached to your Desktop; right-click it and select *Extract Here*. Now do:```
sudo cp Desktop/RT2870_Firmware_V22/rt2870.bin /lib/firmware
```Now unload and reload the driver so it grabs the new firmware:```
sudo modprobe -r rt2800usb
sudo modprobe rt2800usb
```Now see if /proc/net/wireless looks better. As I said, it may or may not help.

---

### Post by Sedio on 2012-03-21
Thanks for the help!  Unfortunately it does not work still.

I attempted to install ralinks official driver using the instructions found below.  It fails when I run 'make' with the following output.

[http://ubuntuforums.org/showthread.php?t=960642&highlight=link+quality]("http://ubuntuforums.org/showthread.php?t=960642&highlight=link+quality")

```
brt@sedio:~/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1$ make
make -C tools
make[1]: Entering directory `/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools/bin2h
cp -f os/linux/Makefile.6 /home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile
make -C /lib/modules/3.0.0-16-generic/build SUBDIRS=/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-16-generic'
  CC [M]  /home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52:2: error: implicit declaration of function ‘usb_buffer_alloc’ [-Werror=implicit-function-declaration]
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52:13: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:78:3: error: implicit declaration of function ‘usb_buffer_free’ [-Werror=implicit-function-declaration]
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:234:9: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:241:9: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:278:11: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:507:12: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62:20: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:566:13: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:596:12: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:610:12: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:628:13: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type [enabled by default]
/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
cc1: some warnings being treated as errors

make[2]: *** [/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/sedio/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-16-generic'
make: *** [LINUX] Error 2
brt@sedio:~/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1$ 
```

---

### Post by chili555 on 2012-03-21
I get the same thing when I try to compile it. I fear the older 2010 version is too old to compile against a 3.0.xx kernel. There is no newer version that I can find since development is now devoted to rt2800usb.

You could try the compat-wireless suite:```
sudo apt-get install linux-backports-modules-cw-3.2-oneiric-generic
sudo modprobe -r rt2800usb
sudo modprobe rt2800usb
```Beyond that, I am out of mojo/talent/ideas.

---

### Post by Sedio on 2012-03-21
Last attempt failed!  Damn my desire to update to the 11.10 version!

It looks like I will end up having to get another wireless card that has full support for wireless extensions in 11.10.  Do you have any suggestions off hand?  I need to find one that will be able to utilize the command 'iwspy' because I specifically need to find signal strength/noise level between all links within an Ad-hoc.

Thanks for all your help!

---

### Post by chili555 on 2012-03-21
> Do you have any suggestions off hand? None, sorry.

---

