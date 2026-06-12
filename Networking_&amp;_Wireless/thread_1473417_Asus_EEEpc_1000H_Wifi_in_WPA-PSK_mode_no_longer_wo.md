---
title: "Asus EEEpc 1000H Wifi in WPA-PSK mode no longer works"
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by wkcchampion on 2010-05-05
Hello.
I have an Asus EEEpc 1000H netbook with both Ubuntu and WinXp.
I just updated from Ubuntu 9.1 to 10.04 and I can no longer connect to my home WiFi!

I have a Netgear router and the network is WPA-PSK password protected. All other devices can perfectly connect. The netbook can under WinXp and could with Ubuntu 9.1. Now, with the 10.04, it keeps asking for the password but never connects. Obviously I triple checked the password and there's no chance of a mistype error.

Thanks for the help!

---

### Post by GSF1200S on 2010-05-05
> **wkcchampion said:**
> Hello.
I have an Asus EEEpc 1000H netbook with both Ubuntu and WinXp.
I just updated from Ubuntu 9.1 to 10.04 and I can no longer connect to my home WiFi!

I have a Netgear router and the network is WPA-PSK password protected. All other devices can perfectly connect. The netbook can under WinXp and could with Ubuntu 9.1. Now, with the 10.04, it keeps asking for the password but never connects. Obviously I triple checked the password and there's no chance of a mistype error.

Thanks for the help!

I cant see any good reason why you should have this problem. Can you momentarily plug it into your router via ethernet and install wicd?
```
sudo apt-get install wicd
```
That issue, unless im mistaken, sounds like an issue with the upgrade that left the network manager unusable. Wicd is another type of network manager that works for many people. Also, can you post the results of:
```
lspci
```
and
```
lsmod
```
so that we can get an idea what wireless chipset you are using?

I have an Asus 1005HA-P using the default network manager and I have no issues, although I wiped XP off of it and did a fresh install of 10.04 (SO much faster). Good luck :)

---

### Post by wkcchampion on 2010-05-05
Ok I wrote teh first "install wicd" in the Terminal.
I have no idea at all what that command means. I think it installed something, apparently it worked.

Results of "lspci" and "lsmod"

pregnosplatter@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
pregnosplatter@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  4 
uvcvideo               56990  0 
psmouse                63245  0 
drm_kms_helper         29297  1 i915
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24177  2 i915
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
drm                   162471  5 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 intel_agp,drm
rt2860sta             481561  0 
eeepc_laptop           12847  0 
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
atl1e                  28018  0

---

### Post by int on 2010-05-05
Exist one regression in the kernel 2.6.32 Wifi drivers of almost all EEEpcs (RaLink RT2860)

You have to comment the bug report here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093?comments=all)



One simple solution and safe, is to install the (ubuntu 2.6.33 kernel)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/)

And run the 2.6.33 kernel until the new kernel with the fix be released...

---

### Post by wkcchampion on 2010-05-05
> **int said:**
> Exist one regression in wifi of almost all EEEpcs

You have to comment the bug report here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/496093?comments=all)



One simple solution and safe, is to install the (ubuntu 2.6.33 kernel)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.33.3-lucid/")

And run the 2.6.33 kernel until the new kernel with the fix be released...

ouh this is interesting. I'll install that Kernel and post back ok?

---

### Post by wkcchampion on 2010-05-05
ok, I've installed that Kernel and IT WORKS NOW!!!!! Greeat!!!! Thank you :)

What shall I do about that bugtracker?

Ah btw, the Kernel I had before was the .32 (previous)

---

### Post by int on 2010-05-05
> **wkcchampion said:**
> ok, I've installed that Kernel and IT WORKS NOW!!!!! Greeat!!!! Thank you :)

What shall I do about that bugtracker?

Ah btw, the Kernel I had before was the .32 (previous)

You should go to the bugtracker and selected the options that this bug also affects you.

---

### Post by wkcchampion on 2010-05-05
> **int said:**
> You should go to the bugtracker and selected the options that this bug also affects you.

Posted on Launchpad too

---

### Post by Sven6210 on 2010-05-07
If your WiFi chipset is the Ralink RT2860 you can try the following manual:

[FONT=Verdana, sans-serif]http://ubuntuforums.org/showthread.php?p=9255730
[/FONT]

---

### Post by alwayslurking on 2010-10-14
Just hit this when disabling WEP on my wireless router. Installing the backports package mentioned in the launchpad report resolved this problem for me, without changing kernel level or rebooting.

```

sudo aptitude install linux-backports-modules-wireless-lucid-generic
sudo rmmod rt2860sta
sudo modprobe rt2860sta

```

rmmod/modprobe makes the kernel use the freshly-installed backport module, where the bug is fixed.

Jason

---

