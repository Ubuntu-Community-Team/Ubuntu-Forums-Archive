---
title: "iPhone music sync with Rhythmbox"
date: 2012-04-12
forum: Multimedia Software
---

### Post by grj23 on 2012-04-12
Hi

I feel like this should work, but somehow for me it never has, and I don't understand what I'm doing wrong.

I would like to copy music from my library (Ubuntu 12.04 Beta) onto my iPhone 4.  Here's what happens (and has been happening for about 2 years (with 10.10), and is the only reason I keep a windows partition somewhere in the house):
1. I plug the iPhone in with USB
2. It detects it fine, noting that there are photos and music on the device and offering to open up the relevant bits.
3. On the photos front it's fine, and it also opens up showing the file structure.
4. I open Rhythmbox, and my iPhone shows there, all present and correct
5. I ask it to sync, and it shows me how the iPhone memory will be before and after (I check the library box)
6. It then spends some time copying the music across.  In the end, the iPhone in Rhythmbox has all the songs in it and seems to have worked fine.
7. When I go to the iPhone, under Music it says "No Content".
8. In general the memory space is then gone and undeleteable until I restore the whole thing using iTunes.

The phones are not jail-broken.  I've tried this on iPhone 3 and 4 and various different iOS.  I've used 10.10 & now 12.04.  
I tried to follow the instructions 
[here]("http://askubuntu.com/questions/78535/how-to-install-libimobiledevice") but the repository is not found:
```
W: Failed to fetch http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found
``` 
(ditto with maverick).

Most of the (surprisingly few) queries about this have someone point to [this supposedly up-to-date wiki]("https://help.ubuntu.com/community/PortableDevices/iPhone") which clearly hasn't been updated in two years and does not deal with this problem.

The thing I don't get is that the phone has been freshly installed, the ubuntu has been freshly installed, everything appears to work fine, and then something at the last second just fails.

Ideally I could get it to work in the manner described above, but with a happier final step.  What should I be trying?  Should I push to get the latest libimobiledevice (is there a repository for that)?  Should I go for the jail-break route (hopefully not, and anyway, I think it might not be possible just yet because I updated one of the phones to 5.1 or whatever the latest thing is)?

It was exactly the same for my wife's iPhone 4 with 4.1 (I think), and for mine on 4.0 (before I updated it).

I have this image of millions of happy iPhone-Ubuntu users out there who don't get this problem?  Is that the reason for the lack of complaints on this issue, or is it that most people don't even bother to try the non-windoze/mac route?  ;-)

Really would appreciate any advice and or links to anything helpful.

G

---

### Post by Kaizoku001 on 2012-04-13
I know how you feel. I also had the same problem, and will probably try 12.04 later this month.

I hope somebody finds a solution to this problem.

on the other hand, it would also be great if we could install itunes in 12.04, like this you can also sync the apps. haven't had much luck with that in 11.04

---

### Post by grj23 on 2012-04-13
So I thought I'd add a few more details. 
Firstly, my entire collection is mp3 (thanks to the wonder of Sound Converter).

Secondly I saw some links suggesting getting rid of a file called gconf.xml in a hidden director in your home. 
That location doesn't exist in 12.04, and the file exists is a similar location but removing it makes no difference. A [blog]("http://mildred-of-midgard.dreamwidth.org/59465.html") found some other way of fiddling with this gconf.xml, but similar fiddling did not work for me. Although it was done in a state of complete ignorance, so if you're better at this stuff please have a go and post back!

Lastly, my iPhone is showing several GB  of 'other' (read corrupt music) in Rhythmbox and in iTunes (on my work computer where I don't have any music and it's not the assigned computer, so I can't do much with it). 

Does anyone else share this experience, or know of a cunning step that I'm missing?

Thanks

---

### Post by matt2053 on 2012-04-13
I'm having the exact issues described (my library "syncs" but then my iPhone says "no content when I go to play music).

I hope someone knowledgeable can get this working. I'm not going to have access to Windows for much longer.

---

### Post by grj23 on 2012-04-14
Has anyone tried this with a jail broken phone? Does it have any more success? Or with different music players? Or via a wireless connection?

---

### Post by matt2053 on 2012-04-14
I wonder if this thread would a) be more appropriate, and b) get more pairs of eyes on it, if it were in the "Ubuntu +1 (Precise)" subforum?

---

### Post by cody1233 on 2012-04-14
I have had no luck with my Jailbroken iPod syncing in Ubuntu either.  I have had minimal breakthroughs, however, in "ssh"ing into my iPod and syncing music that way.

---

### Post by grj23 on 2012-04-15
Hi.  Thanks for the feedback on the jail-broken phone.  Useful to know!

I've posted this in the Precise+1 forum as suggested.  Link is [here]("http://ubuntuforums.org/showthread.php?t=1958866")

Thanks again!

---

### Post by Hoverboy on 2012-04-18
I posted in the new thread already, but just so as many people will see it as possible I'll post the answer here too.

You can sync an iPhone 4 in linux, it is kind of a pain, it does have to be jailbroken, here's the guide:

[http://marcansoft.com/blog/2011/01/s...es-with-linux/]("http://marcansoft.com/blog/2011/01/syncing-music-in-new-idevices-with-linux/")

---

### Post by qwertyu on 2012-04-29
I have exactly the same problem with my iphone 3G 3.2.1. I tried all the solutions (disabling MTP plugins, banshee or rhythmnbox, adding hashtab file, syncing with itunes, changing database version from 5 to 4) but nothing works!

I'm surprised that few people reported this problem.
Previously with 11.10 and 11.04 with same firmware on the iphone it was working!!

---

### Post by grj23 on 2012-05-07
Hi

So I'm thinking of trying it with Ubuntu One.  If it's really wireless syncing, and ability to have it all locally on the iPhone, then I'm pretty keen.  It's about $40/year, but I think I could stretch for that to finally be done with Windows.

Has anyone had any experience with this?  I'm assuming that the Ubuntu One app runs and has it's song data completely separately from the native iPhone music player and so it's just a question of getting rid of the native player and using the Ubuntu One player?

Any real user experiences to say that this actually workks?

---

### Post by bowhat on 2013-01-26
Not sure if it'll work for IPhones or IPod but this script worked a peach for Android:
[http://ubuntuforums.org/showthread.php?p=12475542](http://ubuntuforums.org/showthread.php?p=12475542)

It prompts you for all your rhythmbox playlists and lets you pick which ones to sync. Moves the files over. Creates a playlist on the device as well. It is a sync not a copy -- so other music files on your device on the Music folder get removed.

Pretty sweet.

---

