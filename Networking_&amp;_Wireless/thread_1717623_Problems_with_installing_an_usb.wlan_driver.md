---
title: "Problems with installing an usb.wlan driver"
date: 2011-03-30
forum: Networking &amp; Wireless
---

### Post by mazingaro on 2011-03-30
Hi,

in [this thread]("http://ubuntuforums.org/showthread.php?t=1285828") is solved how to install drivers for the TENDA USB wireless stick by downloading&installing it directly from the terminal;
i have problems with installing the newest, the [RT5370 USB]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXhMekF6THpBeEwyUnZkMjVzYjJGa05qWXdPRGc0T0RZMU1pNWllakk5UFQweU1ERXhYekF5TWpWZlVsUTFNemN3WDFKVU5UTTNNbDlNYVc1MWVGOVRWRUZmVmpJdU5TNHdMakZmUkZCUExuUmhjZz09Qw%3D%3D") driver, which is also possible to download manually here [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) .

I have downloaded it on my /Desktop, but i have problems with installing it from the terminal.

Can somebody help me?

---

### Post by mikewhatever on 2011-03-30
I can try helping if you tell what the problem is.;)

---

### Post by mazingaro on 2011-03-30
The problem is that i am a newbie and i'm not able to install it,i have problems with extracting it from the terminal and installing it after, i was trying to configure it following the tips on the other topics, but it was a fail... :/
In general,  want to make my USB wireless stick work :)

---

### Post by mikewhatever on 2011-03-30
Extracting is easy, just right click the archive and select 'Extract here'. Then, go on with the installation, and as soon as you get an error, post it here.

---

