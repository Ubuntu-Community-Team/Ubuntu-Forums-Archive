---
title: "How to set up Ubuntu as network file server?"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by Golevel on 2009-05-11
I've got Ubuntu 9.04 Desktop version installed on my computer at home. I have 4 other computers (two desktops, two laptops) that I would like to be able to share files between, but windows is a POS when it come to that.

So, I would like to set up my ubuntu desktop as a file server for the other computers on my network, so that they can upload/download files to my ubuntu machine and only have access to a particular folder.

Any ideas?
Thanks!

---

### Post by Peter09 on 2009-05-11
Look at

[http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver)

---

### Post by Iowan on 2009-05-11
Based on Gutsy, that server may be getting a bit old (since Gutsy officially retired April 18, 2009). [Howtoforge.com]("http://www.howtoforge.com/howtos/linux/ubuntu") has several other "perfect server" articles, but you should be able to meet most of your needs with [Samba]("https://help.ubuntu.com/community/SettingUpSamba").

---

### Post by dmizer on 2009-05-12
> **Iowan said:**
> Based on Gutsy, that server may be getting a bit old (since Gutsy officially retired April 18, 2009).

Yes, it's also inaccurate in several places, including (but not limited to) enabling the root account, omitting the leading "/" on directory paths, and including the "force group" option.

---

