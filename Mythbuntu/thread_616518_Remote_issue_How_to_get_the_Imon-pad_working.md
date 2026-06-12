---
title: "Remote issue: How to get the Imon-pad working?"
date: 2007-11-18
forum: Mythbuntu
---

### Post by SlamBam on 2007-11-18
Hi all,

I really like Mythbuntu! It installed flawlessly on my box the first time.Even the Imon vfd.  So am really really happy with that. I have just one issue: the imon pad. Its not working. I currently made a workaround by using the buttons around the pad for up/down/left/right. It works but it is not ideal. 

I checked all the fora, but can´t find a ready solution. I checked [http://www.mythtv.org/wiki/index.php/Imon#Patches_for_iMON_PAD_Controller](http://www.mythtv.org/wiki/index.php/Imon#Patches_for_iMON_PAD_Controller) but unfortunately am not that good in Linux to give the patches a try. Basically I am scared  that I break the working Lirc. 

Does anyone have a step-by-step guide on how to do this in mythbuntu?

Thanks!

---

### Post by reclusivemonkey on 2007-11-18
I have the very same piece of hardware, and it worked flawlessly in Feisty, but somewhere along the way in Gutsy it went FUBAR. I have compiled from source and had some success, but I've not had the time to get a working setup. The Venky method seemed to work great, but now that support is supposedly in the stock LIRC its just refused to work for me. Same with the LCD.

---

### Post by SlamBam on 2007-11-18
Ah, yes. Under Feisty I had it working also. But that was with an older MythTV version, and a lot of other problems. 

Under Feisty I used the stacktrace guide: [http://stacktrace.org/index_html/20070208lirc-fix-for-linux-2.6.19/200600912lirc-imon-the-debian-way](http://stacktrace.org/index_html/20070208lirc-fix-for-linux-2.6.19/200600912lirc-imon-the-debian-way)  and [http://stacktrace.org/index_html/20070208lirc-fix-for-linux-2.6.19](http://stacktrace.org/index_html/20070208lirc-fix-for-linux-2.6.19)

Not sure though how I should translate this to Mythbuntu. Hope someone does.

---

### Post by hinge on 2007-12-14
Why is the pad functionality not included in the "standard" lirc driver?
same goes for the Power button.
Is there a good explanation for this? is somebody working on it? will it be part of some release?
...I'm not bitching - just plain curious...sorry

---

