---
title: "Connecting to Windows Shared folder with Read &amp; Write Access"
date: 2012-08-08
forum: Networking &amp; Wireless
---

### Post by regmem on 2012-08-08
Hi,

I have a Xubuntu 12.04 setup with pyNeighborhood installed.
I can connect to a windows shared network, but all the folders are read only and I cannot edit any file.

Following is the command I used to connect

```
mount.cifs //X.X.X.X/common/ /mnt/gdrive -o credentials=/home/abcde/.pyNeighborhood/.authstore rw
```

After that I can see browse the folders thru thunar but Cannot edit file.

Please tell me what am I missing.

Thanks

---

### Post by Merrattic on 2012-08-08
Why use pyNeighbourhood when Gigolo is installed by default?

Try using user credentials (user ...and pass if required) first to test where the user can successfully read/write

---

### Post by regmem on 2012-08-08
> **Merrattic said:**
> Why use pyNeighbourhood when Gigolo is installed by default?

Try using user credentials (user ...and pass if required) first to test where the user can successfully read/write

Gigolo hangs for me when I provide the server details

---