### Post by mazingaro on 2011-03-30
i did it already, but my problem is that i don't know how to start the installation, cause there is not an "installer" in the extracted folder but files that i don't know hot to manage...
[http://img291.imageshack.us/img291/1231/driverp.jpg](http://img291.imageshack.us/img291/1231/driverp.jpg)

---

### Post by mikewhatever on 2011-03-30
Have you done step 3 yet? If so, open Applications->Accessories->Terminal and do the following:
```
sudo apt-get install build-essential

cd ~/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO

make
```

Let's explain the above a little. build-essential is the package that's usually needed to build stuff from source, so we are installing it, the second command moves you to the source code directory, and make will try and build the driver.

---

### Post by mazingaro on 2011-03-30
it ends with an error:
WARNING: modpost: missing MODULE_LICENSE() in /home/mazinga/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt5370sta.o
see include/linux/module.h for more information
  CC      /home/mazinga/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt5370sta.mod.o
  LD [M]  /home/mazinga/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt5370sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
cp -f /home/mazinga/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt5370sta.ko /tftpboot
cp: cannot create regular file `/tftpboot': Permission denied
make: *** [LINUX] Error 1
mazinga@mazinga:~/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$ 


:/

---

### Post by mikewhatever on 2011-03-30
Try 'sudo make' as the last command.

---

### Post by mazingaro on 2011-03-30
i did it, and it stops in a similar way, like this: 

Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/mazinga/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt5370sta.o
see include/linux/module.h for more information
  LD [M]  /home/mazinga/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt5370sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
cp -f /home/mazinga/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux/rt5370sta.ko /tftpboot
mazinga@mazinga:~/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$ ^C
mazinga@mazinga:~/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$

---

### Post by mikewhatever on 2011-03-30
Well, it is supposed to stop, but there is no error as before, which is good. Now, run **sudo make install**.

---

### Post by mazingaro on 2011-03-30
OK, i did it :D and now? (btw thanks a lot for your patience!!)

mazinga@mazinga:~/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$ sudo make install
make -C /home/mazinga/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux -f Makefile.6 install
make[1]: Entering directory `/home/mazinga/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/mazinga/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/
install -m 644 -c rt5370sta.ko /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/
/sbin/depmod -a 2.6.35-28-generic
make[1]: Leaving directory `/home/mazinga/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO/os/linux'
mazinga@mazinga:~/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$

---

### Post by mikewhatever on 2011-03-30
No worries, been where your are myself.
Let's continue:

```
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/

sudo apt-get install tofrodos

sudo fromdos /etc/Wireless/RT2870STA/RT2870STA.dat

sudo chmod +x /etc/Wireless/RT2870STA/RT2870STA.dat

sudo cp common/rt2870.bin /lib/firmware/
```

---

### Post by mazingaro on 2011-03-30
on the 3rd step of your last tip, it says:

sudo: dos2unix: command not found
mazinga@mazinga:~/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$ sudo dos2unix /etc/Wireless/RT2870STA/RT2870STA.dat

---

### Post by mikewhatever on 2011-03-30
Ah, 'unix2dos' seems to have changed to 'fromdos'. Changed above.

---

### Post by mazingaro on 2011-03-30
aha, the after changing it, i proceeded and it is like this now:
sudo fromdos /etc/Wireless/RT2870STA/RT2870STA.dat
[sudo] password for mazinga: 
mazinga@mazinga:~/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$ sudo chmod +x /etc/Wireless/RT2870STA/Rmazinga@mazinga:~/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$ sudo cp common/rt2870.bin /lib/firmware/

---

### Post by mikewhatever on 2011-03-30
Looks like it's all done, now try loading the module:
```
sudo modprobe rt5370sta
```

...then run **ifconfig** to see if a new interface is up.

---

### Post by mazingaro on 2011-03-30
it reports an error after modprobe:

sudo modprobe rt5370sta
FATAL: Error inserting rt5370sta (/lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/rt5370sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)
mazinga@mazinga:~/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$ sudo modprobe rt5370 sta

---

### Post by mikewhatever on 2011-03-30
Make sure there is no space in the module name. rt5370sta.

---

### Post by mazingaro on 2011-03-30
tryed again, it is the same... maybe if i try "sudo modprobe rt5372sta"?

---

### Post by mikewhatever on 2011-03-30
Sure, try rt5372sta.

---

### Post by mazingaro on 2011-03-30
it's the same :(

FATAL: Module rt5372sta not found.

---

### Post by mikewhatever on 2011-03-30
Hm..., let's see what dmesg has to say:
```
dmesg | tail -n20
```

---

### Post by mazingaro on 2011-03-30
it says this:

[12696.624623] rt5370sta: Unknown symbol usb_register_driver (err 0)
[12696.624920] rt5370sta: Unknown symbol usb_put_dev (err 0)
[12696.625048] rt5370sta: Unknown symbol usb_get_dev (err 0)
[12696.625261] rt5370sta: Unknown symbol usb_submit_urb (err 0)
[12696.625564] rt5370sta: Unknown symbol usb_free_coherent (err 0)
[12696.625843] rt5370sta: Unknown symbol usb_control_msg (err 0)
[12696.626205] rt5370sta: Unknown symbol usb_deregister (err 0)
[12696.626743] rt5370sta: Unknown symbol usb_kill_urb (err 0)
[12926.112600] rt5370sta: Unknown symbol usb_alloc_urb (err 0)
[12926.112749] rt5370sta: Unknown symbol usb_free_urb (err 0)
[12926.112955] rt5370sta: Unknown symbol usb_alloc_coherent (err 0)
[12926.113259] rt5370sta: Unknown symbol usb_register_driver (err 0)
[12926.113558] rt5370sta: Unknown symbol usb_put_dev (err 0)
[12926.113686] rt5370sta: Unknown symbol usb_get_dev (err 0)
[12926.113899] rt5370sta: Unknown symbol usb_submit_urb (err 0)
[12926.114219] rt5370sta: Unknown symbol usb_free_coherent (err 0)
[12926.125771] rt5370sta: Unknown symbol usb_control_msg (err 0)
[12926.126122] rt5370sta: Unknown symbol usb_deregister (err 0)
[12926.126632] rt5370sta: Unknown symbol usb_kill_urb (err 0)
[13117.117784] npviewer.bin[7253]: segfault at 418 ip 00000000f600dd36 sp 00000000ffa63838 error 6 in libflashplayer.so[f5da0000+b5f000]

---

### Post by mikewhatever on 2011-03-30
Not quite sure what to say to this really. Perhaps 'fromdos' wasn't needed, at least the README file in the source doesn't mention it.

```
sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/

[s]sudo apt-get install tofrodos[/s]

[s]sudo fromdos /etc/Wireless/RT2870STA/RT2870STA.dat[/s]

sudo chmod +x /etc/Wireless/RT2870STA/RT2870STA.dat

sudo cp common/rt2870.bin /lib/firmware/


```

and then 

```
sudo modprobe rt5370sta
```

---

### Post by mazingaro on 2011-03-30
so how do i proceed now?

the error remains...

mazinga@mazinga:~/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$ sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/
mazinga@mazinga:~/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$ sudo chmod +x /etc/Wireless/RT2870STA/RT2870STA.dat
mazinga@mazinga:~/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$ sudo cp common/rt2870.bin /lib/firmware/
mazinga@mazinga:~/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$ sudo modprobe rt5370sta
FATAL: Error inserting rt5370sta (/lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/rt5370sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)
mazinga@mazinga:~/Desktop/2011_0225_RT5370_RT5372_Linux_STA_V2.5.0.1_DPO$

---

### Post by mikewhatever on 2011-03-30
Looks like we are kind of stuck for now.:(
I'm gonna drop a line to [chili555]("http://ubuntuforums.org/member.php?u=35909"), he's much more of an expert then myself.

---

### Post by mazingaro on 2011-03-30
thanks a lot mike i really appreciate your help!
i've attached a new USB 2.0 pci card today, so maybe there is also a connection between this and the problem

---

### Post by mazingaro on 2011-03-30
I've retried with the older drivers and i got forward!!

it goes forward from "sudo modprobe" and then i ran also "ifconfig" and this is how it looks:

mazinga@mazinga:~/Desktop/2010_0223_RT3370_LinuxSTA_V2.3.0.0/MODULE$ sudo cp common/rt2870.bin /lib/firmware/
mazinga@mazinga:~/Desktop/2010_0223_RT3370_LinuxSTA_V2.3.0.0/MODULE$ sudo modprobe rt2870sta
mazinga@mazinga:~/Desktop/2010_0223_RT3370_LinuxSTA_V2.3.0.0/MODULE$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8d:6c:dc:46  
          inet addr:192.168.0.187  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fe6c:dc46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:150055 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134396 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:166384249 (166.3 MB)  TX bytes:23921363 (23.9 MB)
          Interrupt:22 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:592 errors:0 dropped:0 overruns:0 frame:0
          TX packets:592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46736 (46.7 KB)  TX bytes:46736 (46.7 KB)


maybe some idea how to finish it now, after that we passsed that error? :)

---

### Post by mikewhatever on 2011-03-30
Well, the original howto kind of brushes over it.

```

sudo ifconfig ra0 inet 192.168.0.33 up

iwconfig ra0

```

---

### Post by mazingaro on 2011-03-30
uf, and when i was expecting and end, i get this:

mazinga@mazinga:~/Desktop/2010_0223_RT3370_LinuxSTA_V2.3.0.0/MODULE$ sudo ifconfig ra0 inet 192-168.0.33 up
192-168.0.33: Unknown host
ifconfig: `--help' gives usage information.
mazinga@mazinga:~/Desktop/2010_0223_RT3370_LinuxSTA_V2.3.0.0/MODULE$

---

### Post by mikewhatever on 2011-03-30
...but why the dash, 192**-**168.0.33? it's supposed to be a dot, 192.168.0.33.

---

### Post by mazingaro on 2011-03-30
sorry, my mistake, i corrected it and it states another type of error/lack:

mazinga@mazinga:~/Desktop/2010_0223_RT3370_LinuxSTA_V2.3.0.0/MODULE$ sudo ifconfig ra0 inet 192.168.0.33 up
[sudo] password for mazinga: 
SIOCSIFADDR: No such device
ra0: ERROR while getting interface flags: No such device
ra0: ERROR while getting interface flags: No such device

---

### Post by mazingaro on 2011-03-31
Do you recomend to buy a new usb wifi stick? This one is Tenda w311Ma.

---

### Post by mikewhatever on 2011-03-31
No, at least not yet, cause we might get this one working.
Are you sure you've been compiling the right drivers?
Can you post the output of lsusb?

---

### Post by mazingaro on 2011-03-31
yes, i reyed also the ones that i got on the original device cd; it was tested on redhat, and that is why i tought that ubuntu will go as well :/
now in this moment, i don't have the usb here, i gave it to a friend which tries to install it on his pc.

i will have it back this days, then i'll post here a solution if he found it or the lsusb so you can help me again :) Ok? Thanks!

---

### Post by mazingaro on 2011-04-16
so, we were trying to do this, but it was a fail... so i have back the usb wireless and the only thing that i can think about starting from the beginning with trying to install this driver is to post here the read.me file in the cd of the gadget, it writes what has to be done, but it was tested in red hat and not ubuntu...

* README
*
* Ralink Tech Inc.
* 
* [http://www.ralinktech.com](http://www.ralinktech.com)
*

=======================================================================
ModelName:
===========
RT2870 Wireless Lan Linux Driver


=======================================================================
Driver lName:
===========
rt2870.o/rt2870.ko


=======================================================================
Supporting Kernel:
===================
linux kernel 2.4 and 2.6 series. 
Tested in Redhat 7.3 or later.


=======================================================================
Ralink Hardware:
===================
Ralink 802.11n Wireless LAN Card.


=======================================================================
Description:
=============
This is a linux device driver for Ralink RT2870 USB ABGN WLAN Card.


=======================================================================
Contents:
=============
Makefile            : Makefile
*.c                    : c files
*.h                    : header files


=======================================================================
Features:
==========
   This driver implements basic IEEE802.11. Infrastructure and adhoc mode with 
   open or shared or WPA-PSK or WPA2-PSK authentication method. 
   NONE, WEP, TKIP and AES encryption. 


=======================================================================
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
    
=======================================================================
CONFIGURATION:  
====================
RT2870 driver can be configured via following interfaces, 
i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file

i)  iwconfig comes with kernel.  
ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.
iii)modify configuration file "RT2870STA.dat" in /etc/Wireless/RT2870STA/RT2870STA.dat.
           
