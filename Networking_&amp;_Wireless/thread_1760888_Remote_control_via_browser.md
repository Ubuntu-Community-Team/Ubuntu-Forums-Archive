---
title: "Remote control via browser"
date: 2011-05-17
forum: Networking &amp; Wireless
---

### Post by f3ktony on 2011-05-17
Hi, I've been struggling with this all day. I'm due to go in to hospital soon and had a short stay last week. The bedside computer system runs IE6 (ugg) on Embedded XP and is secured so much that I can't access some of my hobby forums that I'd very much enjoy following while laid up in bed. Trying to contact the system admins has proved pointless so I need a work-around.

So after a few searches it seems I could use vnc and java and possibly access remote control through IE6, there is no way of adding to, editing or changing the bedside system. I plan to leave either my eee or a compaq laptop running so that I can access it from the hospital (hopefully). At the moment I can't get anything to work on my local network. Best I've got is running tightvncserver with the message 'Found /sr/share/tightvnc-java for http connections' and 'New 'X' desktop is tony-laptop:1' then 3 more lines about startup and logs.

Info and things I've done.
eeepc runs Ubuntu 10.04 (netbookremix I think) but using Gnome Desktop.
Compaq laptop is running the same (how can I tell if it's NBR?)
I have a static IP address.
A Netgear DG834PN modem router
tightvnc-java is ver. 1.2.7-8
tightvncserver is ver. 1.3.9-6
vnc-java is ver. 3.3.3r2-8
vnc4server is version 4.1.1+xorg4.3.0-37
vnc is in 'Firewall Rules' out and in - in is forwarded to the compaq's reserved LAN IP no. 192.168.0.3
Router 'Service Table has vnc listed as TCP on 5800
Chrome has no chance of accessing [http://tony-laptop:1](http://tony-laptop:1) - message is 'Error 312 (net::ERR_UNSAFE_PORT): Unknown error.'
Entering [http://192.168.0.3:5800](http://192.168.0.3:5800) gives 'Oops! Google Chrome could not connect to 192.168.0.3:5800'
Firefox gives 'This address is restricted' when using [http://tony-laptop:1](http://tony-laptop:1)', adding 'network.security.ports.banned.override + 5800'to 'about:config' has no effect at all, when every search says 'just' do this and bingo!, not for me it isn't.
Firefox gives 'Unable to connect' when using [http://192.168.03:5800](http://192.168.03:5800)
I can access the Compaq using Remote Desktop from the eee and vise versa, at the same time too.
The Compaq has XP Pro and IE6 for testing in Windows.

My head is in a spin and I'm at a loss. Hope someone can help.
Tony

---

### Post by f3ktony on 2011-05-18
Success - of sorts.

After my head stopped spinning I searched some more and found this - [How to remote access using Firefox]("http://ubuntuforums.org/showthread.php?t=541656&highlight=ssh+vncviewer"). It's a bit old (2007) but it got me trying other things and by using 192.168.0.12:5801 I at least get a terminal that I can use to start Chrome and browse the web. This may well be faster that having my whole desktop, so I have enough and now have to hope that the hospital system IE6 is java enabled.

---

