---
title: "NETGEAR WG311v3 Troubleshooting."
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by aBlkSheep on 2013-05-10
Hello, i'm very new & could not find the " absolutely new/beginner " forum to post in, hence me being here.

Just installed Ubuntu 12.04 LTS onto my HP Compaq dc 5850 Microtower.  
No internet connection.
My wireless card is 54mbps wireless NETGEAR WG311v3 .
I don't have a Windows OS running along side Ubuntu.

I've followed the following thread: 
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

When i use " dpkg -i (filename) " it says the file cannot be found or does not exist.

Files i've downloaded:
-ndiswrapper-common_1.57-1ubuntu1_all
-ndiswrapper-utils-1.9_1.50-1ubuntu1_i386
-Windows 2000 driver 

Please help in providing any solution to connecting to a home network.  
Ethernet cable is not an option.
Thank you.

---

### Post by squakie on 2013-05-10
First, I would undo what you have done, including removing ndiswrapper so it's at a "clean" state.

Then:
[LIST]
[*]reboot
[*]once rebooted, insert the livedvd media - close out anything about a software source being found
[*]use the file manager, navigate to the /pool/main/n/ndiswrapper folder on the livedvd.  You should see 2 things there:  ndiswrapper common and ndiswrapper utils.
[*]Click on the ndiswrapper common file to start it's installation.  This will probably bring it up in the software center .
[*]When that has finished, do the same with the ndiswrapper utils file
[*]now navigate to the /pool/main/n/ndisgtk folder.  You should see a single file there for ndisgtk.
[*]click on the ndisgtk file to begin it's installation.  This will probably bring it up in the software center
[*]now unpack the windows 2000 driver so that the .inf and .sys files are in a new folder - perhaps "netdriver"
[*]start ndisgtk (it will be windows drivers), click add and point it to the .inf file
[*]wait a few minutes then check in network manager to see if wireless networks are now showing
[/LIST]

There are a couple of things to be mentioned, though:

Most adapter drivers can now be installed by temporarily hard-wiring your pc to a router, then using additional drivers to install one, without a need for ndiswrapper.

It used to be that ndiswrapper only worked with Windows XP drivers.  Also, the driver architecture (32 or 64 bit) *must* match the OS - 32 or 64 bit.  

The link you posted is pretty old from what I saw - back to Fiesty, and we're in Quantal now.

I hope I got this right.  I'm not my Unix box right now, so I can't double check it first.

---

### Post by aBlkSheep on 2013-05-10
Thanks for the reply Squakie.

Typo: My OS is Ubunutu 12.04 LTS.

When Software Center opens it doesn't allow me to click on install.  Here is what it says.

" Some vendors do not release specifications of the hardware of provide a linux driver for their wireless cards.  This project implements Windows kernel API and NDIS API within linux kernel.  A Windows driver for wireless network card is then linked to this implementation so that the driver runs natively, as though it is in windows, without binary emulation. 

This package contains wrapper scripts to call out to the proper versions of whatever -utils-X.X package is installed "

I also did a little research on hardwiring to pc to router & was wondering if you could explain this a little more.

---

