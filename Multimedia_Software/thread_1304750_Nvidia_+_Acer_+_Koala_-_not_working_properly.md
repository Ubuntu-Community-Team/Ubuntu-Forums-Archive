---
title: "Nvidia + Acer + Koala - not working properly"
date: 2009-10-29
forum: Multimedia Software
---

### Post by Rytis on 2009-10-29
Hello,
I just installed Ubuntu 9.10 and I am in trouble. Damn system can't detect my 22" screen and 1680x1050 resolution. I used to install drivers (version 173). 

Anyway, system can not detect my monitor:
[[IMG]http://img442.imageshack.us/img442/4804/nuotraukax.th.png[/IMG]](http://img442.imageshack.us/i/nuotraukax.png/)
[[img]http://img300.imageshack.us/img300/8571/nuotrauka1.th.png[/img]](http://img300.imageshack.us/i/nuotrauka1.png/)
[[img]http://img442.imageshack.us/img442/7580/nuotrauka2.th.png[/img]](http://img442.imageshack.us/i/nuotrauka2.png/)
(ne&#382;inomas - unknown)

AS can you see, maximum possible resolution is 640x480. 
How can I fix it? 

Ubuntu is called user-friendly, but some damn drivers can't work :/

Thanks.

Oh, yes.

Monitor: Acer x223w
Video card: Geforce fx 5200

---

### Post by Rytis on 2009-10-29
I really do not like bumping threads, but I really cant do anything on resolution 800x640..

Help please..?

---

### Post by rocketflame on 2009-10-29
try updating the drivers, i believe nvidia is at v. 190?

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by Rytis on 2009-10-29
Thanks, but it gives only 
**Version: 173.14.20 **

That's exactly version which I am using.

---

### Post by rocketflame on 2009-10-29
ok, my card has v. 190...

did you install the driver by yourself or did ubuntu do it for you?

try the other one,

if that doesnt work, post your xorg.conf, then we'll see what happens

---

### Post by Rytis on 2009-10-29
I installed it via hardware drivers updates:
[[IMG]http://img88.imageshack.us/img88/7381/nuotrauka4.th.png[/IMG]](http://img88.imageshack.us/i/nuotrauka4.png/)
(it doesnt give higher than 173)
(I tried both + v185)

And my xorg.conf looks like screwed much:
[http://pastebin.com/m540b2f3b](http://pastebin.com/m540b2f3b)

---

### Post by CharlesA on 2009-10-29
Try installing it using envy-ng

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

sudo apt-get install envy-ng

---

### Post by Rytis on 2009-10-29
> **CharlesA said:**
> Try installing it using envy-ng

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

sudo apt-get install envy-ng

That doesnt help.
I am using ubuntu over 2 years, but never had this weird problem. For the gods sake...

---

### Post by Rytis on 2009-10-29
I managed to fix it.
Here is my xorg.conf, if someone needs it:
[http://pastebin.com/f4b08fafd](http://pastebin.com/f4b08fafd)

---

### Post by niite on 2009-10-29
Nvidia has released a new driver for Geforce  - you can get it here.. it's version 190.42.  works great for me..  

This is for 64bit..  [http://www.nvidia.com/object/linux_display_amd64_190.42.html](http://www.nvidia.com/object/linux_display_amd64_190.42.html)

---

