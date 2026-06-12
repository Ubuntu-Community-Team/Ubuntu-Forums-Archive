---
title: "Problem with homebrew USB and lirc on 9.10"
date: 2010-01-10
forum: Mythbuntu
---

### Post by azmyth on 2010-01-10
I thought I was good at lirc but this one has me horribly stumped. I'm using a homebrew USB receiver and the receiver has a driver that needs compiling. I use 9.10 as my desktop PC so before I upgraded MB to 9.10 I tested on my Desktop knowing this setup could cause problems. Everything worked on the Desktop so I figured it'd work on 9.10 MB. I was wrong as I'm getting the error below when I try irw. 

Right now I'm just trying to get it going command line just to see if it works.

```
$ sudo lircd --nodaemon -d /dev/usbirboy
lircd-0.8.6[1147]: lircd(default) ready, using /var/run/lirc/lircd
lircd-0.8.6[1147]: accepted new client on /var/run/lirc/lircd
lircd-0.8.6[1147]: could not get hardware features
lircd-0.8.6[1147]: this device driver does not support the LIRC ioctl interface
lircd-0.8.6[1147]: major number of /dev/usbirboy is 180
lircd-0.8.6[1147]: LIRC major number is 61
lircd-0.8.6[1147]: check if /dev/usbirboy is a LIRC device
lircd-0.8.6[1147]: Failed to initialize hardware

```

The only difference between the PCs is MB has the 64 bit and the desktop has 32 bit. Same kernel, same version of lirc, same commands, same hardware, same lircd.conf, same driver yet one works and the other doesn't. As a last ditch, I tried compiling lirc but I was left with the same error. I hope someone can help me by pointing me in the right direction as I'm stumped.

---

### Post by azmyth on 2010-01-10
Not really solved but more resolved. I ended up compiling back versions of lirc until one worked. The wheel landed on 0.8.4a.

---

