---
title: "MP3 player doesn't mount"
date: 2012-01-25
forum: Multimedia Software
---

### Post by claus on 2012-01-25
Hi all,

after upgrading to 10.04, my Intenso mp3 player doesn't mount.

lsusb gives the following output:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 03f0:0024 Hewlett-Packard KU-0316 Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 008: ID 0402:5668 ALi Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

How can I mount the player manually?

TIA,

Claus

---

### Post by sanderd17 on 2012-01-25
Can you tell me how many hard drives you have (including external ones and usb sticks that are connected to your computer), and show us the output of

```

ls /dev

```

---

### Post by claus on 2012-01-25
> **sanderd17 said:**
> Can you tell me how many hard drives you have (including external ones and usb sticks that are connected to your computer), and show us the output of

```

ls /dev

```#

I have one hard drive (/dev/sda). My USB stick is usually not connected to the computer.

ls /dev gives the following result:

[IMG]http://home.arcor.de/ccyrny/screenshot.png[/IMG]

Thanks for your reply,

Claus

---

### Post by sanderd17 on 2012-01-25
hmm, I can't find your drive. Can you pull the mp3 player out and in again, and give the last part of the output of the command
```

dmesg

```

I hope I can see it there.

---

### Post by claus on 2012-02-05
> **sanderd17 said:**
> hmm, I can't find your drive. Can you pull the mp3 player out and in again, and give the last part of the output of the command
```

dmesg

```

I hope I can see it there.

Hi,

after typing in ```
dmesg
``` the player is being mounted. I have no idea what's the matter here, but thanks for your help!

Greetings,

Claus

---

