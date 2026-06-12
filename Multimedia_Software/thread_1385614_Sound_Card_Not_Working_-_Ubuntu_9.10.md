---
title: "Sound Card Not Working - Ubuntu 9.10"
date: 2010-01-19
forum: Multimedia Software
---

### Post by brandondiederich on 2010-01-19
I have Ubuntu 9.10 installed and the sound card is not working. I have an onboard sound card. The motherboard is a Gigabyte GA-G1975X with a Creative Labs Sound Blaster Live 24-bit CA0106. It shows up in the preferences as CA0106 but no sound comes out. 

brandon@brandon-desktop:~$ sudo lshw -C multimedia
[sudo] password for brandon: 
  *-multimedia            
       description: Multimedia audio controller
       product: CA0106 Soundblaster
       vendor: Creative Labs
       physical id: 5
       bus info: pci@0000:04:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=CA0106 latency=32 maxlatency=20 mingnt=2
       resources: irq:22 ioport:9000(size=32)
brandon@brandon-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
brandon@brandon-desktop:~$

---

### Post by sports.car.guy on 2010-01-19
Some Soundblaster Live and supposed Audigy models which are rebagged Live ones have issues and are not supported. There is one that is a Bestbuy house brand that has absolutely no support and is a SB Audigy II I believe. I bought this one and found out the hard way it was not supported. Forgoing that, if it is a supported one is your on board sound disabled in the bios?

I almost forgot that unsupported card I encountered still had that driver install and listed devices using aplay -L

It all led me to think the card was supported and after a bit of research it was clearly stated nope not at all. I believe I found it on the Alsa site.

---

### Post by brandondiederich on 2010-01-25
The sound card I have is listed on the ALSA website as supported. Furthermore, I used to have ubuntu on this computer with sound working... I just can't remember how I did it. It is enabled in the BIOS though I have to admit I feel dumb that I hadn't already checked that.

---

### Post by jazzeymike on 2010-02-03
I have the same card. It worked perfectly in 8.04 LTS and, after a bit of tweaking in the sound p[reference settings, 8.10. Anyone know how to tell Ubuntu to use it? It doesn't even show up in preferences in 9.10. There is a "Digital Stereo - this board puts a smiley here if I don't break up the name in the brackets, which are included in the driver name - ( I E C 9 5 8 )" which I have no idea about, where it comes from, whether it is another sound card or just something being picked up by mistake, what's going on?

---

### Post by bliffle on 2010-02-03
I'm using 9.10 on a Thinkpad X60s and sound doesn't work. It used to. Sound is OK on the XP partition.

---

### Post by bliffle on 2010-02-28
This is really horrible because I have no idea how to proceed debugging this problem. I thought maybe 'lspci' would tell me enough that I could figure out what's wrong, but it's so obtuse and has so many options I could spend days with no useful result. For example, when I look at things like 'alsamixer' it talks about 'IEC958', but lspci has different names for things.

I think the only thing I can do is replace the OS, but I've never done that and it sounds dangerous. I suppose I should preserve the 'home' directory, perhaps copy it to a USB HDD in a can, then scratch the disk on the computer. then run the 9.10 CD again. This will set back a months of updates and installs, but maybe it's easier just to do that. Of course, there's the possibility that it is some flag or variable in 'home' itself that is causing the problem. And what if I apply the same update/install again and regress the audio again?

Isn't there some methodical way to find the problem and fix it?

---

### Post by chkneater on 2010-03-02
Bliffle, maybe you should start a separate thread for your problem, that way more people see it and the threads don't get confusing.  Try to include what the terminal displayed when you did -lspci.  I seriously doubt you need to wipe your OS to fix this.

---

### Post by aimstv on 2010-05-08
I have the same issue with sound here, I thought maybe a fresh install of Lucid would fix it but it still doesn't work.

After spending much time googling i found [this on the Alsa Bug Tracker]("https://bugtrack.alsa-project.org/alsa-bug/bug_view_advanced_page.php?bug_id=3560") which seems to have helped the most. 

Originally there was no sound output at all, but after reading the link above i have managed to get white noise! One step closer lol!

---

