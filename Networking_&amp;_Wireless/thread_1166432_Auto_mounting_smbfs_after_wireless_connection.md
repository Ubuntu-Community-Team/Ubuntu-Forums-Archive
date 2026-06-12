---
title: "Auto mounting smbfs after wireless connection"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by quickdraw on 2009-05-21
I know that is one long title, but that's basically the jist of my problem. 

I have a Hp mediavault, and am able to mount it using "sudo mount -t smbfs" just fine, but I'd like to be able to have that happen after I connect to my wifi connection. 

I've read a bit about fstab and even some crontab mentioned, but I need it to happen AFTER I connect to my wireless network ... since naturally ... the HPMV is connected to my wireless router. :D

Any advice would be great. 

Thanks!

---

### Post by puppywhacker on 2009-05-21
can't remember the full details, but if you have it setup in the interfaces file, you;d want to add an "up" or was it "if up" rule running your command as soon as the network goes up. ... add it to the /etc/networking/interfaces file...

---

