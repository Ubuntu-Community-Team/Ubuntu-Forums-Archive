---
title: "Mythbuntu 9.10 - no sound"
date: 2009-12-06
forum: Multimedia Software
---

### Post by zippyblue on 2009-12-06
I'm not absolutely new to Ubuntu, but pretty new.  I have installed Ubuntu 9.10 on three machines so far, including a dual boot on my Pro-Spec Winbook system.  I have recently added Mythbuntu to that machine, and have also tried installing the MythTV package within the Ubuntu install.  In both cases I can not get audio output.  I have searched the forums but have not been able to find a solution, so far.

Basic information:

The multimedia device is Conexant
The Audio card is Intel (ICH6 famly)
Processor is a Pentium 4
RAM = 512mb

---

### Post by LarryJ2 on 2009-12-19
I have the same problem.  Recordings are OK but no sound upon replaying them.   Audigy2 (SB0350) Audio card which works normally outside the mythbuntu frontend and conexent Hauppauge HVR1600 ATSC tuner card.   This all worked fine with mythbuntu 8.10 and myth .21. 

Looks like Mythbuntu 9.10  and .22  need a bit of tweaking.  This is my third "show stopper" I've encountered after installing MB 9.10 and M.22.  I'll report in here if I find something tomorrow.

Larry

---

### Post by RedSingularity on 2009-12-19
In a terminal type 

alsamixer

and make sure the levels are all the way up.

---

### Post by LarryJ2 on 2009-12-20
For me,  I went to the directory where the mythtv recordings are stored, which on my mythbuntu 9.10 is /var/lib/mythtv/recordings.  There I found several .mpg files.  I opened one with  File-Open in the media player VLC. The sound played fine.

Next, I went back into MythFrontend setup and paged to the Audio System.  There I selected ALSA:default, Default, Stereo, and Passive and unchecked the three lines at the bottom of the page. On the next page, Audio Mixer, I selected ALSA:default  Master  and moved the PCM/Master sliders all the way to the right. Independedn Muting was unchecked.

From then on,  I had audio in the Mythbuntu frontend.  Since I have a set of 5.1 speakers,  I believe I had selected 5.1  in the channel selection. Anyway, with all the other problems with MB9.10 / .22,  I'm happy with stereo for now.

---

### Post by scotthew1 on 2009-12-22
hey i've got the same problems. i just tried both of those suggestions and neither of them helped at all. any more suggestions? please

---

### Post by LarryJ2 on 2009-12-22
For the record, my idea that selecting 5.1 audio caused the lack of sound was wrong.  I reformatted and reinstalled (about the 7th time I've done this) and now I have sound with 5.1 selected.  Maybe  the fact that I had installed using 64 bit amd iso was the culprit?   This seems unlikely but that was a difference between sound and no sound installs. 

Now to find out why my s-video fed HVR1600 mpeg encoder is pumping out an off red picture.  At least the sound out of /dev/video0 is OK.

LJ

---

### Post by Poulios on 2009-12-26
> **RedSingularity said:**
> In a terminal type 

alsamixer

and make sure the levels are all the way up.

This helped in my case.
THANKS!

---

### Post by Poulios on 2009-12-26
> **RedSingularity said:**
> In a terminal type 

alsamixer

and make sure the levels are all the way up.

This one fixes my problem but the problem returns after reboot and I have to do it again and again.
Any ideas to solve it permanently?

Thanks in advance

---

### Post by RedSingularity on 2009-12-27
See the little sound icon in the corner of your screen?  Right click it and choose "open volume control".

Change the settings there and see if it sticks.

---

