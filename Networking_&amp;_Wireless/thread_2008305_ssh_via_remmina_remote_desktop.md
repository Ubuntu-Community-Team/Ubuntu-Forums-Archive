---
title: "ssh via remmina remote desktop"
date: 2012-06-22
forum: Networking &amp; Wireless
---

### Post by WebDrake on 2012-06-22
I use Remmina to connect from outside to a Windows machine in my office network.  There's also a Linux machine on the office network which is not accessible outside the company LAN.

Is it possible to ssh into the Linux machine via the Remmina connection, and if so, how?

Thanks in advance for any assistance!

---

### Post by papibe on 2012-06-22
Hi WebDrake.

The simplest solution I can think off is to install Putty (ssh client) on the Windows machine. Once you are connected to the Windows machine, you can ssh to the local Linux box using Putty.

It may be even possible to create a tunnel, so once you are connected to the Windows machine, you could ssh directly from where you are to the Linux box (using Putty's tool plink).

I hope that points you in the right direction.
Regards.

---

### Post by WebDrake on 2012-07-04
> **papibe said:**
> The simplest solution I can think off is to install Putty (ssh client) on the Windows machine.
That's actually what I did in the end -- adequate, though definitely not perfect!  I'll have a look into the tunnelling possibilities you suggest.

Sorry for the belated thanks, I was travelling in the last days and only just checked in on the responses here.

---

