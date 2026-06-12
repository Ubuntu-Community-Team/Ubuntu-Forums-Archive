---
title: "network drive eclipse says folder is read-only"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by sc1447 on 2011-10-26
Hi,

I have an iomega network drive on the router. I mount it after editing the /etc/fstab and it loads fine using //SERVER/SHARE /MOUNT-POINT smbfs guest 0 0

I can create and delete folders on the drive but when I open eclipse project which is on the drive it says "folder marked read-only" so it won't build anything. 

On the windows side, I can see the folder properties and indeed "read-only" is checked.

I'm not sure whats going on, I can create files via console and explorer. But eclipse is not able to do that? Can anyone help, im using the most recent Ubuntu version 11.10.

Thanks

S

---

### Post by sc1447 on 2011-10-28
Experts, cny help would be very nice. Thanks

---

### Post by fdrake on 2011-10-28
when you edit the file are you logged as "guest" or with another username? try first with:
```

sudo su guest
<go to your dir and lunch eclipse from terminal>

```

---

### Post by sc1447 on 2011-10-29
I wasn't logged in as guest on my linux machine. I tried a different mount which seems to work .. atleast at the moment. Thanks for your reply though.

---

