---
title: "Can't share files"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by Muster Mark on 2010-10-17
Hi,

I am running ubuntu 10.10 and can view file shares on my other computers (OSX 10.6/win xp) but can't can't view the files on this computer from the other computers.  Screen sharing works between the ubuntu machine and the the mac, but I can't share files.

I have personal file sharing enabled, I have my home folder shared, I have downloaded all the smb packages I can find (as well as an SSH server), what else do I need to do?  For something that worked perfectly, with 0 configuration, in 9.04, this is friggin annoying.

Note: despite my best efforts to nurture my samba deamons, when I try to add shared folders, the only option is nfs, might this be indicative of something?

---

### Post by jackdale on 2010-10-23
I am also having the same problem (Ubuntu 10.10).  I can access my MacBook Pro (OS X 10.6.4) with Ubuntu, but I cannot access the Ubuntu with the from the Mac. I can access screen sharing both ways.  I know that I can do it by scripting the ubuntu avahi server to look like a mac server, but this is less than elegant.  It would be nice to have an out-of-the-box solution that required to editing of config files.

I used to be able to use FUGU through SSH on mac and avahi on ubuntu, but no more since 10.10.

Edit Getting closer:
When in doubt, right click....
So, on the Ubuntu machine, right click the home folder (or whatever folder you want to share) and chose "sharing options", enable sharing and say OK at the prompt to download the appropriate packages, click on Restart Session, to enable sharing.

This seems to download the windows solution. (but i don't have a windows machine to check it).

I am still looking for the Mac OS solution.

Edit2:

For the Mac:

in ubuntu I had to remove my FireStarter (would not allow access to my mac even when its address was included in the allowed exceptions)
For some reason installing the avahi browsers let my mac see the ubuntu
install ssh server in ubuntu (open ssh)
Reconfigured Fugu preferences to delete past known hosts

now vnc and ssh working both ways :)

---

### Post by luvshines on 2010-10-24
> **Muster Mark said:**
> 
I have personal file sharing enabled, I have my home folder shared, I have downloaded all the smb packages I can find (as well as an SSH server), what else do I need to do?

Note: despite my best efforts to nurture my samba deamons, when I try to add shared folders, the only option is nfs, might this be indicative of something?

When you choose share folder from right click, aren't you able to simply share the files ?

---

### Post by jackdale on 2010-11-01
> **luvshines said:**
> When you choose share folder from right click, aren't you able to simply share the files ?

nope

the problem is that it does not broadcast over the network and if you try to just access it, it will refuse the connection.

Still, I'm very happy to be able to use vnc both ways with compiz and cairo dock without the extreme lag that we had in the past

---

