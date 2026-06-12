---
title: "DVD Backup"
date: 2010-07-02
forum: Multimedia Software
---

### Post by rensell on 2010-07-02
Hi all, I'm looking for help getting a dvd ripper to work with my new "server."  I recently made a new home server running xUbuntu 10.04 - I used to use windows XP pro. I have a PS3 and a HTPC that connect to a samba share for videos. In XP, I used anydvd and dvdshrink. AnyDVD removes all encryption and I use DVD-shrink to copy the main movie as 1 large vob file to my hard drive - with NO compression. I use shrink because it's a small program and no problems with this combination. I then change the extension from vob to mpg and it plays on anything I want it to play on and if I ever I want to put it on a disc I change it back to vob and run IFO Editor on the file and I then have a folder I can burn.

Anyway, I'm looking for something that will work on linux to do what I described above. I run my server "headless" so if it runs right from my command line (putty\ssh) that's great, if not I use x forwarding for some stuff I do anyway.

Thank you so much for all suggestions

Ray

---

### Post by rensell on 2010-07-02
I just realized that I didn't specify in my first post, I owe all the movies that I have saved on my hard drive, I just prefer to simply "click" on the mpg on my PS3 or HTPC and watch the movie rather than track down the movie to find it's not in the right case, etc. etc. So, please nothing about "that's illegal" 

Thanks :)

---

### Post by wkulecz on 2010-07-02
I use DVDrip and then cat the resulting 1GB VOB files into a single mpeg file from the command-line.  There is a command line utility VOBcopy or something like that to do what DVDrip does.

The "Community Docs" should have a section in the howtos with all the gory details.   This might be a good place to start:
[https://help.ubuntu.com/10.04/musicvideophotos/C/index.html](https://help.ubuntu.com/10.04/musicvideophotos/C/index.html)


I do the same as you so our DVD collection is playable from our Viewsonic VMP-70 media player set top.  I particularly like not having to navigate through the lame menus on DVD disks to play the friggin movie!

Actually I rarely watch movies twice, but at least now my wife doesn't have to wake me up to figure out how to make the movie play :)

---

### Post by rensell on 2010-07-03
what a coincedence, I'm in nearly the same boat as your. 1. I hate the menus, 2. I like the "click and ply" for the girlfriend and mostly when we have company. The girlfriend knows I'm a geek, but I don't want to get all elaborate on the company that's visiting, now I can say you see the cover and the name, click it and your good to go. I don't even tell everyone I made the program that runs on the HTPC lol. I tried VOBcopy, but it seems to crap out on me when I try to copy with -l (so it doesn't split it into 2gb files) and when I didn't use -l my PS3 said it was corrupt data, so I figure something fishy in the coding somewhere. Anyhow, I'll try it ago very simple and use the cat command you mentioned, if it doesn't work I'll try the other program you mentioned. If that doesn't work, I'll stick with AnyDVD and DVDshrink on my laptop and just transfer the file over to the server when I feel like letting my computer sit and transfer the 6ish gigs of movie. 

Thanks for your response,

Ray

---

### Post by rensell on 2010-07-03
I just tried dvdrip and it doesn't seem to like my system (?) I get an error message (when trying to read the table of contents) to verify my DVD drive settings in preference and to verify I have a DVD inserted. I know there is a DVD inserted and I've verified my settings - I get all OK messages in preferences. I don't know why it's not working. I'm trying copyvob with another dvd - a retail one I grabbed to test the command you said and it doesn't seem to want to copy this dvd at all - I first tried 1 I burned after decrypting it, it was on my desk. I've installed the xUbuntu-restricted files and libdvdcss, but it doesn't seem to work still. 

Any suggestion(s)?

-Ray

---

