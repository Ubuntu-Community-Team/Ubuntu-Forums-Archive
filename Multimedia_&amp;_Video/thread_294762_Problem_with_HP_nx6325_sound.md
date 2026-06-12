---
title: "Problem with HP nx6325 sound"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by manishk on 2006-11-07
I'm using a HP nx6325 laptop (AMD Turion X2, ATI Radeon Chipset). 

I recently installed Ubuntu (Dapper Drake 64-bit) on it...the in-built speakers aren't working BUT I can hear sounds if I connect through headphone jack! Pls help

I dont know which 'model' the speakers are.

---

### Post by wolfchri on 2006-11-08
Try the How-Tos at tuxmobile.org:

[http://tuxmobil.org/hp_compaq.html](http://tuxmobil.org/hp_compaq.html)

--> scroll down to the nx6325, there are several links to installation reports that solved that problem

This one might also help:

[http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nx6325](http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nx6325)

and this one is for Ubuntu/Debian:

[http://www.puchalla-online.de/nx6325.html](http://www.puchalla-online.de/nx6325.html)

---

### Post by manishk on 2006-11-08
Great link,thanks.

But can you please help me figure this out...?

The link([http://www.wolframschenck.de/nx6325.htm](http://www.wolframschenck.de/nx6325.htm)) to installing SuSe on the laptop gives me these lines

> Minor hardware installation problems

Sound

You have to add the following options to the sound module: model=hp position_fix=1

This can be done with yast2

What does that mean...to a Ubuntu user? And a noob?!!

Whats the Yast equivalent in Ubuntu.

And regarding the Video will the SuSe driver work for Ubuntu? And how do I install it?

Pls help

Thanks in advace

---

### Post by manishk on 2006-11-08
Another doubt

The Gentoo link is pretty good (I think). Most of the terminal commands will work in Ubuntu also right??

---

### Post by wolfchri on 2006-11-09
manishk,

give me some days, my brand new NX6325 arrived yesterday. I am going to install Edgy on it, so I have to solve the same problem. 

However, I suggest that you use Edgy instead of Dapper since the Dapper kernel is just too old. Especially the sound needs a ALSA version that does not come with Dapper, and as a newbie, you do not really want to compile your own kernel, do you? :mrgreen: 

I will post my results here and in the Ubuntu Wiki, so stay tuned.  

BTW In a German blog, I even read that sound works out of the box with Edgy. Maybe you really better go with Edgy.... 

[http://blog.computer-tipps.info/2006/10/15/ubuntu-auf-dem-compaq-nx6325/](http://blog.computer-tipps.info/2006/10/15/ubuntu-auf-dem-compaq-nx6325/)

---

### Post by manishk on 2006-11-09
Thats *sounds* good. 

The reason I dint want to try edgy was that I'm a little paranoid about using a new distro since finding help for that is difficult and I know I cant do it myself.

But now it seems like a different scenario! 

Pls tell me where I can stay in touch wit your blogs or anything of that sort? I'm pretty bad at navigating efficiently through the Ubuntu site too!

THANKS A TON

---

### Post by wolfchri on 2006-11-10
Hi there,

here is my installation report for Ubuntu Linux Edgy Eft on my HP NX6325:

[http://vale.homelinux.net/wordpress/?p=106](http://vale.homelinux.net/wordpress/?p=106)

I am not yet finished, so stay tuned. I will move the final report to the Ubuntu Wiki as a HowTo.

In essence, Edgy runs very well on the NX6325 out of the box; even the WLAN is working with a little manual tweaking. Sound is not an issue with Edgy anymore :p

---

### Post by manishk on 2006-11-11
It would be nice if it can be a lil more newbie friendly!!

And cant I install ndiswrapper without LAN connection because my only option is connecting thru wifi and thru Windows.

Thanks again

---

