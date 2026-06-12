---
title: "Network and Synergy"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by Abinitio on 2010-01-13
Hi,

I'm a newbie, so be gentle....

I have a laptop running fedora 12 and a Desktop running Ubuntu. I want to set up a home network and then use the two machines from one keyboard and be able to drag/move back and forth across screens from laptop to desktop seamlessly. 

I think synergy: [http://synergy2.sourceforge.net/index.html](http://synergy2.sourceforge.net/index.html) is the way to do this. But I have no idea how to set up a home network with linux. I have done a bit of googling and it seems you need to set up one machine as a server. Is it not possible to use the router I already have to do this and connect the two machines across this router? 

Any help/advice/general shoves in the right direction to find out how this is done is greatly appreciated!

Thanks

---

### Post by KeLa on 2010-01-13
From that synergy page what i read was that you install server application to that
computer where the mouse and keyboard are connected and client application to others.
So no extra server needed.

---

### Post by shredder12 on 2010-01-13
If you have your machines connected to the router then they are probably on a home network.
Now, all you have to do is setup a synergy server and client.. 
this might be of some help to you [http://linuxers.org/article/manage-multiple-system-using-single-mouse-and-keyboard-use-synergy](http://linuxers.org/article/manage-multiple-system-using-single-mouse-and-keyboard-use-synergy)

---

### Post by Abinitio on 2010-01-13
Hi, 

Thanks for the replies.

I have got synergy working well - now I need some more help....

I want to set up shared file system so that I can access files from both machines. But I also want to be able to take my laptop off the network.

So 
1) How do set this up using NFS?
2) If I auto mount the common folders on start up will removing my lap-top from the network cause problems? And if so whats the best way around it?

Thanks in advance!

---

### Post by R.Bucky on 2010-01-13
I have much the same setup: 2 monitors, 2 machines, 1 keyboard/mouse. To solve the share folder problem, I set up a samba share on my central server for both machines to access. Alternatively, you could use Dropbox and enable LAN sync if you do not have a central server.

---

