---
title: "ATI x1400 memory issue"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by Marxen on 2006-06-21
I have a Dell E1505 (6400) laptop with the 256MB ATI x1400 video card.  I was able to get the fglrx driver (8.25.18) working with 3D acceleration.  However, in the ATI Control Panel the Information tab is showing that the video card only has 128MB of memory.  

I don't know if this is a configuration problem or an ATI driver problem.  Any help on this issue would be greatly appreciated.

-Luke-

---

### Post by Bollenator on 2006-06-22
I haven't installed Ubuntu yet on my e1505, but I recall reading that the X1300/X1400 ATI cards that come with the e1505 share half their memory with the system; so our X1400's with "256MB" of video memory actually have 128MB dedicated video memory and grab up to 128MB of system memory for textures and the like.

I'm pretty sure it has nothing to do with Ubuntu, though you'd expect ATI's own control panel would know the difference.  Hope that helps!

---

### Post by Marxen on 2006-06-22
Thanks for the reply.  I figured that was part of the issue, I found that ATI calls it HyperMemory.  My BIOS only shows that there is 128MB of video memory, but in WindowsXP the ATI drivers show that there is 256MB of available memory.  So it seems to be regulated by software/drivers.

I guess the question is, is Ubuntu using only 128MB of video memory or is it using the 128 + 128 of system memory?  If it is only using the 128MB of video memory, is there a way to enable the use of "HyperMemory"?  Is this something that would need to be done in the xorg.conf file or is this a problem with the ATI drivers that ATI needs to address?

Any information or insight on this would be greatly appreciated.

---

