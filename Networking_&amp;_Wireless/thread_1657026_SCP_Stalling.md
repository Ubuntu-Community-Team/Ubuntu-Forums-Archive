---
title: "SCP Stalling"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by xeemo on 2010-12-31
A little over a year ago I was using SCP to successfully transfer large files over my LAN (exact same hardware). I can't seem to do this any more, and I'm not sure why.

I think it's either something with iptables, or a network card driver problem. I use the same driver for both computers (b43 wireless). I think there was a major change with the driver somewhat recently, but I'm not sure on the exact details.

I can't do FTP transfers either. They start going, but quickly stall. I've used the Firestarter (iptables gui) to allow all the correct connections.

One last thing: When I tried to connect to ssh using an alfa wireless card (not sure of the drivers), I couldn't even connect to ssh period. Same settings were used.

Any ideas? Help would be appreciated.

---

### Post by PatchesTheCaveman on 2010-12-31
Are you not otherwise having any other network difficulties?  Some people have better luck with the Broadcom STA wireless driver over the kernel b43 driver.  For more info see this thread:  [http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

Firestarter is actually a GUI for *ufw*, a replacement for *iptables*.  You can try completely disabling the firewall with this command to completely eliminate it as a cause:
```
sudo ufw disable
```

You might want to also make sure your SSH packages are up to date:
```
sudo apt-get upgrade ssh
```

Also, you really should be using SFTP instead of SCP.  It's a more modern protocol that accomplishes the same task (transferring files over SSH).  See [FONT="Courier New"]man sftp[/FONT] for details or use the FileZilla GUI, which works great IMHO.  You can install that by running:
```
sudo apt-get install filezilla
```

---

