---
title: "Network-manager sub par Wicd works like a charm"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by yogo on 2008-12-11
Having read through a few different threads ie Nvidia vs ATI, Windows vs Linux, Firefox problems with Ubuntu, this to me is a major problem with the out of the box Ubuntu install.

Reading thru this forum, I was somewhat surprised, not really that there were more than 850 pages of different threads.

To make a long story short, I decided last night to get a wireless going on a desktop that is two feet away from the router. I had an old DWL-122 laying around and I decided to get it going rather than connecting and disconnecting the hard wired ethernet cable between the two pc's.

I issued every command for diagnosing wireless connections under Network-manager edited etc/modprobe.d/aliases and several other files, read thru different threads and then decided to remove network-manager. So I used gmail to email myself some links on the pc without internet connection. I connected the ethernet cable to the pc that I want wireless on and restarted my networksudo /etc/init.d/networking restart

I then logged into my gmail, added the key thru terminal, then added Wicd to my added repositories, then installed Wicd, all the while my ethernet cable was still connected. The moment Wicd was installed, instantly the light(link) was lit green, I knew then that my internet was working. I disconnected my ethernet cable and confirmed my belief that I was indeed connected thru the dwl-122 and sure enough I was..

I further confirmed thru the Wicd gui that it saw my Buffalo router.

Why Ubuntu does not include Wicd in their installations is beyond me, it just works without having to issue a thousand different commands. I have used Wicd before and it has always been easy to get wireless going.

---

### Post by cariboo on 2008-12-11
I on the other hand have not been able to connect wirelessly on my laptop with Wicd, Network Manager just works for me, even using my usb wireless device on my desktop, Network Manager sets the connection up properly. The reason Network Manager is the default is that it is part of the Gnome desktop.

Jim

---

### Post by yogo on 2008-12-12
> **cariboo907 said:**
> I on the other hand have not been able to connect wirelessly on my laptop with Wicd, Network Manager just works for me, even using my usb wireless device on my desktop, Network Manager sets the connection up properly. The reason Network Manager is the default is that it is part of the Gnome desktop.

Jim
   

I have not posted much in the wireless forum other than more than a year back and remember going thru quite a bit to get wireless going back then on an Edimax wireless card.

Maybe it is just a hardware issue but it seems like wireless problems are abundant here. I only have two experiences with wireless but both seemed to work better with Wicd. I just figured with more than 850 pages containing several individual threads per page that wireless seems to be a huge issue.

By all means if Network=manager works, use it, my topic was not meant derogatory towards the default program.  Possibly removing and reinstalling Network-manager would have had the same result, instantly picking up the router on install, possibly something was corrupt in the install that was removed because that desktop always was hard wired.

---

### Post by iponeverything on 2008-12-12
Network-manager works well for me under 8.10. I had a few issues that I had work through 8.04, but it seems to the opposite for many. I am never sure though how many of the problems that people have getting connected after going to 8.10 is caused by mn and how many are caused by driver changing in the kernel.  Though is yogo's case the issues is clearly with nm.

With all of NM tie-in's with dbus, key chain and other parts of the gnome desktop -- I can understand I can understand why its taken a while to debug.

Network-manager does seem to improving quickly,

I have no problem with recommending that people try wicd if they have issues. In a significant number of the cases, it solves the problem. And my goal here is to help people.

---

