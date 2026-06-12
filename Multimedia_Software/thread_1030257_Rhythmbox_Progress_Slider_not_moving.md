---
title: "Rhythmbox Progress Slider not moving"
date: 2009-01-04
forum: Multimedia Software
---

### Post by thornate on 2009-01-04
I'm running Intrepid. Ever since I first installed it, Rhythmbox has not worked properly; the music plays, the timer on the right side updates correctly but the progress slider does not move. It is completely disabled, so I'm not able to drag it to select a particular point in the song that I want to listen to. See the attached screengrab.

In all other respects, Rhythmbox works fine. VLC runs fine on my computer with no slider issues. I have uninstalled Rhythmbox and reinstalled it to no effect. I'm not sure whether it's relevant, but Rhythmbox did not have this problem under Gutsy or Hardy.

How can I fix this?

---

### Post by thornate on 2009-01-05
Nobody? Can anyone point me in the direction of somewhere else I can ask this?

---

### Post by xalf on 2009-05-12
Hey dude!

did you ever fix the slider problem? if so please enlighten me :)

peez!

---

### Post by thimad on 2009-07-16
I also have this problem. No solution.

---

### Post by stoneg64 on 2009-07-28
I have the same issue

---

### Post by lipilee on 2009-08-06
Amazing how this bug has not been fixed in the last 3 years. I wonder if we are left with it forever :popcorn:

---

### Post by Losik on 2009-11-21
I had the same issue on my Karmic but after I have removed the files from rhythmbox and have them rescaned everything works fine.

P.S. [https://bugs.launchpad.net/rhythmbox/+bug/373534](https://bugs.launchpad.net/rhythmbox/+bug/373534)

---

### Post by francois.marot on 2009-11-27
same for me here, with 9.10 Karmic 64bit: slider was not moving.
- I selected a folder with no MP3 as my library folder
- restarted rhythmbox
- then re-selected my original folder with all my MP3
=> it works correctly from now on.
This is a strange bug !

---

### Post by dracuella on 2010-01-08
> **francois.marot said:**
> same for me here, with 9.10 Karmic 64bit: slider was not moving.
- I selected a folder with no MP3 as my library folder
- restarted rhythmbox
- then re-selected my original folder with all my MP3
=> it works correctly from now on.
This is a strange bug !

Francois, you're the man! This worked for me as well, so anyone having slider issues, please try this obscure as it may sound.

How you ever figured out to try this combination is beyond me :)

---

### Post by Tristan Schmelcher on 2010-04-21
I just tried that and it didn't work for me.

The right bug for this issue is this one: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/442304](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/442304)

The developers want someone to test again on the Lucid/10.04 beta, but I'm using Karmic/9.10. Is anyone out there using 10.04 who could test it and report the results at the link above?

---

### Post by altjx on 2010-10-13
Wow, this is still happening on Ubuntu 10.10, and my timer isn't even moving neither is the slider... The hell?

---

### Post by linux.alucard on 2010-10-18
I've same problem | Ubuntu 10.10

---

### Post by linux.alucard on 2010-10-20
working after I installed the package gstreamer0.10-plugins-ugly!

---

### Post by W.McL on 2011-02-16
gstreamer0.10-plugins-bad installed, tired every single other fix I could find on the internet, progress slider and play time not updating, seeking through progress timer surprisingly works nonetheless.

Problem occurs with ogg and mp3 files. Als rhythmbox occasionally stops playing.

Let's see when  the problem gets fixed... :popcorn:

---

### Post by ashishverma.pu on 2011-06-08
guys it doesn't work on songs having rate 128 Kbps but works for 320 Kbps songs chek it out...

---

### Post by lancelotj on 2011-06-15
It's because gstreamer0.10-ffmpeg was installed to decode mp3. Install  gstreamer0.10-plugins-ugly and re-import your mp3 files can resolve this problem.

---

### Post by amir_pasha on 2011-09-09
This will work:
remove gstreamer0.10-ffmpeg
-sudo apt-get autoremove gstreamer0.10-ffmpeg
-remove: ./.gnome2/accels/rhythmbox; ./.cache/rhythmbox/; ./.local/share/rhythmbox/
-reinstall Rhythmbox
when asks you to search for plugin do not install gstreamer0.10-ffmpeg (gstreamer0.10-plugins-ulgly installed preassumedly)

---

### Post by altjx on 2011-09-09
> **amir_pasha said:**
> This will work:
remove gstreamer0.10-ffmpeg
-sudo apt-get autoremove gstreamer0.10-ffmpeg
-remove: ./.gnome2/accels/rhythmbox; ./.cache/rhythmbox/; ./.local/share/rhythmbox/
-reinstall Rhythmbox
when asks you to search for plugin do not install gstreamer0.10-ffmpeg (gstreamer0.10-plugins-ulgly installed preassumedly)

Thanks, already went back to 7 after a lot more random stuff came about. ^_^

---

