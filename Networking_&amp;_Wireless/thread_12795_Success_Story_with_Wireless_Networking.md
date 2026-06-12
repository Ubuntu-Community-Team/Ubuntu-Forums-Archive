---
title: "Success Story with Wireless Networking"
date: 2005-01-26
forum: Networking &amp; Wireless
---

### Post by ahood on 2005-01-26
I am writing about my experience with wireless networking and how I got it working with Ubuntu Warty 4.10. 

I have tried to do wireless networking during the past year. I previously got a US Robotics PCI adapter (model USR5416) to work with a different linux distribution and the driverloader wrapper (linuxant). 

I switched to Ubuntu and found out that the driverloader would not install. For some reason I am unable to download and install the kernel headers. In case you are wondering, I enabled all the repositories and it still didn't work. I eventually gave up and searched the Ubuntu forum for the most likely PCI wireless adapter that will work "out of the box". I selected the D-Link DWL-G520 (Hardware version B2; Firmware version 3.1.6). I made sure that the box that the D-link adapter came in specified the "atheros" chipset (front display panel).

So, I powered down the machine, opened it up, replaced the PCI USR5416 with the DWL-G520. I then rebooted the machine and logged into Ubuntu. I then clicked on 'Computer | System Configuration | Networking in the Gnome task bar at the top of the screen. I was pleased to see that Ubuntu had automatically detected the D-link adapter because a new device was listed in the Connections tab, the type is  "Wireless LAN Card" and the device name is 'ath0'. 

My next step was to enter the DNS settings in the DNS tab. This might seem peculiar but I wanted to be sure this was going to work, plus I figured that this wasn't going to hurt anything. I entered both the primary and secondary DNS IP addresses. I got these DNS IP addresses from the homelan router (see your router documentation on how to access its configuration panel).

I then went back to the Connections tab and highlighted the 'Wireless LAN Card' and clicked on the 'Properties' button. I entered the ESSID name of the wireless network (Wireless Settings) and selected 'Automatic DHCP' (Connection Settings), the WEP was left blank. I clicked the 'Ok' button.

With the 'Wireless LAN Card' still highlighted, I clicked on the 'Activate' button and the cursor changed into an animated circle. I left it be and the animated circle appeared for quite a bit of time (about two, maybe three minutes). Strangely, the checkbox next to the 'Wireless LAN Card' becomes unchecked while the animated circle is visible. Eventually, the white circle went away, and when it did, the entire Network Settings dialog box also disappeared; however, I found myself connected to the net wirelessly.

I have been using the wireless device for the past two weeks and it has been up nearly 100%. A few days ago, I did lose wireless connectivity and I could not bring it back up by activating the wireless device through the Network Settings dialog window. I tried several times. I resorted to turning off and on the wireless access point device on the network. After I did that, I was then able to activate the wireless device again. 

Tip: I found that adding the 'Wireless Link Monitor' applet to the task bar to be beneficial in detecting whether Ubuntu has recognized the device and can communicate with the outside world. I think it is still necessary to activate the wireless device in order to surf the net. I also find the network monitoring utilities in gdesklets to be quite handy as well.

---

