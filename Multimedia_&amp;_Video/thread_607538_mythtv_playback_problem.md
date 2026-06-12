---
title: "mythtv playback problem"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by keeganl on 2007-11-09
My backend and frontend are both on the same machine.  I go into my recorded video section and the preview of the show plays perfect, but when I select a show, the video gets jumbled. Any suggestions as to why this is happening?

---

### Post by keeganl on 2007-11-09
To clarify my situation.  I am currently running Mythtv on Ubuntu Gutsy Gibbon.  I am using the nvidia drivers and I have installed all necessary codecs for playback.  I can watch all of my videos previously downloaded or ripped from DVD and music playback is no problem.  I can even go into my recorded tv programs folder and play them in mplayer.  The problem comes in when I try to watch them fullscreen through Mythtv.  The preview in the bottom right corner plays the video fine while I am in the recorded programs folder in mythtv, but when I select a recorded program to watch it fullscreen the video turn pink and looks majorly distorted.  The distortion freezes after about 2 seconds, but the audio still works perfectly.  I hope this is enough details for someone to help me out.  I have played with all of the playback settings in the mythtv frontend setting, but nothing is working.  Also, when I first installed mythtv 2 days ago, everything worked perfectly.  It just quit working on me last night.  Thanks for any help.  This is giving my girlfriend one more thing to complain about with my linux pvr project.  I would love to fix it up so she will enjoy it.  Thanks again.

---

### Post by mwc on 2007-11-09
Roll your Nvidia driver back to 100.14.11. The latest Nvidia drivers, both 100.14.19 and 100.14.23 Beta are buggy to say the least.

This fixed all my video problems on Gutsy 64bit, hope it helps you.

---

### Post by keeganl on 2007-11-10
thanks I'll give it a shot

---

### Post by elj4176 on 2007-11-12
I'm having a similar problem. 

I have a FE/BE that runs dapper and an HP laptop w/nvidia go 7600 that I upgraded to Gutsy (64 bit). As soon as I "upgraded" to gutsy on my FE laptop X  has been very unstable and I'm finding that it will not play my recorded programs using the myth frontend. The preview looks fine but when I play it the video is skunked up bad.
If I change sessions from gnome to blackbox the recorded programs play fine. Turning off desktop effects in gnome does not seem to help either.

How do I roll back my nvidia drivers? 

Thanks!

---

### Post by wandernot on 2007-11-15
I also had this problem and resolved it by down grading to 100.14.11 of the NVIDIA driver. neither 19 nor 23 of this driver release would work for me. System is AMD 3200+ 2.6.22-14-generic x86_64 with a NVIDIA GeForce 6200 rev a1. I also found that mplayer would also show the corrupted image on valid avi files.  I never found a sample image given anywhere on what it looks like when things go bad so one is attached.

I never found this solution in launchpad or other postings on mythtv or general vidoe postings. I had assumed it was the mpeg codec because that was the type of file that showed corrupted. Thanks for the thread. I really didn't want to down grade the system to 32bit.

---

