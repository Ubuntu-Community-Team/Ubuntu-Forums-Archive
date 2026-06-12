---
title: "Getting workstation shares working on Windows machines"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by gwagnon on 2009-08-27
I have installed a number of different linux systems; currently, I am setting up an 8.04LTS desktop system, and I have installed the packages for samba.

I have also used the administrative tool for sharing files, and tried all of the combinations of settings that this tool offers.  I am having the same difficulties that I usually encounter with packaged Samba setups, namely, that I can browse and access shares on other Windows computers, but I am unable to access the linux shares on the Windows systems.

I am running a peer to peer network with mixed linux and windows machines (Win98SE, Win2k & XP), with no domain controller, and I have not tried to configure Samba's domain controller features.

Everytime in the past, I have had to resort to swat in order to get everything working, but this time, I really hoped that the packaged system would work.  I really don't want to blow everything away and start from scratch with swat this time.

The linux shares are visible, but not accessible on the XP machine.  The linux machine can be seen, but not browsed on the Win98SE machine.  On the Ubuntu box, the access is similar to the XP, I can see the shares, but not access them either.

In all cases, I get a dialog asking for a password, but the password is never accepted.  Is there a simple fix for this via the packaged administration, or is Ubuntu still back in the needing swat to make it work state?

---

### Post by Iowan on 2009-08-27
[This]("http://ubuntuforums.org/showthread.php?t=1169149") is for viewing Windows shares from an Ubuntu box, but some hints might help.

---

