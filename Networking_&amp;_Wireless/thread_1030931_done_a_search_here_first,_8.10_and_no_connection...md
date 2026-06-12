---
title: "done a search here first, 8.10 and no connection..."
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by mtandrews on 2009-01-04
but may I ask first, I see that when folks that help will give you a command to input and tell you "post the response here". How do I do that without having to write it longhand then shut down Ubuntu and boot up to XP Pro to log onto internet to post response?  I don't have access to another computer, just the dual boot/3 HD machine that I'm using now. My box has an ASUS P5GC-MX board, Intel dual core 1.6 mhz processor, 4gb memory, 3 Western Digital Sata drives, AOpen DVD-Rom burner, D-Link DWA-552 wireless PCI card, Lexmark X6570 wireless printer, Polyview flat screen, logitech wireless board and mouse.  In XP everything works (believe it or not). In 8.10 everything seems to be okay except I have no internet. Being new to Ubuntu (hell, Linux period) I am all ears as I really really wanna get into Linux.

---

### Post by damis648 on 2009-01-04
Are you using wired or wireless? What model network card do you have? Could you try
```
lspci | grep -i network
```
and
```
lspci | grep -i ethernet
```
and tell us the output? (Sorry:popcorn:)

---

### Post by mtandrews on 2009-01-04
Wireless,   D-Link DWA-552 Xtreme N desktop adapter

---

### Post by mtandrews on 2009-01-04
[B]lspci | grep -i network[B]   01:00.0 Network controller: Atheros communications Inc. AR5008 Wireless Network Adapter (rev 01)
**lspci | grep -i ethernet[B]   02:00.0 Ethernet controller: Attansic Technology Corp. L2 100 Ethernet Adapter (rev aO)**[/B][/B][/B]

---

### Post by cabbiinc on 2009-01-05
> **mtandrews said:**
> but may I ask first, I see that when folks that help will give you a command to input and tell you "post the response here". How do I do that without having to write it longhand then shut down Ubuntu and boot up to XP Pro to log onto internet to post response?  I don't have access to another computer, just the dual boot/3 HD machine that I'm using now. My box has an ASUS P5GC-MX board, Intel dual core 1.6 mhz processor, 4gb memory, 3 Western Digital Sata drives, AOpen DVD-Rom burner, D-Link DWA-552 wireless PCI card, Lexmark X6570 wireless printer, Polyview flat screen, logitech wireless board and mouse.  In XP everything works (believe it or not). In 8.10 everything seems to be okay except I have no internet. Being new to Ubuntu (hell, Linux period) I am all ears as I really really wanna get into Linux.

If you have a USB drive or other removeable drive you could use that instead of writing.

---

### Post by mtandrews on 2009-01-05
I plan on getting a usb thumb drive but I don't have one. Now for some odd reason Ubuntu won't shut down. It hangs on the shutdown screen with the logo with the line underneath it.

---

### Post by cabbiinc on 2009-01-05
> **mtandrews said:**
> I plan on getting a usb thumb drive but I don't have one. Now for some odd reason Ubuntu won't shut down. It hangs on the shutdown screen with the logo with the line underneath it.

ubuntu has a notpad type program, in Windows Wordpad reads it easy enough. You could place the file on the C drive (no subfolders) for easy retrieval, or make a folder with a shortcut on both boots.

---

### Post by ByKeLaO on 2009-01-06
I also have a D-Link card with that chipset (but a different model number strangely).
I compiled the new versions of the kernel wireless drivers and installed them per these instructions: **[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)**, then restarted my computer.
And now I can connect to my network! Admittedly it's very slow, but slow is infinitely better than non-existent.

---

### Post by whitestag13 on 2009-01-06
guys i need a bit of help..i am currently downloading ubuntu 8.10.have being a wondows user for a long time.i tried 8.04 a good while ago..my wireless card is the problem.i need to no are there a driver for an azure wave card..

---

