---
title: "Tried various things, still not working..."
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by Cable on 2006-06-08
I've tried a couple things I found here, but my wireless is still not working.  I tried doing what is described [here]("http://ubuntuforums.org/showthread.php?t=185174"), but that did not work.  During/after this setup, never once did I see the light on the wireless card turn on (to verify that it is actually running).  It seems that Linux sees my wireless card, but doesn't know how to ***use*** it.  (Question:  Is there a way to remove what I did from that guide and start fresh to try again?)

     I was going to try ndiswrapper, but the driver file I downloaded was an exe, and for some reason I couldn't use cabextract to unpack the file (unless I did somethig wrong) to get to the .inf and .sys files.  So I don't know what to do there.  The driver file I downloaded is linked to on the [ndiswrapper list]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List").  The driver file is [here]("ftp://ftp.linksys.com/pub/network/WMP54Gv4_20040415.exe").  The ndiswrapper guide I was using is [here]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto").

     In the guide I posted in the first paragraph, it mentions towards the end (of the guide, not the thread) that the card is now set up to use B.  I really need to be able to use G, not B, due to the distance between my router and my computer.

Here's some info about my card just for reference:
Linksys WMP54G
Broadcom 4306 (V2)
Shows up as eth0, not wlan0 (which I've seen on the forums many a time)

If any more information is needed, just ask!  Hopefully someone has a solution to my problem.

---

### Post by DarthMandeep on 2006-06-08
You could use Wine to get the driver files from the exe packages.

---

### Post by Cable on 2006-06-08
Alrighty, I found the driver files in a zip, so I have those.  But now, when I go into ndiswrapper to install the driver, nothing happens after I tell it where the .inf file is.  It doesn't even appear in the installed drivers list.  The driver I found is in the Linksys website.  The driver is located on [this]("http://www.linksys.com/servlet/Satellite?c=L_Download_C2&childpagename=US%2FLayout&cid=1115417109934&packedargs=sku%3D1121874576430&pagename=Linksys%2FCommon%2FVisitorWrapper") page.

As I asked above, how do I remove the files/configuration that I did in the first paragraph of my first post?  I just want to start fresh and see if I can get ndiswrapper to work.

---

### Post by ComplexNumber on 2006-06-08
> I was going to try ndiswrapper, but the driver file I downloaded was an exe, and for some reason I couldn't use cabextract to unpack the file (unless I did somethig wrong) to get to the .inf and .sys files. So I don't know what to do there.
do what i did. installed the exe on windows, grabbed the sys and inf files, then uninstalled.

---

### Post by Cable on 2006-06-08
>  do what i did. installed the exe on windows, grabbed the sys and inf files, then uninstalled.
Yeah, I got the driver files I needed.  Now I just need to know how to "reset" all of my wireless configuration so I can start fresh.

---