Configuration File : RT2870STA.dat
---------------------------------------
# Copy this file to /etc/Wireless/RT2870STA/RT2870STA.dat
# This file is a binary file and will be read on loading rt.o module.
#
# Use "vi RT2870STA.dat" to modify settings according to your need.
# 
# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure
# 2.) set Channel to "0" for auto-select on Infrastructure mode
# 3.) set SSID for connecting to your Accss-point.
# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"
# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"
# for more information refer to the Readme file.
# 
#The word of "Default" must not be removed
Default
CountryRegion=5
CountryRegionABand=7
CountryCode=
SSID=Dennis2860AP
NetworkType=Infra
WirelessMode=9
Channel=0
BeaconPeriod=100
TxPower=100
BGProtection=0
TxPreamble=0
RTSThreshold=2347
FragThreshold=2346
TxBurst=1
WmmCapable=0
AckPolicy=0;0;0;0
AuthMode=OPEN
EncrypType=NONE
WPAPSK=
DefaultKeyID=1
Key1Type=0
Key1Str=
Key2Type=0
Key2Str=
Key3Type=0
Key3Str=
Key4Type=0
Key4Str=
PSMode=CAM
FastRoaming=0
RoamThreshold=70
HT_RDG=1
HT_EXTCHA=0
HT_OpMode=1
HT_MpduDensity=4
HT_BW=1
HT_AutoBA=1
HT_BADecline=0
HT_AMSDU=0
HT_BAWinSize=64
HT_GI=1
HT_MCS=33
HT_MIMOPSMode=3
EthConvertMode=
EthCloneMac=
IEEE80211H=0
TGnWifiTest=0
WirelessEvent=0
MeshId=MESH
MeshAutoLink=1
MeshAuthMode=OPEN
MeshEncrypType=NONE
MeshWPAKEY=
MeshDefaultkey=1
MeshWEPKEY=
CarrierDetect=0

