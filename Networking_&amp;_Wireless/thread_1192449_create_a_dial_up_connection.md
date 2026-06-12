---
title: "create a dial up connection"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by A-750 on 2009-06-20
Hello
My Dial up modem is [B]U.S. Robotics V.92 Voice Modem
[/B]
How can i install it on ubuntu  9.04 ?
How can i create a dial up connection?

Thank you

---

### Post by haemulon on 2009-06-20
I don't know what type of modem the v.92 US Robotics is.

If it's an internal modem it will be more difficult to set up, and may not even work at all.

If it's an external modem, it will just work and you won't have to set up anything special as Linux will recognize it.

The easy way to set up a dial up connection after you get the modem issue sorted out is to use wvdial.

wvdial is a very easy program to use and set up, use the package manager to download it.  Look for the README file, it's simple to set up the connection.

good luck.

---

### Post by A-750 on 2009-06-20
> If it's an internal modem it will be more difficult to set up, and may not even work at all.
It's internal modem

---

### Post by A-750 on 2009-06-21
how about this internal modem?
**Motorola SM56 Speakerphone Modem**
can i install it?

---

### Post by ubu_maury@italy on 2009-07-31
Hello to all,
are Italian, I also wanted to add to the problem of A-750 I have the same internal Motorola SM56 modem on Ubuntu 9.04.

---

### Post by Bartender on 2009-08-13
The Motorola SM56 is a softmodem.  Good luck.  You need to find out what chipset in on the modem and then you might be able to make it go.

I won't waste my time with softmodems any more.

---

