---
title: "problem printing to network printer"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by KeithBCDN on 2010-09-14
I understand this is an internet/wireless forum but thought there would be someone here that could shed some light on this.

The HP Laserjet 1018 printer is connected to a networked  XP machine that is accessible from the Ubuntu 10.04 machine. I  can open shared files on the XP machine from Ubuntu so assume that communication is correct.
I have set up the printer as instructed in this help file...
[https://help.ubuntu.com/community/WindowsXPPrinter](https://help.ubuntu.com/community/WindowsXPPrinter)
SAMBA sees the printer on the network , verifies the printer and the driver(from Ubuntu files) loads.
Everything goes along just fine until "print test page" or I try printing a text doc.
The printer is assigned the job# but there is no action.
The printer shows up in the "Printing -local host" window.
Under "printer properties" the "Make and Model"are showing the correct device in the correct location.
The "Printer State" shows "idle - /usr/lib/cups/filter/foomatic-rip failed"
I have purged, uninstalled and re-installed CUPS.
No change.
The articles I have found searching are old and are mostly to do with the driver that was not in Linux at that time.
Any thoughts would be appreciated. Please note that I am new to Linux and am a novice at line code.

---

### Post by blakep2 on 2010-09-15
Try going to Administration > Printing > add printer > network printer> find printer> enter hostname> .....find a driver if supported.

---

### Post by KeithBCDN on 2010-09-15
The printer is on the host and will "verify"
Connection is "windows printer via SAMBA"
The driver is listed in "choose driver" window.
When I select "HP" the driver recomended is "HP910hpijis,3.10.2
However, when I then select "Lasejet 1018" it says "HP910hpijis,3.10.2 requires proprietary plugin"
Not sure what that plugin is or where to get it.
Will do a search...

---

### Post by KeithBCDN on 2010-09-15
Found some info referring to HPLIP and tried to open the HPLIP toolbox to see if it's installed but the GUI didn't open.
tried "sudo apt-get install hplip" and it looks like there was an update.
Still cant open GUI

---

### Post by 23dornot23d on 2010-09-26
From the last remarks in this I think they solved the problem ..... with the drivers ..... [LINK]("http://forums.debian.net/viewtopic.php?f=5&t=41141")

Try here too if you do not want to read through all that   ..... [LINK]("http://hplipopensource.com/hplip-web/downloads.html")

A solution here too ..... sometimes[ other linux forums have answers ]("http://forums.linuxmint.com/viewtopic.php?f=49&t=10461")..... might be worth [setting up the printer ]("http://foo2zjs.rkkda.com/forum/")directly onto the Linux machine first to ensure that the drivers are ok ..... if possible ....

( I think your problem will probably lie with the printer driver )

---

### Post by KeithBCDN on 2010-09-27
I'm sorry for not updating.
I now have network printer working.
Wiped HD and re installed latest Ubuntu.
Made sure Ubuntu machine was on the correct Windows network. I had created a new network that was not WORKGROUP but a different name.
Issue solved.

---

### Post by 23dornot23d on 2010-09-27
Ok good to know .... let me know if you have any other issues ......

Please mark as solved in the Threads Tab above the first post ty ;)

---

### Post by beast2k on 2010-10-10
I just installed 10.10 and now I have a very similar problem with this same printer, I have NEVER had a problem with this printer. I can get the printer to print with the links and instructions here but whenever I reboot my machine I must start all over again. This constant messing around with printing is taking up to much of my time, does anyone know of a solution ?
Just in case I messed something up I am going to reinstall Ubuntu 10.10.

---

