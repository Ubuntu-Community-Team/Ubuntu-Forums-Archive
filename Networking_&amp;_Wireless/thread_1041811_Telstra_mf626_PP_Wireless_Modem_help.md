---
title: "Telstra mf626 PP Wireless Modem help"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by brandon88tube on 2009-01-16
My Australian friend needs help using his Telstra mf626 PP Wireless Modem. If anyone has any info on how to connect using this device please share. Also, try and keep in mind that he is new to Ubuntu and Linux in general.

---

### Post by brandon88tube on 2009-01-18
Anyone have any idea?

---

### Post by danni-la on 2009-01-19
edit: [http://ubuntuforums.org/showthread.php?t=935055&highlight=telstra](http://ubuntuforums.org/showthread.php?t=935055&highlight=telstra) 
this might help?

---

### Post by danni-la on 2009-01-21
ok I finally have mine working...

followed this guide [http://www.matt-barrett.com/?p=5](http://www.matt-barrett.com/?p=5)

also had to unlock the modem by calling the prepaid line and getting the puk key now it works like magic!

EDIT: also have to run sudo wvdial in terminal, mine isn't working with gnome-ppp.

---

### Post by msbsydney on 2009-01-28
Hi, absolute noobie here, just downloaded the Wubi Ubuntu installer and it worked excellently, no trouble at all and can dual boot and all seems to be well from my completely untrained Windoze eye.

But I also have the MF626 Wireless Modem but use Vista so believe that Hyperterminal is unavailable and was wondering what program to download to help me configure the modem?  

The instructions outlined here [http://www.matt-barrett.com/?p=5](http://www.matt-barrett.com/?p=5)  seem to be suitable for most Windows versions but not Vista.  A free version of Hyperterminal for Vista used to be available but no longer.

I'm looking for a quick and painless way to do this as I don't even know where half the screens you guys talk about above are viewable from.  To use an analogy, I'm a driver, not a mechanic and if I ask where the lever to pull the hood is, then that sums up pretty nicely how little I know about "sending commands to modems" and other such heady language.

It's quite humbling to be a noob, wondering if any of you kind gurus can help me?

If anyone has any ideas, I'd be grateful to hear them as I'm sure once I can configure the modem to the net, I'll be able to start using and enjoying Ubuntu.  The Ubuntu OS (even without a dedicated partition) seems very fast, about twice as fast as Vista and without any of the 'pause' or 'delay' that occurs using Vista from time to time.

So looking forward to becoming a convert!

Thanks very much to anyone kind enough to help me out :)

---

### Post by danni-la on 2009-01-29
I did find instructions for vista in my searches but I have all those bookmarks on my home computer.. I will have a look later and hopefully post a link for you!

edit: this might help?
[http://ubuntuforums.org/showthread.php?t=1005910&highlight=telstra](http://ubuntuforums.org/showthread.php?t=1005910&highlight=telstra)

---

### Post by msbsydney on 2009-01-30
Thanks danni-la, believe it or not, I managed to find a downloadable version of Hyperterminal 3.6 which although unavailable from the official website, I did find after an hour or more via Google search.  

It seems to work with no problems on the Vista OS, the trick is getting hold of a copy of it as there seems to have been concerted efforts to make the program unavailable or appear that it's incompatible with Vista (persuading you to part with cash for the newer Hyperterminal version) when in fact the old free version 3.6 seems to work without so much as a hiccup.  It was late and after downloading it I closed the link... I shall try to find it again and post here for other users.

The next part of my quest to get the MF626 Telstra/ZTE wireless prepaid broadband modem to work with ubuntu is to get the program 'Gnome-PPP', (as it doesn't seem to come standard with the ubuntu 8.10 release I have downloaded) then download it via my net connection from the Vista OS and somehow hope I can save it into the ubuntu folder. 

As I have installed ubuntu 8.10 via the Wubi installer it, in effect, lives on Vista and I hope a copy/paste will enable the program to copy from Vista OS proper to the ubuntu folder and then open and install Gnome-PPP from inside the ubuntu OS.

I'll let you know how it goes, I'm not holding my breath.

Thanks again for the link danni-la, it seems to deal more with a different model of modem (and from my enquiries, seems to require different process to get it working) but the more information I have, then the more likely there is light at the end of this tunnel, so much appreciated :)

---

### Post by Lunx on 2009-01-30
Best place for help would probably be on the Whirlpool Forums

[http://forums.whirlpool.net.au/](http://forums.whirlpool.net.au/)

The people on this forum here are very helpful too, and you should get an answer pretty promptly

[http://www2b.abc.net.au/science/techtalk/](http://www2b.abc.net.au/science/techtalk/)

Hope that points your friend in the right direction

---

### Post by danni-la on 2009-01-30
msbsydney: no probs happy to help. I found when trying to get mine to work that combined info from all the different models was helpful. 

Also I think you will find gnome-ppp in the package manager thats where I got it, though it doesn't actually work for me.

one other place I found helpful info was on the zte forums 
[http://www.zte.com.au/ztebb2/](http://www.zte.com.au/ztebb2/)

Lunx: whirlpool is a great resource! also thanks for the other link haven't seen that one before.

Cheers Danni

---

