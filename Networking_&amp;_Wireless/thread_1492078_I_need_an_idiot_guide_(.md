---
title: "I need an idiot guide :("
date: 2010-05-24
forum: Networking &amp; Wireless
---

### Post by myscus on 2010-05-24
Hi, being a total newbie to linux I have Ubuntu that works fine when plugged in by ethernet & a USB wireless adapter (Edimax EW-7711USn) that just doesn't seem to want to work... (works fine in windows so I know it's not the adapter...)

I'm presuming that I need to install the driver that came on the disk?

But! Looking at the driver install instructions they may as well be written in a different language... I don't understand one bit of what it wants me to do (or maybe I have missed a script that will automate the process?)

If one of you fine guys could translate the below into some less geeky form of language I would truely appreciate it (bearing in mind I have zero knowledge of Linux)

I'm going to presume that this lot makes some sense to someone ?

Thanks for looking :)

=========
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
    ** Build for being controlled by NetworkManager
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
    ** Build for being controlled by WpaSupplicant with Ralink Custom Event
       Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
       command: #./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make                                    # compile driver source code

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


](*,)](*,)](*,)](*,)

---

### Post by pdc on 2010-05-25
the other option is buy an OOTB wireless stick

post #7 larry finger gives the specs for the Netgear WG111V2

[http://forums.opensuse.org/get-help-here/wireless/437852-usb-wireless-device-works-ootb.html](http://forums.opensuse.org/get-help-here/wireless/437852-usb-wireless-device-works-ootb.html)

otherwise it is hard for a newcomer to linux 

eg

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1476321](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1476321)

the rt3090 is also a problem .......

this post that is ongoing

