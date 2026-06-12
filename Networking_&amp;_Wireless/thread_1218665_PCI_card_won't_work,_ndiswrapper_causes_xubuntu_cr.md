---
title: "PCI card won't work, ndiswrapper causes xubuntu crash"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by yeanomaybe on 2009-07-20
I'm a complete newbie when it comes to ubuntu, but i got windows off my older computer and xubuntu onto it. however, i didn't know how to configure my network (which is based off of a windows computer) to allow an auto-configuration for DHCP. I read in a couple places that DHCP may allow people I don't want onto my network. I don't know if that's true. My network uses a WEP key. 

I still have the disc with the drivers for the PCI card installed into the computer, and thought I had found my solution when I installed the drivers using ndisgtk. However, my computer started acting strangely, not allowing me to close the network manager or to open several programs. It was also still not even detecting my wireless network. 

I restarted the computer in hopes of fixing it, and the system went on to fail to start up after I logged in. It said there was some type of error with the network manager. After a long time trying to figure something out with the terminal I was given, including trying to simply wipe network manager from the face of my OS, I gave up and simply wiped the hard drive with DBAN and reinstalled xubuntu. I thought that maybe a driver had been left over from my partition that included Windows, but when I went through the same process again my computer acted the exact same way. 

I believe I may have figured out the problem, but I'm not sure. When I looked up all the devices connected to my computer and searched through for the PCI card, I found it running the driver tulip. Is it possible that the conflict between the tulip driver and the driver from the disc is causing the system failure? If so, can someone please tell me how I can remove tulip and simply use ndiswrapper/ndisgtk to fix this.

p.s. since the computer is (as forementioned) not connected to the internet, I've had to download .deb files onto my other, internet-connected windows computer and burn them into discs to use programs. However, I still have the boot disc and can take programs from that. I believe I'm on Xubuntu 8.04. Help.

---

### Post by cariboo on 2009-07-20
It would really help if you told what make/model your pci card is.

---

### Post by yeanomaybe on 2009-07-21
My card is pretty old- DWL-G510 AirPlus G 2.4GHz PCI adapter is what it says on the installation guide.

---

