---
title: "mp3 player does not pop up when plugged in"
date: 2008-05-31
forum: Multimedia Software
---

### Post by nix4me on 2008-05-31
Ubuntu 8.04 will not pop up a file browser when I plug it in.  Any ideas why?  Older version of Ubuntu worked fine along with Fedora.

I get nothing when I plug it in and there it is not mounted at all.

---

### Post by abhiroopb on 2008-05-31
plug it in open a terminal and type in:
```

lsusb

```
and
```

sudo fdisk -l

```

and paste the output of both please.

---

### Post by nix4me on 2008-05-31
After issuing lsusb, the drive is mounted and rythmbox opens.

Why is this not happening on plugin?

---

### Post by abhiroopb on 2008-05-31
Hmmm I don't think lsusb has anything to do with it. lsusb is just to see what usb devices are plugged in. Perhaps you just had to restart the computer or something.

---

### Post by nix4me on 2008-05-31
Nah, never restarted.  The device is not being detected when plugged in.  The lsusb command shows no device.  Then a second later, the mount happens and rythmbox starts.  Another lsusb command shows the device.

1st "lsusb"
nix4me@desktop:~$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000

2nd "lsusb"
nix4me@desktop:~$ lsusb
Bus 008 Device 013: ID 0781:7432 SanDisk Corp. 
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000

Seems like a bug to me.  I filed one on launchpad.

nix4me

---

### Post by abhiroopb on 2008-05-31
maybe it just takes time? try restarting the computer and waiting a few seconds after plugging it in...what mp3 player is it?

---

