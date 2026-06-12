---
title: "64 bit Flash Plugin Not Working"
date: 2011-10-07
forum: Multimedia Software
---

### Post by GreenRaccoon on 2011-10-07
I solved this problem, but I just want to make a thread for anyone looking for a way to solve it.

I had to reinstall Ubuntu 11.04 Natty Narwhal today (long story) and after I installed the Ubuntu Restricted Extras from Ubuntu Software Manager, Flash still wasn't working.  I use Google Chrome, which has its own Flash, so it was odd that Flash wasn't working (maybe it's different in Ubuntu; I don't know).  I tried uninstalling and reinstalling in Synaptic, but that didn't work.

I also tried installing the ppa for the Flash 11 Beta plugin ([http://www.ubuntugeek.com/how-to-install-adobe-flash-11-beta-2-on-ubuntu-64-bit-using-ppa.html]("http://www.ubuntugeek.com/how-to-install-adobe-flash-11-beta-2-on-ubuntu-64-bit-using-ppa.html")), but this didn't work either.

Then I realized that the package in the Ubuntu repository was Flash 10, the old version; the current version is Flash 11.  What I finally had to do was uninstall the bad Flash plugin through Ubuntu Software Center (or Synaptic), and then go here under FIREFOX (won't work in Google Chrome):
[http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")
I downloaded the "APT for Ubuntu 10.04+" and chose to open this in Ubuntu Software Center.  It said that this was a third party source with an unknown license, but this is probably just because Ubuntu hasn't upgraded from the old Flash 10 yet.

This whole issue was a bit ridiculous.

---

### Post by garvinrick4 on 2011-10-07
> This whole issue was a bit ridiculous. 	
When you install flash it just extracts and puts libflashplayer.so in /usr/lib/mozilla/plugins

I have not yet figured out a way to make it not work if you know that libflashplayer.so go's
into /usr/lib/mozilla/plugins

---

### Post by GreenRaccoon on 2011-10-07
> **garvinrick4 said:**
> When you install flash it just extracts and puts libflashplayer.so in /usr/lib/mozilla/plugins

I have not yet figured out a way to make it not work if you know that libflashplayer.so go's
into /usr/lib/mozilla/plugins

Thanks, garvinrick4.  I'm sure that'll be very useful to me in the future.

---

