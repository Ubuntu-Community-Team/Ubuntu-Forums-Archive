---
title: "UNOFFICIAL Acer Aspire One Wireless HOWTO Thread"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by stoopid_noob on 2008-12-17
Hello, I struggled with this for two days before getting it, but with some excellent help from Crissy(thanks a lot love!) and some patience I was able to get it up and running. I was new to Linux and Ubuntu and had no Linux programming background at all but knew most of what the commands were doing. I figured that it would be easier to writeup a quick HOWTO for all of the othe AAO users out there that are coming from the same. 

Ubuntu Wireless on Acer Aspire One


1.Connect your Acer Aspire One via wired Internet through router (modem direct does not always work) 
2.Click System>Administration>Software Sources then in Ubuntu software tick all boxes except CDROM,(next window)”Third Party Software” tick all boxes,(next window) “Updates” tick all boxes and close to Save
3.Open Terminal (Applications>Accessories>Terminal) and type in : “sudo apt-get install linux-backports-modules-intrepid-generic” (without the quotes) Hit Return and enter your password, hit Return again 
4.Reboot your machine after the installation is complete from the above (wait a few moments until your master command line is back)
5.Click System>Administration>Update Manager 
6.Do all updates (there may be up to 200+) and reboot after installation of all are completed 
7.Once up and running again open a Terminal and type in: “sudo apt-get install madwifi-tools” (without the quotes) Hit Return and enter your password if asked, hit Return again
8.After installation of the above is complete type in: “sudo gedit /etc/modprobe.d/blacklist” (without the quotes), this will bring up a text file and scroll to the bottom , hit Return to leave a line of space and add these next lines: 

# try to get wireless working on acer one
blacklist ath_pci 

9.Hit Save and close this window
10.In the same Terminal type in: “sudo gedit /etc/rc.local” (without the quotes), hit Return
11.Enter the following text in the document:

 modprobe ath5k (add this directly below the line exit0)
12.Hit Save and close document
13.Reboot computer 
14.Once you are back up again go to your “Hardware Drivers” (System-Administration-Hardware Drivers) and activate “Support for 5xxx series of Atheros” and deactivate “Support for Atheros 802.11 wireless” 
15.Reboot computer
16.Open a Terminal and type in: “sudo gedit /etc/modprobe.d/madwifi” (without quotes), hit Return and uncomment ie; remove # from these lines:

blacklist ath_hal
blacklist ath_pci
17.Click Save and close document
18.In Terminal type in: sudo gedit /etc/modules/ and hit Return
19.At the bottom of the document add "ath5k" (without the quotes) 
20.Hit Save and close document
21.Reboot machine

After this you should now see “Wireless Networks” under the tab Connections at the top of your screen. It may take a few moments to scan available networks, or you can add your own (provided you know your connection information) by clicking “Create New Wireless Network...” and entering the appropriate information.

Good Luck!

---

### Post by willis575 on 2008-12-25
Thanks for the guide! However, I followed the directions exactly and the wireless still doesn't work. The only thing I can think of is that when I got to step 16, /etc/modprobe.d/madwifi was blank. I added blacklist ath_hal and blacklist ath_pci though. Any thoughts?

---