-----------------------------------------------
*NOTE:
    WMM parameters
            WmmCapable            Set it as 1 to turn on WMM Qos support                
            AckPolicy1~4        Ack policy which support normal Ack or no Ack
                                (AC_BK, AC_BE, AC_VI, AC_VO)        
    
    All WMM parameters do not support iwpriv command but ¡¥WmmCapable¡Š¡Š, 
    please store all parameter to RT2870STA.dat, and restart driver.     

-----------------------------------------------
syntax is 'Param'='Value' and describes below. 

@> CountryRegion=value                                 
    value
        0: use 1 ~ 11 Channel
        1: use 1 ~ 13 Channel
        2: use 10 ~ 11 Channel
        3: use 10 ~ 13 Channel
        4: use 14 Channel
        5: use 1 ~ 14 Channel
        6: use 3 ~ 9 Channel
        7: use 5 ~ 13 Channel
       31: use 1 ~ 14 Channel (ch1-11:active scan, ch12-14 passive scan)
                                                  
@> CountryRegionABand=value                                  
    value    
        0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel
        1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel
        2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel
        3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel
        4: use 149, 153, 157, 161, 165 Channel
        5: use 149, 153, 157, 161 Channel
        6: use 36, 40, 44, 48 Channel
        7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel
        8: use 52, 56, 60, 64 Channel
        9: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 132, 136, 140, 149, 153, 157, 161, 165 Channel
       10: use 36, 40, 44, 48, 149, 153, 157, 161, 165 Channel
       11: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 149, 153, 157, 161 Channel

