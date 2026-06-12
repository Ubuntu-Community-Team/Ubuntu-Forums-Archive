---
title: "Broadcom/UNR 9.10/Acer Aspire One AOD250-1116"
date: 2010-02-05
forum: Networking &amp; Wireless
---

### Post by berktt on 2010-02-05
Ok, I have filled out the details as described for filling a wireless ticket. Here's the problem. I just installed UNR on my netbook, and I'm pretty new to Linux in general. When I first installed it I could not get wireless to work, and it took me a few hours to get it to the working stage, but even now it is very problematic.I have installed the necessary drivers, (not the Windows drivers, the Linux drivers) and when I turn off my computer and start it up again, the wireless does not work again. So, I go into system settings and go to Hardware Drivers, and for my wireless card, it says This driver is installed but not currently active. Also at this stage I cannot turn my wireless card on through the wireless switch on the netbook. However, after I remove and than activate the drivers, I can get it working again by using the wireless switch. Although, sometimes the computer completely freezes after it connects to a wireless network ( I lose the GUI, it shows the command prompt but frozen, and my caps lock indicator is blinking). When I do get it working though, it's mostly fine and if I just go to standby or suspend, and come back, it will still be working. It stops working when I restart the computer.

C'mon guys I'm new to Linux and I really want to make the switch. What happened to all this talk about I hear about Linux being a better and more robust OS :D
[B]

1 ) Machine Brand and Model (PC/Laptop)[/B]:
     Code:
     **Acer Aspire One AOD250-1116** 
**2 ) Wireless Brand, Model and Wireless Chipset:**
     Code:
     01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


 **3 ) check interface:**
     Code:

     $ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
         

**4 ) Check for modules:**

Sorry I'm not sure which one was for wireless, I'm guess wl?
     Code:
     $ lsmod

nls_iso8859_1           3740  0 
nls_cp437               5372  0 
vfat                   10716  0 
fat                    51452  1 vfat
usb_storage            52576  0 
lib80211_crypt_tkip     8636  0 
wl                   1272936  0 
lib80211                6432  2 lib80211_crypt_tkip,wl
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
iptable_filter          3100  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ip_tables              11692  1 iptable_filter
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
x_tables               16544  1 ip_tables
uvcvideo               59080  0 
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56500  0 
soundcore               7264  1 snd
serio_raw               5280  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
led_class               4096  0 
ndiswrapper           185532  0 
atl1c                  30880  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221320  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp


**5 ) Kernel boot messages**
     Code:
     $ dmesg | grep "eth2"
[12698.178538] udev: renamed network interface eth1 to eth2
[12698.186958] eth2: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9
[12698.279966] udev: renamed network interface eth1 to eth2
[12708.520062] eth2: no IPv6 routers present
[13478.849092] eth2: no IPv6 routers present
[13534.208047] eth2: no IPv6 routers present
[14187.480084] eth2: no IPv6 routers present


 **6 ) Network configuration**
     Code:
     $ sudo lshw -C network

  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth2
       version: 01
       serial: 00:26:5e:74:75:06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.10.91.9 ip=172.16.12.23 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:57100000-57103fff


**7 ) Scan for networks:**
     
I'm not sure why it can't scan, I can connect to the wireless right now.

Code:
     $ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      Interface doesn't support scanning.




**8 ) Ubuntu Version: **
     Code:
     $ lsb_release -d

Description:    Ubuntu 9.10


**9 ) Kernel/architecture (including 32 vs. 64 bit): **
     Code:
     $ uname -mr

2.6.31-19-generic i686


**10 ) Restarting the network:**
     Code:
     $ sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                                                                       Ignoring unknown interface eth2=eth2.

---

### Post by berktt on 2010-02-06
bumping this thread... I thought problems with this family of Broadcom chips were common, I'm hoping someone has a solution for me.

---

### Post by johnzbesko on 2010-02-06
Hmm, I have the same problem of no wireless on an AOD250-1165. It used to work fine. My kernel is 2.6.31-16-generic i686

What got updated in the last few days that may have caused this?

---

### Post by berktt on 2010-02-08
What I've done now is install the Linux drivers supplied by Broadcom, and I've carefully followed the instructions given in the readme file. Now, it's still more or less the same problem. When I restart the computer, the wireless card doesn't work again, and I basically have to retype the last commands to get them working again. Here are those two lines of code:

```
# modprobe lib80211
# insmod wl.ko

```

I guess a quick and dirty fix for this would be to get the computer to do this automatically on startup, which I'm not entirely sure how to do, but I'm hoping still that someone can tell me the proper way to get my drivers working.

---

### Post by johnzbesko on 2010-02-09
My work-around for this problem is to boot a previous kernel, specifically, 2.6.31-15-generic i686 (or -14.)

I'll try the modprobe commands on -16 and -19 versions tonight.

---

### Post by berktt on 2010-02-10
Hi john, like I have mentioned, I am new to the Linux world in general. :) So I was wondering how you boot to a previous kernel in UNR. I have an updated kernel, but on my desktop after GRUB loads I have the choice to choose a kernel version. This is not the case with UNR, it just boots up (I have it updated)

> **johnzbesko said:**
> My work-around for this problem is to boot a previous kernel, specifically, 2.6.31-15-generic i686 (or -14.)

I'll try the modprobe commands on -16 and -19 versions tonight.

---

### Post by Megaptera on 2010-02-10
Hi,
This may interest you? Quote from link below:
"Usually installing the proprietary Broadcom wireless driver in Ubuntu is handled with couple mouse clicks by the Hardware Drivers (aka jockey-gtk). But Ubuntu 9.10 Karmic Koala has shipped with a bug that makes jockey unable to recognize the card and install the driver. No worries, the fix is incredibly easy and only requires a wired internet connection."

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

I've used it on laptop not Dell Mini - hope it's of help?

---

### Post by tractor on 2010-02-13
This fix worked perfectly for an Acer Aspire 1 netbook with Ubuntu 9.10 (not remix). Before the fix, you could see the wireless networks, but not connect. After installing the driver through synaptic, it connected immediately. Thank you so much!!!!!!!

---

### Post by Megaptera on 2010-02-14
You're welcome ... glad it worked!

---

### Post by fidolip on 2010-03-19
I don't really have anything new to say, just wanted to thank you Megaptera for pointing me in the right direction - my AAOD250 finally sees and connects to wireless networks with UNR onboadr!:] Cheers!

---

