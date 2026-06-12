---
title: "share wifi with android and block Ads"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by phonicboom on 2012-02-08
hello, 

I asked this on an Android forum but realized that it is an Ubuntu question. 

I have a comprehensive /etc/hosts file on Ubuntu and I wish to share ubuntu's wifi with my android tablet with the idea being that if android is sharing the wifi from Ubuntu that Ads will be blocked getting to android because of the /etc/hosts file on Ubuntu. 

correct? 

I have to ask as I've tried and it seemed to not work (blocking Ads that is). I wonder if the sharing failed or my theory is dumb?

---

### Post by sikander3786 on 2012-02-08
I am also interested in this one. :)

Were you at least successful in sharing the Ubuntu's Internet over the Wifi to Android tablet? I've tried it a few times and came to know that 'Gingerbread' doesn't support Ad-hoc Wifi networks. Don't know if 'ICS' supports it.

I don't have to offer anything regarding the /etc/hosts file and blocking of the ads though.

---

### Post by satanselbow on 2012-02-08
Wifi tethering / adhoc networks is available in later version of a "clean" android environment. The problem arises with the tweaks that the various phone suppliers make to "customise" <-- read as "cripple" the default setup by disabling some services; frequently network related.

Depending how brave you are feeling you may want to look into finding an alternate rom for your phone (some may also require flashing a new kernel) [http://www.xda-developers.com/](http://www.xda-developers.com/) is a good place to look and for more "advanced" android hackery ;)

I have not tried the specific setup you are after on my xperia x10 mini pro but find the wifi has massively improved stability and flexibility (tethering etc) now that it is running the CM7 rom with the NAa kernel when compared with the SE stock flakey rhubarb it came supplied with ;)

---

### Post by phonicboom on 2012-02-08
thanks, 

I'm tempted to try a new rom on my tablet but probably not my phone, but that is another story and for now I'm keen to set up home wifi sharing - especially if I can block ads this way without needing to root and add an /etc/hosts to android.

---

### Post by satanselbow on 2012-02-08
All that said... you could just push your tweaked hosts file to your tablet ;)

[http://forum.xda-developers.com/showthread.php?t=514698](http://forum.xda-developers.com/showthread.php?t=514698)

You could then just connect to your wifi router (assuming you have one) as normal and get the same benefit as on ubuntu.

---

### Post by phonicboom on 2012-02-08
sanselbow - very promising option - thanks!

---

### Post by kerry_s on 2012-02-08
if your rooted, just install adfree from the Android market.

i use opera mobile & a urlfilter.ini file to block ads in just opera. no root needed.

---

### Post by phonicboom on 2012-02-08
hi, 

I was looking for a non root option as my first choice. 

a non root option would be very popular an beneficial to the android community.

---

### Post by kerry_s on 2012-02-08
> **phonicboom said:**
> hi, 

I was looking for a non root option as my first choice. 

a non root option would be very popular an beneficial to the android community.

see my edit above. attached the file for you here.
(first time I've ever found the need to upload from Android. lol )

---

### Post by phonicboom on 2012-02-08
Kerry_s wow excellent solution. 

opera is quite a bit quicker than stock too. 

thanks

---

### Post by phonicboom on 2012-02-08
erm... what do I do with this file?

---

### Post by kerry_s on 2012-02-08
> **phonicboom said:**
> Kerry_s wow excellent solution. 

opera is quite a bit quicker than stock too. 

thanks

you know how to use it or do you need need me to write up some instructions? 
that block list is very stream lined so as not to affect speed.

---

### Post by phonicboom on 2012-02-08
> **kerry_s said:**
> you know how to use it or do you need need me to write up some instructions? 
that block list is very stream lined so as not to affect speed.

help please  !) 

I have to go for a while now but will check back later thanks.

---

### Post by kerry_s on 2012-02-08
> **phonicboom said:**
> erm... what do I do with this file?

download it on your phone & remove ".txt", you can put it anywhere, i put mine in /mnt/sdcard/opera

in opera type "opera:config" in the address bar
search "urlfilter"
then just point it where you put it /mnt/sdcard/opera/filter.ini (if i remember right, i think it opens a file picker for the task, so click back till your at / then go from there)

---

### Post by phonicboom on 2012-02-08
love your work! 

that is an excellent solution. opera and this file in combination give a very fast and smooth web browsing experience. no Ads and no root required! 

big solve. 

> **kerry_s said:**
> download it on your phone & remove ".txt", you can put it anywhere, i put mine in /mnt/sdcard/opera

in opera type "opera:config" in the address bar
search "urlfilter"
then just point it where you put it /mnt/sdcard/opera/filter.ini (if i remember right, i think it opens a file picker for the task, so click back till your at / then go from there)

---

### Post by kerry_s on 2012-02-08
> **phonicboom said:**
> love your work! 

that is an excellent solution. opera and this file in combination give a very fast and smooth web browsing experience. no Ads and no root required! 

big solve.

your welcome!  
i love my Android mini tablet (galaxy player 5.0) i lock mine in landscape using orientation control. i don't even think about using a pc anymore. lol, the last time i tried i kept trying to touch the screen.

---

