---
title: "Tv out and ati driver"
date: 2005-12-25
forum: Multimedia &amp; Video
---

### Post by splater on 2005-12-25
Hi everybody !

I come back with this point, cause I am sure lots of people are interested in this subject !!!

I have my ATI mobility 9700 working fine and TV out as well !!! I can see application on clone mode on tv and laptop BUT not videos .... :( I have to change my xorg.conf to have video on tv or on laptop .... 

Does anyone know a way or to have video on both or to be able to change (without changing xorg.conf and restartind X server) from laptop to TV and vice versa ...

Thank you for your help !!!

Bye

---

### Post by Treviño on 2005-12-25
What do you mean about changing xorg.conf file? Maybe adding *Option "OverlayOnCRTC2"*?
In my case the only way to see videos was changing video output in the software engine used as a player (i mean VLC, gstreamer...).

Suggestions?

---

### Post by jacek2v on 2005-12-27
I have ATI 9550 in desktop computer, I use fireglconsole to switch TV Out but always Xserver restart needed.
Or
I think if I use high resolusion ( > 1024x768 ) then TvOut is disable, switch to 1024x768 and TvOut is enable - I try this at evening.

---

### Post by splater on 2005-12-27
Thx trevino for your answer. I tried to change some parameters on my VCL player. I succeded to have the 2 videostreaming on tv and laptop !!! But (there is always a but !!!) it seems that the driver doesn't support well the overlay as the streaming is quiet slow when I switch to full screen ...

Anyone has an idea ?

Thx

---

### Post by Adalgisel-Grimo on 2005-12-28
@Splatter:

How did you get the tv-out working with your ATI?
 
I got a Mobility 9600 and had no success. I would be glad, if you would post your experience.

---

### Post by splater on 2005-12-28
OK, it's quite simple indeed. 
I install ubuntu 5.10 and just after I download the last ati driver on the web site. You run the script downloaded and follow the instruction (you have too run it as root).

I almost choose all the default option during the installation ( I choose only the clone mode within the tv out option). If you have a 1280x800 wide screen, it doesn't works with the automatic xorg.conf generation, you have to put it manualy afterwards ...

I leave you my xorg.conf if you have to have a look !!!

Chears.

Does anyone have an idea about the clone mode and how to get full support of overlay when using tv out with ati driver????



++

---

