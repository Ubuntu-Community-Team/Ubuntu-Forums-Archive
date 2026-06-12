---
title: "Lynksys WUSB600N.v2 don't work in 11.10 64biuts"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by miguelpires on 2012-02-08
Hello,
I need help. I try all the tuturioals i can find but i can put the thing to work. Can someone please try to help me step by step?
Best regard's
Miguel Pires

---

### Post by jonobr on 2012-02-08
I have not used it or done it myself,

but [these ]("http://stu.westga.edu/~cslappe1/My%20Website/Pages/Contact%20Info/Pages/News%20and%20Interests/index.html#Ubunt:%20WUSB600N%20Fix") instructions look pretty clear and concise?

> Ubunt: WUSB600N Fix

Charles Slappey
May 26, 2010
Wednesday: 4:26pm

So there are a ton of tutorials online about how to get the Linksys WUSB600N v2 model to work, but I'm a little curious why someone doesn't just post the files already modified online. It is not hard, but for noobs (and for me since I downloaded the wrong ranlink drivers twice) it would be nice to knock it down to 2 steps.

Also I know that an old way to fix it is to use the ndiswrapper fix, but I think that only works with v1 (not sure) plus it seems like it would be better to run my internet without the use of another program. (I don't even like using the linksys software on Windows... just seems to leave more room for something to screw up.)

So without further ado:
(See the Extended/ Noobish ed. below for more details.)

    Step 1: Download wusbfix and extract it.
    Step 2: cd to the folder in the terminal.
    Step 3: type commands:
      sudo make
      sudo make install
      sudo modprobe rt3572sta

Extended/ Noobish ed.

    Step 1: Download wusbfix and extract it to your desktop.   Double click to open file then drag and drop to desktop. Or  **_continued on website_**

---

### Post by fubofo on 2012-02-18
Tried the above, got the following errors:

```
kaipee@zoostorm-ubuntu:~/Downloads/wusbfix/wusbfix$ ls
chips             LICENSE ralink-firmware.txt  RT2870STACard.dat         tools
common            Makefile                     RT2870STA.dat
include           os                           sta
iwpriv_usage.txt  README_STA                   sta_ate_iwpriv_usage.txt
kaipee@zoostorm-ubuntu:~/Downloads/wusbfix/wusbfix$ sudo make
[sudo] password for kaipee: 
make -C tools
make[1]: Entering directory `/home/kaipee/Downloads/wusbfix/wusbfix/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/kaipee/Downloads/wusbfix/wusbfix/tools'
/home/kaipee/Downloads/wusbfix/wusbfix/tools/bin2h
cp -f os/linux/Makefile.6 /home/kaipee/Downloads/wusbfix/wusbfix/os/linux/Makefile
make -C /lib/modules/3.0.0-16-generic/build SUBDIRS=/home/kaipee/Downloads/wusbfix/wusbfix/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-16-generic'
  CC [M]  /home/kaipee/Downloads/wusbfix/wusbfix/os/linux/../../common/crypt_md5.o
In file included from /home/kaipee/Downloads/wusbfix/wusbfix/include/chip/rt2870.h:41:0,
                 from /home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp_chip.h:47,
                 from /home/kaipee/Downloads/wusbfix/wusbfix/include/rt_config.h:62,
                 from /home/kaipee/Downloads/wusbfix/wusbfix/os/linux/../../common/crypt_md5.c:28:
/home/kaipee/Downloads/wusbfix/wusbfix/include/chip/mac_usb.h:1:1: warning: multi-line comment [-Wcomment]
/home/kaipee/Downloads/wusbfix/wusbfix/include/chip/mac_usb.h:178:2: error: #endif without #if
In file included from /home/kaipee/Downloads/wusbfix/wusbfix/include/chip/rt35xx.h:43:0,
                 from /home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp_chip.h:54,
                 from /home/kaipee/Downloads/wusbfix/wusbfix/include/rt_config.h:62,
                 from /home/kaipee/Downloads/wusbfix/wusbfix/os/linux/../../common/crypt_md5.c:28:
/home/kaipee/Downloads/wusbfix/wusbfix/include/chip/mac_usb.h:1:1: warning: multi-line comment [-Wcomment]
/home/kaipee/Downloads/wusbfix/wusbfix/include/chip/mac_usb.h:178:2: error: #endif without #if
In file included from /home/kaipee/Downloads/wusbfix/wusbfix/include/rt_config.h:73:0,
                 from /home/kaipee/Downloads/wusbfix/wusbfix/os/linux/../../common/crypt_md5.c:28:
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:727:34: error: ‘NUM_OF_TX_RING’ undeclared here (not in a function)
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:1495:28: error: ‘HW_BEACON_MAX_COUNT’ undeclared here (not in a function)
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:1495:49: error: ‘HW_BEACON_OFFSET’ undeclared here (not in a function)
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:2259:2: error: unknown type name ‘RTMP_INF_TYPE’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:2398:2: error: unknown type name ‘RTMP_INF_TYPE’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:2423:2: error: unknown type name ‘HT_TX_CONTEXT’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:2457:2: error: unknown type name ‘RX_CONTEXT’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:2573:2: error: unknown type name ‘TXWI_STRUC’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:2584:2: error: unknown type name ‘TX_CONTEXT’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:2584:30: error: ‘BEACON_RING_SIZE’ undeclared here (not in a function)
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:2585:2: error: unknown type name ‘TX_CONTEXT’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:2586:2: error: unknown type name ‘TX_CONTEXT’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:2587:2: error: unknown type name ‘TX_CONTEXT’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:2894:2: error: unknown type name ‘RT28XX_RXD_STRUC’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:2895:2: error: unknown type name ‘PRXWI_STRUC’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:3712:6: error: unknown type name ‘INT_SOURCE_CSR_STRUC’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:3803:5: error: unknown type name ‘PTXWI_STRUC’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:3823:9: error: unknown type name ‘PTXWI_STRUC’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:3829:9: error: unknown type name ‘PTXWI_STRUC’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:3865:6: error: unknown type name ‘PRT28XX_RXD_STRUC’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:4543:5: error: unknown type name ‘PRT28XX_RXD_STRUC’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:5515:5: error: unknown type name ‘PRXWI_STRUC’
In file included from /home/kaipee/Downloads/wusbfix/wusbfix/include/rt_config.h:73:0,
                 from /home/kaipee/Downloads/wusbfix/wusbfix/os/linux/../../common/crypt_md5.c:28:
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:6433:5: error: unknown type name ‘PRXWI_STRUC’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:6437:7: error: unknown type name ‘PRT28XX_RXD_STRUC’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:6670:5: error: unknown type name ‘RTMP_INF_TYPE’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:6865:5: error: unknown type name ‘PRXWI_STRUC’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:6866:5: error: unknown type name ‘PRT28XX_RXD_STRUC’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:6871:5: error: unknown type name ‘PMGMT_STRUC’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:6893:5: error: unknown type name ‘PTXINFO_STRUC’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:7115:5: error: unknown type name ‘PTX_CONTEXT’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:7121:5: error: unknown type name ‘PHT_TX_CONTEXT’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:7128:5: error: unknown type name ‘PRX_CONTEXT’
/home/kaipee/Downloads/wusbfix/wusbfix/include/rtmp.h:7174:6: error: unknown type name ‘PRX_CONTEXT’
In file included from /home/kaipee/Downloads/wusbfix/wusbfix/include/rt_config.h:74:0,
                 from /home/kaipee/Downloads/wusbfix/wusbfix/os/linux/../../common/crypt_md5.c:28:
/home/kaipee/Downloads/wusbfix/wusbfix/include/ap.h:86:5: error: unknown type name ‘PRT28XX_RXD_STRUC’
make[2]: *** [/home/kaipee/Downloads/wusbfix/wusbfix/os/linux/../../common/crypt_md5.o] Error 1
make[1]: *** [_module_/home/kaipee/Downloads/wusbfix/wusbfix/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-16-generic'
make: *** [LINUX] Error 2
kaipee@zoostorm-ubuntu:~/Downloads/wusbfix/wusbfix$ sudo make install
make -C /home/kaipee/Downloads/wusbfix/wusbfix/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/kaipee/Downloads/wusbfix/wusbfix/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/kaipee/Downloads/wusbfix/wusbfix/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/
install -m 644 -c rt3572sta.ko /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 3.0.0-16-generic
make[1]: Leaving directory `/home/kaipee/Downloads/wusbfix/wusbfix/os/linux'
kaipee@zoostorm-ubuntu:~/Downloads/wusbfix/wusbfix$ sudo modprobe rt3572sta
FATAL: Error inserting rt3572sta (/lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/rt3572sta.ko): Invalid module format
```

---

### Post by fubofo on 2012-02-27
I managed to get this working perfectly.
Check my thread [here]("http://ubuntuforums.org/showthread.php?t=1929286") for noob-proof instructions (also left a copy / paste method at the end)

---

