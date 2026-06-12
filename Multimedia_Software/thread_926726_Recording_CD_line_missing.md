---
title: "Recording CD line missing"
date: 2008-09-22
forum: Multimedia Software
---

### Post by ezelic on 2008-09-22
High all.
It seams I don't have all of meh recording lines in sound control. For input source I can select Line, Mic, and Front Mic. I'm missing CD, and it's really important for me because meh tv tunner (Leadtek TV2000 XP Expert) is using that line for sound playback. I can't hear any sound either from TV or FM. I'm guessing that line is muted, but since it's missing from sound recording controls I can't check it or unmute it.

MB: DFI Lanparti 790FX
Sound: Realtek ALC885

Does anyone has any ideas how to fix this?

---

### Post by lian1238 on 2008-09-22
Did you go to Edit->Preferences and then check CD?
It should come up in Playback instead of Recording. (at least mine does)

---

### Post by ezelic on 2008-09-22
yea, I checked all the settings inside volume control,it simply isn't there...
I played with every input, unmuted them in case it's just called differently, but with no success. 

but since I'm a noob concerning Ubuntu maybe I'm missing something somewhere..

---

### Post by lian1238 on 2008-09-22
Try going to File->Change Device and try a different one.

---

### Post by ezelic on 2008-09-22
yea, tried them all :)

---

### Post by ezelic on 2008-10-01
This is the error i get when i type dmsg in console

[   58.063363] hda-intel: Invalid position buffer, using LPIB read method instead.

Maybe it's related  with meh ALSA problems and lack of CD line.

Any ideas how to fix?

---

### Post by markbuntu on 2008-10-01
The ALC 885 has a number of options due to the various misconfigurations by the OEMs.
This is the HDA excerpt from my guide: 
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

If you are having problems with the HDA card/chip on your laptop or one of these:

HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8 ),
		ATI SB450, SB600, RS600,
		VIA VT8251/VT8237A,
		SIS966, ULI M5461
 you should look here (look through the entire thread if the OP does not fix your problem , people have posted solutions for many specific machines):

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

Start in Post #2 here:

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

