---
title: "barebone ideq 330p and Kubuntu 7.04 AMD64"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by dr_squalo on 2007-05-05
here is my little odyssey with the new Feisty Fawn and the Ideq 330P Barebone.

It took me almost 8h in sum of my rare sparetime for installation.

The first challenge was running a video-mode of 1366x768 with 
a NVIDIA 6600. After downloading the beta NVIDIA drivers and messing
around with modelines and Xorg.conf it worked (but getting the right frequencies
wasn't that easy). IMHO: only expert-mode

The second challenge was to run WLAN (a must, cause no wire access the router)
The problem was: No WPA2 support comes along the ISO-CD Image. 
First I have to download it. But how with no access? 
Moving the whole system to the router was sucking work.
Finally it did work.

The third challenge was setting up my TV-Card. It is a DVB-S Twinhan (1022A) and
all modules were loaded (I thought). This costs me really a lot of time finding out, that
at last the dvb-bt8xx module (and its depends) were not loaded automatically.
Did this manually and some other modules.conf stuff and at least I could run Kaffeine
(but no Xawtv nor Kdetv nor MythTV. MythTV has btw. a really awful UI handling)
but with **no sound**!
Here I stopped further investigations
cause still these points are no working:

[LIST]
[*]still no sound (even no noise)
[*]no awaking after standby
[*]no awaking after hibernate
[*]no heat control (got dropp offs)
[/LIST]

 
Finally I got to say, that after all the years of developement  'Linux' is not
the right OS for Multimedia in a handsome way.
I got running two servers (/wo X) very well (6.06 and sarge 3.1)
but in this case WinXPHome has won the race clearly.
It costs me 80 bucks and 1 hour of work and everything work fine (until now :-)
Sorry, if I post a sentence like this here - this should be no bashing.

Regards

---

