---
title: "Installing a new video card in 9.04"
date: 2009-07-08
forum: Multimedia Software
---

### Post by Adamras on 2009-07-08
I have a build of 9.04 goin' on to which I have been using the onboard ATI graphics card.  Today I purchased a Nvidia 260GTX card.  I put it in, booted it up and what happens is:

I see the Ubuntu screen, then the scrolling ubuntu screen indicating that the OS is loading what is needs.  Then when it would ususally kick up the login in screen I am shown a command prompt login for 1.5 sec, a flicker of the screen, the prompt again and then the screen goes black for another 1.5 sec. Then a flicker again with what it looks like it's attempting to load the logon screen but then the screen goes black and the system is totally frozen.

I have disabled the onboard video.

I thought maybe it was not enough power so I went and got a new PSU.  To no avail.  I thought then maybe I will try to boot from the cd to see if it's the card or the install (or whatever).  With the boot cd it loaded just fine.

Does anyone have any suggestions as to what I can try to remedy this and help me not have to rebuild the system to get it working?

The motherboard with the on-board video is:
MA78GM-US2H

Thanks in advance.

I'm kind of a newb but can follow directions very well :)

---

### Post by Sub101 on 2009-07-08
If you boot into recovery mode from grub, you should be presented with an option to configure X. 

Try that, then continue with boot.

---

### Post by gruebel on 2009-07-31
I had the same problem (Radeon HD4850 to GTX 260). Tried almost everything before I found the simple solution, apt-get remove --purge *fglrx* :)

---

