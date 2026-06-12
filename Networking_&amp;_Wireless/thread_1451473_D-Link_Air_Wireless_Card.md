---
title: "D-Link Air Wireless Card"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by 1roxtar on 2010-04-10
I have a D-Link Air DWL-520 wireless card on my desktop computer.  It runs well with Windows, but doesn't seem to work with Ubuntu.  I am using Lucid Beta 2.  I have tried googling, but have not come across any clear solutions on how to make it work.  Your help will be much appreciated.

---

### Post by gordintoronto on 2010-04-10
According to this page:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI)

there are multiple DWL-520 wireless cards. Some should work "out of the box" with Ubuntu, some do not. Have you used this card with an earlier version of Ubuntu? In which case, your question should go in the Lucid beta forum.

If you would like further help, please open a terminal and enter the command:
lspci
It should produce about 20 lines of output, near the bottom will be your wireless card, please copy/paste that line into a message.

Do you have a network manager icon at the top-right, near the volume control?  Can you right-click it, select "edit connections," then click the wireless tab, "add" and enter your SSID, encryption type and passphrase?

---

