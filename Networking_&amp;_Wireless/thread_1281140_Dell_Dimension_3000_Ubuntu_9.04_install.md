---
title: "Dell Dimension 3000 Ubuntu 9.04 install"
date: 2009-10-02
forum: Networking &amp; Wireless
---

### Post by TriumphCycles on 2009-10-02
I just wiped my wifes old Dell Dimension 3000 pc to install ubuntu 9.04. after completing the install my internet would work for maybe 2 or 3 minutes then stop. I uninstalled the old gnome network manager and installed wicd. However this did not solve the problem. I am running a zoom cable modem through a Apple Airport Base Station. It seems as though it gets stuck trying to get an IP address if that helps. Please any help would be great.
Thank you in advance

---

### Post by kreggz on 2009-10-03
Perhaps reinstall gnome-network manager, when it connects type the command "ifconfig". This will tell you if you are getting an IP address.

So are you using Wi-Fi or ethernet?

---

### Post by TriumphCycles on 2009-10-03
I am trying a wired ethernet connection. It doesn't seem like it gets an IP address at all. It occassionally Shows the two two monitors and says connected but I can't connect to the Internet then when I try clicking "wired" again it was stuck at "obtaining IP address" or it would fail to connect in Gnome.

---

### Post by kreggz on 2009-10-03
Hey,

Try this in the Terminal:

Accessories/Terminal

lscpi


Can you see your network card there?

---

### Post by Iowan on 2009-10-04
[This]("http://ubuntuforums.org/showthread.php?t=1156441") one solved my wired DHCP problem.

---

### Post by TriumphCycles on 2009-10-04
I tried the lscpi command it says "command not found" i also tried Iowan's post and the same thing happened. Network manager says im connected but it stops working after a few minutes. Has anyone else had this problem? I think it is grabbing the Airport Base Station's IP address instead of getting assigned my networks.

---

### Post by kreggz on 2009-10-04
That was meant to be:

lspci

Sorry!


ls = list
pci = pci

---

### Post by TriumphCycles on 2009-10-04
> **kreggz said:**
> That was meant to be:

lspci

Sorry!


ls = list
pci = pci


I typed in lspci not to sound like a noob or anything but i wasnt quite sure what i was looking for, and for another update i tried plugging Ubuntu directly into my Zoom cable modem after reseting the modem and it still did the same thing....so would i be correct in guessing that its either the ethernet bridge in my computer...or my cable modem?

---

### Post by TriumphCycles on 2009-10-04
Thinking of trying a new wired ethernet bridge any recommendations?

---

### Post by kreggz on 2009-10-05
if you post the output of that command it would be helpful

---

### Post by TriumphCycles on 2009-10-05
Update: I bought a TRENDnet USB 2.0 Ethernet adapter and everything runs like a dream! After a lot of googling i found out that other people had a problem with the internet connection as well.

---

### Post by kreggz on 2009-10-05
Good work

---

