---
title: "SSH Keys"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by tr1xjolly on 2010-10-15
I'm running Ubuntu 64 bit Server in VMWare on my Windows 7 desktop.  I have Cygwin installed on the desktop.   I'm trying to generate SSH keys so I can SSH from Ubuntu to my desktop without entering a password.  I've done this in other distro's of Linux but I can't seem to get it here.  The weird thing is, I've been able to generate the keys in Cygwin and then SSH from Cygwin to Ubuntu with no password, but I can't go the other way.  The steps I'm following are:

(on ubuntu) ssh-keygen -t dsa
Press enter 3 times so no passphrase is used.
(on ubuntu) scp id_dsa.pub windowsip:/home/user/.ssh
(on ubuntu) ssh windowsip
(on ubuntu) cd /home/user/.ssh
(on ubuntu) cat id_dsa.pub >> authorized_keys2

Then when I try to SSH from Ubuntu to Windows/Cygwin, I get the error "Agent admitted failure to sign using the key."   And then it prompts me for the password.

I've already searched all over the internet and have re tried doing this in different ways about 30 times, posting here is my last resort!  Thanks for any suggestions you guys may have.

---

