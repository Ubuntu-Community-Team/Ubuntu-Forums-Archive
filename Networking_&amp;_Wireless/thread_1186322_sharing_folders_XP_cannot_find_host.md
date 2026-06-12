---
title: "sharing folders: XP cannot find host"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by srem on 2009-06-13
I know there are millions of posts on the subject and I've read them all (or most!).
I have a jaunty px and an xp one, in a wireless home network through a wifi router.
I have installed Samba on ubuntu jaunty, I have modified the conf file making sure both PCs are in the same workgroup, I have shared a folder with Nautilus in jaunty, I have enabled guest user.

The pc with XP can ping the jaunty machine and can also connect to its desktop via tight vnc.

From XP I go to "run" and type "\\jaunty ip\sharedfolder"
but I only get "The network path was not found"

Any ideas? what am I missing?

---

### Post by srem on 2009-06-13
I have tried the 
smbpasswd -a your-user thing
and I have changed to:
security = share

and restarted samba

---

### Post by Iowan on 2009-06-14
Firewall (Windows or Jaunty)?
It's probably safe to assume that Jaunty doesn't show up in Network Neighborhood, either...

---

### Post by superprash2003 on 2009-06-14
does only \\jaunty ip work?

---

### Post by srem on 2009-06-14
I have switched off the firewall in XP, I haven't installed one in jaunty.

---

### Post by srem on 2009-06-14
Same, even with "\\jaunty ip" alone.

I have also tried with another jaunty machine in the network and the 2 jaunties cannot see each other.

---

### Post by superprash2003 on 2009-06-15
post output of **smbtree** from the jaunty machines

---

### Post by Iowan on 2009-06-15
I stumbled across [another ]("http://ubuntuforums.org/showthread.php?t=1188383") thread today that solved Samba issues by installing **smbfs**. I'll also point out [this]("http://ubuntuforums.org/showthread.php?t=1169149") How-To - in case you haven't already seen it.

---

### Post by lisati on 2009-06-15
Sometimes Windows likes you to run the "Network setup wizard" before it lets you see other computers on the network.

---