[http://ubuntuforums.org/showthread.php?t=1482382](http://ubuntuforums.org/showthread.php?t=1482382)

offers some answers in recent posts #8 and #9

---

### Post by chili555 on 2010-05-25
The driver rt2870sta is already built in to the kernel. Please open a terminal and do:```
sudo modprobe rt2870sta
iwconfig
```Do you have a wireless interface, wlan0 perhaps? Can you click the Network Manager icon, see your network and connect? If not, please run:```
dmesg | grep -i rt2
```You can copy and paste the output from the terminal into a text document (Applications > Accessories > gedit) and transfer it on a USB key if you don't have internet access on the computer in question.

I reject the term 'idiot.' You are new as all of us were at some time.

---

### Post by linuxonbute on 2010-05-25
> **chili555 said:**
> 

I reject the term 'idiot.' You are new as all of us were at some time.

I agree. When anyone wants to learn about any subject with any depth to it then that's great.
Sometimes it can be difficult ( I should know I still find some of it hard after years ) The main thing is that each time someone gives some advice if you don't understand some of it then just say what does xxxxxx mean?
That way we can all help each other grow in knowledge and so benefit us all.
Surely that's what it's all about isn't it.:P

---

### Post by chili555 on 2010-05-25
> Surely that's what it's all about isn't it.Absolutely.

I try as well as I can to explain clearly when a new user says that he is new. I sometimes fail but I never mind a new user asking for clearer steps.

---

### Post by myscus on 2010-05-25
> **pdc said:**
> the other option is buy an OOTB wireless stick

My stick was sold as supporting Linux (OOTB) :(

> **chili555 said:**
> The driver rt2870sta is already built in to the kernel. Please open a terminal and do:```
sudo modprobe rt2870sta
iwconfig
```Do you have a wireless interface, wlan0 perhaps? Can you click the Network Manager icon, see your network and connect? If not, please run:```
dmesg | grep -i rt2
```You can copy and paste the output from the terminal into a text document (Applications > Accessories > gedit) and transfer it on a USB key if you don't have internet access on the computer in question.

I reject the term 'idiot.' You are new as all of us were at some time.

That's really great for taking a look at my problems, I've pasted below what you asked....

graham@graham-laptop:~$ sudo modprobe rt2870sta
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.conf.save, it will be ignored in a future release.


graham@graham-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan4     IEEE 802.11bgn  Mode:Ad-Hoc  Frequency:2.412 GHz  
          Cell: Not-Associated   Tx-Power=5 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster1  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"SKY35320"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


graham@graham-laptop:~$ dmesg | grep -i rt2
[   19.567048] Registered led device: rt2800usb-phy0::radio
[   19.567072] Registered led device: rt2800usb-phy0::assoc
[   19.567097] Registered led device: rt2800usb-phy0::quality
[   19.567515] usbcore: registered new interface driver rt2800usb
[   19.568492] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   19.573506] usbcore: registered new interface driver rt2870
[   19.579644] Error: Driver 'rt2870' is already registered, aborting...
[   19.579649] usbcore: error -16 registering interface     driver rt2870
[   19.637019] rt2800usb 1-7:1.0: firmware: requesting rt2870.bin
graham@graham-laptop:~$ 

If it helps, it is a dell laptop with built in wireless (disabled in BIOS) & using the USB wifi adapter in my post above. If I enable the built in wireless then it works, I know the obvious answer is to use the laptops wifi but I have to get this USB adapter working on another PC & am using my laptop as a dual boot 'scratch pad' to see any issues first...

---

### Post by chili555 on 2010-05-25
Let's have a look at:```
lsmod | grep rt2
lsusb
```It looks like two modules are grabbing this device at the same time. Also, I notice this:> wlan4 IEEE 802.11bgn [COLOR="Red"]Mode:Ad-Hoc [/COLOR]Frequency:2.412 GHz
Cell: Not-Associated Tx-Power=5 dBm
Retry long limit:7 RTS thrff Fragment thrffWhat happens if we do:```
sudo iwconfig wlan4 mode managed
sudo iwlist wlan4 scan
```If you get scan returns, then your card is working correctly.

---

### Post by myscus on 2010-05-26
> **chili555 said:**
> Let's have a look at:```
lsmod | grep rt2
lsusb
```It looks like two modules are grabbing this device at the same time. Also, I notice this:What happens if we do:```
sudo iwconfig wlan4 mode managed
sudo iwlist wlan4 scan
```If you get scan returns, then your card is working correctly.

graham@graham-laptop:~$ lsmod | grep rt2
rt2870sta             488820  0 
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
input_polldev           3716  1 rt2x00lib
mac80211              181140  4 iwl3945,iwlcore,rt2x00usb,rt2x00lib
crc_ccitt               1852  1 rt2800usb
led_class               4096  4 iwl3945,iwlcore,rt2x00lib,sdhci
cfg80211               93052  4 iwl3945,iwlcore,rt2x00lib,mac80211



graham@graham-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 3538:0042 Power Quotient International Co., Ltd Cool Drive U339 Flash Disk
Bus 001 Device 002: ID 7392:7711  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


graham@graham-laptop:~$ sudo iwconfig wlan4 mode managed
[sudo] password for graham: 
graham@graham-laptop:~$ 


graham@graham-laptop:~$ sudo iwlist wlan4 scan
wlan4     Interface doesn't support scanning : Network is down

On Windows it is possible to use device manager to see what is happening/not happening with hardware, I presume that Ubuntu has not got a similar facility?

---

### Post by chili555 on 2010-05-26
> $ lsmod | grep rt2
rt2870sta 488820 0
rt2800usb 37372 0
rt2x00usb 11548 1 rt2800usb
rt2x00lib 29756 2 rt2800usb,rt2x00usb
input_polldev 3716 1 rt2x00lib
mac80211 181140 4 iwl3945,iwlcore,rt2x00usb,rt2x00lib
crc_ccitt 1852 1 rt2800usb
led_class 4096 4 iwl3945,iwlcore,rt2x00lib,sdhci
cfg80211 93052 4 iwl3945,iwlcore,rt2x00lib,mac80211Wow! That's a lot of drivers for your card; some of them are conflicting and fighting. Let's ban some of them. Please open the terminal and do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor gedit will open and you will add three lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proffread carefully, save and close gedit. Now reboot. Only rt2870sta should now be driving your device. Is it working correctly? If not, open the terminal and post:```
dmesg | grep -i RT2
```Thanks.

---

### Post by myscus on 2010-05-26
Still no luck :(

graham@graham-laptop:~$ dmesg | grep -i RT2
[   18.433705] Registered led device: rt2800usb-phy0::radio
[   18.433728] Registered led device: rt2800usb-phy0::assoc
[   18.433751] Registered led device: rt2800usb-phy0::quality
[   18.444558] usbcore: registered new interface driver rt2800usb
[   18.445546] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   18.450440] usbcore: registered new interface driver rt2870
[   18.458804] Error: Driver 'rt2870' is already registered, aborting...
[   18.458809] usbcore: error -16 registering interface     driver rt2870

---

### Post by chili555 on 2010-05-26
> usbcore: registered new interface driver rt2800usbIf rt2800usb is still loading, either you didn't reboot or you didn't add the lines to *blacklist* correctly. Please let me see:```
cat /etc/modprobe.d/blacklist.conf | tail -n5
```Thanks.

---

### Post by myscus on 2010-05-27
> **chili555 said:**
> If rt2800usb is still loading, either you didn't reboot or you didn't add the lines to *blacklist* correctly. Please let me see:```
cat /etc/modprobe.d/blacklist.conf | tail -n5
```Thanks.

graham@graham-laptop:~$ cat /etc/modprobe.d/blacklist.conf | tail -5
blacklist amd76x_edac
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

I'm glad that you understand all of this, I was lost about 1/2 a page ago ;)

I presume that the blacklist is OK? - what else could be the issue?

---

### Post by chili555 on 2010-05-27
> I presume that the blacklist is OK?It looks fine. Did you reboot after you made these changes? May I see:> cat /etc/modules
lsmodThanks.

---

### Post by myscus on 2010-05-28
graham@graham-laptop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
graham@graham-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
usb_storage            52768  1 
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
iwl3945                77372  0 
snd_hda_codec_idt      59876  1 
rt2870sta             488820  0 
iwlcore               112796  1 iwl3945
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
arc4                    1660  4 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
ecb                     2524  4 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
input_polldev           3716  1 rt2x00lib
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              181140  4 iwl3945,iwlcore,rt2x00usb,rt2x00lib
dell_wmi                2564  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
crc_ccitt               1852  1 rt2800usb
dell_laptop             8128  0 
dcdbas                  7292  1 dell_laptop
ricoh_mmc               3676  0 
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
led_class               4096  4 iwl3945,iwlcore,rt2x00lib,sdhci
psmouse                57332  0 
serio_raw               5280  0 
cfg80211               93052  4 iwl3945,iwlcore,rt2x00lib,mac80211
soundcore               7264  1 snd
lp                      8964  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
b44                    28652  0 
ssb                    35524  1 b44
mii                     5212  1 b44
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
video                  19380  1 i915
output                  2780  1 video
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp
graham@graham-laptop:~$ 


Whilst I don't profess to understand the above - I presume the above is a list of loaded modules? - would I be correct in saying that the line 'rt2800usb 37372  0' should read 1 as the last digit rather than 0 ?

Yes, I had rebooted the computer after changes were made.

---

### Post by chili555 on 2010-05-28
> I presume the above is a list of loaded modules?Correct.> would I be correct in saying that the line 'rt2800usb 37372 0' should read 1 as the last digit rather than 0 ?Not necessarily. The important detail is that it and its henchmen, rt2x00 et al are there at all, despite being properly blacklisted as well as *not* being explicitly loaded in */etc/modules*. The important issue is that rt2800usb and rt2870sta conflict and fight. 

Let's try the opposite approach. Please amend your blacklist file as outlined abobe and remove the rt2800usb lines and add rt2870sta.```
--- snip ---
blacklist amd76x_edac

blacklist rt2870sta
```Reboot and tell us how it's working now.

---

### Post by myscus on 2010-05-28
Still no luck :(

When editing the blacklist.conf file I wasn't sure if you meant to delete all the previous added lines & add blacklist rt2870sta or just delete the rt2800usb line & add...

I tried both ways just to be sure...

...I'm starting to wonder how this is so difficult if Ubuntu is supposed to carry the drivers for the Wifi adapter. Is it just a poor choice of adapters?

---

### Post by chili555 on 2010-05-28
May I see:```
lsmod | grep rt2
dmesg | grep -i RT2
```My intention with respect to your blacklist file was to remove:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```And to add:```
blacklist rt2870sta
```And then to reboot.

---

### Post by myscus on 2010-05-29
graham@graham-laptop:~$ lsmod | grep rt2
rt2800usb              37372  0 
rt2x00usb              11548  1 rt2800usb
rt2x00lib              29756  2 rt2800usb,rt2x00usb
input_polldev           3716  1 rt2x00lib
mac80211              181140  4 iwl3945,iwlcore,rt2x00usb,rt2x00lib
led_class               4096  4 iwl3945,iwlcore,rt2x00lib,sdhci
crc_ccitt               1852  1 rt2800usb
cfg80211               93052  4 iwl3945,iwlcore,rt2x00lib,mac80211


graham@graham-laptop:~$ dmesg | grep -i RT2
[   18.823704] Registered led device: rt2800usb-phy0::radio
[   18.823728] Registered led device: rt2800usb-phy0::assoc
[   18.823752] Registered led device: rt2800usb-phy0::quality
[   18.835853] usbcore: registered new interface driver rt2800usb
[   18.842006] usbcore: registered new interface driver rt2870

---

### Post by chili555 on 2010-05-29
Now you have the rt2800usb group loading and not rt2870sta. That's good. Does this say Managed or Ad Hoc?```
iwconfig wlan4
```If it's Ad Hoc, please do:```
sudo iwconfig wlan4 mode managed
```When you click the Network Manager icon, do you see networks? Can you connect?

---

### Post by myscus on 2010-06-04
Hi chili555,

Looks like my problem is that when the onboard wireless is disabled in the BIOS then also my USB adapter gets disabled too. If I turn on my onboard wireless then my adapter suddenly wants to play. It shows me no connections but then again it puts me into the position of having to fight against wlan0 (Wlan0 is fine & shows connections).

This is really not a place that a Ubuntu novice needs/wants to be...

In my frustration I have purchased another USB adapter that just works (I tried a few of my friends first). My reasoning is as follows:
I needed to set this up on a PC that didn't have internet access (ethernet connection not really a possibility) and, whilst I am genuinely thankful for your help & time, I do not feel confident enough to transfer the help & information that you have gave onto another PC.

But, all well that ends well, my PC is connected now & hopefully I will be able to learn a little more about Ubuntu in the process.

Again, many thanks for your invaluable help :)

---

