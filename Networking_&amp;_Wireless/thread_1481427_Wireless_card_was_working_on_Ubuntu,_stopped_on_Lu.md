---
title: "Wireless card was working on Ubuntu, stopped on Lubuntu install"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by wideaperture on 2010-05-12
I had my wife's ancient Dell Inspiron 8200 running on Ubuntu, then Xubuntu—I keep going for more and more lightweight OS's.  I just installed Lubuntu, and the wireless card that had been working fine on the previous distros is suddenly not working.  I have pastebins of the before-and-after driver/hardware information.

Here's the pastebin from Xubuntu, when all the hardware, including the wireless card, was working: [http://pastebin.com/1idFTXR9](http://pastebin.com/1idFTXR9)

And here's the same readout from Lubuntu, where the wireless card is no longer working: [http://pastebin.com/SA1U73ZF](http://pastebin.com/SA1U73ZF)

The pastebins contain terminal readout (lsusb, lspci, lsmod, lshw) from both distributions.

Can anyone tell me what broke between one OS installation and the next?  Or better yet, how to fix it?

---

### Post by wideaperture on 2010-05-16
For whatever reason, the problem appears to have been with the full installer.  After several days on IRC and various forums trying to get the system to recognize the wireless card, to no avail, I wiped the system and installed from scratch using the Lubuntu Wiki [instructions]("https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Minimal%20Install") for conducting a minimal install.  After installing this way, the system recognized the wireless card just fine.

I'm not sure why the Lubuntu installer disk didn't work, while the minimal install method did, but it might be something to look into if you're a developer on the project.

---

