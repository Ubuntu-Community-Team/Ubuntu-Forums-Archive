---
title: "Sound stopped from internal speakers, Intel HDA Haswell, Ku 14.04"
date: 2014-05-05
forum: Multimedia Software
---

### Post by marinosr2 on 2014-05-05
Hi all, any help with this problem would be greatly appreciated!

Problem: Sound has stopped coming from internal speakers. Headphone jack works fine, as does sound in Windows. It worked upon initial install (new system) but stopped.

System: Kubuntu 14.04 / Windows 8 dual boot, Intel HDA Haswell sound, Dell Inspiron 15 7000 (7537), i7-4500u

Steps Taken:
1. Followed sound troubleshooting guides, full reinstall of ALSA, etc.
2. Reinstalled Kubuntu entirely after noticing sound worked on Live CD version. Sound worked for a bit, and then stopped after a few boots. Sound now no longer works on Live CD version. Then, on one boot a few hours ago, sound came back; on the next boot it was gone. (Kicking myself for not running the ALSA diagnostics when it was working.) 
3. Tried to run the ALSA HDA analyzer scripts, but they fail on the following error: 
```
ValueError: wrong proc file format (unknown dig1 bit 'KAE')
```

ALSA Diagnostic Output:
[http://www.alsa-project.org/db/?f=d971c969174733432657d2a197fa20dce400d8fb](http://www.alsa-project.org/db/?f=d971c969174733432657d2a197fa20dce400d8fb)

Similar Problems:
This person is having the exact same problem - to the letter - on the same (it seems) system:
[http://askubuntu.com/questions/457028/sound-suddently-stopped-working-for-internal-speakers-headphones-still-work](http://askubuntu.com/questions/457028/sound-suddently-stopped-working-for-internal-speakers-headphones-still-work)
... and someone running Linux Mint with the same problem on the same HDA sound hardware:
[http://forums.linuxmint.com/viewtopic.php?f=196&t=165626](http://forums.linuxmint.com/viewtopic.php?f=196&t=165626)

Truly a mystery... anybody have ideas?

**Update** Shut the lid, opened it again, and sound is back. Rebooted, sound is still back. Wrote out the alsa-info for comparison: 
[http://www.alsa-project.org/db/?f=d971c969174733432657d2a197fa20dce400d8fb](http://www.alsa-project.org/db/?f=d971c969174733432657d2a197fa20dce400d8fb)

---

### Post by SeijiSensei on 2014-05-06
If your machine has multiple audio outputs, say analog and HDMI, you need an application to direct the output to the proper channel.  You'd think that would be a piece of cake, but for some reason it's always been a bit of a challenge in KDE.  Some applications, and maybe even the system sounds, can switch the channel.  Keep an eye out for KDE notifications about the state of your sound card.  You'll see pop-ups when that happens.

In the past I used to install **pavucontrol** to manage sound because I found kmix fairly brain-dead.  However someone here (monkeybrain maybe) put me on to the Veromix widget.  Click the "cashew" at the right-hand end of the Panel, choose Add Widgets > Categories > Multimedia > Veromix.  I dropped it into the System Tray, then disabled the default mixer, kmix.  If your machine has multiple sound outputs, Veromix will let you change the output channel for different applications.  I have both HDMI to my TV with poor-quality sound, and a standard analog connector from the computer's speaker jack to my home audio system.  I usually prefer the latter, but sometimes I'll just use the TV's speakers for convenience.  I can switch between channels easily in Veromix.

---

### Post by marinosr2 on 2014-05-12
Thanks for the response. I don't think the sound was getting directed inappropriately, because I could look at the output levels for various output devices (HDMI vs. internal speakers vs. headphones) and you could see that audio was in fact being outputted to the speakers, just nothing came out of the speakers.

After struggling mightily with this for a few days, the sound just started working all of a sudden and hasn't quit yet. On one hand I'm pleased, but on the other hand I would have liked to have fixed something to make it work, not live in perpetual fear (OK that's hyperbolic) that it will stop working again. 

Thanks for the tip about Veromix, thougn. It's great!

---

### Post by kyaume on 2014-08-19
In my case sound also stopped working on a Sony Vaio, while nothing wrong with it in the past and under windows. Why does every upgrade have to come with so much pain? 
More speicifcally, how can I get my sound working again? System tools do not give a clue.

---

### Post by n.hinton on 2014-12-10
Same with an optiplex gx620. have followed lots of threads, reinstalled alsa pulse etc tried lots of 'option codes in alsa-base.conf all to no avail. It worked perfectly on 12.04, 14.04 can't seem to find the internal speakers:

14.04 no internal speakers
[https://www.dropbox.com/s/h38d1w4n16etdyh/Screenshot%20from%202014-12-02%2013%3A40%3A50.png?dl=0](https://www.dropbox.com/s/h38d1w4n16etdyh/Screenshot%20from%202014-12-02%2013%3A40%3A50.png?dl=0)
12.04 all detected
[https://www.dropbox.com/s/0k376713gb0ptod/Screenshot%20from%202014-12-02%2013%3A34%3A05.png?dl=0](https://www.dropbox.com/s/0k376713gb0ptod/Screenshot%20from%202014-12-02%2013%3A34%3A05.png?dl=0)

---

### Post by ram17 on 2014-12-31
Same problem with Dell Gx620 .Sound worked perfect in 12.Have tried everything .

---

### Post by n.hinton on 2015-01-02
Wondering if its more to do with device detection and maybe firmware!

---

