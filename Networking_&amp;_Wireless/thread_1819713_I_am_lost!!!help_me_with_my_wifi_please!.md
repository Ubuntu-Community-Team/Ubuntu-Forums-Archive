---
title: "I am lost!!!help me with my wifi please!"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by ineedwifihelp on 2011-08-06
I have 10.04 lucid installed on a presario 2800t laptop(it's old and hasn't got  much memory).  Anyway, now I can't get my Netgear WNA1100 to work. I know it works right away with 11.04, but that isn't really an option for me. It's too slow on this old computer. 
  So can anyone help me get it working with 10.04?

---

### Post by wildmanne39 on 2011-08-06
Hi, please run these commands in a terminal 
```
lsusb
```
```
sudo lshw -C network
```
```
iwconfig
```
```
lsmod
```
```
rfkill list all
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by ineedwifihelp on 2011-08-06
Ok, I did that and it still does not work.

---

### Post by nrundy on 2011-08-06
> **ineedwifihelp said:**
> Ok, I did that and it still does not work.

reread wildmanne39 post. he's trying to help you.

---

### Post by ineedwifihelp on 2011-08-06
Sorry I misread that. Here you gome@angcomputer:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bb2:6098 Ambit Microsystems Corp. USB Cable Modem
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9030 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
me@angcomputer:~$ sudo lshw -C network
[sudo] password for me: 
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       version: 42
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=66 maxlatency=56 mingnt=8
       resources: memory:40100000-40100fff ioport:2000(size=64)
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 00:19:7e:83:8b:89
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=24.230.172.101 link=yes multicast=yes
me@aingcomputer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

me@angcomputer:~$ lsmod
Module                  Size  Used by
nls_utf8                1069  1 
isofs                  29250  1 
binfmt_misc             6587  1 
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
snd_mixer_oss          13746  1 snd_pcm_oss
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 30784  0 
snd_timer              19098  2 snd_pcm,snd_seq
radeon                678735  3 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    50103  1 radeon
snd                    54244  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cdc_ether               3541  0 
drm_kms_helper         29329  1 radeon
joydev                  8740  0 
usbnet                 14943  1 cdc_ether
soundcore               6620  1 snd
yenta_socket           20408  1 
drm                   162377  5 radeon,ttm,drm_kms_helper
intel_agp              24375  1 
i2c_algo_bit            5028  1 radeon
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
ppdev                   5259  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
agpgart                31724  3 ttm,drm,intel_agp
irda                  186844  0 
shpchp                 28835  0 
psmouse                63677  0 
crc_ccitt               1339  1 irda
parport_pc             25962  1 
lp                      7028  0 
serio_raw               3978  0 
parport                32635  3 ppdev,parport_pc,lp
e100                   28211  0 
mii                     4381  2 usbnet,e100
floppy                 53016  0 
me@angcomputer:~$ rfkill list all
me@angcomputer:~$ rfkill list all
me@angcomputer:~$ rfkill list all

---

### Post by ineedwifihelp on 2011-08-06
Thanks

---

### Post by wildmanne39 on 2011-08-06
Hi, here is a link to directions to get your wireless to work, please do what post two says to do.
[http://ubuntuforums.org/showthread.php?t=1663232&highlight=Netgear+WNA1100](http://ubuntuforums.org/showthread.php?t=1663232&highlight=Netgear+WNA1100)
Thank you

---

### Post by wildmanne39 on 2011-08-06
Hi, run these commands please.
```
lsmod | grep ath9k
```
```
iwconfig
```
```
nm-tool
```
```
dmesg | grep wlan0
```
```
sudo iwlist scan
```
```
dmesg | grep ath9k
```
and post the results here.
Thank you.

---

### Post by ineedwifihelp on 2011-08-06
ath9k_htc              38860  0 
mac80211              237348  1 ath9k_htc
led_class               2864  1 ath9k_htc
ath9k_common            2551  1 ath9k_htc
ath9k_hw              276057  2 ath9k_htc,ath9k_common
ath                    13021  2 ath9k_htc,ath9k_hw
cfg80211              142116  3 ath9k_htc,mac80211,ath
compat_firmware_class     6168  1 ath9k_htc

---

### Post by ineedwifihelp on 2011-08-06
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by ineedwifihelp on 2011-08-06
NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            cdc_ether
  State:             connected
  Default:           yes
  HW Address:        00:19:7E:83:8B:89

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         24.230.172.101
    Prefix:          23 (255.255.254.0)
    Gateway:         24.230.172.1

    DNS:             24.220.0.10
    DNS:             24.220.0.11

---

### Post by ineedwifihelp on 2011-08-06
dmesg | grep wlan0 this command didn't do anything when I hit enter

---

### Post by ineedwifihelp on 2011-08-06
o        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by ineedwifihelp on 2011-08-06
[   22.846108] usb 1-1: ath9k_htc: Firmware - ar9271.fw not found
[   22.846215] ath9k_hif_usb: probe of 1-1:1.0 failed with error -22
[   22.846266] usbcore: registered new interface driver ath9k_hif_usb

---

### Post by wildmanne39 on 2011-08-06
Hi, give me a few minutes I am researching the problem.
Thank you

---

### Post by chili555 on 2011-08-06
> Firmware - ar9271.fw not foundCan you do:```
sudo apt-get install linux-firmware
```I believe the firmware is in there. Post back if you install it, reboot and the wireless doesn't start.

---

### Post by wildmanne39 on 2011-08-06
Thank you chili!!! that is what I was researching, looking for the firmware.

---

### Post by chili555 on 2011-08-06
Not sure it's in *linux-firmware* in 10.04. We may need to send it.

Edit: Here ya go! Can you handle it from here, Wild Man?

---

### Post by nm_geo on 2011-08-06
Hello everyone..
I have been out of pocket for a few days..

First I checked my 10.04 linux-firmware 
it does not have the ar9271.fw  

Then I found this link

[http://linuxwireless.org/en/users/Drivers/ath9k_htc#Firmware](http://linuxwireless.org/en/users/Drivers/ath9k_htc#Firmware)

Maybe it will help.

Over And Out

---

### Post by ineedwifihelp on 2011-08-06
sudo apt-get install linux-firmware
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by wildmanne39 on 2011-08-06
@nm_geo Thank you for the information and the link.

@ineedwifihelp Chili555 gave you the file you need, he added to his previous post.

Give me a few minutes to see how you install the firmware.
Thank you

---

### Post by wildmanne39 on 2011-08-06
Hi, Chili, yes I should be able too.
Thank you!!

---

### Post by ineedwifihelp on 2011-08-06
ok I downloaded the file.
Thank you everyone for helping me sort this thing out.

---

### Post by mpvick on 2011-08-06
hey i did the strait link to router and i did the camand but it came up as not found also i am on linux agin

---

### Post by wildmanne39 on 2011-08-06
@mpvick, you have posted in the wrong thread, I will reply to you in the other thread.
Thank you

---

### Post by chili555 on 2011-08-06
> **ineedwifihelp said:**
> ok I downloaded the file.
Thank you everyone for helping me sort this thing out.Wherever the file went when you downloaded it, drag and drop it to your desktop. Right-click it and select Extract Here. Now, in a terminal, do:```
sudo cp Desktop/ar9271.fw /lib/firmware
sudo chown root:root /lib/firmware/ar9271.fw
```Reboot and tell us if your wireless is working. If not, please let us see:```
dmesg | grep ath
```

---

### Post by ineedwifihelp on 2011-08-06
[    2.115862] device-mapper: multipath: version 1.1.0 loaded
[    2.115867] device-mapper: multipath round-robin: version 1.0.0 loaded
[   22.922625] usb 1-1: ath9k_htc: Firmware - ar9271.fw not found
[   22.922698] ath9k_hif_usb: probe of 1-1:1.0 failed with error -22
[   22.922749] usbcore: registered new interface driver ath9k_hif_usb

---

### Post by ineedwifihelp on 2011-08-06
This is a lot of work for wifi.....

---

### Post by chili555 on 2011-08-06
Let's see where it went. Please post:```
ls -al /lib/firmware | grep ar92
```

---

### Post by ineedwifihelp on 2011-08-06
rw-r--r--  1 root root   51312 2011-08-06 20:26 ar9271.fw

---

### Post by ineedwifihelp on 2011-08-06
I have no idea what we are doing here.

---

### Post by chili555 on 2011-08-06
Please post:```
modinfo ath9k_htc | grep firm
```Maybe it actually wants other firmware also. It's hard for me to diagnose since I don't have 10.04 or the device.

---

### Post by ineedwifihelp on 2011-08-06
firmware:       ar9271.fw
firmware:       ar7010_1_1.fw
firmware:       ar7010.fw
depends:        ath9k_hw,compat_firmware_class,mac80211,led-class,ath9k_common,ath,cfg80211

---

### Post by chili555 on 2011-08-06
Here is a zip file called ath.zip. Download it to your desktop. Right-click it and select Extract Here. Now, in a terminal, do:```
sudo cp Desktop/ath_firmware/* /lib/firmware
sudo chown root:root /lib/firmware/ar7*
```Verify that it all arrived:```
ls -al /lib/firmware | grep -e ar9 -e ar7
```It ought to read just like this:> -rw-r--r--  1 root root   70624 2010-11-18 16:20 ar7010_1_1.fw
-rw-r--r--  1 root root   70624 2010-11-18 16:20 ar7010.fw
-rw-r--r--  1 root root   51312 2011-03-03 10:03 ar9271.fwReboot and say a prayer.

It's hard for me not to type: sudo chown root:beer /lib/firmware/ar7*

---

### Post by ineedwifihelp on 2011-08-06
-rw-r--r--  1 root root   70624 2011-08-06 20:58 ar7010_1_1.fw
-rw-r--r--  1 root root   70624 2011-08-06 20:58 ar7010.fw
-rw-r--r--  1 root root   83968 2010-12-14 10:25 ar9170-1.fw
-rw-r--r--  1 root root    3508 2010-12-14 10:25 ar9170-2.fw
-rw-r--r--  1 root root   15960 2010-12-14 10:26 ar9170.fw
-rw-r--r--  1 root root   51312 2011-08-06 20:26 ar9271.fw

---

### Post by chili555 on 2011-08-06
> **ineedwifihelp said:**
> -rw-r--r--  1 root root   70624 2011-08-06 20:58 ar7010_1_1.fw
-rw-r--r--  1 root root   70624 2011-08-06 20:58 ar7010.fw
-rw-r--r--  1 root root   83968 2010-12-14 10:25 ar9170-1.fw
-rw-r--r--  1 root root    3508 2010-12-14 10:25 ar9170-2.fw
-rw-r--r--  1 root root   15960 2010-12-14 10:26 ar9170.fw
-rw-r--r--  1 root root   51312 2011-08-06 20:26 ar9271.fwIt looks like you have everything and more! Did you reboot? Did you say a prayer?

---

### Post by ineedwifihelp on 2011-08-06
preying now

---

### Post by ineedwifihelp on 2011-08-06
I am on wifi !!!! THANK YOU ALL VERY MUCH!!!!! I never would have done it without you.

---

### Post by chili555 on 2011-08-06
Glad it's working! Have fun. Would you please use thread tools at the top and Mark Solved?

---

### Post by wildmanne39 on 2011-08-06
Hi, I am glad it is working.

Thank you Doctor chili, it was above my pay grade.

---

### Post by ineedwifihelp on 2011-08-07
I was lost on it for sure. You guys were great!!! I am loving the wifi. I'm going to mark this one as solved.

---

