---
title: "Flash Not Working For Some Sites AMD64 Intrepid"
date: 2008-11-15
forum: Multimedia Software
---

### Post by slowtrain on 2008-11-15
I've been struggling for some time to get Flash to work on my AMD64 machine, in which I'm running 64bit Ubuntu.  Just upgraded to Intrepid, but that did only part of the trick:  I can now see Flash videos on many sites, just not when the videos are longer ones, such as full episodes on NBC or CBS.  Those look like they start to load, but then nothing happens.  

Is this just me, or are others having this problem?  Does the same thing happen w/ Firefox / Flash running 32 bit?  If not, I guess I could install 32 bit using virtualbox (have had no luck trying to get 32 bit libraries running directly in the 64 bit system.

I've precisely followed the instructions and troubleshooting suggestions in the Comprehensive Multimedia & Video Howto, so I should have all the necessary codecs and software.

Any suggestions welcome!

---

### Post by slowtrain on 2008-11-15
A new bit of information:  I tried installing Ubuntu Intrepid 32 bit in VirtualBox, again w/ all the codecs & so forth.  As in my 64 bit installation, I can get simpler / shorter Flash movies, but not full episodes on the major channels.  The new installation doesn't have the complication of a lot of different software being installed, such as Firefox extensions.  Either the Intrepid version of Flash just doesn't play certain kinds of Flash movies, or there's something blocking these movies.  I've checked in my Firestarter firewall, but don't see any effort to block these streams.

There is another wrinkle to this:  I was getting Flash just fine in Hardy up till some point this summer, and then it stopped working, I believe, after an update.

---

### Post by zeddock on 2008-11-24
Same problems here.

zeddock

---

### Post by Arup on 2008-11-24
Please upgrade to x64 Flash, instructions can be found on the x64 thread. Everything works fine, you must totally remove older x32 flash and nsplugin wrapper.

---

### Post by slowtrain on 2008-11-24
Hi Arup:  Do you mean [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490) and are you suggesting the Flash 10 install (I don't see anything about x64 specific flash)?  I guess I'm a bit nervous about using the instructions there because they rely on calls to software on a non-institutional server--would be an easy way to introduce malicious software.

---

### Post by slowtrain on 2008-11-28
Looks like I got Flash working--for the most part!  I installed Flash 10, 64-bit using instructions here:  [http://labs.adobe.com/technologies/flashplayer10](http://labs.adobe.com/technologies/flashplayer10) .  These instructions have the virtue of not installing software from people's private websites (I'm too paranoid to do that).  CBS videos work.  NBC Video Rewind still doesn't, but this is an alpha player.  Have heard that some people have problems w/ the player (instability etc.), but others say it's more stable.

---

