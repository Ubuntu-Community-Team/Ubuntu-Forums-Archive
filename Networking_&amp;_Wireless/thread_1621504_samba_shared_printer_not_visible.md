---
title: "samba shared printer not visible"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by Paul A C on 2010-11-14
I am trying to access a shared printer from one Ubuntu PC to another.

On the Server PC, I have the printer working, I have set it to shared, and I have set the server setting to Publish shared printers.  I can see and use the printer fine from a windows PC.

On my Ubuntu Client PC, I have samba installed, including smbclient, and all other samba components I can think of.  I can see other computers on my home workgroup (Windows and Ubuntu fine).  I can also add a printer connected to my windows PC.  However I cannot find the printer connected to the other ubuntu PC.

I see the instruction in the Samba guide saying

"Now enter your Ubuntu Samba Print Server (set up as above) IP address in the box on the left titled "smb://"."

However I do not have fixed ip addresses, so what am I supposed to enter in the box.  If I enter nothing I can browse the network and can see the host computer, but the printer is not displayed.  I can also see the printer connected to the windows PC.  How do I 'see' the Ubuntu printer?

---

### Post by Paul A C on 2010-11-14
Well, I have found a sort of solution.

On the Client computer, if I go to server, and tick show printers shared by other systems, then I can see the printer.  However, I cannot 'control' the printer settings, despite the host PC being set up to allow remote control.


[I]A bit of an aside...

[/I]Seems Samba has a way to go to make it easy an intutive!  It is a shame it is harder to share a printer between 2 Ubuntu PC's than between a windows PC and a Ubuntu one.

I also am having MAJOR issues getting all rpinter features I want to work, like using Photo black ink when printing photos.

We desperately need to improve printer setup and functionality in Linux.  I am more than willing to help.  I have a Canon ip3600 & ip4300 at present.

---

### Post by SteveDee on 2010-11-14
> **Paul A C said:**
> ...On my Ubuntu Client PC, I have samba installed, including smbclient, and all other samba components I can think of...

You should not have to add samba packages to a Lubuntu (printer) client.
The libsmbclient is installed by default.

If you go to:-
 Preferences > Printing
...and the printer has not been discovered, continue to:-
 Add > Network Printer > Find Network Printer 
...then enter the IP address of the host and search.

Regarding black ink, not sure if black is missing from colour photo, or you want to print as greyscale.

---

