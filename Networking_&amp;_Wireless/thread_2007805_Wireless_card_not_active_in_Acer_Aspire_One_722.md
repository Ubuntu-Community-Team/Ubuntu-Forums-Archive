---
title: "Wireless card not active in Acer Aspire One 722"
date: 2012-06-21
forum: Networking &amp; Wireless
---

### Post by Xtensity on 2012-06-21
I recently got this netbook with the intent of having Ubuntu on it.... 12.04 was far too laggy, even in classic mode.

in 10.04 the network card would not work.

Switched to 11.04 and same problem..

I've read over 100 forum topics on the issue regarding this particular netbook and each seemed to have different solutions that didn't work for mine in any way.

I have even tried following, for hours, the ubuntu wireless troubling shooting guide... no dice. 

What now? If I can't get wireless working(the FN+f3 doesn't turn it on either), then my purpose for the netbook has been defeated.

---

### Post by chili555 on 2012-06-21
Please open a terminal and run and post:```
lspci -nn | grep 0280
rfkill list all
lsmod | grep acer
```Thanks.

---

### Post by Xtensity on 2012-06-21
```
scott@ubuntu:~$ lspci -nn | grep 0280
07:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
scott@ubuntu:~$ rfkill list all
scott@ubuntu:~$ lsmod | grep acer
scott@ubuntu:~$ 

```


Yes I realize the last 2 commands did nothing....and not a clue why not.

---

### Post by chili555 on 2012-06-21
Now let us see:```
sudo modprobe ath9k
dmesg | grep ath9k
iwconfig
```Thanks.

---

### Post by Xtensity on 2012-06-21
```

scott@ubuntu:~$ sudo modprobe ath9k
[sudo] password for scott: 
scott@ubuntu:~$ dmesg | grep ath9k
[   20.224821] ath9k 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   20.224849] ath9k 0000:07:00.0: setting latency timer to 64
[   20.233197] ath9k 0000:07:00.0: Failed to initialize device
[   20.233796] ath9k 0000:07:00.0: PCI INT A disabled
[   20.233812] ath9k: probe of 0000:07:00.0 failed with error -22
scott@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

scott@ubuntu:~$ 


```

modprobe did nothing

---

### Post by chili555 on 2012-06-21
> [   20.233197] ath9k 0000:07:00.0: Failed to initialize device
[   20.233796] ath9k 0000:07:00.0: PCI INT A disabled
[   20.233812] ath9k: probe of 0000:07:00.0 failed with error -22
Looks ugly, doesn't it? It is sometimes the case that there is a conflict in AAO 722s between the wireless and the ethernet. Please see here: [http://bernaerts.dyndns.org/linux/202-ubuntu-acer-ao722](http://bernaerts.dyndns.org/linux/202-ubuntu-acer-ao722)

You may need to look around in the BIOS. Please let us know what you see. 

I am off for the evening; see you tomorrow.

---

### Post by Xtensity on 2012-06-21
I tried all those bios modifications before and they had no effect on the problem.

The wireless works fine in Win 7 and in 12.04(which is too laggy for me to run).


What could be causing the conflict?

Is there a way I could disable the ethernet before ubuntu boots so that the wireless can boot? There is no options in the bios to separate the Ethernet and Wireless...

---

### Post by chili555 on 2012-06-22
Please try another step:```
sudo modprobe -r ath9k
sudo modprobe ath9k btcoex_enable=1
dmesg | grep wlan
```Any improvement? If so, we'll write a one-line file and make it persistent.

---

### Post by Xtensity on 2012-06-22
scott@ubuntu:~$ sudo modprobe -r ath9k
scott@ubuntu:~$ sudo modprobe ath9k btcoex_enable=1
scott@ubuntu:~$ dmesg | grep wlan




Yeah...no responses. No sign of any changes.

---

### Post by Xtensity on 2012-06-22
I also recently flashed my bios to the latest version to see if it would open up any new options in the bios, but it did not.

I did notice what seems to be a conflict with the Atheros Ethernet before the boot menu even comes up and before I can choose an Operating system. This did not happen before I installed Ubuntu.

It might be worthy to note that I installed ubuntu within Windows 7, though I'm not sure if that would cause any errors. 

Think I might have luck putting the Ubuntu ISO onto a USB(due to lack of CDROM on netbook) and install Ubuntu separate from Windows 7?

