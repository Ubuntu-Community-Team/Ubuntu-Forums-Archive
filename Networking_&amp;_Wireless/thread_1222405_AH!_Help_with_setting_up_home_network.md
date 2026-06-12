---
title: "AH! Help with setting up home network"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by ztmike on 2009-07-24
Okay..I'm having one hell of a time setting up a home network.

Here's what I'm wanting to do:

I have a older computer running Xbuntu that I want to use as a file holder (where I can store my files) but I also want to be able to change files/delete as necessary, from my main computer running Ubuntu. I also have another computer running Ubuntu under the same log-in name but I don't really need this computer to be part of the file sharing process. 

The guides I have found so far have been confusing to say the least. 

It seems from what I want to do, the simplest way is do a FTP server? But how?

---

### Post by ztmike on 2009-07-24
I just spotted this thread
[http://ubuntuforums.org/showthread.php?t=1221943&highlight=home+network](http://ubuntuforums.org/showthread.php?t=1221943&highlight=home+network)

But on the Xbuntu machine, "Sharing Options" doesn't show up? But on my 2 Ubuntu machines it does? The Xbuntu machine is the computer I want to store my files on..

---

### Post by Iowan on 2009-07-25
The power supply failed before I got to experiment much with my Xubuntu machine, but it seems like it needed some additional software to share via Samba.  You might also consider sharing via SSH or NFS (both will require server software installation), or installing Samba server software.
There are a couple of FTP server versions you might check, too. [This]("http://ubuntuforums.org/showthread.php?t=1213999") thread might be of interest.

---

### Post by ztmike on 2009-07-25
I had Samba installed on the Xbuntu machine.. But I still should of been able to see "Sharing Options"

---

### Post by Iowan on 2009-07-26
The "Sharing options" *might* be a function of Nautilus - which Xubuntu may not use. (just guessing here - Thunar comes to mind). You should still be able to set up shares via */etc/samba/smb.conf*.

---

