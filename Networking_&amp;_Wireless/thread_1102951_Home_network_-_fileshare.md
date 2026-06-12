---
title: "Home network - fileshare"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by Abbobo on 2009-03-22
Hi,

I have been using Ubuntu for a while now on both my laptop and desktop. I have spent many hours transferring files between them via usb or whatever means, and has only just struck me that I could network them. In theory anyway - actually trying to do so, it has become aparent that I have no idea what I am doing.

So all I want is to be able to send files from my desktop to laptop, and vice versa. They both have wireless cards. Can anyone give me a starting point? I am using 8.10 and have network manager 0.7.

My google searches have so far proved fruitless.

Thanks
abi

---

### Post by mhgsys on 2009-03-22
```

sudo apt-get install samba

```

```

man samba

```

---

### Post by Abbobo on 2009-03-22
Thank you!

---

### Post by Hobgoblin on 2009-03-22
> **Abbobo said:**
> Hi,

I have been using Ubuntu for a while now on both my laptop and desktop. I have spent many hours transferring files between them via usb or whatever means, and has only just struck me that I could network them.

Since they are both running Linux, [NFS](https://help.ubuntu.com/8.10/serverguide/C/network-file-system.html) may be more appropriate.

---

### Post by mhgsys on 2009-03-22
> **Hobgoblin said:**
> Since they are both running Linux, [NFS](https://help.ubuntu.com/8.10/serverguide/C/network-file-system.html) may be more appropriate.

Your absolutely right about that one, 
Though I use samba myself, lot's off people who come to my home boot windows, so by using samba I can access my shared files with both operating systems.

I found this to be easier.

---

