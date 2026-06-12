---
title: "network share -- needs work"
date: 2012-10-05
forum: Networking &amp; Wireless
---

### Post by mike acker on 2012-10-05
today, after getting my new u-box running i had to carry data from my old Win7 box on a thumb drive

because i can't remember quickly how to establish a network share

i did it on my test machine and it was a PITA+++

I had to create a Samba user ID, authorize it to use the share and equate it to the incomming user id from Windows.  and most of this had to be on using terminal and sudo.  we need a better tool

and no, I'm NOT going to use the cloud.

i never did find a PDF with step by step instructions -- that would have made me happy, particularly if it was in our sticky notes.  i did find pdf's with a series of hints which i was finally able to piece together:(

---

### Post by JRV on 2012-10-05
it's easy:
```

nautilus smb://Windows_Hostname/Windows_Sharename

```

This works if you have not changed anything in /etc/samba/smb.conf

It may work if you changed /etc/samba/smb.conf but I have not tested it.

---

