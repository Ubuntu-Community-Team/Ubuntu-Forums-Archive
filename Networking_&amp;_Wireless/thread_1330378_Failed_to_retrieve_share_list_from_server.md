---
title: "Failed to retrieve share list from server"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by OpenTangent on 2009-11-18
I am getting this error trying to connect to a windows PC. I have only been getting this error since i upgraded to 9.10. Connecting straight to the specific shared folder works though, except when i set the windows user to disabled which worked in 9.04. I need that user set to disabled because i need the windows PC to boot straight to the desktop (main user has no password). What is going on with Samba?

---

### Post by Iowan on 2009-11-18
[This]("http://ubuntuforums.org/showthread.php?t=1169149") How-To might help.

---

### Post by OpenTangent on 2009-12-13
My solution was to not require a password for the shared folders on the Windows PC. Thanks for the link Iowan.

---

### Post by denniscardinale on 2010-01-04
Had the same problem.  Could not see anything through findsmb, and got message "Failed to retrieve share list from server".  And this was on a 9.10 installation that was working fine until I left for vacation.

Tried all the fixes I could find...no luck.

Boy...am I red in the face!  Winds up I had moved the computer, which has 2 network adapters, and plugged the network cable into the wrong adapter.

My smb.conf had this line:

   interfaces = 127.0.0.0/8 eth0

Obviously, it wouldn't use eth1.  Anyway, thought I'd post here in case anyone made the same mistake.

Dennis

PS -> A message more detailed than "Failed to retrieve share list from server" would be useful.  Something like, "Hello there, you idiot.  There ain't no Windows network attached to eth0.  In fact, there ain't no network there at all..." :)

---

