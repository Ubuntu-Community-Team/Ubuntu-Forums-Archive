---
title: "Help! Is it possible to set this up"
date: 2009-04-22
forum: Multimedia Software
---

### Post by modifiedcompacts on 2009-04-22
Wondering if its possible to setup my vga outputs to do something like this?

vga0 - output desktop one to my laptop lcd display 
vga1- output desktop two to my external monitor

possible way to change the xorg.conf file to do this or create a file that would tell it to setup the monitors in this way if external monitor is plug in? I have search all over google and still havent came up with any put the way that you make the screen width wider and have the extra go to the output. I just want the output monitor to display the second desktop panel. Any suggestions of help would be great.

---

### Post by wolfen69 on 2009-04-22
what kind of video card are you using? did you install the drivers? we are not mind readers here.

---

### Post by modifiedcompacts on 2009-04-23
using 8.10 for os, graphics card is ati radeon, and yes i do have the drivers install. basically i would like to be able to use the second monitor for leaving either virtualbox or pidgin open on it. if possible.

---

### Post by wolfen69 on 2009-04-23
have you tried configuring the monitors with the [ATI Catalyst Control Center]("http://ati.amd.com/products/catalystcontrolcenter/index.html")? there is a link at the bottom. or do: 
```
sudo apt-get install fglrx-amdcccle
```
give that a try.

---

### Post by modifiedcompacts on 2009-04-23
ok i already have the ati catalyst installed, but whenever I try to open it. It just tells me that the ait driver is not installed. Which it is? From this point I am lost... Any help guys

---

### Post by modifiedcompacts on 2009-04-23
Okay so after I deactivated my ATI driver. I then rebooted my system, and I went back and reactivated the same ATI driver and now my ATI catalyst program opens right up. And now I am testing out the ATI catalyst program. Do you have any suggestions on using it or are there any how tos out there. Thanks for your help

---

