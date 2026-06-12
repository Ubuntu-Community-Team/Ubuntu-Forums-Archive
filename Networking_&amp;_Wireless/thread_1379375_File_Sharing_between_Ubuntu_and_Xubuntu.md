---
title: "File Sharing between Ubuntu and Xubuntu"
date: 2010-01-12
forum: Networking &amp; Wireless
---

### Post by paulbdavis on 2010-01-12
I have Ubuntu 9.10 on my laptop and Xubuntu 9.10 on my desktop and I need to share files between the two but cannot figure it out. I have tried looking all over the web but can only find solutions for sharing files between Linux and windows boxes. 

I should note that Xubuntu on the desktop is not functioning properly, there are no menu bars/trays on the top and bottom of the screen (something about an HPLIB error pops up on startup).

Any help with this would be greatly appreciated.

---

### Post by puppywhacker on 2010-01-12
I use nautilus. use "go"-"location" or ctrl-l or the little notepad left almost top.

In in the location bar type "sftp://user@192.168.1.2/" substituting your user and the remote client. This should provide you with a sftp sharing, which should work by default. Other alternatives are NFS and SAMBA, but they require more setup.

The HPLIB error is related to a HP printer/scanner library. And the missing bars are because gnome-panel isn't started or even installed

---

### Post by gradinaruvasile on 2010-01-12
Well xfce4-panel (not gnome-panel) should be installed. Press alt+f2 and type:

xfce4-panel

Sharing is straightforward in Ubuntu (Gnome): just right-click on the folder you want to share, click sharing options etc. First time you will be asked to install a file sharing server - choose samba here. 

Mounting shares is easy too: click File -> Connect to server -> select windows share (or samba, no difference), enter the IP of the target computer and youre set. Or just browse the network, might be slower.

On Xubuntu its a little different: Applications -> System -> Shared folders, install samba when prompted. Choose the folders you want to share (first authenticate by clicking on the key icon).
Mounting shares is about the same: Applications -> System -> Remote Filesystems (the program is named Gigolo :) ), click on the 2 monitor icon, select windows share etc just like in Ubuntu. Opening the share is double-clicking on the share.
 
Tips:
On Xubuntu: make sure the file manager is gvfs-open in the Gigolo Preferences and Unix-type file manager is selected.
Install the smbfs, gnome-mount, gvfs,gvfs-fuse  packages to make mounting work righ. Some of them are already installed, but you need to make sure - Open a terminal and type:

sudo apt-get install gnome-mount gvfs gvfs-fuse smbfs

You can use ssh too, but that too needs to be installed aswell:

sudo apt-get install ssh

Using samba is better if you transfer much data and want to share files quick, its far faster than sftp (ssh), but not that secure. If you use it on your closed LAN, no problems.

---

### Post by PyrO_PrOfessOr on 2010-03-01
Excellent! I have been looking for how to enable file sharing on XUbuntu most of this evening! Glad I screwed up my search and stumbled upon this! 

Cheers!

---

### Post by uRock on 2010-03-17
This thread just helped me big time. Thanks!

---

### Post by djinnkeeper on 2010-08-07
> **gradinaruvasile said:**
> On Xubuntu its a little different: Applications -> System -> Shared folders, install samba when prompted. Choose the folders you want to share (first authenticate by clicking on the key icon)
I have a question about this, but please forgive me if it's simply something that has changed recently, therefor no longer applying.   I noticed this thread references 9.10, but I am using 10.04 (Ubuntu on one system, Xubuntu on another) .. in Gnome, everything pretty much carries out as described.  It prompts me to install samba, etc, so forth.. however, in XFCE, I do not see **Applications > System > Shared Folders** .. though I do appear to have Gigolo installed and in the right place.

I kinda have to wait to start messing around with it again, because everyone else is still asleep and the offending computer is out in the living room.  I'm not even sure if I know what my question is and I know if I keep messing around with it, I'll eventually figure it out.  When I'm using Samba and Gigolo (on the XFCE end anyhow) can anyone tell me, will I have to use the target server's name or network address?  Both?  I'm a little bit confused by Gigolo.

Thanks in advance for any pointers, help, etc.. but no worries if I have to figure it out alone.  (I know when I figure it out, I'll feel a bit dumb)

---

### Post by tracr on 2010-08-17
djinn:
go to **Applications>Settings>Main Menu**
scroll down to *Administration *and you'll see the *Shared Folders* icon to the right.  Check the "Show" box to the left of it.

Next, go to **Applications>System>Shared Folders**
and you will be prompted to add the Linux and/or Win compatible services and once they are installed, you can begin adding shares.

---

