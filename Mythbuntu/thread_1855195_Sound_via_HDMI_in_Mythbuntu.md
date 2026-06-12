---
title: "Sound via HDMI in Mythbuntu"
date: 2011-10-05
forum: Mythbuntu
---

### Post by MickSulley on 2011-10-05
Hi,
New install of Mythbuntu 11.04 and I am trying to get sound to work via the HDMI cable to my TV.  Currently I get no sound at all.  

In order to try to diagnose the problem and prove the hardware is OK I have installed Ubuntu 11.04 as a dual boot on the same machine and I have got the sound to work there by going to System > Preferences > Sound and on the hardware tab selecting the correct HDMI output hardware profile.  How can I do this in Mythbuntu?  I guess I need to install something, but what?

Thanks
Mick

---

### Post by nickrout on 2011-10-06
> **MickSulley said:**
> Hi,
New install of Mythbuntu 11.04 and I am trying to get sound to work via the HDMI cable to my TV.  Currently I get no sound at all.  

In order to try to diagnose the problem and prove the hardware is OK I have installed Ubuntu 11.04 as a dual boot on the same machine and I have got the sound to work there by going to System > Preferences > Sound and on the hardware tab selecting the correct HDMI output hardware profile.  How can I do this in Mythbuntu?  I guess I need to install something, but what?

Thanks
Mick

You need to set the output device im mythtv from settings|general about the 4th page. scan for audio devices then choose the one you want. It is probably something like alsa:HDMI.

---

### Post by PhilWig on 2011-10-07
I found this helpful when configuring sound to HDMI:
[http://ubuntuforums.org/archive/index.php/t-1140776.html](http://ubuntuforums.org/archive/index.php/t-1140776.html)
see the entry about alsamixer by DrJohn999 dated 29 April 2009

HTH
Phil

---

### Post by nineironputt on 2011-10-08
Is it possible to have more than one audio output working at the same time, for instance HDMI as well as an on board audio?

---

### Post by nickrout on 2011-10-08
> **nineironputt said:**
> Is it possible to have more than one audio output working at the same time, for instance HDMI as well as an on board audio?

Yes, there are ways to do this, search the mailing list archives.

---

### Post by MickSulley on 2011-10-22
I have sort of fixed it.  I gave up on Mythbuntu and worked with a standard Ubuntu install, that has the tools needed to get HDMI sound working.  I installed MythTV and various other Myth bits and it is all fine.  This approach has also solved problems I had with networking and some other stuff.  It looks just like Mythbuntu now, just got LibreOffice and so on, but I can always remove them.

---

