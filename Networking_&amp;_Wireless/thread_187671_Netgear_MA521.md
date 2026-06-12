---
title: "Netgear MA521"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by yumigator on 2006-06-03
I'm having trouble getting my Netgear MA521 (rtl8180) to work with Kubuntu. The list of available networks is fully functional, but once I try connecting to one of them, it fails.

I've tried to use ndiswrapper, but it's not installed, and when I apt-get install ndiswrapper the package is not found. I've also tried downloading the tar package of ndiswrapper, but I can't compile it because build-essential isn't installed either, and I can't get that because the package isn't found. Every time I try to install packages like gc++ and those others they all rely upon each other and I can't perform the install.

Can anyone tell me how to install ndiswrapper (and those other packages as well, if possible)? Or will ndiswrapper not help at all? Is it possible to get the card working?

Thanks for any help I can get.

---

### Post by Titus A Duxass on 2006-06-03
ndiswrapper is on the CD.

I am surprised that your card is not detected during the install process.
Ubuntu does detect the card.

You could try and do a ubuntu install, get the card working and then install the kde desktop maybe that would work.

---

### Post by yumigator on 2006-06-03
Yeah I put the CD in and used Adept to try to find the package on it. It did find the ndiswrapper-utils package, but it didn't install correctly.

And I don't think the ndiswrapper package is installed either, because when I use the command in Konsole it says the command doesn't exist or something like that.

I have done an Ubuntu install before (breezy) and I had the same issue, although, I was able to use apt-get successfully under that install. Do you know why apt-get isn't working, even though I'm requesting packages that do exist, like python-glade2 or ndiswrapper-utils or wine?

I'll try and get the Dapper release of the gnome Ubuntu and see how that works out.

---

