---
title: "Direct Connect Windows 7 and Ubuntu 10.04"
date: 2011-08-29
forum: Networking &amp; Wireless
---

### Post by ductiletoaster on 2011-08-29
Title says it all...but just in case!
I have two computers:

Windows7:
Wireless card (connected to the internet) 192.168.1.xxx
Gig lan (connected to Ubuntu machine) 192.168.0.xxx

Ubuntu 10.04:
Wireless card (connected to the internet) 192.168.1.yyy
Gig lan (connected to Windows machine) 192.168.0.yyy

I can SSH from windows to Ubuntu using the LAN ip of the UBuntu machine. But Windows Still says Undefined Public network... Haha and this bugs me! SO....

TO my fellow Linux users is there anyway to define this "network" so that Windows can finally figure out its crap?

---

### Post by northd_tech on 2011-08-29
It sounds to me like you need to setup a Samba server on your Ubuntu machine if you want Win7 to be able to "see" it.  You might already have a Samba client running on the Ubuntu machine if it can browse the Windows Network (file shares and printers).

I'm FAR from an expert on Samba, but if you search this forum for "samba" you should be able to find a LOT of information.

Here are some articles aimed more towards the Samba beginner, plus the official HOWTO:

[B][Easy Samba Setup]("http://www.linux.com/learn/tutorials/296391-easy-samba-setup")
[/B][http://www.linux.com/learn/tutorials/296391-easy-samba-setup](http://www.linux.com/learn/tutorials/296391-easy-samba-setup)

[B][Quick and dirty Samba setup  ]("http://www.linux.com/learn/tutorials/305771-quick-and-dirty-samba-setup")
[/B][http://www.linux.com/learn/tutorials/305771-quick-and-dirty-samba-setup](http://www.linux.com/learn/tutorials/305771-quick-and-dirty-samba-setup)[B]

The Official Samba HOWTO
[/B][http://us5.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us5.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

EDIT:  here is a recent thread here about setting up a Samba server- you might want to read that or even post your findings/difficulties on that thread:

[B]Configuring Samba Server
[B][http://ubuntuforums.org/showthread.php?t=1833892](http://ubuntuforums.org/showthread.php?t=1833892)

[/B][/B]Also, I'm not entirely certain from your OP what it is exactly that you are trying to "direct connect," but Samba is the way to go for file and print sharing- the Samba share "link" should show up **as if it was a physical drive or printer** under Linux if everything is working properly and then you just copy, move, push, poke, etc. whichever file or resource you are needing.

If you are trying to use 'remote control' of 'remote' computers on this network, you probably want to look into Virtual Networked Computing (VNC):

**Configuring the VNC server/viewer in Linux.**
[http://bobpeers.com/linux/vnc.php](http://bobpeers.com/linux/vnc.php)
Configuring the VNC server/viewer in Linux.

---

### Post by ductiletoaster on 2011-08-29
Essentially I have the two machines connected to each other via a crossover cable. I can SSH in and the computer can see each other. But Windows Sees the "Network" as undefined... so i was trying to see if there is a way to Setup ubuntu so that Windows can recognise the network type

---

### Post by northd_tech on 2011-08-29
Well if you're just trying to share resources (like a printer, scanner, or projector) or to access a "common" directory (like "My Music" and "My Pictures") to/from both computers, then having both a Samba client and server under Ubuntu should be pretty painless, once you get it set up correctly.  That should also enable you to read, execute, and write files in both places from either machine (depending upon your permissions and sharing settings under Ubuntu and Win7).

Here are a couple of fairly short & quick Samba articles:

**[Install Samba Server on Ubuntu]("http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/")**
[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

                                                                                                                               
                                                   **[Share Ubuntu Home Directories using Samba]("http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/")**

 [http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/](http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/)

To save having duplicate files in both places, it is probably best to move all your music, photos, data, etc. to** one** location on whichever drive partition has the most free space once you get the Samba server up and running (or else Windows95-Win7 won't be able to see the Ubuntu/Samba shared part under Windows Networking).   You will also want to make sure that your "Workgroup" is the same on both/all machines.  Once you get the Win7 and Ubuntu machines "talking" to each other, then adding more machines (or OS-'independent' wireless printers) to the network should be fairly painless, too.

Of course- as one simple alternative, I just set up a "Shared Data" NTFS partition for a relative who does TONS of multimedia/art work when we installed his Ubuntu 10.04 LTS and Win7 just "sees" that "Shared Data" partition automatically at startup. 

From my experience, it is MUCH easier to see a Windows Networking printer **from Linux computers** than the other way around, but I seem to remember it being pretty easy to go the other direction too.  When I was at University, people started printing on my Linux printer out in the middle of the desert (over a microwave dish internet link) from the University about 200 miles away, so I needed to add user/password (and possibly MAC address) access control to the Linux printer to prevent people from using all my paper and ink.  This was about 10 years ago under Red Hat Linux, so it is probably much easier now under Ubuntu.

If you're interested in "peer-to-peer," here's a 102-page HOWTO here at Ubuntuforums:

[B]HOWTO: Setup Samba peer-to-peer with Windows 
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
[/B]

---