---

### Post by chili555 on 2012-06-22
> The wireless works fine in Win 7 **and in 12.04**(which is too laggy for me to run).Did you have trouble with Unity? Did you try Gnome Shell? Have you tried any of the more lightweight versions such as lubuntu or xubuntu?

If it works perfectly in 12.04, I suggest you find a version you like and install it.

---

### Post by chili555 on 2012-06-22
> Think I might have luck putting the Ubuntu ISO onto a USB(due to lack of CDROM on netbook) and install Ubuntu separate from Windows 7?Probably. You can certainly try running the USB in a live session to see if the wireless is working and if you like Gnome Shell. If so, I'd install it.

---

### Post by Xtensity on 2012-06-22
Ubuntu Classic with Gnome Shell in 12.04 Lags to hell and sometimes doesn't comeback. 11.04 on the other hand works great with classic. Unity is partially okay on 11.04, but not fast enough for me to have the patience to use it.

---

### Post by chili555 on 2012-06-22
> and sometimes doesn't comeback.Meaning what? Is this with the correct video drivers installed? 

Please let me see:```
modinfo ath9k | grep 0032
```Thanks.

---

### Post by Xtensity on 2012-06-22
scott@ubuntu:~$ modinfo ath9k | grep 0032
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
scott@ubuntu:~$ 





---

What I meant was that it will lag so hard that it'll get to a point where it doesn't unlag. It just freezes after lagging so badly. Freezing where I can move the mouse with ease but nothing responds to clicks

But 11.04 Classic is very smooth

---

### Post by cortman on 2012-06-22
Have you tried setting Network Boot first in the BIOS options? That solved a wireless connectivity/freezing up issue for me with my Aspire One 722.

---

### Post by Xtensity on 2012-06-22
> **cortman said:**
> Have you tried setting Network Boot first in the BIOS options? That solved a wireless connectivity/freezing up issue for me with my Aspire One 722.

That was one of the first thing I tried

funny thing is, instead of just saying Network Boot, like it does in every picture I see. It says Network Boot: Atheros Boot Controller....or maybe agent, controller or agent

---

### Post by cortman on 2012-06-22
> **Xtensity said:**
> That was one of the first thing I tried

funny thing is, instead of just saying Network Boot, like it does in every picture I see. It says Network Boot: Atheros Boot Controller....or maybe agent, controller or agent

That makes sense- if it is enabled you should get an error message at every startup saying something about "PXE not detected". You're getting that at boot?

---

### Post by Xtensity on 2012-06-22
> **cortman said:**
> That makes sense- if it is enabled you should get an error message at every startup saying something about "PXE not detected". You're getting that at boot?

Yes exactly. What do you think about the matter?

---

### Post by cortman on 2012-06-22
> **Xtensity said:**
> Yes exactly. What do you think about the matter?

I think that I know about that much and no more, and that you have a wireless guru (chili555) helping you out, so listen carefully to him. :) Good luck!

---

### Post by chili555 on 2012-06-23
Thanks for the kind comments, cortman. 

