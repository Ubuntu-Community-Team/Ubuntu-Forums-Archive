---
title: "windows share mounting issues (fstab to Vista, security)"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by chrisbrousseau on 2009-08-10
After following the excellent how-to's on this topic outlined by dmizer ([http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)) to create a **Permanant Mount of a windows share** I was still stuck... 

Despite a bunch of work on my Vista machine (e.g. enabling file sharing, enabling file/print sharing on the laptop firewall, etc), AND a bunch of work on the linux box (e.g. installing smbfs, crafting fstab, etc) I was unable to successfully mount a share from my work laptop to my linux machine (running jaunty), even though I could easily mount similar shares from my XP machine also on my network.  Yes, I checked the password carefully, blah blah - but that wasn't it.  

Given the uselessness of the linux error messages I was getting (from CIFS), I then tried to map the share as a drive from my XP machine, and was confronted with repeated password challenges that would never go through.  **Then, I discovered this link:**
[http://thinkabdul.com/2007/03/11/tip-how-to-enable-network-file-sharing-between-windows-vista-and-mac-os-x-or-linux/](http://thinkabdul.com/2007/03/11/tip-how-to-enable-network-file-sharing-between-windows-vista-and-mac-os-x-or-linux/)

Thanks Abdul!

This pages shows **how to revise an obscure setting on the Vista laptop that prevented successful shares,** even though it otherwise appeared to be setup correctly in Vista.  Basically, what this setting does is enable a "well known authentication method" (per the tips author), that was disabled by default in Windows Vista.  Note, this change requires Administrator access on the Vista machine.

---

### Post by quixote on 2009-08-11
Interesting!  Thanks for sharing that.  It's the type of thing where you can tear your hair out for days on end and get nowhere.

---

