---
title: "Wireles device does not show when actually present"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by ibates on 2010-10-15
I am running Ubuntu 10.04 LTS from its own HDD and Windows XP Pro SP3 from another HDD.  Boot is selected by GRUB with Ubuntu as the default.

I have a Windows program WADM running on the Windows HDD.  It is the Digital Media Manager for a Philips Streamium wireless audio system consisting of one "Centre" and two independent "stations".

The WADM program finds all audio units, and offers the choice of each of the three units to be connected to the PC via the WLAN.  Normally only the "centre" would be connected because that is the unit with the HDD on which music is recorded.  Content can be edited from the PC when the "Centre" is connected.

When running this program from the Windows PC, all three wireless audio units are "found" and available for connecting.

Now; for the problem.

I have Windows XP Pro SP3 installed on a Virtual Box Virtual Machine running as a guest on the Ubuntu host.

I have installed the WADM program on that Windows VM, but, unlike the program running on the raw disk, the VM Windows only finds two of the audio units, and the missing one is the "Centre".

Given that the VM utilises hardware infrastructure from the host Ubuntu, why does WADM running on the VM not "find" the "Centre".

Using network utilities, all three "ping" correctly, and everything indicates that the "centre" should be available.  But it remains invisible.

Any suggestions as to what is happening, or more to the point is there is any configuring I can do to the Ubuntu host to enable WADM running on the VM to find the "centre"?

---