So you can confirm that Network Boot is first in the boot order and Network Boot is enabled, correct? If you are getting this:> [   20.233197] ath9k 0000:07:00.0: Failed to initialize device
[   20.233796] ath9k 0000:07:00.0: PCI INT A disabled
[   20.233812] ath9k: probe of 0000:07:00.0 failed with error -22...And the interface won't start, connect, etc. then I'm fairly sure it's a problem with the driver version in 11.10. If you are unwilling to try any version of 12.04, including the more lightweight versions such as lubuntu or xubuntu, then I suggest you open Synaptic package manager and look for and install linux-backports-modules-cw-3.1-oneiric-generic. There are updated drivers in that package. Reboot and let us see again:```
dmesg | grep ath9k
```

---

### Post by Xtensity on 2012-06-23
I am using 11.04

So that driver does not exist in synaptic.

I'll install linux-backports-modules-cw-3.0.0-natty-generic

Which seems to be the latest version. I'll post results in a second

---

### Post by Xtensity on 2012-06-23
scott@ubuntu:~$ dmesg | grep ath9k
[   18.700415] ath9k 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.700444] ath9k 0000:07:00.0: setting latency timer to 64
[   18.708660] ath9k 0000:07:00.0: Failed to initialize device
[   18.709258] ath9k 0000:07:00.0: PCI INT A disabled
[   18.709273] ath9k: probe of 0000:07:00.0 failed with error -22
[  339.020104] Modules linked in: binfmt_misc parport_pc ppdev snd_hda_codec_hdmi joydev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm ath9k radeon snd_seq_midi mac80211 snd_rawmidi snd_seq_midi_event ath9k_common ath9k_hw snd_seq ath ttm uvcvideo snd_timer drm_kms_helper snd_seq_device drm snd cfg80211 psmouse videodev k10temp v4l2_compat_ioctl32 serio_raw sp5100_tco soundcore i2c_algo_bit i2c_piix4 snd_page_alloc video lp parport usb_storage uas atl1c ahci libahci
scott@ubuntu:~$

---

### Post by chili555 on 2012-06-23
I have no other suggestions aside from 12.04 in a lightweight version. Sorry.

---

### Post by Xtensity on 2012-06-23
Would you be kind enough to briefly explain the differences between the various versions of 12.04. I always saw them in the installation menu but never knew what the big differences were.

---

### Post by chili555 on 2012-06-23
From here: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)> *  Kubuntu (Ubuntu with KDE Plasma instead of Unity)

  *  Edubuntu (Ubuntu focused on education)

  *  Xubuntu (Ubuntu with XFCE instead of Unity)

  *  UbuntuStudio (Ubuntu focused on multimedia production)

  *  Mythbuntu (Xubuntu-based XFCE4 desktop OS with MythTV installed)

  *  Lubuntu (Ubuntu with LXDE instead of Unity) 

Regular Ubuntu comes with the windowing manager Unity. It's slick but it uses a lot of resources, particularly in graphics. That's exactly the weakest spot in a netbook. The load is reduced quite a bit with Gnome Shell.

Xubuntu runs XFCE; Lubuntu runs LXDE; they both are quite lightweight and use fewer resources. I run Lubuntu on an old Celeron (!!) running 756Mb of RAM that's available in a guest bedroom for visitors. It runs perfectly well.

Of course, the best way to find out is to download either to a USB and run a live session. Does it lag? Does the wireless work? If everything works well, I'd install it.

Perhaps cortman will chime in here.

---

### Post by cortman on 2012-06-23
I run [Bodhi Linux]("http://bodhilinux.com/") on my netbook- it runs ridiculously well. Never had an issue with the wireless.
Bodhi 1.4 (current release) is based on Ubuntu LTS for extra stability, but uses the latest available kernel for Ubuntu (3.0, I believe). The 2.0 release, scheduled for July, will be based on Ubuntu 12.04 LTS.
I would echo chili555's advice to use a lightweight version of 12.04- Lubuntu or Bodhi. Good luck!

---

### Post by Xtensity on 2012-06-23
I'm going to try one more time with 12.04 Ubuntu in classic mode with Gnome Shell and see how it runs. Mainly because I've fallen in love with the general ubuntu desktop and I don't really want to get accustomed to other versions unless I have to. 

I'll post back if there are any unsolveable issues.

---

### Post by chili555 on 2012-06-23
> I've fallen in love with the general ubuntu desktop and I don't really want to get accustomed to other versions unless I have to. Perfectly reasonable. To quote Mrs. Chili in this regard, "I like what I like." She likes Gnome Shell.

If it lags, you might open a terminal and run:```
top
```See what process(es) are eating all your CPU cycles and troubleshoot from there. Get out of *top* with q.

---

### Post by Makcum on 2012-06-27
I have just ordered the same wifi card for my AO722.
The original one for me is BCM4313 - which as a lot of complains too.
Will test it when it comes and let you know if wont forget :-D

try to use "ndiswrapper" for now. I remember I had to use it before for atheros wifi cards. - not sure if it is still alive and supported though.

---

### Post by cortman on 2012-06-27
> **Makcum said:**
> I have just ordered the same wifi card for my AO722.
The original one for me is BCM4313 - which as a lot of complains too.
Will test it when it comes and let you know if wont forget :-D

try to use "ndiswrapper" for now. I remember I had to use it before for atheros wifi cards. - not sure if it is still alive and supported though.

Atheros cards should use the ath9 or ath5 driver that is included with the kernel- it should be pretty safe.

---

