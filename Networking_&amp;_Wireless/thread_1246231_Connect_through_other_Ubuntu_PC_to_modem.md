---
title: "Connect through other Ubuntu PC to modem"
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by rfkrocktk on 2009-08-21
I have two Ubuntu PC's and I'd like to connect them both together and to the internet. What I'd like to do is connect the desktop to my phone (to the internet via tethering), and connect the laptop to the desktop to be able to use the internet. 

I'm already able to connect to the internet through the phone on both computers, so that's not the issue. When I connect both computers with a LAN cable, nothing happens. Am I missing something? 

Also, is it possible to share files over LAN between these two Ubuntu computers?

---

### Post by Iowan on 2009-08-21
There is [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") ICS help page that will need some modification to work with a modem.  How do you have the LAN cable connected... meaning, is it a straight or crossover cable? Some newer cards can auto-configure, but the kind I use do not. Next, how do you have addressing set up - static or DHCP? Can the machines **ping** each other? It is possible to share files, but you will need to set up one (or both) machines to be a server - what kind depends on what protocol you choose to use.
[This]("http://ubuntuforums.org/showpost.php?p=7825110&postcount=3") touches on some options.

---

### Post by rfkrocktk on 2009-08-24
I guess I'll have to look into this a lot more. I was just wondering if there was an easy thing that I could do to connect these two computers to the internet through one modem. I don't want to have to mess with my setup just yet, but I'll look into the link you sent if I ever get to that point :)

As for filesharing, I'll look into NFS. It seems pretty straightforward, so I'll check it out.

---

