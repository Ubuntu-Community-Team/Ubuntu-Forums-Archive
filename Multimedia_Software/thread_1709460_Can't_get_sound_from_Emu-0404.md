---
title: "Can't get sound from Emu-0404"
date: 2011-03-18
forum: Multimedia Software
---

### Post by geeve420 on 2011-03-18
Hello everyone! I am having a terrible time getting my sound card working. I have ubuntu 10.10 x64 everthing works great except my Emu-0404 PCI. I can't seem to get any sound of it at all. I do know for sure it is the revision that does work. My system doesn't even see it as a Creative card. I can run Fedora 14 and it works without any intervention at all, However Ubuntu just does not see it. 

Can someone who has this card working please tell me how they did it. I have found the turoial with rebulding the Kernal with the latest ALSA, but I just don't see that being the problem as both Fedora and Ubuntu use the same realese. 

I would also like to say that when I boot Ubuntu I get a black screen before the log in that says it sees the Emu, but no firmware is found. I downloaded and installed ALSA firmware that supports the emu, but it acts like it doesn't load the emu10k1 driver at all, just the default and I am stuck. 

I would like to use Ubuntu over Fedora simply because the graghics driver for fedora just suck installing and seem to crash x, where as Ubuntu is nice and easy. Thanks in advance :)

Geeve

Edit: Not sure if it maybe a 64bit problem? IDK

---

### Post by cchhrriiss121212 on 2011-03-18
I take it the card shows up in lspci?
Have you tried manually loading the module, like this:
```
sudo modprobe snd-emu10k1
```?

---

### Post by geeve420 on 2011-03-18
Yeah it shows up in lspci, I will try manually loading when I get home from work. I was thinking there was a way to do that, just couldn't remember. Thanks and I will report back later

Geeve

---

### Post by geeve420 on 2011-03-19
> **cchhrriiss121212 said:**
> I take it the card shows up in lspci?
Have you tried manually loading the module, like this:
```
sudo modprobe snd-emu10k1
```?


Tried the code, I still have no sound :( I tried 

```
sudo alsamixer
```

and it says no such file or directory. I am at a loss here, The only thing showing in my sound properties for hardware is pcm2900? I feel kinda dumb because I wrote a guide for this for Fedora 12, I just can't get ubuntu to work.

Here is some output for y'all:

greg@greg-desktop:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:04.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fb] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [GeForce 6150 LE] [10de:0241] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.2 RAM memory [0500]: nVidia Corporation MCP51 Memory Controller 0 [10de:0272] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev a1)
00:0f.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0267] (rev a1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
04:07.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
04:09.0 Multimedia audio controller [0401]: Creative Labs SB0400 Audigy2 Value [1102:0008]
greg@greg-desktop:~$ 

As you can see, it knows it's there

greg@greg-desktop:~$ modinfo soundcore
filename:       /lib/modules/2.6.32-30-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     51925557ECF0F2838930862
depends:        
vermagic:       2.6.32-30-generic SMP mod_unload modversions 586 
parm:           preclaim_oss:int


Soundcore is there, looking in Synaptic I have green check box:
 
alsa-tools 
alsautils
alsa base
alsa-tools
Gnome alsamixer

I don't have alsamixer, and gnome alsamixer does nothing :( If you can help please do 

Thanks

Geeve

---

### Post by Kirito on 2011-03-19
Did you come across this page? [http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga)

Following that guide worked for me. Also, did you disable your on-board sound (or change default to the EMU card)?

Don't know if you already tried, but these things were the problem when I was trying to install the firmware for the same card.

---

### Post by cchhrriiss121212 on 2011-03-19
After loading the snd module, you need to check aplay -l and see if the card is listed. And alsamixer is a part of alsautils package, try running it without sudo.

---

### Post by geeve420 on 2011-03-19
> **Kirito said:**
> Did you come across this page? [http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga)

Following that guide worked for me. Also, did you disable your on-board sound (or change default to the EMU card)?

Don't know if you already tried, but these things were the problem when I was trying to install the firmware for the same card.

> **cchhrriiss121212 said:**
> After loading the snd module, you need to check aplay -l and see if the card is listed. And alsamixer is a part of alsautils package, try running it without sudo.

Kirito, I will check it out thanks!! I have my onboard soundcard off in the bios

cchhrriiss121212, I tried to load i again and this is my output:

greg@greg-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

also:

greg@greg-desktop:~$ alsamixer
cannot open mixer: No such file or directory
greg@greg-desktop:~$ 


Seems to only see a USB audio, which I don't even have a usb soundcard. Thanks for the help so far everyone. I know we can get this thing going :)

Geeve

---

### Post by geeve420 on 2011-03-19
Sorry for the double post...

It was seeing my USB record player as a sound card. I disconeted it and I now have no sound cards at all! Just keeps getting worse :(

greg@greg-desktop:~$ aplay -l
aplay: device_list:223: no soundcards found...
greg@greg-desktop:~$ 

also

greg@greg-desktop:~$ alsamixer
cannot open mixer: No such file or directory
greg@greg-desktop:~$ 

I tried sudo modprobe snd-emu10k1 again as well, stil no love

I am at a loss


Geeve

---

### Post by cchhrriiss121212 on 2011-03-20
> I downloaded and installed ALSA firmware that supports the emu
Maybe this is the problem, because AFAIK, you don't need any firmware upgrade for this card. Could you explain what you did here?

Also:
Do you get any message after loading the snd module?
What does lspci -v show for the card?

---

### Post by lidex on 2011-03-20
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by geeve420 on 2011-03-21
Thanks for all your suggestions and help so far everyone. I gave up and went with Fedora 14 because it just works right out of the box. Thanks again for your time :)

Geeve

---

### Post by lidex on 2011-03-21
Any chance I can convince you to keep an ubuntu partition long enough to file a bug report and follow up on it to get it fixed upstream?
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

