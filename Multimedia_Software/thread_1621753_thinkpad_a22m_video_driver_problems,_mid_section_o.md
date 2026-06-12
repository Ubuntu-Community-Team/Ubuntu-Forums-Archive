---
title: "thinkpad a22m video driver problems, mid section of desktop blurry"
date: 2010-11-14
forum: Multimedia Software
---

### Post by Bertram Garonfolo on 2010-11-14
hi 
I have a problem with the graphics on my thinkpad a22m laptop.
specs: 
900mhz cpu
256 ram 
20gig hd 
??ati rage mobility m3 video card ??

when I start up ubuntu (10.10) and reach the desktop, the screen is messed up. The center of the screen becomes blurry, and it looks like what is normally the right part of the screen is duplicated in the middle of the screen (with what should be the middle of the screen disappearing).

I think its an ATI video card, and I tried to install different driver from Softwarecenter but no succes.

I know the screen is working, because when I boot forinstance, the Ibm logo is showed nicely across the screen. So its not a hardware issue. Another thing, I got puppy linux to work correctly after having the same grapphic issues on that OS when I first installed it. But some how I managed to get the right drivers. But as I like ubuntu more, I would appriciate your help with figuring this out :-)

ps. when I try to setup screen resolution in System>Settings>"resolution", Ubuntu says "unknown display" (marked with red color).

thanks in advance
cheers
Bertram

---

### Post by acy76 on 2011-02-15
In case anyone is looking for information on this problem:

[This thread]("http://georgia.ubuntuforums.org/showthread.php?t=828588") should have all you need to fix the problem - one of the [responses]("http://georgia.ubuntuforums.org/showpost.php?p=6481426&postcount=43") is regarding the Thinkpad A22m specifically. The machines in the thread all seem to share the ATI Rage Mobility 128 video card.

You'll also need to create the xorg.conf file for newer (10.04+?) versions of Ubuntu, as it does not exist by default (mentioned in the same thread [here]("http://georgia.ubuntuforums.org/showpost.php?p=9806280&postcount=80") on page eight).

I'll mention in passing that I found this information while searching for a way to fix this same issue on my Thinkpad A22p (notice the differing last character in the model name). As the A22p has a different screen resolution than the A22m mentioned in the thread I linked, anyone looking for A22p information should see the Debian forums post [here]("http://forums.debian.net/viewtopic.php?f=6&t=38600"). One of the responses contains an xorg.conf listing that worked for me verbatim on lubuntu (lightweight ubuntu) 10.10 and the aforementioned Thinkpad A22p.

---

