---
title: "Booting a diskless workstation without floppy,hdd and even without a screen..."
date: 2009-01-28
forum: Networking &amp; Wireless
---

### Post by Aranyik on 2009-01-28
Hi,

I've got this old Pentium II _desktop_ that I'd like to use.  So the first step is to make it boot.

The desktop **has** a:
[INDENT]-floppy dd and one diskette;
- IBM etherjet wakeup on lan NIC;
- USB ports;
- BIOS that allows booting from network.[/INDENT]

but the desktop **has NOT**:
[INDENT]-Screen :!:
- Hard disk drive;
- BIOS that supports booting from a USB device.[/INDENT]

That's why I'm thinking of booting it from a network. A server could be placed on my _laptop_ for booting the desktop.

My laptop has:
[INDENT]-CD ROM drive;
-One ethernet network card;
-USB ports.[/INDENT]

and **has NOT**
[INDENT]-A floppy disk drive.[/INDENT]

The only extra material I have is a **USB hdd** and a **USB pen**.

I have already tried waking up the desktop by sending a manually generated ip frame and it worked. But the DHCP + tftp servers did make it boot. I've read the forums about diskless workstation but I had to stop at the part that says "*Boot client from a diskette*". The diskette is actually empty and the listings up-above explain why.

Now, since a diskless workstation main purpose is to get everything from the network and doesn't need any disk, there must be a way to configure the client directly on the server.

(Any kind of solution with the listed material would be valid)

Thank you all in advance.

---

### Post by nixscripter on 2009-02-04
The specifics are a bit complex, but I would suggest a [GRUB boot floppy]("http://linux-sxs.org/administration/grubflop.html"), with a tiny linux kernel on it which uses a [serial console]("http://tldp.org/HOWTO/Remote-Serial-Console-HOWTO/index.html") and connects to the server.

I would also suggest, however, at least getting a screen.

EDIT: And a USB floppy drive can create the floppy disk if you could buy that, they're real cheap.

---

### Post by Aranyik on 2009-02-05
Thank you

I have tried FreeSCO which is great but you still need a screen and a floppy. The main purpose of this post was chalenging people to find a way to push the whole thing through a network by relying on the network boot sequence.

I still think there could me a way, but now I must handle other problems elsewhere...

Maybe one day this post will continue!

---

