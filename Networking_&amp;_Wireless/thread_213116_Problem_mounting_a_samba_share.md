---
title: "Problem mounting a samba share"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by kimu on 2006-07-10
I'm trying ti mount a samba share. I can connect from samba, but when I try to mount it, this is the response:

```

kimu@kimuntu:~$ sudo mount -t smbfs //OFS/sharedDocs /media/OFS
mount: wrong fs type, bad option, bad superblock on //OFS/sharedDocs,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

I don't understand what I'm doing wrong. Any suggestion?
This is a windows folder and it's not necessary any password or user name to connect. What's wrong?

---

### Post by scxtt on 2006-07-10
try smbmount?

---

### Post by kimu on 2006-07-10
> **scxtt said:**
> try smbmount?

command not found, this is the answer? I didn't find anything in Synaptic too.
Where do I get it?

Thanks

---

### Post by scxtt on 2006-07-10
do you have samba packages installed on your ubuntu box? -- i'd imagine it's installed along w/ them ...

---

### Post by kbayly on 2006-07-10
you should try installing the **smbfs** package if you havent already.

word up!

---

### Post by kimu on 2006-07-10
> **scxtt said:**
> do you have samba packages installed on your ubuntu box? -- i'd imagine it's installed along w/ them ...

I had samba-common, but not samba. I've installed samba but with smbmount was still the same... command not found...:confused: 

I noticed that I hadn't installed smbfs, uhu ](*,) that was the problem :mrgreen: . I've installed smbfs and now mount -t smbfs //OFS/sharedDocs /media/OFS has done its job....

Thanks anyway ...if not for you I could have spent hours trying to understand the problem without noticing that smbfs wasn't installed on my system...

Bye

---

