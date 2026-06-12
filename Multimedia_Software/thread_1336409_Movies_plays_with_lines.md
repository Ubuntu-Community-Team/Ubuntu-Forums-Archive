---
title: "Movies plays with lines"
date: 2009-11-24
forum: Multimedia Software
---

### Post by ezacon on 2009-11-24
I have reinstalled my HTPC with Ubuntu 9.10/64. I was running 9.04 before. From the 9.10 reistall, i have a problem playing movies, that was not present with 9.04 with exactly same hardware.
When i play movies, when the cam moves, there appears lines, like sync problem (see attached image).
[IMG]http://www.infonegocio.com/acopen/screen.jpg[/IMG]
It happens with al codecs, all players and all sources.
I have a Nvidia 8300 chipset with latest ubuntu repositories nvidia drivers. I can move windows inside desktop with all visual enhancements without problem. My system has enougth power to play full HD ( AMD dual core 3000Mhz and 8Gb ram).
How can i find the problem?
Where to start?

---

### Post by hwttdz on 2009-11-24
Do you still observe the behavior if you disable all desktop effects?  system->preferences->appearance->visual effects->none

---

### Post by ezacon on 2009-11-25
I have just tested it now and it looks like the problem disapears.
I need to make moore testings.
Anyway, how is it possible in 9.04, with same effects turned on and same hardware the movies plays fine?.
I dont need the destop effects, so i have now dissabled all of them.
I have tested codecs, kernels and lot of stuffs but never han the idea to disable visual effects. Thanks

---

### Post by ezacon on 2009-11-26
Confirmed. It works fine without desktop effects.
Thank you HWTTDZ.

---

### Post by hwttdz on 2009-11-26
And the next thing I would check would be to enable desktop effects one by one, also possibly try different driver versions.  I think it likely that a possible change in video driver version is causing the trouble.

---

### Post by Boksa on 2011-03-31
i have same problem got nvidia gtx260m, tried driver from ubuntu, and from nvidia site, changed effects to none (i would like to have them on) but still no effect.
I'm on ubuntu maverick 10.10.

thanks in advance


ok searched little bit more and found solution here 

[http://ubuntuforums.org/showthread.php?t=1305320](http://ubuntuforums.org/showthread.php?t=1305320)

it worked for movies, but i still have some lines when watching clips on youtube - it's not over yet !! 
hope this helps somebody

---

