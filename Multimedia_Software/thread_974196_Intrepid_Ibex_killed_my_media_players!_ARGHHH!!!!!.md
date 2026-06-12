---
title: "Intrepid Ibex killed my media players! ARGHHH!!!!!!"
date: 2008-11-07
forum: Multimedia Software
---

### Post by IKhider on 2008-11-07
Greetings fellow Ubuntu users,

I wish these linux developers could figure out how to upgrade systems without disabling my media playing software in the process. I have a single core 2.6 Ghz Processor with 2 gigs of ram. I was using Hardy Heron yesterday and had three media players to play my music files including XBMC, VLC, and Rhythmbox. I updated my OS and now I cannot play my music directory. I used rhythmbox--no longer works--it scrolls and scrolls and scrolls the directory with a red icon. I used VLC to import the directory, no longer works--it freezes. XBMC crashes withing seconds after I launch it.AAHHHHHHHHHHHH!!!!

WHY? WHY? WHY? Am I asking too much? Just to play my damn music directory? I am tired of trying to run basic functions and having to smash my head against the monitor!

---

### Post by cariboo on 2008-11-07
Have you tried removing the configuration files that were created in Hardy, to see if that helps? the configuration files are hidden, so open Places-->Home Folders and press Ctrl-H to view the hidden files and directories.

When the configuration files have been removed the applications will create new ones, when you run the apps.

Jim

---

### Post by Sense on 2008-11-09
As you can read here: [http://xbmc.org/forum/showthread.php?p=185738](http://xbmc.org/forum/showthread.php?p=185738)
there is a separate PPA for Intrepid. I hope that works for you.

---

### Post by sosaudio1 on 2008-11-09
> **IKhider said:**
> Greetings fellow Ubuntu users,

I wish these linux developers could figure out how to upgrade systems without disabling my media playing software in the process. I have a single core 2.6 Ghz Processor with 2 gigs of ram. I was using Hardy Heron yesterday and had three media players to play my music files including XBMC, VLC, and Rhythmbox. I updated my OS and now I cannot play my music directory. I used rhythmbox--no longer works--it scrolls and scrolls and scrolls the directory with a red icon. I used VLC to import the directory, no longer works--it freezes. XBMC crashes withing seconds after I launch it.AAHHHHHHHHHHHH!!!!

WHY? WHY? WHY? Am I asking too much? Just to play my damn music directory? I am tired of trying to run basic functions and having to smash my head against the monitor!


I am glad you got XBMC to work in Heron...mine works but not as well as I would like. mp4 media..it has a problem...ie waaaaaaaay off sync. Quicktime....no problems. I can't figure out how to use it to watch DVD's. I have a script for shoutcast X...works...brings up a directory but cant watch the stream....If anyone can jump in and make a forum on here or...a thread on here that spells out how they made X plugin and X script to work, PLEASE START ONE. I hate looking through seven different forums and getting bits and pieces of code that may or may not work..LOL

I just want to hear how you got this plugin and that script to work with the system....

BUT I wouldnt have to worry about that if I could just get MIRO to stop crashing and hard locking my system...I think I have gotten away from the hard locks by leaving xine player instead of gstreamer...with xine it just...crashes which I am in favor of instead of hardlocks that mean killing the system with the power button. For those of you familiar with Miro and the linux shows on there, I can now watch sneaky linux albeit with the screen halfway on top of itself on the left side...but...i will say....XBMC will play that no problems...there is a FLV Ubuntu screencast that for whatever reason I cannot get miro or xbmc to play...dunno why....

but enough..I could go on...if anyone has a magic pill that I have not yet tried then lay it on me....

L8R
Rich

---

### Post by IKhider on 2008-11-12
Hello All, 

I have looked at the problem and consulted others--here are the findings;

With regards to Amarok, Rhythmbox not working--the problems seems to be with my gstreamer. 

With regards to XBMC, I am told the drivers for my graphics card are not installed as they are restricted. 

I am not sophisticated enough to tackle either of those problems.

Currently I use NCMPC, a terminal-based media player to listen to music on my hard drive.  

If anyone knows of a simple way to rectify either of those problems, please share. 

I was told it was a bad idea to upgrade to latest and I should have stuck with Hardy. 

Thanks, 

-I-

---

### Post by Sense on 2008-11-13
> **IKhider said:**
> Hello All, 

I have looked at the problem and consulted others--here are the findings;

With regards to Amarok, Rhythmbox not working--the problems seems to be with my gstreamer. 

With regards to XBMC, I am told the drivers for my graphics card are not installed as they are restricted. 

I am not sophisticated enough to tackle either of those problems.

Currently I use NCMPC, a terminal-based media player to listen to music on my hard drive.  

If anyone knows of a simple way to rectify either of those problems, please share. 

I was told it was a bad idea to upgrade to latest and I should have stuck with Hardy. 

Thanks, 

-I-
What graphic card are you using? The older nVidia cards are currently having some problems with the drivers. I'm not sure when it will be solved since the new drivers that should solve this issue are still be said to be quite buggy(is this true?).

Didn't you install the restricted drivers because you don't want to install restricted drivers, or didn't you install them because you didn't know? In that case you could try *System->Manage->Hardware Drivers*. That program could help you.

---

