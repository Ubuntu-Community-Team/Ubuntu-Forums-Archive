---
title: "a better version for wireless?"
date: 2010-04-23
forum: Networking &amp; Wireless
---

### Post by roundhead on 2010-04-23
Since I am new to Ubuntu and am not very learned with computers, do you think there is a better version for wireless laptop users than 9.10? should I try installing a previous version in hopes of being able to use the wireless with less difficulty? 
thanks

---

### Post by snowpine on 2010-04-23
I would not recommend "downgrading" to an older release; hardware support gets better and better with each new release in my experience. :)

Without knowing what kind of wireless card you have or what kind of "difficulty" you're experiencing, all I can do is point you towards the Ubuntu documentation: [https://help.ubuntu.com/community/NetworkDevices](https://help.ubuntu.com/community/NetworkDevices)

If you want to post back with more details, I will try my best to help you. :)

---

### Post by bkratz on 2010-04-23
> **roundhead said:**
> Since I am new to Ubuntu and am not very learned with computers, do you think there is a better version for wireless laptop users than 9.10? should I try installing a previous version in hopes of being able to use the wireless with less difficulty? 
thanks

You might check this out (Linux Mint) , it is Debian based and is compatible with the Ubuntu repositories.  I have been wanting to try it myself. Anyway, they claim it focuses on, quote "There is a strong focus on making things work out of the box (WiFi cards drivers in the file system, multimedia support, screen resolution, etc)".

[http://www.linuxmint.com/about.php](http://www.linuxmint.com/about.php)

---

### Post by roundhead on 2010-04-23
Thanks. Thanks again Bkratz you have been a big help. Snowpine, I will post all the info as soon as possible. I may hold out a few days and try the latest version that will be released on the 26th.

---

### Post by bkratz on 2010-04-23
> **roundhead said:**
> Thanks. Thanks again Bkratz you have been a big help. Snowpine, I will post all the info as soon as possible. I may hold out a few days and try the latest version that will be released on the 26th.

well I just download it, and also the 10.04 release candidate--just have to decide which to try first!

---

### Post by Ayuthia on 2010-04-23
roundhead - I am catching up on your posts.  From what I can tell, you have a Broadcom wired and wireless hardware.  The wired card is most likely causing some problems for you.  Can you try the following when you have a chance (I am assuming that you still have the Broadcom STA driver installed):
```

sudo modprobe -r b43 b44 ssb wl ndiswrapper
sudo modprobe wl
sudo modprobe b44
sudo iwlist scan

```
The first command is going to remove the wired and wireless drivers that can be associated with your two cards.  The next command is going to load the Broadcom STA driver (wl) and the one after that is going load your wired card back.  The last command is going to scan for wireless sites.

If this works, we will need to add a command to help get your wireless and wired cards loaded in the correct order.  The ssb module is most likely capturing your wireless card before the wl driver is loaded so the wl driver is not able to work properly.

I hope this helps.

By the way, I would stick with 9.10 instead of going back to previous versions.  It seems to work the best so far with the Broadcom cards.

---

### Post by roundhead on 2010-04-23
Thanks
I am unable to connect with the cable now as well and so am using a desktop. I no longer see any of the eth notices I used to see. I have done alot of tinkering around just trying to learn as I go. I may try to reinstall 9.10 and start over from scratch. If I can get the internet to work, I will try your suggestions. Thanks Ayuthia
Stewart

---

### Post by roundhead on 2010-04-23
regarding the drivers...I did try to install the BCM 4312 for linux. my problem was extracting it and adding the correct .inf file. I read somewhere that I may have to do this in a windows system and then transfer the file with a thumb drive. currently the driver is showing up under hardware drivers Broadcom STA wireless driver but is not activated. I cannot activate the driver for some reason. then under windows wireless drivers I see bcmwl5 which I am not sure where it came from maybe the ndiswrapper. but it says that there is no hardware present. I dont know.

---

### Post by Ayuthia on 2010-04-23
> **roundhead said:**
> Thanks
I am unable to connect with the cable now as well and so am using a desktop. I no longer see any of the eth notices I used to see. I have done alot of tinkering around just trying to learn as I go. I may try to reinstall 9.10 and start over from scratch. If I can get the internet to work, I will try your suggestions. Thanks Ayuthia
Stewart

If you are able to see information from:
```
lshw -C network
```
you might try the commands that I posted.  There is a chance that the wired card will come back and you might be able to connect with it.

If you see the bcmwl5 information in the windows wireless drivers application, then that is the Windows driver that you are trying to use with NDISwrapper.  If it shows no hardware present, it could mean that the driver that you are using does not want to work with your wireless card.  Was that the driver that came with your computer or did you find it from another site?

---

### Post by snowpine on 2010-04-23
> **roundhead said:**
> regarding the drivers...I did try to install the BCM 4312 for linux. my problem was extracting it and adding the correct .inf file. I read somewhere that I may have to do this in a windows system and then transfer the file with a thumb drive. currently the driver is showing up under hardware drivers Broadcom STA wireless driver but is not activated. I cannot activate the driver for some reason. then under windows wireless drivers I see bcmwl5 which I am not sure where it came from maybe the ndiswrapper. but it says that there is no hardware present. I dont know.

Ah yes, Broadcom wireless... I have one of those too! :)

