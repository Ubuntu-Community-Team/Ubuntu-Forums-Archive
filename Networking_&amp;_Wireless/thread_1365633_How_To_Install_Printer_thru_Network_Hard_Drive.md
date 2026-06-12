---
title: "How To Install Printer thru Network Hard Drive"
date: 2009-12-27
forum: Networking &amp; Wireless
---

### Post by undoIT on 2009-12-27
I am trying to setup up an HP Officejet G85xi printer through an Iomega Home Media Network Hard Drive, so that the printer can be shared over the network without requiring that an attached computer be turned on to print. There is a place on the back of the Network Hard Drive to plug in the printer with USB. Then the printer is available over the network via SMB at the following location: //WORKGROUP/IOMEGADRIVE/Printer1

When I add a new Network printer, Ubuntu sees the printer on the network and I am able to install the printer driver. However, when I go to print, nothing happens.

Previously, when I tried to install the G85xi locally with USB, the Ubuntu printer driver installed but did not work. If the printer is installed in HPLIP then it works. And then, after the printer is installed locally on a computer with USB through HPLIP, it can be shared as a network printer and I am able to print from other computers simply by adding the Network printer without going through HPLIP on the client computers.

There does not seem to be a way to install an SMB shared printer in HPLIP on the client computers and it seems that HPLIP only supports printers connected directly to the network. Is there any way to get this working directly through the Network Hard Drive so that the computer next to the printer does not have to be turned on in order to print?

---