@> CountryCode=value
    value
        AG, AR, AW, AU, AT, BS, BB, BM, BR, BE, BG, CA, KY, CL, CN, CO, CR, CY, CZ, DK, DO, EC, SV, FI, FR, DE, 
        GR, GU, GT, HT, HN, HK, HU, IS, IN, ID, IE, IL, IT, JP, JO, LV, LI, LT, LU, MY, MT, MA, MX, NL, NZ, NO,
        PE, PT, PL, RO, RU, SA, CS, SG, SK, SI, ZA, KR, ES, SE, CH, TW, TR, GB, UA, AE, US, VE
        "" => using default setting: 2.4 G - ch 1~11; 5G - ch 52~64, 100~140, 149~165
                                                           
@> SSID=value                    
    value
        0~z, 1~32 ascii characters.
                        
@> WirelessMode=value
    value    
        0: legacy 11b/g mixed 
        1: legacy 11B only 
        2: legacy 11A only         //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
        3: legacy 11a/b/g mixed     //Not support in RfIcType=1(id=RFIC_5225) and RfIcType=2(id=RFIC_5325)
        4: legacy 11G only
        5: 11ABGN mixed
        6: 11N only
        7: 11GN mixed
        8: 11AN mixed
        9: 11BGN mixed
       10: 11AGN mixed    
                     
@> Channel=value
    value
        depends on CountryRegion or CountryRegionABand
                        
@> BGProtection=value
    value
        0: Auto 
        1: Always on 
        2: Always off
                        
@> TxPreamble=value
      value
        0:Preamble Long
        1:Preamble Short 
        2:Auto
                        
@> RTSThreshold=value
    value
        1~2347                                                       
                                                               
@> FragThreshold=value
    value           
        256~2346
                        
@> TxBurst=value
    value
        0: Disable
        1: Enable

@> NetworkType=value                
    value 
        Infra: infrastructure mode
           Adhoc: adhoc mode
                                                                                                                                                                                                                      
@> AuthMode=value
    value
        OPEN         For open system    
        SHARED          For shared key system    
        WEPAUTO     Auto switch between OPEN and SHARED
        WPAPSK      For WPA pre-shared key  (Infra)
        WPA2PSK     For WPA2 pre-shared key (Infra)
        WPANONE        For WPA pre-shared key  (Adhoc)
        WPA         Use WPA-Supplicant
        WPA2        Use WPA-Supplicant

