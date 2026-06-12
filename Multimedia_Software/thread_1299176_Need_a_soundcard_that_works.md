---
title: "Need a soundcard that works"
date: 2009-10-23
forum: Multimedia Software
---

### Post by ravalox on 2009-10-23
Can anyone recommend me a PCI or PCI express sound card that is best supported by Ubuntu?  Pulse Audio is killing me and I need to find the most ubiquitously supported sound card.

---

### Post by markbuntu on 2009-10-23
WHat are you using now, maybe we can get that working and save you some money. ANd what exactly are the problems, a lot of problems can be fixed fairly easily.

lspci

aplay -l

these will tell us what you have and what driver it is using.

Anyway most hardware problems are caused by the ALSA drivers, not pulseaudio.

---

### Post by ravalox on 2009-10-23
It's an audigy 2, I've struggled through 3 versions of Ubuntu now: 8.10, 9.04, 9.10- none of which cope properly with the sound card.  It's one of the most ubiquitously supported sound card and Pulse Audio simply can't seem to get it right.  I just need whatever 3 cards this craptastic audio "solution" actually works with.  (as you can see I'm at the end of my patience with it, a gentoo CD is burning in my other machine's tray right now)

---

### Post by markbuntu on 2009-10-23
The problem with the audigy cards is that the ALSA driver by default is switched to digital instead of analog output. I am assuming that you cannot hear anything. If your problem is something else please let me know.

You can fix this problem easily. Open the volume control and uncheck the digital or IEC958 box. You may have to go to edit/preferences to make this switch visible in the control panel.

---

### Post by ravalox on 2009-10-23
I've had a variety of problems; in 8.10 it outright made no sound no matter what I adjusted.  In 9.04 it worked perfectly EXCEPT the line-in wouldn't work so a crucial part of my entertainment system wouldn't work.  This time(9.10) around sound works well unless I start any flash video and then it blocks the audio altogether.  I had this issue once with 8.10 when I ran out and purchased a different soundcard so I know it's been on the vine for a while.

---

### Post by ravalox on 2009-10-23
Honestly, I'm kind of defeated by the amount of reformatting I've had to do; can anyone name a card that works issue-free?

Oh and also at times my audio crackles.  I should say, I just learned a good deal more.  I'm running mythtv and when it's running the audio is silent but I can't play ANYTHING else.  When I turn off mythfrontend the audio crackles and everything seems to work.

---

### Post by markbuntu on 2009-10-23
Ok, well I have a SIIG Soundwave 7.1 card and it is cheap and it has worked OOB in every distribution I tried, ubuntu hardy, interpid, jaunty, karmic, Debian, Mandriva, SUSE, Fedora. It has a c-media 8768 chipset.

---

