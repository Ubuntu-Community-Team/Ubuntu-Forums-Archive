---
title: "Wireless won't connect automatically at start-up"
date: 2011-12-17
forum: Networking &amp; Wireless
---

### Post by out_2_lunch on 2011-12-17
I'm using QIMO (setting it up for the kids) that's based on Ubuntu 10.04, and I'm pretty much a newbie.

I got a Belkin N300 Micro USB wireless adapter working using ndiswrapper  and the XP drivers, but it doesn't work after a restart until I type  "sudo ip link set wlan0 up", then all is good.

I'm following the ndiswrapper instructions ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper))  and gather that the problem is that ndiswrapper is not loading at  startup. The instructions say that if I use the applet I should use:

gksudo gedit /etc/modules

and add "ndiswrapper". I don't have this file in /etc, so I'm not sure  if all I need to do is create it (a text file?) and write "ndiswrapper"  in it, or if there is normally some other commands/text in the file.

I had tried the previous instruction on that page that said to enter:  "sudo ndiswrapper -m", but nothing happened, which is why I assume I  have to edit "modules". However, I'm honestly not sure if I'm using the  manual configuration it talks about ow what, since I do have  "ndiswrapper.conf" in /modprobe.d :confused:

Thanks for any help I can get on this.


Edit: Obviously, I'm not with it today, because I mistakenly thought this file wasn't there, and I decided to just charge ahead and see if I could figure it out on my own. I realize now it likely was, and I was not looking in the right place.

Anyway, I used the command line to create a file called "modules" with only "ndiswrapper" in it, and overwrote (?) the one already there. Will this be a problem, or is it something I can fix somehow, not knowing what was in this file before? Can I undo it? Damn, it didn't even fix my one problem....

---

