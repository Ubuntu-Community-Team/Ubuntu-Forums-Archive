---
title: "should i install the ATI driver?"
date: 2006-01-06
forum: Multimedia &amp; Video
---

### Post by zahidism on 2006-01-06
I have an ATI mobility radeon 9000 (i believe it's an IGP...not sure) on my Dell 600m and i just installed ubuntu, everything looks great, and i dont really game...well at all and i dont plan on it...what else would i need the ATI driver for?  can someone tell me how to check to see what ubuntu is recognizing it as?

---

### Post by Rob2687 on 2006-01-06
**lspci** will give you a device list.

---

### Post by zahidism on 2006-01-06
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [Radeon Mobility 9000 M9] (rev 02)

that means its installed right?

---

### Post by reet on 2006-01-06
That means you have one plugged in to your computer, it doesn't have anything to do with the driver.

I personally think it's always a good idea to install the latest drivers for everything. It's not a lot of work either. Check the "Tips and Tricks" section for a howto.

To see what driver xorg is currently using, the easiest way to do this is to look in the xorg.conf file. Look under Section "Device", for a line that says:

Driver "something"

Where "Something" is the current driver being used.

---

### Post by zahidism on 2006-01-06
Driver		"ati"

---

### Post by matthew on 2006-01-06
That means you have the proper driver installed for 2D work and so on. Unless you need 3D acceleration you don't need to do anything else. If you want to play 3D games you would want to install the "fglrx" driver, but from your initial post it really doesn't sound like you need it. If you are happy with the current performance of your video card, then you don't need to do anything else.

---

