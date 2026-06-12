---
title: "Cannot browse windows network shares but can go to them direct"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by oceanexplorer on 2009-01-02
I know this was raised as an issue in previous version of Ubuntu, but I wondering if it was still outstanding.

I can get to my windows share easily with the following:

smb://fss-data/data/

however if I go to 

smb://fss-data I just get a blank screen, I cannot see the share "data".

It was mentioned that this was an issue with gvfs, if I use gnome commander I can see the shares quite happily.

Any suggestions to get this working or is it an outstanding bug?

Kind regards

Paul

---

### Post by superprash2003 on 2009-01-02
is that a hidden share?

---

### Post by oceanexplorer on 2009-01-02
No it is a normal share that I can view fine in Windows and also with Gnome Commander, but not Ubuntu's integrated browser Nautilus, I think this maybe something to do with the move to GVFS.

---

### Post by Kellemora on 2009-01-02
Hi Ocean

There is a MAJOR BUG in Nautilus that has gone unresolved now for well over two years!

The sad thing about this is, all the help given when the BUG appears has nothing to do with making Nautilus work and just messes things up even worse.

If you have smbtree installed and type smbtree in your command line and ALL of your shares show up.  Then your network is up and running perfectly and Samba is working perfectly.  IF You can PING all of your locations no problem.
But if your shares still do not show up in Nautilus, then OBVIOUSLY the problem lies with Nautilus!

In Nautilus, if you go up to Go/Location and put in the IP address and the share opens.  Once again, it's the BUG in Nautilus that keeps them from displaying as they should.

Normally, I can do THREE cold reboots and Nautilus will start working.  But not always.  Sometimes you can reboot 50 times in a row and Nautilus still won't pick them up.  So I wait until the next day and for some reason, it's working again.
No rhyme or reason behind it.

And worse than SAD, they've known about this BUG now for over Two Years and OBVIOUSLY no one cares about it or is working on resolving it either.

There are Three Primary user interfaces to a computer!
The Keyboard, the Mouse and the Monitor!
Ubuntu has no support for extended business keyboards, and absolutely NO support whatsoever for meeces over two buttons.  And 99% of meeces today have 3 buttons or more.  I dumbed down from a 7 button mouse to a 3 button mouse with scroll wheel, and never dreamed it wouldn't be supported in Ubuntu!
Oh, what THEY call support is a DEFAULT setting that less than 1/2 of 1% of the population would use the third button for.
Most of us want it to be FUNCTIONAL and setable.

And WHAT DOES everyone do with their computers these days?
They GO ONLINE!  Internet seems fairly well supported, and the LAN works OK if you don't mind doing things manually, because Nautilus has NEVER BEEN FIXED from day one!  Has the SAME BUGS it had since inception.  None have been corrected!

OK, off my rant!

I'm having another bad day due to BUGS in Nautilus!!!!!

TTUL
Gary

---

### Post by cabbiinc on 2009-01-02
I am no computer expert, and very new to Ubuntu and Non-Windows based computers in general. But I have been trying to figure this out myself for a while for sharing in my Vista computer. LLTD is what windows now uses for networking stuff. [note. there's an update that makes XP use or at least talk to a computer with LLTD]

I found this page [http://www.howtoforge.com/installing-the-lltd-protocol-responder-for-linux-on-debian-lenny](http://www.howtoforge.com/installing-the-lltd-protocol-responder-for-linux-on-debian-lenny) and it appears to me (an untrained eye) that it's at least directed at this bug.

I don't know code, so can't tell you if it's the real deal.
I don't know if this would be detrimental to your system otherwise I would have tried it on my system.
I don't know if it's reversable if you do try it.
I'm not responsible if your system crashes, maybe someone who does know a few things can comment.

---

### Post by albinootje on 2009-01-02
> **oceanexplorer said:**
> No it is a normal share that I can view fine in Windows and also with Gnome Commander, but not Ubuntu's integrated browser Nautilus, I think this maybe something to do with the move to GVFS.

How do you connect to your samba-server from Gnome Commander actually ?
Gnome commander only shows a samba share from my desktop-machine, but not from my file-server.
When I type in \\my-samba-server-hostname in Gnome Commander in the bar at the bottom, it crashes with a segmentation fault.

Nautilus does work fine here when I use smb://my-samba-server-hostname/
Same for Konqueror.

I'm using Ubuntu 8.10 on my desktop. (The local file-server is still running Ubuntu Feisty/7.04)

---

### Post by ermannobonifazi on 2009-01-03
Is you Windows computer on the same subnet? I saw some issue browsing computer that are not on the same network/subnet of Ubuntu computer. In my case I access my windows server over a VPN. I was able to fix the issue editing the /etc/samba/smb.conf and adding some information like:

wins server = 10.x.x.x (where this is the IP of my corporate Wins/DNS Server)
wins proxy = yes (this tell samba to work as wins clients)
dns proxy = yes (this tell samba to use your DNS to resolve names)ù

MOST IMPORTANT I change the way the priority for name resolution work for samba:

name resolve order = wins hosts lmhosts bcast 

After this change just doing a samba restart and all my computers in the network and all the shares of a computer show up in Nautilus.
Hope this help.

---

