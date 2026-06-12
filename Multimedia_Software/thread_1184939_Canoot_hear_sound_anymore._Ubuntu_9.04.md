---
title: "Canoot hear sound anymore. Ubuntu 9.04"
date: 2009-06-11
forum: Multimedia Software
---

### Post by grungy on 2009-06-11
Hi folks,

Ubuntu was running like a charm sor far. A couple of minutes ago.

I was looking at the services activated and i noticed that the alsa mixer manager was not checked (even though i could hear sound months ago). So i decided to check it. Next thing i know no more sound.

Knowing that:


grungy@Opiate:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
grungy@Opiate:~$ 


Where is the problem.

---

### Post by weisel on 2009-06-11
I am in the same boat i installed the new Ubuntu 9.04 updates now there is no sound on my radio stations. I had to boot back into windows to listen.

---

### Post by wooly62 on 2009-06-11
Interesting. I had sound yesterday and downloaded and installed lots of updates today (the 2nd day I've had a machine using Utubu) and I have no sound now either. **Can anyone tell me how to retrieve it (I don't have windows on this)**. The message I found says 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect stream: Invalid argument

When I click the volume icon at the top of the screen I get No volume control GStreamer plugins and/or devices found.. Day 2 and I have a problem!

---

### Post by weisel on 2009-06-11
> **weisel said:**
> I am in the same boat i installed the new Ubuntu 9.04 updates now there is no sound on my radio stations. I had to boot back into windows to listen.

I have to take that back i rebooted and radio started working.

---

### Post by MarkJBrader on 2009-06-12
I also would like help.  I Installed Jaunty when it first appeared, as dual-boot with Windows, and all was well.  But some update within the last two weeks has taken the sound away.  Still works under Windows.  I have tried the instructions given in the sticky thread, and it shows that a driver is installed.  alsamixer does not give me any sound, though I make sure all is unmuted.  I have seen no error messages at all.

Just some update in the last couple of weeks killed the sound.

---

### Post by xshad0wfx on 2009-06-12
im having the same issue, i installed ubuntu and upgraded to Jaunty and everything was working fine prior to that.  Now NO sound works regarding video.  I can watch videos with vlc, and mplayer, and youtube just got no audio.  I also couldn't listen to my music with banshee so i tried switching all my audio to OSS and that got my music going but still no audio with videos =/.  I hate it when bugs like this happen >.<

---

### Post by wooly62 on 2009-06-12
I have re-booted the machine this morning, but it's made no differece. Can anyone tell meho to get the sound back please?

---

### Post by gradinaruvasile on 2009-06-12
you might try looking over here:

[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by flamingpolo on 2009-06-18
I am having the same problem here, in Ubuntu 9.04. Eveything was running smoothly, i actually had the latest Alsa Drivers.

My digital out sound just stopped working. I had not clue, but it does make sense that this happened after the last update.

Will try what gradinaruvasile suggests..

---

### Post by therico on 2009-06-18
I'm having the same issue. ALSA recognizes the sound card, alsamixer has no mutes, I've followed the 'clean Pulseaudio configuration' guide, but nothing. Literally sound one day, no sound the next.

The only relevant update I see is hald:

Preparing to replace libhal1 0.5.12~rc1+git20090403-0ubuntu1 (using .../libhal1_0.5.12~rc1+git20090403-0ubuntu2_amd64.deb) ...

Preparing to replace hal 0.5.12~rc1+git20090403-0ubuntu1 (using .../hal_0.5.12~rc1+git20090403-0ubuntu2_amd64.deb) ...
 * Stopping Hardware abstraction layer hald
   ...done.

Setting up libhal1 (0.5.12~rc1+git20090403-0ubuntu2) ...

Setting up hal (0.5.12~rc1+git20090403-0ubuntu2) ...
 * Reloading system message bus config...
   ...done.
 * Starting Hardware abstraction layer hald
   ...done.

---

### Post by tixetsal on 2009-06-27
Ditto.  Bug time.

---

### Post by tixetsal on 2009-06-27
I discovered that by booting 2.6.28-11-generic, instead of 2.6.28-13, my audio was restored, as long as I booted that kernel. I have another box with Asus P5N7A-VM MOBO, and this bug did not effect that machine. My AMD geforce 8200 will not play nice with 28-13 though. My sound card shows up in lspci, but aplay -l tells that I have no sound card.

---

