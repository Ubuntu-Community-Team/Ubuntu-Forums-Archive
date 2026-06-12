---
title: "ALSA doesnt work?"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by maniacmusician on 2006-08-15
Hi,

I'm approaching Linux Audio as a complete newbie not only to recording on linux, but just recording music in general. So I'm obviously facing a gigantic upward learning curve. with that being said, I can't seem to get ALSA to work on my computer. I've installed many of the apps recommended on the Ubuntu studio wiki, and then some, and any of them that use ALSA are giving me errors. For instance, as soon as i open up JACK control, it says "Could not open ALSA sequencer as a client. MIDI patchbay will not be available". in the messages window, there is also an accompanying "ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory." This second error (could not open /dev/snd/seq) is displayed by multiple apps. what should I do about this? I have all things ALSA installed, as far as I can tell.

Similar error messages:
AMS: "Could not open file." In terminal, it shows:
```
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
LADSPA_PATH: /usr/lib/ladspa
loadPath: , savePath:
Preset path now /usr/share/doc/ams/demos
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Error opening ALSA sequencer.

```

I am also having problems with some other apps (not related to ALSA) but i figured i'd tackle one thing at a time. any input would be appreciated,

thanks.

---

### Post by edev on 2006-08-16
Hello maniac,

Make sure snd_seq is loaded.

Type in a terminal :

```
sudo modprobe snd_seq
```

and restart jack. If you don't see the message "Could not open ALSA sequencer as a client..." then it's just that this module isn't loaded at boot time.

Hope this helps,

Eric,

---

### Post by dolson on 2006-08-17
Yes, this is covered in the UbuntuStudio.com wiki page.

---

### Post by maniacmusician on 2006-08-24
thanks, that worked. 

@dolson: I know you think sometimes that no one reads or appreciates your wiki, but that's not true. without it, i wouldn't even have known where to start. I guess I must've missed it, or havnt gotten to it yet (only looked at the preparation page where it said what apps to install). I just recently switched fully to linux so i still have to get most of my stuff off of dvd's and un-rar it and get this computer totally set up. I dont have a lot of time to devote to it either so its sort of a half finished mess now. but back to the point: ubuntustudio.com is an amazing resource and an amazing place to start for people. 

the only thing i would suggest adding for total newbies are the fundamentals of recording and what kind of a hardware setup is good. ie: is it better to use a mixer, or do a direct line in from instruments? what kind of cables are used to connect to the audio card? for guitar and mics, what's required to transition from one cable type to another? stuff like that. anyways, you've done a great job so far, and i'm sure that once i have time to do a proper studio setup, your website will help me even more than it already has. thanks for your amazing contribution.

---

### Post by dolson on 2006-08-25
(The stuff about snd_seq is on the prep page.)

To be honest, I think that those non-Linux-specific details such as using a mixer, recording direct, etc. are better covered by better existing resources, such as Studio Central. However, I wouldn't be opposed to adding it, I just don't have the time when everything else is largely unfinished.

WRT hardware, that is covered somewhat on the hardware page, but we can only recommend devices that we have experience with, so the more people who contribute, the more of a resource that will become.

How to use the software to do.. well, anything, is where I want to focus the wiki on now that most of the technical details are taken care of. I'm still learning this stuff, but I'd like to write many small tutorials for specific tasks for things like Ardour and seq24 and JAMin. Anyhow. Way off topic now. :)

---

### Post by maniacmusician on 2006-08-26
i think those small tutorials are great ideas. I understand the difficulties with not having enough time. But i didn't know about Studio Central, so thanks for that. I'm starting to figure out ardour, but i havnt even tried seq24 or JAMin. the latter is especially out of my league at the moment lol. err yeah. off topic.

---

