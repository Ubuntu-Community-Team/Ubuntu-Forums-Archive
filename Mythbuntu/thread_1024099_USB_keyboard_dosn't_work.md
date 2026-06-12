---
title: "USB keyboard dosn't work"
date: 2008-12-28
forum: Mythbuntu
---

### Post by Peter Martin on 2008-12-28
I am installing Mythbuntu 8.10 amd64 on my amd64 3200+
I have a Logitech **MX5000** bluetooth keyboard mouse combo plugged into a USB port. I've checked that the BIOS is enabled for these items on a USB. The unit works with Windows installed, and works through the first part of the live CD install of Mythbuntu. At the screen where there is the option of going with Mythbuntu live, or doing an install, the keyboard still works. By the next screen it had been cut off. Thankfully I had a PS2 mouse and keyboard lying around, and was able to continue the install.
I found a spot under 'Applications / xfce setting manage / removable Drivers & media /' to put in a command to auto run when USB keyboard is connected ( and dito for mouse)??

Any help will be much appreciated. Looking at a 47" HDTV from the end of a 3' mouse cord sucks.

Peter Martin

---

### Post by newlinux on 2008-12-29
when you have the MX 5000 connected, what does

```

lsusb

```

return? just seeing if for some reason it is not even seeing the keyboard for some reason on the install...

---

### Post by Peter Martin on 2008-12-30
lsusb returns

Bus 003 Device 006: ID 046d:c709 Logitech, Inc. BT Mini-Rx (HCI mode)
Bus 003 Device 005: ID 046d:c70a Logitech, Inc. MX5000 cordless desktop
Bus 003 Device 004: ID 046d:c70e Logitech, Inc. MX1000 Bluetooth laser mouse
Bus 003 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 media card reader
Bus 003 Device 002: ID 046d:0602 Ligitech, Inc. BT Mini-Rx (HID prox mode)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
- - - - - - - - - - - - -

The system clearly knows that everything is there so, there must be a very simple reason that it doesn't let me use it??
All very encouraging, Thanks 

Peter Martin

---

### Post by Peter Martin on 2008-12-30
Wow! got it

My son dropped over and gave me a hand.
The problem was not USB, but Bluetooth.
A mating problem.

Input code
[FONT="Arial"]bluetooth-properties[/FONT]

From the window that this function opened, select 'add device'
then pressed the mating button on the bottom of the mouse. 
Waited until the computer found the mouse, then 'add device' and pressed the mating button on the keyboard. Now it all works.

Now that I have a working keyboard I can tackle some of the next problems.

Thanks for the help

Peter Martin

---

### Post by newlinux on 2008-12-30
that was going to be my next question, to see if it was a pairing problem. But you helped yourself, and maybe the next person with the same problem. happy troubleshooting.

---

