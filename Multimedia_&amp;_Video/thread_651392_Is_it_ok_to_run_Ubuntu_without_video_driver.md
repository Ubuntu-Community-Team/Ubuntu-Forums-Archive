---
title: "Is it ok to run Ubuntu without video driver?"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by Jahgro on 2007-12-27
Ok so I have Ati Radeon HD 2600 Pro AGP graphics card.  I have tried absolutly everything i know of to get it to work, and i just can't.  I'm not that good with linux yet anyways but i've worked on it for two days straight.

Anyways it seems to run ok without a driver.  I can't do anything graphics heavy on it like play zsnes or anything, but normal use it works fine.

Can i just use it how it is or will that not be good.  

Also i'm using 7.4 feisty, do you recomend i upgrade to 7.10?

Thanks
  Jahgro

---

### Post by icheyne on 2007-12-27
> **Jahgro said:**
> I can't do anything graphics heavy on it like play zsnes or anything, but normal use it works fine.
Can i just use it how it is or will that not be good.  


Should work fine for normal use. You won't be able to play games or start Google Earth - that's about it.

>  Also i'm using 7.4 feisty, do you recomend i upgrade to 7.10?

It fixed quite a few problems for me.

---

### Post by Yellow Pasque on 2007-12-27
Have you tried the RadeonHD open-source driver yet? It should at least give you full 2D support.

---

### Post by Jahgro on 2007-12-27
No i haven't tried the Radeon HD open-source driver yet.  any idea where i can find it or should i just google it.

Also once i install a driver that doesn't work, i'm kind of stuck and have no idea how to get back to where i was before the driver install.

So i don't want to try this if i'm going to have to reinstall everything all over again.

Thanks
   Jahgro

---

### Post by terminal on 2007-12-27
I have ATI radeon hd2600 pro pci express edition compeltely working on 7.10 gutsy . Open source driver as well as fglrx driver provided in gutsy both DOES NOT work for me . I was able to get it working with latest ATI drivers released on their site . I am sure fiesty will haev no problem running it . 
Follow every instruction on this wiki and u should get it working . 
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)


Whenever u get stuck  select recovery mode from grub . you will land at root prompt just type "dpkg-reconfigure xserver-xorg" from driver list select vesa and just  follow further instruction and you should have graphics on next boot .

---

### Post by Yellow Pasque on 2007-12-27
A recent version of radeonhd was not provided in gutsy the last time I checked. Also, keep in mind that AMD is releasing the specs for M76/Radeon 2400 this week (as well as RS690/X12x0), so the driver should have 2D/3D acceleration soon.

---

### Post by Jahgro on 2007-12-27
> I have ATI radeon hd2600 pro pci express edition compeltely working on 7.10 gutsy . Open source driver as well as fglrx driver provided in gutsy both DOES NOT work for me . I was able to get it working with latest ATI drivers released on their site . I am sure fiesty will haev no problem running it .
Follow every instruction on this wiki and u should get it working .
[http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)


Whenever u get stuck select recovery mode from grub . you will land at root prompt just type "dpkg-reconfigure xserver-xorg" from driver list select vesa and just follow further instruction and you should have graphics on next boot .

I tried both methods of this and all i got was a black screen where i couldn't do anything.  

I really appreciate all of your guys help though.  I guess i just will have to play games on my other pc.

thanks again.  Oh by the way, thanks for the dpkg-reconfigure xserver-xorg command line, not only did it revert my system back, it also gave me the option of having 1152x854 resolution which i love, and it works great so thanks!

---

