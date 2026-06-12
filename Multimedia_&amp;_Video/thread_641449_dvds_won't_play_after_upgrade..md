---
title: "dvds won't play after upgrade."
date: 2007-12-15
forum: Multimedia &amp; Video
---

### Post by RDUBBALO on 2007-12-15
I have just upgraded to Ubuntu 7.10 before that I could make copies of any dvd I wanted and play them fine on my dvd player. Now that I have upgraded I can play them on my pc and burn them fine. I can also play the burned movies on any other computer, but however they will not play on any dvd player. I use k9copy and I also tried burning with k3b. No luck . Yes I have the libdvdcss2 package installed from the synaptic package mgr. Any ideas or help would be awesome. Am I missing a new update or file?

---

### Post by mc4man on 2007-12-15
i haven't noticed any problems but you're not the only one with issues. I'm using ver. 1.2.1 so maybe thats why. part of the changelog
Changes:
- Improved compatibility with standalone players
- Fixed freezes in dvd backup 
Though I wouldn't think earlier releases wouldn't work at all. 
If you have time post add. info
Title 
iso size in mb. or bytes
blank media used - brand and type  (+ or - r)
size of burned disk 
model of stand alone

---

### Post by RDUBBALO on 2007-12-15
The version 1.2.1. you speak of do yeah me the version of k9copy? I am using hp dvd+r 4.7gb the .iso size is definitely under that. I have use different programs and tried copying the movie, burning the iso. now it plays on my other dvd player my newer one,b ut not on my older one. Maybe with the new change it just wont play on those crapy old dvd players. LOL

---

### Post by mc4man on 2007-12-15
Some (usually older)stand alones can have problems with +r's, I have no idea if any of the linux burning apps can be used to set the booktype for +r's to dvd-rom. Not all drives support this and  (at least for me) it's a drive setting that only has to be done once. ImgBurn (run in wine) will set select drives. Other than who knows- maybe your old player was getting old
1.2.1 - latest k9 release
slightly ot - alot of blank media is being produced in either India or Singapore now and the quality is not as good as made in Japan media, check cdfreaks for media info ( nothing personal to residents of those places) I use Taiyo Yuden usually though I got some Maxwell medicals that are excellent

---

### Post by drisay on 2007-12-17
I don't think it is simply a media issue.  I recently changed from Windows Vista to Gutsy.  I never had issues playing DVDs burned in Vista (or XP on my laptop) on my older DVD player, but can't for the life of me get it to work with Ubuntu (same media I used to burn with on Windows).

Any help with this would be great.  This is the only snag I've run into with my switch to Linux that is driving me nuts and I can't seem to solve.

I use +r and have no issue with them if burning from Windows.

---

### Post by Ordhaj on 2007-12-17
I'm having the same problem. I had the previous two versions of Ubuntu installed and could play DVDs. This time, there is no way that my computer can even recognize DVDs. It has suddenly become just a CD drive. 

I've other serious problems related with this version (video drivers, OpenGL) but I'll post them there.

---

### Post by wjston on 2007-12-22
> **RDUBBALO said:**
> I have just upgraded to Ubuntu 7.10 before that I could make copies of any dvd I wanted and play them fine on my dvd player. Now that I have upgraded I can play them on my pc and burn them fine. I can also play the burned movies on any other computer, but however they will not play on any dvd player. I use k9copy and I also tried burning with k3b. No luck . Yes I have the libdvdcss2 package installed from the synaptic package mgr. Any ideas or help would be awesome. Am I missing a new update or file?

I haven't been able to get dvd's, created using k9copy on gutsy, to play in my standalone player either. I have reinstalled, tried kubuntu, ultimate edition 1.6 and different versions of k9copy...no luck. Today, I installed Ultimate Christmas Edition 2007 and tried again using the k9copy that is part of the build. Same results....dvd works in computer but doesn't play in standalone player. I decided to compile the latest K9copy from source. The first thing I did was to ensure I had all the dependencies as indicated here [https://help.ubuntu.com/community/BuildingK9CopyfromSource](https://help.ubuntu.com/community/BuildingK9CopyfromSource). I was missing lidvdread3-dev, which I had installed before on different attempts. I then found this link that finally resolved my problem [http://ubuntuforums.org/showthread.php?t=607991&page=2](http://ubuntuforums.org/showthread.php?t=607991&page=2). Take note on the fifth response where mc4man added this:[COLOR="Blue"]edit: just compiled 1.21 works pretty good though needed some add. packages for the make, i did several at once, probably libavcodec-dev and libaformat-dev did the trick.[/COLOR] [COLOR="Red"]The only problem I had was libaformat-dev should actually be libavformat-dev.[/COLOR] One of these dependencies is what solved my problem. I backed up a dvd after compiling the newest version of K9copy (1.2.1) and I am watching it as I type this response. [COLOR="DarkGreen"]**[COLOR="Black"]"Thank you mc4man"[/COLOR]**[/COLOR] for your post as I have made at least 15 coasters and was about to give up on K9copy. Hope this will resolve your problem with K9copy also.

---

