---
title: "Trying to setup a network printer"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by CurtM on 2010-05-29
I am using Ubuntu 10.04 and I am having trouble connecting to my HP LaserJet 5000 printer, which is connected by Ethernet to my router (D-Link DI-524).

Just today I successfully created a network and setup file sharing between my Ubuntu computer and my girlfriend's Windows Vista computer.  (Yes, that means I have Samba installed.)  Now I want to set up the printer so we can both use it.  The printer is not connected to either computer.  It is connected by Ethernet cable to the router with a Hewlett Packard JetDirect card inside the printer.

I can connect the printer via parallel port to parallel-to-USB cable, and Ubuntu and Windows both automatically recognize it.  That works great most of the time.  But I want to instead use the printer as a network printer.

Everything is connected and turned on.  But I don't find the printer on the network, either in Windows or in Ubuntu.  I need someone to hold my hand and walk me through the process to figure out what step I am missing.

In Ubuntu, I go to System-Administration-Printing.  I click Add, then Network Printer.  I then see a list of items:
   Find Network Printer
   AppSocket/HP JetDirect
   Internet Printing Protocol (ipp)
   LPD/LPR Host or Printer
   Windows Printer via Samba

What should I do next?

When I print the configuration page from the printer, it tells me that it's IP address is 192.168.1.103.  I have tried poking around in the Network Printer page mentioned above, but I haven't found any options that recognize my printer on the network.  I tried clicking on Find Network Printer, and entered 192.168.1.103 for the host and clicked Find.  It reported "No printer was found at that address."

Can anyone help?  Do you need more info?
Curt

Unrelated information:
I am fairly new to Linux and Ubuntu.  I started using Ubuntu about 8 months ago, and I like that it does a good job of recognizing my hardware, and is generally easy to use.  I especially like the big supply of available software.  It has made the transition from Windows to Linux a bit easier.  I don't like that I had to upgrade my computer motherboard, CPU, and RAM to get Ubuntu running at a reasonable speed.  I am obviously not a computer guru in Windows or Linux or networking.  My next project will be to set up a dual-boot with Windows and Linux.

---

### Post by CurtM on 2010-06-19
I finally figured it out.  The HP LaserJet 5000 has the JetDirect 600n turned off by default.  I had to go through the menus (in the buttons on the printer) to turn it on (BOOTP=ON, if I remember correctly), and then both Windows and Linux noticed the printer on the network.  Just now I printed test pages from all three computers, and the world is a happy place.

In unrelated news, I found Lubuntu and love it.  I reformatted my Ubuntu hard drive, and put Lubuntu on it instead.  I have a pretty fast computer with a quad core processor and 4GB of RAM, but I still like the idea of trimming down Linux as much as possible.  Software bloat is one of the reasons I am using Linux instead of Windows as much as possible.  On my computer 32 bit Lubuntu runs faster than 64 bit Ubuntu did, and I still have access to Ubuntu software.  I am a happy man.

---

