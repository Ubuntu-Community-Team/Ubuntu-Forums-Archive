---
title: "A7U Asus Laptop no sound (newbie)"
date: 2008-07-01
forum: Multimedia Software
---

### Post by xammap on 2008-07-01
Hi All

I have tried to follow the various threads to get my sound working, but they all leave me stranded at what seems to be the most important area. I must be missing something obvious. The trouble is, once their system is working, all interest stops.

I have the Asus A7U laptop with what appears to be the standard sound card for this. However, it could be Intel or it could be ATI (depending on which question is asked). I'm also having trouble working out what all the various driver/utilities do on the volume/sound control.

That's probably just the noob nature of things, but clarification would be appreciated.

Please take pity on an enthusiastic amateur!

Max

---

### Post by xc3RnbFO8P on 2008-07-01
Check **sudo gedit /etc/modprobe.d/alsa-base** if got this line:
options snd-hda-intel model=auto 
If not, add it and restart the computer.

---

### Post by xammap on 2008-07-01
Hi Ringi

Thanks for the answer.

Yes, my alsa-conf file has this line in it and my system has been rebooted since it was added.

I'm sure there is something simple which hasn't been done (or has been done and shouldn't have been).

Can you suggest anything else?

Max

---

### Post by xc3RnbFO8P on 2008-07-02
1. Did you get sound with Live CD?
2. Did you check all boxes in Volume Control> Edit> Preferences?

Show the output of **dmesg**

Find this file: snd-hda-intel.ko (or snd-hda-intel)

Do you got /etc/modprobe.d/alsa-conf file?

---

### Post by xammap on 2008-07-03
Hi Ringi

I have run dmesg and have looked through it. Not much about audio... The zipped text file is attached.

I have booted from the live cd. No sound from any options.

All options under Volume Control>Edit>Preferences are checked and all outputs are unmuted and at high volume.

I have found snd-hda-intel.ko under the ../alsa-driver-hda.1.0.17rc1/pci/hda folder. I thought I had downloaded the rc3 files, but obviously not.

My alsa-conf file consists of one line: options snd-hda-intel model=auto

Thanks for your help so far.

Max

---

### Post by xc3RnbFO8P on 2008-07-03
Next install **Paman** in Synaptic Package Manager.
Check devices.

---

### Post by xc3RnbFO8P on 2008-07-03
Can you give full path of  **../alsa-driver-hda.1.0.17rc1/pci/hda**

---

### Post by peakshysteria on 2008-07-03
In terminal:
```
alsamixer
```
See if there is something turned off.

---

### Post by xammap on 2008-07-04
Hi Ringi

I have installed (only) Paman.

Under Devices there are no sinks or sources.
The commentary at the bottom of the window says "Failure: Connection refused."

full path for snd-hda-intel.ko:/usr/src/alsa/alsa-driver-1.0.17rc1/pci/hda

Max

---

### Post by xammap on 2008-07-04
> **peakshysteria said:**
> In terminal:
```
alsamixer
```
See if there is something turned off.

Hi Peakhysteria

Yep, done that. Every output is turned up.

Max

---

### Post by peakshysteria on 2008-07-04
A bit old but maybe it can help:[http://ubuntuforums.org/showthread.php?t=591607&highlight=Asus+A7U](http://ubuntuforums.org/showthread.php?t=591607&highlight=Asus+A7U)

---

### Post by xc3RnbFO8P on 2008-07-04
Try in terminal:
> pulseaudio -D

---

### Post by xammap on 2008-07-05
Hi All

Thanks for the help regarding my sound problem.

Following a bit of a rest from it, I have gone back to basic principles and uninstalled/reinstalled everything alsa-. My installation was running (and synaptic seems to insist on) 1.0.14, but I have downloaded and manually installed 1.0.15.

Once I did that, I edited the appropriate files according to this link: [https://answers.launchpad.net/ubuntu/+question/23893](https://answers.launchpad.net/ubuntu/+question/23893), changing the *model=toshiba probe_mask=8* to *model=auto* for my A7U laptop.

Lo and behold, it all works now.

NB: When uninstalling the alsa drivers, my Madwifi wireless installation gets uninstalled too. I don't know why. Once it is reinstalled, I can get back on the net!

Thanks again for your interest and your help.

Best regards

Max

---