@> EncrypType=value
    value
        NONE        For AuthMode=OPEN                    
        WEP            For AuthMode=OPEN or AuthMode=SHARED 
        TKIP        For AuthMode=WPAPSK or WPA2PSK                    
        AES            For AuthMode=WPAPSK or WPA2PSK                     
        
@> DefaultKeyID=value
    value
        1~4

@> Key1=value
    Key2=value
    Key3=value
    Key4=value
    value
        10 or 26 hexadecimal characters eg: 012345678
        5 or 13 ascii characters eg: passd
    (usage : "iwpriv" only)     

@> Key1Type=vaule
    Key2Type=value
    Key3Type=vaule
    Key4Type=vaule
    value
        0   hexadecimal type
        1   assic type
    (usage : reading profile only)

@> Key1Str=value
    Key2Str=value
    Key3Str=vaule
    Key4Str=vaule
    value
        10 or 26 characters (key type=0)
        5 or 13 characters  (key type=1)
    (usage : reading profile only)    

@> WPAPSK=value                  
    value
        8~63 ASCII          or 
        64 HEX characters
                                                                                                                                                            
@> WmmCapable=value
    value
        0: Disable WMM
        1: Enable WMM
        
@> PSMode=value
    value
        CAM                Constantly Awake Mode
        Max_PSP            Max Power Savings
        Fast_PSP        Power Save Mode

@> FastRoaming=value
    value
        0                Disabled
        1                Enabled

@> RoamThreshold=value
    value
        Positive Interger(dBm)

@> HT_RDG=value
    value
        0                Disabled
        1                Enabled

@> HT_EXTCHA=value (Extended Channel Switch Announcement)
    value
        0                Below
        1                 Above

@> HT_OpMode=value
    value
        0                HT mixed format
        1                HT greenfield format

@> HT_MpduDensity=value
    value (based on 802.11n D2.0)
        0: no restriction
        1: 1/4 £gs
        2: 1/2 £gs
        3: 1 £gs
        4: 2 £gs
        5: 4 £gs
        6: 8 £gs
        7: 16 £gs

@> HT_BW=value
    value
        0                20MHz
        1                40MHz

@> HT_AutoBA=value
    value
        0                Disabled
        1                Enabled

@> HT_BADecline
    value
        0                Disabled
        1                Enabled <Reject BA request from AP>

@> HT_AMSDU=value
    value
        0                Disabled
        1                Enabled

@> HT_BAWinSize=value
    value
        1 ~ 64

@> HT_GI=value
    value
        0                long GI
        1                short GI

@> HT_MCS=value
    value
        0 ~ 15
        33: auto

@> HT_MIMOPSMode=value
    value (based on 802.11n D2.0)
        0                Static SM Power Save Mode
        1                Dynamic SM Power Save Mode
        2                Reserved
        3                SM enabled
    (not fully support yet)

@> EthConvertMode=value
    value
        dongle
        clone
        hybrid

@> EthCloneMac=value
    value
        xx:xx:xx:xx:xx:xx

@> IEEE80211H=value
    value
        0                Disabled
        1                Enabled

@> TGnWifiTest=value
    value
        0                Disabled
        1                Enabled

@> WirelessEvent=value
    value
        0                Disabled
        1                Enabled <send custom wireless event>
        
@> MeshId=value
    value
        Length 1~32 ascii characters

@> MeshAutoLink=value
    value
        0                Disabled
        1                Enabled

@> MeshAuthMode=value
    value
        OPEN         For open system    
        WPANONE        For WPA pre-shared key  (Adhoc)

@> MeshEncrypType=value
    value
        NONE        For MeshAuthMode=OPEN                    
        WEP            For MeshAuthMode=OPEN
        TKIP        For MeshAuthMode=WPANONE
        AES            For MeshAuthMode=WPANONE

@> MeshWPAKEY=value
    value
        8~63 ASCII          or 
        64 HEX characters

