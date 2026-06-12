---
title: "[SOLVED] Nvidia 7950 GT - Every Install method I can find fails in Gutsy"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by badmedic on 2007-10-27
I have spent the last 3 days trying everything I can imagine to get my 7950 GT card working with 3d in Ubuntu 7.10.

Tried Restricted Drivers manager. 
Tried Envy.
Tried at least 2 methods for manually installing the latest driver from the Nvidia site.
Tried a manual install of the newer beta driver from the Nvidia site as well.

I went through the necessary driver removal steps between these and even two full Ubuntu reinstalls just to make sure things weren't becoming a mess.

No matter what I try I end up with a failed attempt and my system booting in low-graphics mode :(

Anyone have any ideas?

---

### Post by badmedic on 2007-10-27
GRRRR!!!!

After digging through some log files (/var/log/gdm) I finally found that the system thought a power connection was missing on my card!

Adding the following to the device and screen sections of my xorg.conf file seems to have fixed things,

option "NoPowerConnectorCheck" 

OMG what a painful process this has been!
Not to sound negative, but I have to say... Between this video issue and another with my LAN I am not sure why I stuck with it. Vista (which I am trying to get away from) may be craptastic, but it hasn't wasted 15+ hours to get some fairly common hardware working. :(

Anyhow...Sorry for the rant. A working Ubuntu is a beautiful thing. I just wish the "working" part could happen easy enough for the average user.

Hope the info above helps someone out there waste a bit less time than I did!

---

### Post by ScottoGato on 2008-01-29
I just want to say thanks for your hard work, badmedic.

I have the same video card and had the exact same problem!

It's very much appreciated that you stuck with it to figure it out.

I can't seem to figure out a way to say thanks on here, but until then...+1 on the thanks!

---

