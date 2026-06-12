---
title: "Networking trouble"
date: 2009-07-26
forum: Networking &amp; Wireless
---

### Post by n2iw on 2009-07-26
Hi Folks,

I have tried for a couple of hours now to find a post with a problem similar to this to no avail. So forgive me if one exists and please point me to it.

Otherwise consider the following:

The Laptop is 8.10 the desktop is 9.04 and the windows machine is XP

I have a Cable modem. It is connected to a LinkSys WRT160N wireless N Router. I have a LinkSys WUSB 600N connected to a desktop. I have a System 76 Darter laptop that has an Intel wireless 5100 adapter built in. I also have a windows machine with a hard wired connection.

My Linux desktop connects and communicates to the router and out to the Internet with no problems. The Windows machine also has no issues. But my Linux laptop will only connect for a few seconds and then it goes into a mode that is so slow it times out. If I reconnect it, it connects for a few seconds and then the same.

It does not matter whether or not I try to connect wireless or hard-wired. I It connects for about 1 second and then goes into dead mode. It does not matter if I use the internal wireless card or an external one. Still will not work. It worked in the past with a Wireless B router. It also worked hard wired with the same  router.

I don't see anything out of the ordinary in the router logs. I am not sure were to look in the Linux logs.

Does anyone have or know of any suggestions?

Thanks in advance.

John

---

### Post by quixote on 2009-07-27
Do you know for sure that there isn't a problem with the laptop's networking hardware?  I don't know much about networking so I could easily be wrong, but that sure doesn't sound like any software problem I can imagine, especially since it happens for both wired and wireless.

Anybody else have an idea?

---

### Post by n2iw on 2009-07-28
Yes I have confirmed the hardware is working. If I boot from a live CD all works fine.

I also found that if I run a VMWare vm the wireless connection on VMWare actually works! Even tho it does not work at the OS level. Go figure.

I have tried all kinds of things I have seen on the net but nothing seems to work.

It connects up for a few seconds and then it goes dead.

I would like to know if there is a way to completely reset the networking, without reinstalling the whole OS.

---

### Post by n2iw on 2009-07-28
Update:

I am not sure what this means but when I booted into the previous kernel version which I believe is 2.6.27-9 all works fine. I mean like light and day. I don't remember what I was using I think it was 27-14 or 17. Whatever the latest one from canonical is.

I am not sure how the grub boot menu works but could it be kernel related? Or is the grub menu giving me an older system image complete with configuration files?

Whatever it is doing it works. Now I need to figure out how to get it to stay this way? If any developers see this I would be delighted to provide more details.

John

---

### Post by n2iw on 2009-07-28
I got it. VMWare is the culprit.

After I booted into 27-9 kernel I found that VMWare was no longer working. Then I booted back into the latest kernel and viola wireless works without flaw.

But VM Ware is gone, at least it doesn't work anymore. Oh well, at least I have networking. Now I guess I will peruse the VMWare boards for tips on how to get that working again.

J

---

### Post by quixote on 2009-07-28
Interesting problem.  I'm impressed you tracked down what the source of it was!

Give VirtualBox a try instead of VMWare, perhaps?

---

### Post by n2iw on 2009-07-28
I have heard of this virtual box but have not had a chance to look into it. I have a bunch of stuff set up in some VM ware VMs that I need to do my job... 

So I would rather fix VM ware, if I can. 

When I get some free time I will then try Virtual Box. Although at first glance it looks fairly interesting.

John

---

