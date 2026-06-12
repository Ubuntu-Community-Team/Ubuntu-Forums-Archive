---
title: "Share folder on a secondary NTFS drive"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by MockY on 2009-01-12
My wifes backup hard drive is still formated with NTFS (I will get around to change that in the future) and I would like to share a folder from that drive. The sharing part is not the hard part, it's getting to it that is the hard part.
By browsing the network, the share is visible, but when I try to access it I am prompted for credentials (just like I should) but it will not accept what I feed it, even though it's correct. This process works just fine when the hosting OS is Windows, but it appears as if something different is going on when the host OS is Ubuntu sharing a folder on a secondary NTFS drive.

Could someone enlighten me?

---

### Post by superprash2003 on 2009-01-12
you need to add a samba user.. thats probably why you face this problem.. try this guide [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html) especially step 2

---

### Post by Paris Heng on 2009-01-12
yes Samba will do

---

