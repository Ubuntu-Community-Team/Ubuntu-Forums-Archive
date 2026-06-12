---
title: "Amarok Freezes When Attempting to Play MP3 in Feisty"
date: 2007-04-15
forum: Multimedia &amp; Video
---

### Post by vgrisham on 2007-04-15
Hi,

I've used Amarok 1.4.5 in Dapper for several months with few problems. Last night, I installed it on my new Feisty installation. It built a library with no problem. I then clicked on an mp3 to play it. It thinks for a while, then pops up it's little box to ask if I want to install mp3 support. It never finishes building that box however, and it will sit there indefinitely and totally unresponsive until I xkill it. 

Any ideas? MP3's will play without a hitch in Rhythmbox; could there be some conflict between xine and totem?

Thanks,
Vaughn

---

### Post by linda_linux on 2007-04-16
Go to amarok director, /usr/lib/amarok. There you will find install mp3. Click it , mp3 support will be installed. Then start amarok, it will work fine.

---

### Post by ChadMC on 2007-04-16
Thanks! I've been trying to get my amarok working for awhile. I hope they fix that in the final release of feisty.

---

### Post by vgrisham on 2007-04-16
> **linda_linux said:**
> Go to amarok director, /usr/lib/amarok. There you will find install mp3. Click it , mp3 support will be installed. Then start amarok, it will work fine.
Lovely Linda! Thank you! That solved it.

---

### Post by feril_grin on 2007-04-19
I am a new user to Linux...much less Ubuntu.  I have to thank all of you that know this product and share your wealth of knowledge.

Thanks to all of you

---

### Post by firstc624 on 2007-04-20
I have this problem too.

Thanks for the one who suggested to go to the usr/lib directory and install it manually.

Kudos

---

### Post by Endium on 2007-04-20
Hmm.. I had this problem too.  

The manual fix works though. Thanks!

---

### Post by akman360 on 2007-04-20
I Also Had this problem similar to this one. I figured out that the problem on mine is a missing libxine1-ffmpeg package. To install the libxine1-ffmpeg package, just run [COLOR="DarkOrange"]sudo apt-get install libxine1-ffmpeg[/COLOR] in terminal.  This should fix the problem.

---

### Post by aboutblank on 2007-04-20
Thanks! I had this problem too.

---

### Post by kylevan on 2007-04-20
well, I can tell you that this never got fixed for the final release of feisty...

thankfully I found this thread.

---

### Post by wataboutbob on 2007-04-20
playing mp3 files isn't a problem for me, but Amarok does freeze/become unresponsive when skipping to the next song or when populating playlists. Any ideas?

---

### Post by Gargamella on 2007-04-21
> **vgrisham said:**
> Hi,

I've used Amarok 1.4.5 in Dapper for several months with few problems. Last night, I installed it on my new Feisty installation. It built a library with no problem. I then clicked on an mp3 to play it. It thinks for a while, then pops up it's little box to ask if I want to install mp3 support. It never finishes building that box however, and it will sit there indefinitely and totally unresponsive until I xkill it. 

Any ideas? MP3's will play without a hitch in Rhythmbox; could there be some conflict between xine and totem?

Thanks,
Vaughn

me too!!! thank you for the thread

---

### Post by vgrisham on 2007-04-21
> **Gargamella said:**
> me too!!! thank you for the thread

You're welcome, and thanks to Linda for the workaround. 

By the way, this has now been confirmed as a bug: [https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/84967](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/84967)

---

### Post by vgrisham on 2007-04-21
> **wataboutbob said:**
> playing mp3 files isn't a problem for me, but Amarok does freeze/become unresponsive when skipping to the next song or when populating playlists. Any ideas?

Hmm. It sounds like the library database is messed up. Did you migrate your database from Edgy? If you don't mind having to rebuild your library, I'd blow it away and let it build fresh. To do this, exit Amarok completely, and delete collection.db from the /home/vaughn/.kde/share/apps/amarok directory.  When you go back into Amarok it will create a fresh database.)

If that is not an option, I'd post a question here: [http://amarok.kde.org/forum/](http://amarok.kde.org/forum/)

---

### Post by wataboutbob on 2007-04-22
> **vgrisham said:**
> Hmm. It sounds like the library database is messed up. Did you migrate your database from Edgy? If you don't mind having to rebuild your library, I'd blow it away and let it build fresh. To do this, exit Amarok completely, and delete collection.db from the /home/vaughn/.kde/share/apps/amarok directory.  When you go back into Amarok it will create a fresh database.)

