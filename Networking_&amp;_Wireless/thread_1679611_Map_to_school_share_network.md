---
title: "Map to school share network"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by Frantumn on 2011-02-01
Hi, I am trying to map to my schools shares VIA their network. 

Normally on windows, I would just say Run and type the network path and it would open a window with the folders. 

the path is \\KNA11.XX.ON.CA 
you need to be on our VPN to connect to it, which I am. 

How do i access this directory in ubuntu? And even better, make it a permanent shortcut or mountpoint so that i can easily access it later without having to re-mount it.

Thanks!

---

### Post by pauljwells on 2011-02-03
I have exactly the same question... Can't find an answer anywhere and I've been looking for weeks.

---

### Post by cipherboy_loc on 2011-02-03
Try something like this:

```

sudo smbmount //IP.ADDRESS(/FOLDER?) /home/username/school/mnt -o username=USERNAME,password=PASSWORD,uid=1000,mask=1000

```

That assumes it is a samba share. You will need to install the samba tools (open up synaptic and search for smb).


Cipherboy

---

### Post by AlexQM on 2011-02-03
Have a look for Gigolo in the Software Center, that will do exactly what you're looking for!

Alex

---

