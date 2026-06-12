---
title: "Windows and Ubuntu networking - Can't ping/connect?"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-04-11
I have two Ubuntu desktops here. Each of them are running Samba. The one I've had running for a few months now, the other I just set up today.

Using an XP laptop, I cannot connect to the other one I just set up. I'm unsure as to what is different about the newly set up one, though. 

The XP laptop can ping each computer by IP, but it can only ping the main Ubuntu computer by computer name, whereas it cannot set up the newly set up Ubuntu computer by computer name and I'm trying to figure out why.

What do I have to do to network a Samba computer with Windows? It shouldn't be too hard, I've done it a dozen times, yet I still can't crack this one to get the laptop to connect.

---

### Post by Technophobia on 2009-04-11
I think the package winbind might help. I'm not totally sure.

sudo apt-get install winbind

---

### Post by Roasted on 2009-04-11
The part I don't get is how I can't connect by the computer name to the one samba server.

I have 2 samba servers for a reason. One I use here at home for file sharing. The other I'm setting up here at home to take to work, so ultimately it'll be at work I use it for my personal files at work so I can access them in other areas of the building.

But what I don't get is when I check each smb.conf of both computers. In both computers config files, their respective computer name is NOT listed. Yet, my main computer can be connected to from an XP laptop via computer name at start - run. AKA = \\Intrepid. That's my main computer and that works. But \\UbuntuDesktop (the other samba server I'm setting up for work) does not. YET, if I do \\192.168.1.120 (the IP of UbuntuDesktop) it works.

I'm just not sure why one works when the other doesn't...

---

