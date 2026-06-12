---
title: "Accessing Windows 7 shares on another PC."
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by Stormlord on 2012-12-12
Ok, that's a first for me. If anyone has faced this, I'd appreciate it if you could help.

I have shared a folder on a Windows 7 computer with full read/write access. I can access that folder from my Xubuntu laptop, I can write any file I like on it, I can download any file I like from it, I can delete anything on it, BUT I can open absolutely nothing while it's there. I have to download the file on my laptop first and I can open it successfully afterwards.

If I try to read a simple text file from that share directly, all I see is an empty document. Same goes for pictures. If I copy them back to my computer, everything becomes 100% readable again.

Any ideas please?
Thank you. ;)

---

### Post by sdowney717 on 2012-12-12
I just followed this today and can open files on the win7 pc

[http://www.swerdna.net.au/susesambawin7.html](http://www.swerdna.net.au/susesambawin7.html)

I had to add everyone and set security as well as sharing.
I also had to allow incoming connections in the windows firewall.

---

### Post by Stormlord on 2012-12-12
> **sdowney717 said:**
> I just followed this today and can open files on the win7 pc

[http://www.swerdna.net.au/susesambawin7.html](http://www.swerdna.net.au/susesambawin7.html)

I had to add everyone and set security as well as sharing.
I also had to allow incoming connections in the windows firewall.

Thank you for your response.  :)
I don't want to have shares accessible by Everyone and I don't think there's a firewall problem since I can send and get files from that share.  The firewall should block those actions too, wouldn't it?  It's just the contents of those files I cannot see.  Not the file itself.

---