If that is not an option, I'd post a question here: [http://amarok.kde.org/forum/](http://amarok.kde.org/forum/)

yes, the library was built from scratch. I don't have any files in my /home as all files are stored on my NTFS partition, so I had no problems just nuking the old 6.10 ext3 and making the 7.04 installation as a clean install.

Amarok stalled as usual at 61% (the same as when I used Edgy) when building the library, but once I let it run for over ~4 hrs I think, it finaly managed to build my 30GB library. The difference here though is that it hangs when playing the next song. I've gotten kinda used to it... its a pain though :D

"fa ina ma'al usri yusra" meaning "Verily, after hardship, comes ease"

could apply to my linux migration from XP....

---

### Post by SonicSteve on 2007-04-22
Thank you for this thread, I'm glad it was an easy fix. I just don't understand why Amarok couldn't play MP3 files but all my other players could. Was this just an Amarok stance against proprietary file types or is there a technical issue here?

---

### Post by stryderjzw on 2007-04-23
> **wataboutbob said:**
> playing mp3 files isn't a problem for me, but Amarok does freeze/become unresponsive when skipping to the next song or when populating playlists. Any ideas?

[http://amarok.kde.org/forum/index.php/topic,13452.0.html](http://amarok.kde.org/forum/index.php/topic,13452.0.html)

Maybe it's a problem with crossfading?  Try link above.

Justin

---

### Post by hagar_am on 2007-04-23
You are my personal hero ;) My mp3 works fine with amarok again:)

---

### Post by vargasman on 2007-04-24
I can hear my mp3's again...Thanks for the answer. It's wierd because in edgy it asked me if I wanted to install mp3 support when I tried to open one in amarok. This needs to be posted in the how-to forum.

---

### Post by Immolatus on 2007-04-24
I don't think this will be fixed until mp3 format is GPL'd but I thought it was nice of them to include the handy script.
See they can't include it by default .....but if the end user installs it it's ok. It's kind of like buying a chevy and installing a pioneer stereo. Chevy can't do it with out making a deal with pioneer, but if the consumer does it it's all good.
Oh and thanks for the thread...one headache down.:guitar:

---

### Post by nikkkko on 2007-04-25
This fixed it for me:

sudo apt-get install libmad0 libxine-extracodecs

(Kubuntu user)

---

### Post by amadeov on 2007-05-01
> **wataboutbob said:**
> playing mp3 files isn't a problem for me, but Amarok does freeze/become unresponsive when skipping to the next song or when populating playlists. Any ideas?

Mine is doing the same thing.  I can get one song to play, but it will quit after one song and will freeze entirely.

---

### Post by TechBlazer on 2007-05-01
> **linda_linux said:**
> Go to amarok director, /usr/lib/amarok. There you will find install mp3. Click it , mp3 support will be installed. Then start amarok, it will work fine.

Thanks linda_linux. I upgraded from Edgy with no problems. I ran into this problem when I did fresh install of Feisty. It's working now.

---

### Post by wataboutbob on 2007-05-04
> **amadeov said:**
> Mine is doing the same thing.  I can get one song to play, but it will quit after one song and will freeze entirely.

its been a long time since I'd logged in as I've been travelling. I had given up on getting Amarok working without hiccups until it was inadvertently fixed when I was installing the w32codecs to help DVD playback with VLC. 

[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

Amarok doesn't freeze anymore when playing the next song on the playlist. It doesn't use its usual 50% CPU process time either.... hope it helps for you. I wish I could understand why the w32codec has anything to do with Amarok though.

---

### Post by sorgud on 2007-07-18
THANK YOU SO MUCH LINDA!!!!!!


talueguito
raul

---

### Post by rahimveron on 2007-07-30
> **linda_linux said:**
> Go to amarok director, /usr/lib/amarok. There you will find install mp3. Click it , mp3 support will be installed. Then start amarok, it will work fine.

Thanks Linda that was the easiest way

---

### Post by Tranquilo on 2007-08-02
Thanks wataboutbob!
Solved my freezing problem and speeded up amarok.
Strange but true! :)

---

### Post by jupetsu on 2007-09-25
Hurrah! Thanks a lot! My Amarok is working now.:)

---

### Post by vgrisham on 2007-10-14
For anyone thumbing through this thread that still has this problem in mid-October...

Whatever the cause was, this issue doesn't arise with Amarok installed in Gutsy.

---

### Post by Ozztopia on 2007-11-11
I'm still using Feisty and Amarok 1.4.5. The solution to play MP3 songs, which linda_linux has suggested, is the easiest solution. Thanks!:)

---

