---
title: "Yet another ndiswrapper question..."
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by Cable on 2006-06-07
I'm trying to get my WMP54G to work.  I downloaded the driver file, so I'm on step 7 of the ndiswrapper wiki.  However, it says to use cabextract or unshield to unpack the file in order to access the .sys and .inf files.  When I try to use unshield on the file, it says it can't open the file as an InstallShield file or something along those lines.  I'd really like to get my wireless working!  What should I do?  I have the Broadcom 4306 wireless card (WMP54G V2).

---

### Post by joplass on 2006-06-07
Dapper came with a default driver for Broadcom cards.  My WPC54G is working with it now.  Check System => Networking to see if you have eth1 in there.  Configurate with your wireless settings.  Unless you want to use ndiswrapper.  By the way there is a wireless page in Wiki that will show you how to disable the default drive and use ndiswrapper.

---

### Post by Cable on 2006-06-07
Well, my WMP54G most definitely doesn't work.  I've tried connecting to my router (with WEP) and it *says* it's active, and looks to connect successfully, but I still don't have internet when that happens.

---

### Post by Cable on 2006-06-08
So, how do I extract the drivers from that exe file?  Please tell me it's possible...

---

### Post by phace on 2006-06-08
Cable:
Download the bcm43xx-fwcutter:
"sudo apt-get install bcm43xx-fwcutter"

After downloading remove ndiswrapper from kernel modules, aliases etc...

Copy the drivers from the install media (the .inf and .sys files) to any location.
"sudo cp /media/cdrom/path/to/driver/driver.inf /media/cdrom/path/to/driver/driver.sys /opt"
"cd /opt"
"sudo bcm43xx-fwcutter driver.sys"
"sudo cp *.fw /lib/firmware/$(uname -r)"
"sudo modprobe bcm43xx"

In order to connect to an encrypted network use wpa supplicant:
"sudo apt-get install wpasupplicant"

---

### Post by Cable on 2006-06-08
[QUOTE=phace] After downloading remove ndiswrapper from kernel modules, aliases etc...[/QUOTE]

Not really sure what you mean by this, or how I would do it.  Could you explain?

---

### Post by Cable on 2006-06-08
I also tried going through the process described [here]("http://www.ubuntuforums.org/showthread.php?t=185174"), and that didn't work either. Is there a way to remove what I did from that howto and start fresh?  I also noticed on that howto that it sets the wireless card up to use only B, and not G.  I need to use G.  Is it not possible to use G in linux?  I need the better range of G because our router is in our basement and I have my computer in my bedroom on the 2nd floor.  Works flawlessly in Windows.  Please help.

Edit:  Also, my wireless card shows up as eth0, and my wired card is eth1.  I don't know if that's important or not, but I figured I'd mention it.

---

