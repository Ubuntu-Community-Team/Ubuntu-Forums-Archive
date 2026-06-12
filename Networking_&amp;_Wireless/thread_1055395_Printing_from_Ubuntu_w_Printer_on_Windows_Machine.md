---
title: "Printing from Ubuntu w/ Printer on Windows Machine"
date: 2009-01-30
forum: Networking &amp; Wireless
---

### Post by skunkbad on 2009-01-30
I've got a computer here, and until yesterday it was a Windows XP box. I installed Ubuntu, but don't know how to get the printer that is on the office computer to work with it. The office computer is a WinXP computer. I checked the Brother website, and they do have a driver for Linux/Ubuntu, but I'm guessing that I need some way to connect to the Windows machine. Samba? I've never done this before, and would appreciate a tutorial or some advice.

---

### Post by yther on 2009-01-30
Well I can tell you that this should be pretty easy.  Here on 8.10, I added a new printer (using KDE tools, you'd probably use GNOME equivalent) and just told it the printer was on a Windows machine, then gave the make and model.

On the XP box, enable File and Printer sharing if you haven't already, and remember what the "shared name" of the printer is if it's different from the real name of the printer.  (The shared name is what other computers will see it as, which can be different from what you see in the Printers folder.)

One thing I remember is that I had to provide it with the exact **name** of the printer on the XP box.  This is the "shared as" name I mentioned above.  Once I got that right (took a couple of tries before I had all the settings correct), the test page I had sent while messing around magically queued up and started printing.

Mine is an Epson Stylus C88, and I did not have to download any drivers for Linux; CUPS offered me a few choices and I picked the one that said "recommended."

This was on a fairly default setup of Kubuntu 8.10.  Connection works whether I'm on wireless or wired connection to my home LAN.

---

### Post by skunkbad on 2009-01-30
Well, that was too easy! I did it just like you said. I didn't even choose my printer, I chose one that was close in model #, and it works fine. Thanks!

---

### Post by mrpbjnance on 2009-01-31
I am still unable to print.  I can see files on windows and windows can see my unbuntu files.  My Printer is networked off my XP machine and other computers can see and print to it.  But I am unable to connect with my unbuntu machine.  Any Ideas?

---

### Post by yther on 2009-02-02
> **mrpbjnance said:**
> I am still unable to print.  I can see files on windows and windows can see my unbuntu files.  My Printer is networked off my XP machine and other computers can see and print to it.  But I am unable to connect with my unbuntu machine.  Any Ideas?

Did you verify that you specified the exact name of your printer when configuring CUPS access from Ubuntu?  That would be the name that appears in XP when you go to the Sharing tab of its properties and look at the "Share name" item.

For example, in my Printers folder on XP, the printer shows up as "EPSON Stylus C88" but I chose to call it just "Epson C88" when sharing it.  If I don't type "Epson C88" in the CUPS configuration, it doesn't work.

Aside from that, all I can think of is that it might be some firewall setting, or... well, I don't know.  :(

---

