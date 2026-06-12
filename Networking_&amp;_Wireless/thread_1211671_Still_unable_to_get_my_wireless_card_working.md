---
title: "Still unable to get my wireless card working"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by mightyh on 2009-07-12
Jaunty has identified my wireless card as Texas Instrument ACX 111 54Mbps Wireless interface. I have been using the Linux system for almost 3 months now but so far I had no luck in getting my wireless to work in Ubuntu. I have posted this problem in other forums before but I still have no luck in finding a driver that will make my card work. I like what I see in Ubuntu and I am trying to learn more about the system so I can totally leave the Windows for good. I know somewhere out there somebody can help me with this problem. Of course I can always replace my wireless card and hope that Ubuntu will have the proper driver for it. But that is not the correct way of learning Linux, so I need help.

---

### Post by bkratz on 2009-07-13
Try this link [EMAIL="http://acx100.sourceforge.net/"]http://acx100.sourceforge.net/[/EMAIL] it is supposedly a linux build project for that card specifically.  Good luck ( I didn't really read the whole thing!)

---

### Post by mightyh on 2009-07-27
Thanks for the link that you have suggested _[COLOR=black]bkratz[/COLOR]_. I have already been at that site before and I still could not get my wireless card work under ubuntu jaunty. I do appreciate your help though.:)

---

### Post by martinbaselier on 2009-07-27
It would help to post, what you've tried. 

The output of the following would also be interesting:

iwconfig

sudo lshw -C network

to copy/paste from/to a terminal use ctrl+shift+c / ctrl+shift+v

---

### Post by irv on 2009-07-27
There is a way of using Windows driver for wifi cards. It called "ndiswrapper" Here is a howto for using it.
[http://ubuntuforums.org/showthread.php?t=31926]("http://ubuntuforums.org/showthread.php?t=31926")
When I first bough my laptop it's wifi card was not supported in Ubuntu. I followed this howto and got it to work. Now there is a driver for it, so I don't use the windows driver any more.
I hope this will help you out.
If you have any questions on the ndiswrapper ask them on the howto thread.

---

