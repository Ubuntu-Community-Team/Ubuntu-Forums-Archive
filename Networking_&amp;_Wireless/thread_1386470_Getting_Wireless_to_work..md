---
title: "Getting Wireless to work."
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by OhShift! on 2010-01-20
Version of ubuntu: 9.1.
Laptop: HP Pavilion dv216cl
 
Followed the ndiswrapper tutorial. Found the correct driver and when I went to install the driver. I selected the .inf file, clicked install. An error message popped up stating that "Couldn't verify hardware is present". I pressed "ok" went to the main menu, it said the driver was there, and the hardware was there. But wouldn't let me do the network configuration.
 
I exited out the window, and opened it up again without doing anything the messaged popped up again.
 
Won't let me access my wireless.
 
Any help?

---

### Post by OhShift! on 2010-01-21
Ttt.

---

### Post by OhShift! on 2010-01-22
ttt

---

### Post by bkratz on 2010-01-22
What is your wireless card?

To determine go to the terminal  (Applications>>Accessories>>Terminal) and type in 
lspci  (that is LSPCI in lowercase) Copy/paste the output back here
and also
lsusb  (LSUSB just in case it is a usb device)

---

### Post by blackened on 2010-01-22
Are you sure that model number is correct? I'm not seeing anything on the web that references a dv216cl. Is it hot off the presses or something? Is it made of dark matter?

---

