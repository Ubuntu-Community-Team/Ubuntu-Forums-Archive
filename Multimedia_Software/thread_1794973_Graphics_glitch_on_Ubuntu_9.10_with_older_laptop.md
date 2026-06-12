---
title: "Graphics glitch on Ubuntu 9.10 with older laptop"
date: 2011-07-01
forum: Multimedia Software
---

### Post by K-Ghidorah on 2011-07-01
Greetings all :).  First time poster and an admitted n00b.

I recently installed Ubuntu Karmic Koala onto my old IBM Thinkpad (I THINK it's an X23 model, but don't quote me on it).  The only reason I went with the older, obsolete version is, honestly, it's the only one that will run on it.  That said, I love it and see no reason to go back to Lose-dows full time (I'll still get a Windows machine in order to learn the inner workings of it... thinking of going back to school for a tech job, so the knowledge will do me good).

One problem though.

When I bring up various windows (most disturbingly, my system monitor), I get a bizarre glitch.  It's hard to describe, so I'll give a screencap.

[IMG]http://img.photobucket.com/albums/v450/Nyarlathotep9/screenshot_001.png[/IMG]

I apologize if this has already been posted in a previous thread.  If it has, PLEASE direct me to it.

Thanks in advance!
~K

P.S.  I'm also a n00b in regards to the inner workings.  I know what they're supposed to do, but I don't know the actual names.

---

### Post by snowpine on 2011-07-01
Ubuntu 9.10 has reached its "end of life" and is no longer supported in any way. It's quite possible this graphics bug has been fixed in a newer release; I would suggest trying Live CD's of 10.04 (the long-term-support release) and 11.04 (the current release) to see if they have better support for your graphics card. 

Speaking of which, what kind of graphics card do you have? That will help you find relevant information on the forums. Good luck! :)

---

### Post by K-Ghidorah on 2011-07-01
Tried that.  Laptop wouldn't boot up after installation.  I've reinstalled this OS about 5 times before I gave up on finding anything recent that'd run on it.

I honestly don't know what kind of graphics card is in this, and, embarrassingly, I don't know how to find out.  Like I said, I had to guess as to even what kind of computer I have, other than that it was an IBM Thinkpad.  I know it has a Pentium III processor, 1.13 GHz speed, 20 GB HD, and **I THINK** 256 MB of RAM.

What's the command in Terminal to find out what kind of video card I'm in possession of?

**EDIT:**  Installing Envyng right now so I can get the updated graphics drivers and maybe, just maybe, figure out WTF kind of video card I have.

---

### Post by snowpine on 2011-07-01
No release of Ubuntu will run well on a Pentium 3 with 256mb RAM.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements) 

Give Lubuntu or Xubuntu a try, or possibly an even lighter distro like Puppy. :)

---

### Post by snowpine on 2011-07-01
'lspci' is the terminal command to identify your card. :)

---

### Post by K-Ghidorah on 2011-07-01
I found that out AFTER I tried installing the more recent versions (Ub 10.04 LTS via upgrade, Linux Mint 10, etc) and felt like a total moron for not having checked first.  The LiveCD of Ubuntu 11.04 wouldn't even run.  At this point, I finally was able to get Karmic to run my WMV files and watch YouTube videos, so you can understand my reluctance to go back to square 1.  For right now, 9.10 works well enough overall, and well, this is my only computer.

Yeah, I know... lame.

I'll be looking into Xubuntu and, if I can run my video and music files,  and watch my YouTube videos, I'll get the LiveCD and try that.  I  already plan to order the Legacy OS 2 disc from OSDisc.com.

BTW, I did some snooping on my own (probably what I shoulda done in the first place *facepalm*) and according to lspci my vid card is a "ATI Technologies Inc Radeon Mobility M6 LY". EnvyNG was no help.

---

### Post by K-Ghidorah on 2011-07-01
> **snowpine said:**
> 'lspci' is the terminal command to identify your card. :)

Thanks :).  I began snooping after I asked, and felt like a bit of a dolt when it was maybe the third entry after my Google search.

---

### Post by snowpine on 2011-07-01
I searched and found a ton of discussion on the forums about your card, including the mega-thread:

[http://ubuntuforums.org/showthread.php?t=246746](http://ubuntuforums.org/showthread.php?t=246746)

The early information is very outdated, but towards the end of the thread there is some info on 9.10 and newer...

---

### Post by K-Ghidorah on 2011-07-01
> **snowpine said:**
> I searched and found a ton of discussion on the forums about your card, including the mega-thread:

[http://ubuntuforums.org/showthread.php?t=246746](http://ubuntuforums.org/showthread.php?t=246746)

The early information is very outdated, but towards the end of the thread there is some info on 9.10 and newer...

Thank you very much, Snowpine, for directing me to this thread.  I've got it (and this thread) bookmarked for when I'm ready to tackle this in a few days (got plans this weekend).  Right now, I'm too &@%#@ tired to deal with this tonight and I have work tomorrow morning.

And I thank you for your patience :D.

Ubuntu, and its community rocks.  'Nuff said.
:guitar:

---

