---
title: "smbclient -L What is a share?"
date: 2010-03-26
forum: Networking &amp; Wireless
---

### Post by RichardRicardo on 2010-03-26
So, I've mucked through and figured out how to mount a windows share. I can access the folders I was looking for, but the windows share was not what I thought it would be. I was looking for the specific shared folder. Instead I got a root level parent directory that included the folder I wanted, and a couple others.

smbclient -L <ipaddress> gives me a parent directory on the root

First question: Can I mount a specific folder within a share?
Second question: Could somebody define share?  I thought it was the specific shared folder, but that doesn't seem to be the case.

I don't know if I am coming at this from the wrong direction. Any help would be appreciated.

Thanks,

---

### Post by Iowan on 2010-03-26
I'm not sure I could give an authoritative definition of "share", but it sounds like the share may defined a bit too loosely. Here are some How-To's for windows shares:
[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")
[http://ubuntuforums.org/showthread.php?t=1186877]("http://ubuntuforums.org/showthread.php?t=1186877")
When I mount a share from my Samba server, it is only the directory - not a root directory, so it *can* be done...

---

