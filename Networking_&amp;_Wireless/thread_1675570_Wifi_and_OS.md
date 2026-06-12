---
title: "Wifi and OS"
date: 2011-01-25
forum: Networking &amp; Wireless
---

### Post by RobK62 on 2011-01-25
I have two questions that I really hope that someone can answer.

First  of all, I have a netbook. Its a larger one. I am going to add 2 more GB  of RAM next month. That will be a total of 4. It will take up to 8 GB.

  Here are the spec.,

 [http://us.toshiba.com/computers/laptops/satellite/T210/T215D-S1140](http://us.toshiba.com/computers/laptops/satellite/T210/T215D-S1140)

I wound think that if I am running W& 64 bit, that I can run Ibuntu OK. BUt I am not sure. What you you guys recommend? 

I have tested out both Easypeasy 1.6, and Mint 10.

And  that leads to another problem. So far, on the two distros above, I have  been able to have the WIFI work. HOWEVER, it cylcles from 54 to 1 MB/s,  and then back up. Ever now and then, I will loose connections, but it  comes right back up and starts to cycle.

I have only tested it on  my home wifi set up. Its secure, and its the lowest setting. I checked  Windows, and i say that its getting 54 MB/s and its stable.

Please, if you can offer me any ideas, I would be very grateful.

Thanks,

Rob

PS I have run the OS from a USB, and I have an Atheros AR9285 thats used for the wireless.

---

### Post by mikewhatever on 2011-01-25
It's advisable to run a 64bit OS to utilize all of the available RAM, not that Ubuntu will ever use that much.
As for the wifi, did it work out of the box, or did you have to do something?

---

### Post by RobK62 on 2011-01-25
Hi Mike,

Well I tried out Mint 10, and Easypeasy 1.6. And out of the box, the wifi did work. But, there was a probem with it. It would alter speeds on me from 54 MB/s down to 1 M/s, and then back up. Like a blinking Christmas tree light. And it might disconnect, but come right back up.

I have not tried Ubuntu itself. I am downloading both the version 10, as well as the Netbook. I am still  little unsure as to that might be the best to use.

I am runnng a Toshiba T215D-1140,

ITs has an Atheros AR9285 model card.

Oh, by the way, Windows 7 runs at the speed of 54 MB/s. It does not change.

Rob

---

### Post by cascade9 on 2011-01-25
> **RobK62 said:**
> I have two questions that I really hope that someone can answer.

First  of all, I have a netbook. Its a larger one. I am going to add 2 more GB  of RAM next month. That will be a total of 4. It will take up to 8 GB.

  Here are the spec.,

 [http://us.toshiba.com/computers/laptops/satellite/T210/T215D-S1140](http://us.toshiba.com/computers/laptops/satellite/T210/T215D-S1140)

That system should run any current version of ubuntu fine. 

BTW, 4GB? OK, if you want. 8GB on a single core netbook? Pointless. Anything that needs anywhere near that much RAM is going to be so slow on a netbook its not funny. 

> **RobK62 said:**
> PS I have run the OS from a USB, and I have an Atheros AR9285 thats used for the wireless.

This might help- 

[http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k)

---

### Post by mikewhatever on 2011-01-25
I am not very familiar with Mint or Easypeasy, but perhaps they include the proprietary wireless drivers on cds. Ubuntu doesn't, and you'd probably have to use the Additional Drivers utility under System->Administration. The dropping signal problem may require some research, but a quick look over 'Atheros AR9285' titled threads suggest it might need the backport wireless modules package installed.

---

### Post by RobK62 on 2011-01-25
Hi MIke, 

Tell me, whats that module that you spoke of? I have never heard of that before. 

I am about ready to give up. It it was a desk top, I would just hard wire it. Thats far safer any way, and faster. But being that its a netbook, I really need wifi.

I really do not dislike Windows 7. It not to bad really. I remember using 3.1. Now that was a pain in the butt. I would start my computer, and then go have dinner, and it would be up by the time I got home. I mainly used to ti talk on the MIRC back then, and surf an AD FREE internet. I have had every version of Windows sense And 7 is the only one that I have really liked. Its very stable. And has some useful features.

However, I also know some of the bad things the MS has done to screw people over, and shuffle the deck. I do not like that. And I also am not well off. I like the free software.
I helped a freind of mine to sent of a Ubantu on his laptop that he just got. (it came with it) And when I found all the free software,  just about went crazy! LOL!

I know that Windows has some free stuff too. But there is normally a catch. Spy ware, or they sell your registration information, or its been striped down to wet your appetite for more, and then the sell you the full version.

Look, I know that we like to think that we live in something of a free market. But Lord, be fair. When someone buys something, they buy it. No string attached. It use to be like that. But some guys passed laws and stuff that "protected" a persons work. So, really, you are paying rental on something, not buying it. 

Well anyway enough of that.


I will work on it a bit longer. Then I will give up. And wait until more drivers come out.


Hey Mike or any body. I am a little shky on the wifo software. f I were to get a Linux approved USB WIfi set up to take the place of my internal, with that fix the problem? Or is it a bit more complicated than that?

Thanks very much once again,

Rob:p

---

### Post by mikewhatever on 2011-01-26
> **RobK62 said:**
> Hi MIke, 

Tell me, whats that module that you spoke of? I have never heard of that before. 
...

Sure, check out the link below. 
[https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)
The only problem is, you probably won't be able to install and utilize them running from a live media.

---

### Post by RobK62 on 2011-01-26
Super, I am going to give that a try. Tell me, does this just work on Ubantu10, or will it also work on Mint 10 also? 

Thanks,

Rob

---

