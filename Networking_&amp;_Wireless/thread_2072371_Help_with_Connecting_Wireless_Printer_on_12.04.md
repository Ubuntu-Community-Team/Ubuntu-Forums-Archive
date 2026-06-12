---
title: "Help with Connecting Wireless Printer on 12.04"
date: 2012-10-17
forum: Networking &amp; Wireless
---

### Post by MichaelNevermore on 2012-10-17
Hi. I just recently bought an HP Deskjet 3520. I know of course, that Ubuntu has compatibility issues, but I was hoping that with HPlip I could get the wireless connection working. So I open hp-setup from the terminal, and check off "Network/Ethernet/Wireless Connection (direct connection or Jetdirect)" and hit "next." I've gone through the whole process of setting up the printer on it's own UI, what with selecting languages and loading paper and ink, but the printer doesn't show up on the list of "Discovered Devices." It says "No devices found" at the bottom.

So, is there any way of making the printer discoverable, if it isn't already? And is there anything else I'm doing wrong?

I'd appreciate the help. I have to return the printer within 14 days if I can't get it working.


By the way, I'm running Ubuntu 12.04.


EDIT

Thanks for the replies, guys, didn't expect to get answers so quick, but I already figured to out. I have my laptop dual-booted with Windows 7, so I popped in the setup disk and configured the network, then booted Ubuntu back up, and HPlip found it fine. Thanks again, though, guys.

---

### Post by otetiani on 2012-10-17
I've set up a few HP wireless printers and other than some scanning issues had no issue with using CUPs.

Did you remember to set-up the printer on your wireless network form your printer?

Check the network settings of the printer and print the page, then test by pinging to the address.

I have had one HP printer that would cause a wireless network to fail, so first thing is to ensure you can connect to the network again after you print the first time.

good luck

---

### Post by ahallubuntu on 2012-10-17
There's nothing magical about a wireless printer.  If it's wireless, it's on your network just like a wired network printer (not USB).  It will have an IP address, etc.  All the wireless does is replace a cable.

The trick is getting the printer setup the first time.  This can be a pain and require the manufacturer's setup software (sometimes Mac or Windows-only).  Some printers, fortunately (like my Canon) have a keypad, and I can setup the wireless connection that way without using any computer.  Once I've done that to put it on my network, it might as well be a wired printer as far as any of my computers are concerned.  They can't tell the difference.

I've not setup an HP wireless printer, so I don't know how you must set it up.  Sometimes if you connect it via a network cable the first time, you can access the printer settings without any software (via a web browser) to set up the wireless connection info.  Of course, if it has a keypad like my Canon, you ought to be able to setup the wireless network that way.

Assuming it has been successfully setup on your network: can you find its IP address?  Does the printer have the ability to print a page of configuration info by itself, so you could find out the IP?  That can help you find the printer on the network when trying to install it in Ubuntu.

---