You don't need to use a Windows driver. Broadcom has a native linux driver that works very well. Shouldn't take you more than 5 minutes to get it working following this guide:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

If you can connect to wired internet, this is the easiest way:

> Step 1. Install the b43/STA hybrid drivers/firmware from the restricted repository using the Synaptic Package Manager and search for the bcmwl-kernel-source package and install or in a terminal use the aptitude or apt-get commands:

~$ sudo aptitude update
~$ sudo aptitude install bcmwl-kernel-source

Step 2. Under the desktop menu System > Administration > Hardware Drivers, the drivers can be activated for use.

Note: A computer restart may be required before using the wifi card. 

---

### Post by roundhead on 2010-04-24
I reinstalled 9.10 and here is the readout so far after following Snowpine's advice
stewart@stewart-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:57:0e:36  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe57:e36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21655515 (21.6 MB)  TX bytes:875147 (875.1 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

stewart@stewart-laptop:~$ LSHW -c NETWORK
LSHW: command not found
stewart@stewart-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:57:0e:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.101 latency=64 multicast=yes
       resources: irq:21 memory:c0300000-c0301fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:96:38:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by bkratz on 2010-04-24
You no longer appear to have the sta driver (wl) associated with the card like you did.  Did you do what Ayuthia suggested in post #6 earlier? Which steps (they seem  to be numbered ) in the  Snowpine's reference post did you do?  Could you also post the output of 

lsmod

(LSMOD in lowercase) so we can see what modules are loaded?

---

### Post by roundhead on 2010-04-25
stewart@stewart-laptop:~$ **lsmod**
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
arc4                    1660  2 
snd_mixer_oss          16028  1 snd_pcm_oss
ecb                     2524  2 
iptable_filter          3100  0 
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ip_tables              11692  1 iptable_filter
b43                   122136  0 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
x_tables               16544  1 ip_tables
mac80211              181236  1 b43
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
joydev                 10272  0 
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
cfg80211               93052  2 b43,mac80211
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56180  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
dell_wmi                2564  0 
sdhci_pci               7100  0 
ricoh_mmc               3676  0 
sdhci                  17472  1 sdhci_pci
i2c_piix4               9932  0 
serio_raw               5280  0 
k8temp                  4188  0 
dell_laptop             8128  0 
shpchp                 32272  0 
led_class               4096  2 b43,sdhci
lp                      8964  0 
dcdbas                  7292  1 dell_laptop
parport                35340  2 ppdev,lp
b44                    28684  0 
mii                     5212  1 b44
video                  19380  0 
output                  2780  1 video
ssb                    35300  2 b43,b44
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp
stewart@stewart-laptop:~$

---

### Post by roundhead on 2010-04-25
Good News. I am currently online with wireless. I followed Snowpines advice. all I did was basically reinstall 9.10 and install the B43 wireless driver. I am not sure if that was the right one since Snowpine said to install the "b43/STA hybrid drivers/firmwware" on the driver page from the admin area, both drivers were showing up. I wasnt sure which to install so I did the b43 rather than the STA, then I did everything Snowpine said from post #10. but then one thing I did not realize is that if you click on the wireless signal area at the top, a box will drop down and you are able to connect with the wireless. Since I am new to Ubuntu, I did not know to do that. In windows the wireless signal just appears, unless it is disabled. anyway it is working now and I am glad. hopefully others will read this post and get the help that they need. Thanks Ayuthia, Snowpine, and Bkratz.

---

### Post by bkratz on 2010-04-25
> **roundhead said:**
> Good News. I am currently online with wireless. I followed Snowpines advice. all I did was basically reinstall 9.10 and install the B43 wireless driver. I am not sure if that was the right one since Snowpine said to install the "b43/STA hybrid drivers/firmwware" on the driver page from the admin area, both drivers were showing up. I wasnt sure which to install so I did the b43 rather than the STA, then I did everything Snowpine said from post #10. but then one thing I did not realize is that if you click on the wireless signal area at the top, a box will drop down and you are able to connect with the wireless. Since I am new to Ubuntu, I did not know to do that. In windows the wireless signal just appears, unless it is disabled. anyway it is working now and I am glad. hopefully others will read this post and get the help that they need. Thanks Ayuthia, Snowpine, and Bkratz.




Glad to you got it!  I was just getting ready to start typing a new message and stopped when I saw this, it has been a long fight right, but in the end it is worth it. Enjoy.

---

### Post by leorolla on 2010-06-21
Could you run
```
sudo lshw -C network
```
and post here?

I don't think you're running the b43 driver.
(As of Karmic this device was not b43-supported.)

It would help others in similar situations.

---

