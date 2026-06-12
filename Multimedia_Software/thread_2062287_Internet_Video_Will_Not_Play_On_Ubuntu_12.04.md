---
title: "Internet Video Will Not Play On Ubuntu 12.04"
date: 2012-09-24
forum: Multimedia Software
---

### Post by LordDraco on 2012-09-24
I have a freshly installed version of Ubuntu 12.04 LTS and I can't play ANY Internet videos. I have searched and tried everything I could to get them to work. Nothing has helped. I am running on an emachines T3085 with the AMD Athlon xp processor. Nvidia gforce 4 is installed on the mainboard but I am using an nvidia graphics card instead. Unsure of which one. It has 512 memory on it. I am also running with 2 gigs of memory and using Firefox browser. I have tried Chromium with no success in playing video. Multiple websites were also tried with no success. If anyone knows how to fix this problem I would most grateful. I thank you for your time and assistance in this matter.

---

### Post by irv on 2012-09-24
Make sure you installed the Ubuntu extras.
[ATTACH]224608[/ATTACH]
Also make sure you install:
```
sudo apt-get install libdvdread4

```
```
sudo /usr/share/doc/libdvdread4/install-css.sh

```
The last to will make sure you can play DVD's.

EDIT: if you just installed Ubuntu this is a good link to read.
[http://blog.sudobits.com/2012/04/14/10-things-to-do-after-installing-ubuntu-12-04/]("http://blog.sudobits.com/2012/04/14/10-things-to-do-after-installing-ubuntu-12-04/")

---

### Post by Futant on 2012-09-24
Have you installed the restricted extras? [http://help.ubuntu.com/community/RestrictedFormats]("http://help.ubuntu.com/community/RestrictedFormats")
Edit: slow phone typing didn't mean to repeat above advice!

---

### Post by LordDraco on 2012-09-24
Well, only you tube videos are working. Tried a couple others but nothing plays. Anyone have any other ideas? Would love to get everything working. I have the restricted extras installed as well. I appreciate the help.

---

### Post by irv on 2012-09-25
> **LordDraco said:**
> Well, only you tube videos are working. Tried a couple others but nothing plays. Anyone have any other ideas? Would love to get everything working. I have the restricted extras installed as well. I appreciate the help.

What browser are you using? If you are using Firefox you need Flash plugin. Chrome has it's own flash. What videos are you talking about. Hulu, Amazon, DVD's or what?

---

### Post by LordDraco on 2012-09-25
My appologies. I am using Firefox with the Flash plug-in installed. I have uninstalled and reinstalled but no luck. The videos I am talking about are on Anime Freak, Hulu, The X Factor USA,  CNN.com. I have tried Chromium but all it says is couldn't load plug-in on the same sights listed. I ran an update already so everything is the newest. The plug-ins I have installed are as follows:

 DivX Web Player,  Quick-Time Plug-in 7.6.6, Shockwave Flash 11.2, VLC Plug-In (Totem Compatible 3.01), Windows Media Player Plug-In 10 ( Compatible; Totem), DjView 4.9 and iTunes Application Detector. 
 My Add-Ons are:  

Download Helper 4.9.10, Flash Video Download 1.17, Global Menu Bar Integration 3.4 and Ubuntu Firefox Modifications 2.1.1

---

### Post by irv on 2012-09-25
I had some issues with video awhile back, and I think it was because I was running the 64bit version. I can't remember what I did to fix it, but I think it had something to do with what I told you to install in post #2.
Did you run those two commands I had in that post? If not try running them.

---

### Post by tomdkat on 2012-09-25
> **LordDraco said:**
> My appologies. I am using Firefox with the Flash plug-in installed. I have uninstalled and reinstalled but no luck. The videos I am talking about are on Anime Freak, Hulu, The X Factor USA,  CNN.com. I have tried Chromium but all it says is couldn't load plug-in on the same sights listed.Which CNN.com video are you trying to watch? I'm watching on in Firefox 15.0.1 on Ubuntu 12.04 (64-bit) right now.  The video is on the CNN.com home page and is a Flash video.

I'm also able to watch videos on the "TV & video" part of the CNN.com site:

[http://www.cnn.com/video/](http://www.cnn.com/video/)

Peace...

---

### Post by LordDraco on 2012-09-25
@irv, yes I have run them. Just to be sure I have covered my bases I just ran them again. Unfortunately it didn't help. I'm running the 32bit version of Ubuntu 12.04. I was thinking of installing Ubuntu 9.04 and upgrading from there. I keep wondering if this is happening because I used a cd-rw instead of a regular disc. any thoughts? Also, @tomdkat, I just went to the website given and none of the videos will load for me. I keep hoping there is a simple solution to where I wont need to install the old ubuntu and upgrade. Whatever it takes though to get this back in perfect running order is what I'll do.  I appreciate everyones patience and generosity in this matter. I know its difficult to diagnose and give solutions without being in front of the computer to look over everything and I thank you.

---

### Post by irv on 2012-09-25
OK, lets backup. Seeing it is a fresh install why not start over. What I would do is download fresh iso. Now you can burn a DVD or use Unetbooin and make a bootable USB. Check it for errors. After you install the OS then install all the updates. Then install the Ubuntu Restricted Extras. At that point your videos should play.

---

### Post by LordDraco on 2012-09-25
Thanks irv. Ill give it a try with a fresh disk. Ill post an update with results.

---

### Post by LordDraco on 2012-09-29
Update. I switched back to my home built system and everything works just fine. Hardware error was the culprit. I thank you all for the help.

---

### Post by irv on 2012-09-29
> **LordDraco said:**
> Update. I switched back to my home built system and everything works just fine. Hardware error was the culprit. I thank you all for the help.

Why not mark this thread solved.
[ATTACH]224835[/ATTACH]

---

### Post by LordDraco on 2012-09-29
Once again I thank you irv. I was wondering how to do that.

---

