---
title: "Ripping DVDs"
date: 2009-01-25
forum: Multimedia Software
---

### Post by lsutiger on 2009-01-25
I recently converted my Windows MCE to Ubuntu. When I had the Win MCE,the DVDs I bought, I would backup by running through VLC and saving to an mpg file. I bought an expensive video codec from Nvidia to make it all happen.

Now that I have Ubuntu, I am trying the same thing. I d/l ffmpeg for the decoder. But I am having a problem with artifacts in the recorded video (blurring lines during moving scenes, etc).

Anyone have anything to offer in order to have clear recorded video from a DVD to a playable movie file?

---

### Post by pnutzh4x0r on 2009-01-25
If you are looking for a tool to rip DVDs to avi/mp4/x264, then you can use [HandBrake]("http://handbrake.fr/").  They have a GUI for Linux now and even include Ubuntu packages.

---

### Post by lsutiger on 2009-01-25
OK Thx.
I'lll check it out. I was actually wondering why I was getting bad results ripping it the same way I did before.

Appreciate the input! :D

---

### Post by lsutiger on 2009-02-07
Seems handbrake only has an 8.10 deb package.Running 8.04

---

### Post by mc4man on 2009-02-07
ck. here (haven't tried

[https://launchpad.net/~handbrake-ubuntu/+archive/ppa](https://launchpad.net/~handbrake-ubuntu/+archive/ppa)

---

### Post by lsutiger on 2009-02-08
Followed the instructions to the letter, bet after everything when I do sudo apot-get install hanbrake I get the error that handbrake has no installation candidate.
I have done sudo apt-get update.

---

### Post by howefield on 2009-02-08
> **lsutiger said:**
> ...when I do sudo apot-get install hanbrake I get the error that handbrake has no installation candidate.

Open Synaptic Package Manager and search for it, if you find it install from there.

I expect your mistakes are just typos, but synaptic will remove any doubt.

---

### Post by mc4man on 2009-02-08
go 
```
cat /etc/apt/sources.list
```
and take a look to see if it was added correctly

Usually with a ppa I'd just open System -> Admin... -> software sources -> third party -> add and just copy and paste the line(s) in 

```
deb http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu hardy main

```
```
deb-src http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu hardy main


```
and then click close and reload.

---

