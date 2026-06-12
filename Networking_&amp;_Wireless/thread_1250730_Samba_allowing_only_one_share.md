---
title: "Samba allowing only one share"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by redadept on 2009-08-26
Hi Folks --

This is a strange one.  I'm running Ubuntu Jaunty + Samba and am trying to access multiple shared folders on my Windows XP (Home) machine via workgroup MSHOME (change duly made in smb.conf).  I boot into WinXP without a password and the folders are simply set to "shared" with no password and the WinXP firewall configured to allow the shared folders.  My XP netbook can see and access them all on workgroup MSHOME, but two Ubuntu Jaunty machines (a desktop and a wireless netbook) can mount ONLY ONE of the shared folders.  Each time I try and mount a second share (visible in the Nautilus 'Network' panel) the system asks for a password using my Ubuntu username, the default domain WORKGROUP, and a blank for password.  Needless to say, I've not found any combination of username, domain and password that will successfully connect me to the second shared folder.  

So --- first folder mounts and provides access with no problem.  Second, third, fourth ... folders require some mythical combination of username, domain name and password.

Any ideas ???

Thanks in advance ...

-- Darrell

---