@> MeshDefaultkey=value
    value
        1~4

@> MeshWEPKEY=value
    value
        10 or 26 characters
        5 or 13 characters

@> CarrierDetect=value
    value
        0                Disabled
        1                Enabled

MORE INFORMATION
=================================================================================
If you want for rt2870 driver to auto-load at boot time:
A) choose ra0 for first RT2870 WLAN card, ra1 for second RT2870 WLAN card, etc.
   
B) create(edit) 'ifcfg-ra0' file in /etc/sysconfig/network-scripts/,      
   edit( or add the line) in /etc/modules.conf:
       alias ra0 rt2870sta
   
C) edit(create) the file /etc/sysconfig/network-scripts/ifcfg-ra0  
   DEVICE='ra0'
   ONBOOT='yes'     


NOTE:
   if you use dhcp, add this line too .
    BOOTPROTO='dhcp'

*D) To ease the Default Gateway setting, 
    add the line
    GATEWAY=x.x.x.x   
    in /etc/sysconfig/network
   
=======================================================================
Dongle/Clone Features:
======================
A) Dongle mode: 
       Provides a 1-to-N MAC address mapping mechanism such that more than one PC behind the STA 
       can transparently connect to the AP.

B) Clone mode:
    Provides a 1-to-1 MAC address mapping mechanism. 
    STA can use own MAC as SA MAC or 
            use user desired MAC as SA MAC or
            use source MAC of first packet coming from wired device as SA MAC.
    NOTE: In this mode, only the PC who own the specified MAC can connect to the AP.

 
C) Hybrid mode(Dongle+Clone):
    Provides a 1-to-N MAC address mapping mechanism such that more than one PC behind the STA 
       can transparently connect to the AP.
    STA can use own MAC as SA MAC or 
            use user desired MAC as SA MAC or
            use source MAC of first packet coming from wired device as SA MAC.

D) Please refer to "Config STA to link as dongle mode..." in iwpriv_usage.txt for releated commands.

---

### Post by Joshua Kinney on 2011-04-25
Anyone had any luck with this yet? I am having the same problem.

---

### Post by mazingaro on 2011-05-03
we're probably doomed to buy a new card.....:(

---

### Post by lesser on 2011-06-01
I'm afraid so. I've got the same trouble with a Conceptronic C150RU (148f:3370). Seems I got a little but further, have a look [here]("http://ubuntuforums.org/showthread.php?t=1748136").

---

### Post by vaderj on 2011-09-18
So I have yet to fine a legit forum where anyone has gotten these ralink drivers working.  Its more than a little suspect that they have "rt2870" plastered everywhere when the model is allegedly 5370.  I have a feeling that linux drivers in reality just do not exist for this chipset.  I've screwed around with this damn thing for about 4 days now, completely defining my entire network in that .dat in /etc, as described in the broken english readme and can't even get the light inside the adapter to peap. I don't think I've tried anything but 10.04, but have tried compiling against atleast 3 different kernel versions.  of course it works just dandy in server 2008r2. And I absolutely have build-essential and the linux headers for each kern I compiled against, even compiles with nothing but a hand full of warnings that don't look bad. And yes, I make clean before every make.  I think that they juat are scamming on linux support.
Has anyone, anywhere gotten a rt5370 to work in any linux distro/kernal ver?

---

### Post by nik_nah on 2011-10-09
> **vaderj said:**
> Has anyone, anywhere gotten a rt5370 to work in any linux distro/kernal ver?

Yes, I did had it working on my old hard disk which broke down yesterday, I have to install it again on a new disk.

I downloaded the version from rt2x00.serialmonkey.com's git and copied the .config file from the normal linux sources over to the downloaded kernel & enabled the RT53xx bits.  Then booted from the new kernel, don't just install the module you'll need to use the same kernel.  Unfortunately, their git is broken at the moment. :(

I have a little usb rt5370, small one not even 1cm long.  Got it for <$10 from ebay, probably spent $$$$ of my time fiddling around with the stupid thing.

---

