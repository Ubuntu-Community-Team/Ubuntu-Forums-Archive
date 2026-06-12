---
title: "Mythweather-revamp"
date: 2007-05-07
forum: Multimedia &amp; Video
---

### Post by KuruOujou on 2007-05-07
As many of you MythTV users know, Mythweather has died because MSNBC changed their site, thus killing the feed for MythTV.  I found the fix, mythweather-revamp, and I found the wiki article on how to install here:
[http://www.mythtv.org/wiki/index.php/Using_mythweather-revamp_with_trunk_mythtv]("http://www.mythtv.org/wiki/index.php/Using_mythweather-revamp_with_trunk_mythtv")
However, everytime I try to run "make", i get about 150 errors. Because I have mythtv on another system and I followed the Community Documentaion, it is running openbox and I don't have any way to copy the output into the message box. The errors include issues with code format (expected } after ; or something like that) which make up about 80% of the output and the remaining are issues with qtnetwork.h and mythtv/xfile.h. It can't find them. I think that if I could find the include files that are missing, the remaining issues would go with it. Can anyone help out?

Also, as an unrelated and unecessary question, does anyone know where to get and how to install mythmovietimes?

---

### Post by mbobak on 2007-05-09
Try this:
```
sudo apt-get install build-essential
```

and:
```
sudo apt-get build-dep mythtv
```

The first makes sure you have all the required build tools installed: gcc, automake, etc.
The second installs all the build dependencies for myth.

Hope that helps,

-Mark

---

### Post by KuruOujou on 2007-05-09
Thanks for your fast reply. I ran the first command, and it told me it was already the newest version. I ran the second command, but it told me that it was unable to find a source package for mythtv. Is there like a pre-made deb or something of mythweather-revamp? or is it in the repository somewhere?

---

### Post by pedalwrench on 2007-05-13
> **KuruOujou said:**
> Thanks for your fast reply. I ran the first command, and it told me it was already the newest version. I ran the second command, but it told me that it was unable to find a source package for mythtv. Is there like a pre-made deb or something of mythweather-revamp? or is it in the repository somewhere?

Same here, I added the deb-src for the universe repo and got a new error though.  It couldnt download because a failed dependancy liblame-dev.

Im on edgy for my mythtv box

---

### Post by Rever75 on 2007-05-22
Do we know if the Ubuntu Team will be update Mythweather in the repos?

---

### Post by KuruOujou on 2007-05-22
I don't know for sure, however, I have talked to the people over at MythTV and the people that run ubuntu say probably not and to download and install it from the SVN. I have that on my todo list. At the very bottom :D. I'm just going to wait until they do add it, if ever, but if you need it now, just install from SVN.

---

### Post by electronikjunkie on 2007-05-22
[http://debian-multimedia.org](http://debian-multimedia.org) has the repos for apt-get build-dep mythtv.

---

### Post by rhpot1991 on 2007-05-31
I just created a wiki entry that should help everyone get the latest MythWeather running.
[https://help.ubuntu.com/community/MythWeather](https://help.ubuntu.com/community/MythWeather)

---

### Post by walmartshopper67 on 2007-07-30
> **KuruOujou said:**
> I don't know for sure, however, I have talked to the people over at MythTV and the people that run ubuntu say probably not and to download and install it from the SVN. I have that on my todo list. At the very bottom :D. I'm just going to wait until they do add it, if ever, but if you need it now, just install from SVN.

So you Ubuntu is going to leave a known broken package in the repositories. Nice. That's what I like to see, repositories with broken packages so that beginners (or even non beginners such as myself) install software and wonder why it doesn't work. I realize it's multiverse and most bets are off - but if you KNOW it's broken for EVERYBODY, leaving it there is pretty counterproductive.

That being said - I've been trying to compile it but checking out the SVN code fails when it cannot connect to the server or find the code. Apparently over the last couple months they just let it die and forgot about it?

---

### Post by axelsvag on 2007-08-05
I have tried your ubuntu doc 
[https://help.ubuntu.com/community/MythWeather](https://help.ubuntu.com/community/MythWeather)
but when I use this 

"You need to check out the MythPlugin source from here 

svn co [http://svn.mythtv.org/svn/branches/mythweather-revamp/mythplugins](http://svn.mythtv.org/svn/branches/mythweather-revamp/mythplugins)  "

I get the answer that the svn is gone or something like that. Is it true or does I just have bad luck.??

---

### Post by KuruOujou on 2008-05-10
> **walmartshopper67 said:**
> So you Ubuntu is going to leave a known broken package in the repositories. Nice. That's what I like to see, repositories with broken packages so that beginners (or even non beginners such as myself) install software and wonder why it doesn't work. I realize it's multiverse and most bets are off - but if you KNOW it's broken for EVERYBODY, leaving it there is pretty counterproductive.

At this point I've stopped using mythTV because I really don't feel like finding some way to pay for the TV guide service (I don't have many ways of paying for things online), however, I do feel I need to point out that not everyone in the world knows how to fix the repositories. I love to see people assume EVERYBODY knows EVERYTHING about repositories. Really I don't. I don't know how to update the repositories. So before you start a flame war, think before you post. (I'm saying this from experience on this forum.)

---

### Post by walmartshopper67 on 2008-05-11
> **KuruOujou said:**
> At this point I've stopped using mythTV because I really don't feel like finding some way to pay for the TV guide service (I don't have many ways of paying for things online), however, I do feel I need to point out that not everyone in the world knows how to fix the repositories. I love to see people assume EVERYBODY knows EVERYTHING about repositories. Really I don't. I don't know how to update the repositories. So before you start a flame war, think before you post. (I'm saying this from experience on this forum.)

I think you're misunderstanding me - the problems with the repositories was directed towards Ubuntu itself, the developers/maintainers/etc., not users. What I was saying was that Ubuntu itself had a broken package in the Ubuntu repositories that the developers/maintainers should have fixed/deleted. Ubuntu users themselves don't have any control over what it's in the repositories (the main ones anyway) any more than Windows users have control over what gets included in Windows update. That's not going to start a flame war - because it has nothing to do with users, and I'm not assuming anybody knows anything about the repositories except the repository maintainers. 

And you don't have to pay for the mythtv channel guide, that's been straightened out.

---

