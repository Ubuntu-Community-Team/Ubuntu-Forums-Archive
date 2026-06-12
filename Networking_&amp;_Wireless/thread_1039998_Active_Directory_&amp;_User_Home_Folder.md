---
title: "Active Directory &amp; User Home Folder"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by stm_tech on 2009-01-15
hello there.

NOOB ALERT!!

I work in a school and we have a lot of old pc's that I would like to extend the life of. We are a M$ AD School with over 300 clients.

I have chosen XUBUNTU 8.1 as the tartget machines are Celeron 1GHZ with 256 MB RAM (Compaq D310). They have 20GB HDD's.

I have a machine with 8.10 installed and running. I have also installed likewise AD. I joined the domain with the lin machine and verified this by logging on with a domain account.

What I need to do now is mount the windows share for the user that logs on. They have a home folder that in windows looks like:

\\server\home$\pupil\%username% (year 7-9)
\\172.16.0.52\pupil$\%username% (year 10-11) (a nas box)

They also have a mapped drive to

\\server\shared$

How can I do this in Xubuntu 8.1?

I am desperate to get linux into this school as I am astonished as to the price of the yearly Microsoft licencing.

I assume that I would need to create some kind of script that was run when ever that user logged on.

---

### Post by stm_tech on 2009-01-15
I now now about some system variables in linux such as $LOGNAME

I also know how to mount a windows share using smbmount.

What I need to be able to do is automate the smbmount for whoever is logging on so that their home folder (on NAS or SERVER) is mounted in the work folder.

I assume (probably incorrectly) that likewise can get the relevant value from Active Directory? So I need a script that can query this value and passit to the smbmount command?

I dont't fancy having to create a script for every user, would prefer a generic one that got the values from AD if possible?

---

### Post by stm_tech on 2009-01-23
I have also replied to a thread over at the likewise forum:

[http://www.likewise.com/community/index.php/forums/viewthread/45/](http://www.likewise.com/community/index.php/forums/viewthread/45/)

In case some of you more clever linux bofs are interested in commenting on this.

---

### Post by airmorris on 2009-09-12
Noob to Noob. I was wondering if you have had any success in your quest. I have 22 netbooks with Ubuntu 9.xx and need the same solution. I have been able to join the domain various ways and browse the network shares but that won't work for 4th graders. I need it to automatically mount the shares. Let me know if you find anything.

---

### Post by slavik on 2009-09-12
what you can do is edit the user's .bash_profile script to mount these. That script gets run when they log in to the system. As always, add checks to see if the directory is not already mounted and if something is mounted, to make sure it's the correct one.

then you can edit files in /etc/skel (this is a skeleton that user's home dirs are made from).

---

### Post by kmaynard on 2010-01-26
Hi stm_tech. I have the same problem a year later than you. I posted [this ]("http://ubuntuforums.org/showthread.php?t=1389946")before seeing your thread. Did you get a workable, manageable solution? I went for ldap rather than Likewise so Ubuntu would get the UnixHome dir from the windows server during authentication.

---

