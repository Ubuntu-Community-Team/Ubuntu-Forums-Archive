---
title: "the fate of ndiswrapper (or linux wirelessly)?"
date: 2008-12-27
forum: Networking &amp; Wireless
---

### Post by maclenin on 2008-12-27
I happened upon these statements, just the other day...

> IMPORTANT NOTE: As of early october, the ndiswrapper database has been broken for some time--it returns blank pages when you try to access it. It's not clear when this is going to be resolved. As a result, i copied google's cache of the database pages to my personal website. You can access them here. For the time being, there's unfortunately no easy way to search through the pages--you will have to access them via my site and manually use your browser's search function to find the pci id number that you're looking for. If you don't find it on the first page, you'll have to manually search through all of them until you find it. I'm sorry that this has happened, but hopefully it will be resolved soon.

- [**pytheas22**]("http://ubuntuforums.org/showthread.php?t=885847")

> Also, the ndiswrapper support website/wiki has been offline for several months as of october 2008. It is unknown if the project is still active as queries to the developers go unanswered.

- [**wikipedia**]("http://en.wikipedia.org/wiki/ndiswrapper")

...living a linux life wirelessly without ndiswrapper would be a [**bummer**]("http://ubuntuforums.org/showthread.php?t=340689").

Any thoughts?

---

### Post by Bucky Ball on 2008-12-27
What card do you have?

---

### Post by kevdog on 2008-12-27
ndiswrapper development seems to have stopped, however it still functions within linux very well.

---

### Post by maclenin on 2008-12-27
...bcm 4310 - currently fully functional in fesity (with ndis) - looking to migrate to intrepid - wary of the wireless findings I have posted above (especially in light of my negative fwcutter experience/performance many moons ago)!

---

### Post by kevdog on 2008-12-27
maclenin -- based on your avatar I think you were the author of a most excellent bcm43xx or ndiswrapper tutorial a long time ago.  Its been a while since Ive seen you lurking around the forums.  I was a big ndiswrapper proponent (still am) until Intrepid.  Then my bcm4308 worked after installing the firware -- the OS automatically detected it, asked me to install the firmware -- and then presto -- it magically worked.  In fact its the only way I can use WPA2 with my router -- cant seem to get ndiswrapper/bcmwl5 to be able to use wpa2.  

They have obviously improved the open source drivers a great deal since in Edgy and in Feisty.

---

### Post by Bucky Ball on 2008-12-27
> **maclenin said:**
> wary of the wireless findings I have posted above (especially in light of my negative fwcutter experience/performance many moons ago)!

You might find things different now. Rock solid for me but my card is the 4311. They are usually grouped together as 43xx. In System->Administration->Hardware Drivers, do you have a restricted driver available for the card? b43-fwcutter is now used and after never being able to get my card working in Gutsy, when I changed to 8.04 I had everything up and running with the wireless in about 5 minutes, just clicked the restricted driver and guided me through. Easy. I was astounded. I'd banged my head against a wall for months with ndiswrapper. b43 came about to deal with these problematic Broadcom cards.

---

### Post by maclenin on 2008-12-27
**kevdog**:

The same, indeed! With childcare and other life obligations it has, indeed, been a while - I recognized [**you**]("http://ubuntuforums.org/showpost.php?p=2787003&postcount=211"), as well from, yes, ye olde (it seems) ndiswrapper days. Thanks for the shout out re: the guide and...

**kevdog and Bucky Ball**:

...thanks for the comments re: intrepid wireless install! I'll give it a whirl and post the result - perhaps ndis development has been discontinued for a (good) reason!

Thanks folks!

---

### Post by kevdog on 2008-12-27
maclenin

Thanks for that very old tutorial.  That was one of the first well written tutorials I ran across when I first switched to Ubuntu way back with Edgy.  I didn't have a clue about anything or how things were supposed to be setup.  Thanks a lot for your help back then and setting me straight.

---

### Post by maclenin on 2008-12-27
**kevdog!**

You humble me with your comments. It is abundantly clear, however, that the pupil has become the master! Thanks, again, for the latest wireless lead and your kind words!

---

### Post by maclenin on 2008-12-29
**Bucky Ball and kevdog!**

It seems the fwcutter install via the hardware driver manager under Intrepid is the way to go for bcmX wireless card members!

I may add a link to this "epitaph" from ye olde ndiswarapper guide!

Thanks, again, for the guidance!

---

### Post by Bucky Ball on 2008-12-30
> **maclenin said:**
> **Bucky Ball and kevdog!**

It seems the fwcutter install via the hardware driver manager under Intrepid is the way to go for bcmX wireless card members!

Exactly the same in Hardy 8.04. As I mentioned, I spent months unsuccessfully attempting to get my card up in Gutsy, installed 8.04 and the Hardware Driver and was up in 5 minutes! I almost cried with joy!

---

### Post by doorknob60 on 2008-12-30
That new Broadcom STA driver that popped up on my Parents' Hardy Xubuntu install in Hardware drivers works great for them. Showed up the reboot after installing a bunch of updates (might have came from Backports, not sure, but whatever it is should be in Interpid too). No more ndiswrapper, no more b43, and I'm really glad bcm43xx is dead now XD (It gave me so many problems back then...). They have 4311 BTW if it makes much of a difference. [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

