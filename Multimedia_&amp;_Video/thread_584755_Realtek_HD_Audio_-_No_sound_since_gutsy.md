---
title: "Realtek HD Audio - No sound since gutsy"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by mart78 on 2007-10-21
Hi, i just finished my update to Gutsy and almost everything went fine, especially my GF8800 finally works without having to tweak the driver.

But i noticed my onboard sound is not working anymore. It's a Realtek HD Audio ALC 889A Chipset and it worked fine out of box with Feisty but it seems Gutsy didn't recognize it or didnt't load the driver.

Here is the lshw output for the audio device, can anyone tell me what driver i have to install to get it to work as i never checked in feisty what driver was used for the card.

```
 *-multimedia UNCLAIMED
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: latency=0
```

Thx.

---

### Post by mart78 on 2007-10-21
Nevermind, it was the 386 kernel that apparently didnt't load the driver. WIth the generic it works all fine again... ;)

---

### Post by oedha on 2007-11-05
have you try to install linux-backports-modules ???

get these files
1. linux-backports-modules 2.6.22-14-generic
2. linux-backports-modules-generic_2.6.22.14.21.....

after you install these packages
go to terminal
sudo vi /etc/modprobe.d/alsa-base
add --> options snd-hda-intel model=acer
( acer have to be replaced by your computer type )
reboot

maybe this helps
OedhA

---

### Post by WinterWeaver on 2007-11-05
(hope I'm not hijacking...) just wondering, what do those modules do? I also have audio problems, and want to try as much as possible before recompiling alsa.

ta
WW

EDIT: nvm... found out on IRC. if you install the linux-386 meta package, it installs the extra kernel which you will be able to select on boot.

---

### Post by jkgood on 2007-12-29
Thank you so much. my sound card ALC889a  built-in  GA-73PVM-S2H
your information help me a lot. my computer can play music now.
but still a problem ... my sound card is recognized  as alc885?
[INDENT]grep Codec /proc/asound/card0/codec#* 
Codec: Realtek ALC885[/INDENT]

and i add a line of  
[INDENT]options snd-hda-intel model=auto[/INDENT]
have any suggestion?



> **oedha said:**
> have you try to install linux-backports-modules ???

get these files
1. linux-backports-modules 2.6.22-14-generic
2. linux-backports-modules-generic_2.6.22.14.21.....

after you install these packages
go to terminal
sudo vi /etc/modprobe.d/alsa-base
add --> options snd-hda-intel model=acer
( acer have to be replaced by your computer type )
reboot

maybe this helps
OedhA

---

### Post by HyRax on 2008-02-26
Thanks to oedha's post, I've just got sound working on a Toshiba Satellite A210 (Australian model PSAFGA) notebook with ALC268 Realtek HD audio onboard.

Procedure as follows:
[list=1]
[*]Installed vanilla Ubuntu Gutsy 7.10 from the Live CD.
[*]Went to System->Administration->Software Sources.
[*]Click on the "Updates" tab.
[*]Check the box for "Unsupported packages (gutsy-backports)"
[*]Click close.
[*]Click Reload when prompted about updating the repository list.
[*]Once done, drop into a terminal and type:
```

$ sudo apt-get install linux-backports-modules-2.6.22-14-generic linux-backports-modules-generic

```
[*]Then open the /etc/modprobe.d/alsa-base file in your favourite text editor:
```

$ sudo nano /etc/modprobe.d/alsa-base

```
[*]Go right to the bottom of the file and add the following line:
```

options snd-hda-intel model=toshiba

```
[*]Save and exit.
[*]Reboot.
[*]Unmute and increase volume, then play a test sound and that's it!
[*]As a final step, you might want to go back to Software Sources and disable the Backports option again if you don't want anything else from it, or the automatic updates will pester you to install other backports that you probably do not need.
[/list]

Thanks again oedha! :D

---

### Post by khuxtable on 2008-03-09
As with jkgood above, I also have a Gigabyte GA-73PVM-S2H mainboard. But I think my problem is more basic. I have no /proc/asound directory.

Any ideas how to get one?

---

### Post by khuxtable on 2008-03-10
> **khuxtable said:**
> As with jkgood above, I also have a Gigabyte GA-73PVM-S2H mainboard. But I think my problem is more basic. I have no /proc/asound directory.

Any ideas how to get one?

I have attempted to install the alsa drivers/lib/utils for version 1.0.16, but still no joy. No /proc/asound directory, which seems to be a virtual directory managed by alsa. I have to assume that alsa isn't really installed correctly.

---

### Post by khuxtable on 2008-03-10
Okay, miraculously, removing with purge of the alsa and reinstalling it did the trick. I would swear I've done this before...

---

