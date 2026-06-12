---
title: "Problem installing LW272 3G data card"
date: 2013-03-21
forum: Networking &amp; Wireless
---

### Post by dhirajkhanna on 2013-03-21
After a week of frantically searching for a solution, I am on the verge of giving up.
I have a 3G data card LW272 Teracom (MTNL) which is running absolutely fine in Windows. However I have a problem in installing it on Ubuntu 12.10. lsusb output gives me the Vendor ID as 0x230d and product id is 0x0103. I have installed usb_modeswitch and created a file /etc/usb_modeswitch.d/230d:0103 containing the following information :-

DefaultVendor=0x230d
DefaultProduct=0x0103
Configuration=2

Also /lib/udev/rules.d/40-usb_modeswitch.rules contains the following :-

#Linktop LW272/LW273 (BSNL Teracom)
ATTRS{idVendor}=="230d", ATTRS{idProduct}=="0103", RUN+="usb_modeswitch '%b/%k'"

After having done this, when I plug in the modem, nothing seems to happen. There is no new broadband connection available in the network manager applet.
Some help here please.

---

### Post by bmork on 2013-03-21
> **dhirajkhanna said:**
> After a week of frantically searching for a solution, I am on the verge of giving up.
I have a 3G data card LW272 Teracom (MTNL) which is running absolutely fine in Windows. However I have a problem in installing it on Ubuntu 12.10. lsusb output gives me the Vendor ID as 0x230d and product id is 0x0103. I have installed usb_modeswitch and created a file /etc/usb_modeswitch.d/230d:0103 containing the following information :-

DefaultVendor=0x230d
DefaultProduct=0x0103
Configuration=2

Also /lib/udev/rules.d/40-usb_modeswitch.rules contains the following :-

#Linktop LW272/LW273 (BSNL Teracom)
ATTRS{idVendor}=="230d", ATTRS{idProduct}=="0103", RUN+="usb_modeswitch '%b/%k'"

After having done this, when I plug in the modem, nothing seems to happen. There is no new broadband connection available in the network manager applet.
Some help here please.

This device seems to be unknown so far, so I guess we should add it here and there.  Could you post the output of "lsusb -vd 230d:0103" for a start?

How did you come up with exactly that modeswitch config?

---

### Post by dhirajkhanna on 2013-03-21
@bmork
I referred to this link :-
[http://antojose.com/content/quick-how-to-setup-configure-teracom-lw272-bsnl-3g-usb-data-card-modem-ubuntu-1004-lucid-1010-maverick](http://antojose.com/content/quick-how-to-setup-configure-teracom-lw272-bsnl-3g-usb-data-card-modem-ubuntu-1004-lucid-1010-maverick)

Output of lsusb -vd 230d:0103 is attached.

---

### Post by bmork on 2013-03-21
> **dhirajkhanna said:**
> @bmork
I referred to this link :-
[http://antojose.com/content/quick-how-to-setup-configure-teracom-lw272-bsnl-3g-usb-data-card-modem-ubuntu-1004-lucid-1010-maverick](http://antojose.com/content/quick-how-to-setup-configure-teracom-lw272-bsnl-3g-usb-data-card-modem-ubuntu-1004-lucid-1010-maverick)

Output of lsusb -vd 230d:0103 is attached.

Right. That's nice. Yes, your modeswitch configuration looks fine based on that lsusb output, and there should be a number of drivers picking up this device. Does it work better if you run

sudo usb_modeswitch -v 230d -p 0103 -u 2


If that doesn't seem to make any difference either, could you post the last lines of the "dmesg" output after plugging the modem?  It should tell us which configuration was selected and the loaded drivers.

---

### Post by dhirajkhanna on 2013-03-21
Well, what can I say......You did it !!!!!!
I can't tell you how happy I am. My faith in open source collaborative problem solving is reaffirmed.
Thanks a ton. The output of the command you gave me is :-

```
Looking for default devices ...
   found matching product ID
Getting the current device configuration ...
 OK, got current device configuration (1)
 Found device in default mode, class or configuration (1)
Accessing device 007 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x00
Using endpoints 0x07 (out) and 0x87 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usbserial_generic")
 OK, driver "usbserial_generic" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: &#65533;A_
   Model String: &#1219;&#65533;&#65533;&#65533; jx&#65533;
Revision String: $
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: HSPADataCard
     Product: HSPADataCardA
  Serial No.: 8444311594054030
-------------------------
Changing configuration to 2 ...
 OK, configuration set
Getting the current device configuration ...
 OK, got current device configuration (2)
The configuration was set successfully
-> Run lsusb to note any changes. Bye.

```

After which the data card was detected as a new broadband connection.
Only problem is that the speed that I am getting is much slower than what I get on Windows. 
Anyway, that's more of a configuration issue with the network provider which I shall figure out.
But thanks once again. Really do appreciate it.

---

### Post by dhirajkhanna on 2013-03-21
Ok really dumb thing to ask, but how do I mark this as SOLVED?

---

