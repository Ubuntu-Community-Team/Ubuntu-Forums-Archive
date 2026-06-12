---
title: "Ubuntu 8.04 x64 - dvgrab no camera exists"
date: 2008-08-15
forum: Multimedia Software
---

### Post by Wild-Storm on 2008-08-15
Hi,
I've recently got a new pc with a mobo-firewire plug (so there's no pci-card).
First of all I had to load the 1394 modules and reboot to get the /dev/raw1394 device.

```
mrnice@my-0wn:~$ cat /etc/modules | grep 1394
raw1394
video1394
```

But when I'm trying to record a video from my dv-camera i get the following error:

```
mrnice@my-0wn:~$ sudo dvgrab -i
Error: no camera exists

mrnice@my-0wn:~$ dvgrab -i
Error: no camera exists

```

Chmod:
```

mrnice@my-0wn:~$ chmod 777 /dev/raw1394
mrnice@my-0wn:~$ sudo chown mrnice:video /dev/raw1394

```


What made me a little bit perplex was this one:
```

mrnice@my-0wn:~$ sudo testlibraw
successfully got handle
current generation number: 0
0 card(s) found

mrnice@my-0wn:~$ sudo lshw | grep 1394
mrnice@my-0wn:~$

```

```
mrnice@my-0wn:~$ ls -l /dev/raw1394
crwxrwxrwx 1 mrnice video 171, 0 2008-08-15 08:43 /dev/raw1394

mrnice@my-0wn:~$ lsmod | grep 1394 
video1394              22248  0 
ohci1394               36532  1 video1394
raw1394                31624  0 
ieee1394              106968  3 video1394,ohci1394,raw1394

```

I would be very pleased if somebody could help me.

Cheers

Motherboard: LanParty DK X38

edit:// Forgot one:

```

mrnice@my-0wn:~$ dmesg | grep 1394
[   48.426712] ieee1394: raw1394: /dev/raw1394 device initialized
[   48.434682] video1394: Installed video1394 module
```


```

mrnice@my-0wn:~$ sudo gscanbus
couldn't set port: Invalid argument

```

edit2:// AHCI-Mode is enabled, if that helps something

edit3://

```

mrnice@my-0wn:~$ dmesg | grep firewire
mrnice@my-0wn:~$
```

---

### Post by Carl H on 2008-08-15
I presume the camera is plugged in, switched on, and in the correct mode for Firewire connection?

My camera has both FireWire and USB connections, but only one works at a time and it defaulted to USB. I had to select FireWire in the menu. (As well as loading the 1394 modules, etc, like you've already done).

---

### Post by Wild-Storm on 2008-08-15
Yep it is. The Camera has only the FireWire-Mode (and it worked since i got the new pc)


edit:// Is there maybe any way to find out if my pc has a video-in?

---

### Post by Wild-Storm on 2008-08-15
Okay i got now a PCI-Firewire card from a friend. gscanbus returns now something, but i still can't get dvgrab working (kino doesnt work either..)


edit://
[B]
fixed!
[/B]

oh lord, this time i didn't plug the cable properly ^^

---

