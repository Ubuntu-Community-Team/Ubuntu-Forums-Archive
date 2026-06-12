---
title: "ATI Technologies Inc Rage 128 RF/SG AGP"
date: 2009-04-11
forum: Multimedia Software
---

### Post by Kangarooo on 2009-04-11
I want this card to work. Today in #xubuntu i found one more guy who has the same problem. So now we are 2 but let me start with what i have already done and it didnt work so this is big problem with totally no solution for now..

I wanted my 10y old pc to work fast so i choose you Xubuntu.

Installed Xubuntu 9.04 OLD **ATI** video card didnt work.
In Display settings i could change frequency it said only 0mHz and default was 1280x960 but i changed to 800x600 till ill get video working.
In **Synaptic** there was already installed **xserver-xorg-video-ati** but since video not working i Installed Something what found in **Synaptic** with Keywords like **ATI** and **RAGE**. Installed **xserver-xorg-video-ati-dbg** **xserver-xorg-video-r128-dbg** **xserver-xorg-video-radeon-dbg** after each i logged in and out and when they didnt work.
Changed video to **nVidia** Went to Hardware Drivers and it found NvidiaX and i allowed to install it
Then **nVidia** worked but i want **ATI** to work.
Changed **ATI** After Xubuntu Loading Bar got console- logged in and got 4 choises Start in safe mode or something else or configure new video driver. I choose safe mode.
and in **Synaptic** put **envyng-qt** witch was about 200mb but said that will download latest ATI or NVIDIA driver or the Legacy driver (for older cards). And i choose only one ATI option and restart.
Restarted and after Xubuntu loadingbar it crashed and cant do anything.. not working not even console.. And if could then how to get back working at least to Safe Mode?
So i just installed Ubuntu 9.04 daily yester dowloaded couse i thought it has latest drivers and i wont need to download 333mb updates like with 26march installation couse dailly versions are every day new iso..
So installed 9.04 yesterDaily version today and put EXT4 but for swap couldnt choose EXT4 not even any other..
Ok so installed and in Display settings i finnally could change mHz and more options for resolution but when i changed from Mot**F*** big to 1024x784 and 85 mHz (Display settings allowed this as maximum option 4 this reslution) it gave an
ERROR:
```
Could not apply the selected configuration
```

```
Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```


Here are **Parameters** for This problematic **ATI Technologies Inc Rage 128 RF/SG AGP**

lspci

```
VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP
```

lspci -v

```
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP
	Subsystem: ATI Technologies Inc Device 0048
	Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	I/O ports at d800 [size=256]
	Memory at df000000 (32-bit, non-prefetchable) [size=16K]
	Expansion ROM at dffe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: aty128fb
```


lspci -n
```

01:00.0 0300: 1002:5246
```


lspci -vn

```
01:00.0 0300: 1002:5246
	Subsystem: 1002:0048
	Flags: bus master, VGA palette snoop, stepping, 66MHz, medium devsel, latency 64, IRQ 11
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	I/O ports at d800 [size=256]
	Memory at df000000 (32-bit, non-prefetchable) [size=16K]
	Expansion ROM at dffe0000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: aty128fb
```

---

### Post by brendanpiater on 2009-05-08
I got the same issue trying to get my 19" external monitor to work with a X700 card and the OSS driver. Been stuck with my laptop display since upgrade... not very good me thinks.

Tried all sorts of xrandr combinations, tips and tricks but nothing...

---

### Post by 1915flyer on 2009-05-10
I have 3 cards somewhat similar to yours - VGA compatible controller: ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

I had Ubuntu 8.04 or 8.10 on this one computer. As I recollect, the card was working with some mods to xorg.conf for monitor resolution and refresh only. Then I upgraded to 9.04. The cards still work with varying resolution and refresh freq but xorg.conf is back to the basic configuration.

It works on this 1 computer. I installed 9.04 on another similar computer with the same card and had 800x600 max resolution and 60 refresh. Completely unsatisfactory and I can't figure out how to change it either. Editing xorg.conf doesn't seem to work. I finally changed the video card on my 2nd computer to a Nividia FX5600 from a 3rd computer, checked the Hardware Devices in Admin and loaded them. That worked with the basic xorg.conf.

Wish I could help.

---

### Post by diskmaster23 on 2009-12-21
Was there ever a solution to this? I have the same card and not getting anywhere fast with it. Especially with the TV-Out option.

---

### Post by Kangarooo on 2010-05-22
Also i have another card witch is almost the same (the name different) and also not working.
ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS

---

### Post by rainbowagent7 on 2010-05-26
I have the same Rage card (ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS), it used to work at 1024x768 just fine but has been at 800x600 for several months now. It really sucks because I just can't afford a new card and I know there is a way to make it work again. I've posted about my problem with no replies, but am working diligently to solve it. I'll post any good news I come across, and if you need any info I'm here to help.


                                                                                                                    :guitar:

---

### Post by Kangarooo on 2010-06-02
Actually since this is really old card a little newer used is not expensive for example Geforce Nvidia cards are as ive read best for ubuntu but somewhere should be a wiki about supported cards (here [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards) ) couse one of my Geforce FX5500 also isnt working fully and its also a very old card. But problem here is that this 128 card is not working as it works on other OS.

---

