---
title: "Netgear WG111T"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by Until It Sleeps on 2009-02-11
I've searched throughout the forums attempting to find a solution, until now. If you have been having problems with a Netgear WG111T Wireless USB adapter with Ubuntu 8.10, here's a solution that actually works.

This solution considers the fact that you have not connected to the internet at all since you installed Ubuntu. 

Go to Synaptics package manager, and install the Windows Wireless Drivers utility (If you've tried the other solutions, I'm sure you've done this).

I have attached a driver from the Windows software that comes with it. Keep in mind that this is Version 2 of the software. iirc, there are 2 versions of the WG111T adapter, both looking exactly the same, so you need to look on the box for the version.

Install that single driver through Windows Wireless Drivers, and you're set to go. Note that this seems to be a newer version of the driver. This particular one is the only one that has worked for me personally. It may or may not work. 

Hope this helps anybody who has been having any problems with this.

---

### Post by Pedro D on 2009-02-16
Hello:) I am new to ubuntu ( I just started today ) and I don't quite understand what to do after I open up Synaptics package manager:confused: I have the same wireless usb adapter but it is version 1.3 I thought if I copied the adapter's driver from it's cd that I have and pasted it to that package manager I could click apply and there you go but it turns out that's not it:( What should I do? And how should I do it?

EDIT: When I tried to paste it to the package manager, nothing happened. It couldn't be pasted:O

---

### Post by Until It Sleeps on 2009-02-24
Alright, you need to install the Windows Wireless Drivers utility first. Select that from the list in Synaptics, and if you're connected to a wired network, it should download it. Otherwise, you will have to install it from the Ubuntu install CD, which I will go into more detail if needed.

---

