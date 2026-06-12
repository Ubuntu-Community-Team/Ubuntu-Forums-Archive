---
title: "I need help fixing my sound drivers"
date: 2020-03-06
forum: Multimedia Software
---

### Post by jbh54enwiler on 2020-03-06
I recently purchased a new laptop (HP Pavilion 14-ce2068st) and installed Kubuntu 19.10 on it.  There were two problems at first.  The first problem was a lack of working Wi-Fi drivers, which I fixed.  The second problem was that there was no sound on my system.  I checked my "lspci" output and I see that I have an Intel Cannon Point-LP HD Audio card on my system.  Another command said I had a Realtek HD Audio card, though that may have been a codec or something.  Anyway, I installed the Realtek driver thinking that was the one on my system and now my sound card has dissapeared from my system, with the PulseAudio volume control GUI saying it's controlling "dummy output" and no sound cards can be detected.  

I'm going to guess that I made a "dummy" mistake and installed the wrong driver, and now I need to figure out how to reinstall the correct driver for the Intel chip and get my sound working.  I downloaded source code for what I'm guessing is the correct driver from GitHub at [https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_realtek.c](https://github.com/torvalds/linux/blob/master/sound/pci/hda/patch_realtek.c), which says it's a "Universial interface for Intel High Definition Audio Codec," but I can't figure out how to compile it or install it because I've never had to add anything to the kernel before, and I'm worried I might break my system even further.  Or maybe I don't even need the driver code and I can install from somewhere else?  I'm at my wit's end here and I'm not terribly experienced with having to work at this level with my computer, so a simple solution would be much appreciated if possible.  Just in case you guys need it, my kernel version is 5.3.0-40-generic.

---

### Post by webaake on 2020-03-07
Do you have the package "linux-modules-extra-5.3.xxxxxx" installed? If not, uninstall that Realtech thing you installed and install linux-modules-extra........" for your kernel. 

Do not go that route with source code. The link you provide is to a kernel patch and the work flow of that is; Get the kernel source code, patch it with that patch, then compile the kernel source to functioning kernel. Then install it. The possibilities for problems with this route is endless!
Furthermore, that patch is probably already incorporated into newer kernels, like the one you already have.

I suspect that your problem either lies "linux-kernel-modules..." or configuring sound settings in alsa/pulseaudio. Good Luck!

---

### Post by jbh54enwiler on 2020-03-07
> **webaake said:**
> Do you have the package "linux-modules-extra-5.3.xxxxxx" installed? If not, uninstall that Realtech thing you installed and install linux-modules-extra........" for your kernel. 

Do not go that route with source code. The link you provide is to a kernel patch and the work flow of that is; Get the kernel source code, patch it with that patch, then compile the kernel source to functioning kernel. Then install it. The possibilities for problems with this route is endless!
Furthermore, that patch is probably already incorporated into newer kernels, like the one you already have.

I suspect that your problem either lies "linux-kernel-modules..." or configuring sound settings in alsa/pulseaudio. Good Luck!

How would I go about uninstalling the Realtek driver?  And I'm guessing I replace the Xs in "linux-modules-extra?" with the rest of the version number of my kernel?

---

### Post by jbh54enwiler on 2020-03-07
> **webaake said:**
> Do you have the package "linux-modules-extra-5.3.xxxxxx" installed? If not, uninstall that Realtech thing you installed and install linux-modules-extra........" for your kernel. 

Do not go that route with source code. The link you provide is to a kernel patch and the work flow of that is; Get the kernel source code, patch it with that patch, then compile the kernel source to functioning kernel. Then install it. The possibilities for problems with this route is endless!
Furthermore, that patch is probably already incorporated into newer kernels, like the one you already have.

I suspect that your problem either lies "linux-kernel-modules..." or configuring sound settings in alsa/pulseaudio. Good Luck!

OK, I think I uninstalled the driver, I used sudo make uninstall inside of the directory containing the driver.  But Pulse Audio still can't find the sound card, and when I ran sudo apt-get install linux-modules-extra-5.3... and so on, it said it was already the newest version, which means it's already installed.  Any ideas?  Also, according to the Windows System Information app, (I dual-boot) I seem to have both an Intel HD Audio card and a Realtek HD Audio card.  Which may make things more complicated.

---

### Post by webaake on 2020-03-08
Hmm, you could try to run alsamixer from the terminal. alsamixer can be a more direct way to check your sound settings. It's a good place to fiddle around with the settings, although it may be somewhat un-intuitive. Check this link too: 
[https://www.linuxquestions.org/questions/linux-newbie-8/alsa-installed-but-no-sound-4175594359/](https://www.linuxquestions.org/questions/linux-newbie-8/alsa-installed-but-no-sound-4175594359/)

---

### Post by Yellow Pasque on 2020-03-08
You almost certainly have a regular sound codec and one connected to the GPU (i.e for sound output through HDMI or DisplayPort). If all is working well, it's not complicated. You run pavucontrol, or whatever sound GUI is built into your desktop, and select the card you want if it's not the default.

>  I downloaded source code for what I'm guessing is the correct driver from GitHub
That is probably the driver you want, but it's already built into the kernel. The module is called snd-hda-intel, and it already includes the patch_realtek file.
If it's not working, then perhaps you need a newer version. The best way to test this would to be use a LiveUSB of a very recent distro. That way, you don't mess with your current install. Something like Kubuntu 20.04 should work (Xubuntu would be a smaller download).

Also, getting more info wouldn't hurt: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by jbh54enwiler on 2020-03-09
So my sound's working now.  I reinstalled Kubuntu (Which also fixed some boot problems and gave me the opportunity to fix some partitioning mistakes I made the first time) and I still didn't have sound.  ALSA and linux-modukes-extra were already installed, and using alsamixer wasn't working either.  But some updates installed and when I shut down my PC for the night and booted it up again in the morining, the sound was working!  Thanks for your help, guys!  Although I wish I knew what exactly I did to get the sound drivers working.  Oh well.  Thanks again!

---

### Post by jbh54enwiler on 2020-03-09
Actually, wait.  I switched to Windows to do some work, and when I switched back to Kubuntu, my sound was gone again.  I'm not sure what I need to do to get it back.

---

### Post by CelticWarrior on 2020-03-09
Probably you need to turn off Fast Startup in Windows. It is known not only to keep some partitions semi-hibernated but also certain devices won't work in the dual-boot after restarting Windows.

---

### Post by jbh54enwiler on 2020-03-09
Turning off fast startup didn't work.

---

### Post by Yellow Pasque on 2020-03-09
Does the sound work if you completely shut down the computer and boot directly to Ubuntu?

---

### Post by jbh54enwiler on 2020-03-09
That worked.  Hopefully the sound sticks around now.

---

