---
title: "USB Bridge cable - network adapter how to ?"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by goxi on 2009-05-21
I have USB to USB bridge cable attached to my pc with ubuntu 9.04 and another with WinXP pro. How can I configure to connect them. I have only win driver for USB to USB bridge cable ?

---

### Post by goxi on 2009-06-23
Really, nobody knows something about how to use USB bridge cabel to connect two PC under LINUX (Ubuntu). I have found something here : [http://www.linux-usb.org/usbnet/](http://www.linux-usb.org/usbnet/) and I`ll try to fix this. I`ll post results here.
I believe somebody uses USB bridge cabel and Linux together....

---

### Post by goxi on 2009-06-23
This is my device: [PL-2501 Hi-Speed USB Host to Host Bridge Controller]("http://www.prolific.com.tw/eng/Products.asp?ID=18") The PL-2501 is a single chip Hi-Speed USB Host-to-Host Bridge Controller. With PL-2501 embedded cable, users can quickly transfer large amount and large size of files directly from one PC to another. ** ...**

---

### Post by goxi on 2009-06-23
> **goxi said:**
> This is my device: [PL-2501 Hi-Speed USB Host to Host Bridge Controller]("http://www.prolific.com.tw/eng/Products.asp?ID=18") The PL-2501 is a single chip Hi-Speed USB Host-to-Host Bridge Controller. With PL-2501 embedded cable, users can quickly transfer large amount and large size of files directly from one PC to another. ** ...**
And these are details:
PL-2501 		                     		                      		                    	Hi-Speed USB Host to Host Bridge Controller 		                     		                      		                      	
		                     								                    		                     		                     		                      	[IMG]http://www.prolific.com.tw/eng/images/barove.gif[/IMG] 		                     		                      		                      	
		                     		                      		                      	The PL-2501 is a single chip Hi-Speed USB Host-to-Host Bridge Controller. With PL-2501 embedded cable, users can quickly transfer large amount and large size of files directly from one PC to another. Also it’s useful for computer data backup/restore, synchronization or file sharing. Additionally, the chip enables two or more Hi-Speed USB or USB1.1 equipped PCs to connect to each other using USB ports as a network. Since Hi-Speed USB extends the speed up to 480 Mbps – 40 times more than previous USB, the network constructed by PL-2501 has data rates almost 5 times faster than a conventional 100BT Ethernet network. Implemented with remote NDIS, users can easily build up this network at a turbo speed without the troubled installation of drivers and add-on network interface cards. 		                     						 		                      		                      	
		                     		                      		                      	[IMG]http://www.prolific.com.tw/eng/images/barfea.gif[/IMG] 		                     		                      		                      	
		                     		                      		                      	
[LIST]
[*]Full compliance with the USB Specification v2.0
[*]On-chip USB2.0 Phy
[*]Support both Peer to Peer and Network functions
[*]Transfer data and share resources between two or more PCs with speed up to 480Mbps.
[*]Remote NDIS specification compliant (For network function only)
[*]Embedded Turbo 8032 micro-controller
[*]Supports USB Full/High Speed Control/Interrupt/Bulk Endpoints Transfer
[*]On-Chip 3.3V-2.5V regulator for internal circuit
[*]Dual data buffer supporting two-way data transfer
[*]Supports Suspend, Resume and Remote wake-up power management features
[*]Supports external serial EEPROM to customize vender/product related information
[*]Supports LED indicator for connection and transfer status
[*]Support external customized program ROM via 100-pin LQFP package
[*]Bus powered from either USB port
[*]No glue logic needed – can be embedded in small spaces
[*]64/100 Pins LQFP packages
[/LIST]
  		                     		                      		                    	  		                        	 		                      	 		                     		                      		                      	 		                      	[IMG]http://www.prolific.com.tw/eng/product-images/2501.jpg[/IMG]

---

### Post by goxi on 2009-06-23
HERE I`V FOUND WHAT I NEED [http://www.linuxfoundation.org/en/Net:Bridge ]("http://www.linuxfoundation.org/en/Net:Bridge")BUT STILL CAN`T BRIDGE MY PCs. SOMBODY HAVE SOLUTION ? :confused:

---

### Post by ricojonah on 2009-10-18
I just stumbled across this idea myself recently. A USB bridge cable would me the perfect solution for my small, first-time linux cluster project.

Unfortunately, I've been searching around quite a lot and haven't found much more beyond one possibility, but this might be what you're looking for:[http://www.linux-usb.org/usbnet/]("http://www.linux-usb.org/usbnet/"). (Search for "modprobe usbnet" in the page, and read that section.) It's probably a long shot, but from what I understood, it might be as simple as including a kernel module, then finding & assigning an IP address to the new USB interface: 

1) Adding the required kernel module:
```
sudo modprobe usbnet
```

2) use ```
ifconfig | grep usb
``` to see if there is a new interface called usb0 (or some other usb#).

3) Assign your ip address configuration however you prefer (using ifconfig or the network manager).

The page I linked to above also has a list of different USB bridge cables that are definitely supported.

I don't have a USB bridge cable yet, but I've been VERY tempted to get one. *Please* post back and let me know if this works for you. If it does, I'm ordering several of those cables, stat!

---

### Post by nzo on 2009-10-19
Coincidentally, I decided to try this very same thing this morning. I discovered this thread and had high hopes. No luck. Device still not recognised after modprobe. Link does specify that PL2301/2302 are supported. It may just not support PL2501.

---

### Post by ricojonah on 2009-10-27
Oh, FYI for anyone considering this idea (connecting to systems via USB): Do _not_ try to do this with a regular USB-A to USB-A cable. The type of cables mentioned on this thread are known as 'USB link cables' or 'USB network cables'.

Using a standard USB cable could potentially damage your USB ports, if not your motherboard or power supply as well.

I just wanted to mention this because I almost did the same dumb thing myself before I decided to do a little research first.

From the USB FAQ on USB.org:

"You mean I can't make a direct cable connection like a null modem?"

"Correct. In fact, if you try this with an illegal A to A USB cable, you'll short the two PCs' power supplies together, possibly destroying one or both machines or causing a fire hazard. Even there were no danger to the machines from the problem with two power supplies, there still wouldn't be any way to get the two PCs talking to each other, since USB doesn't support that particular kind of communication. A reasonably priced solution to handle this need is the USB bridge."

Most notably, the cable you would has a component in between the two connectors. Here is an example: [http://www.engadget.com/2009/10/08/belkins-refreshed-easy-transfer-cable-makes-windows-7-migration/]("http://www.engadget.com/2009/10/08/belkins-refreshed-easy-transfer-cable-makes-windows-7-migration/")

Just a heads up!

---

### Post by 2hot6ft2 on 2010-01-30
Here's one that got it working on Intrepid 8.10
[Using USB-USB bridge cable on Ubuntu]("http://ubuntuforums.org/showthread.php?t=993036")
As for Ubuntu to WinXP pro I don't know but the newer driver for xp can be found here: [Prolifics website]("http://www.prolific.com.tw/eng/Download-2.asp?ID=17") if it's the PC-Linq.

Once the drivers are installed a FTP program should be able to do the transfers if the windows and ubuntu systems will talk over it.

I have one buried in my stuff somewhere and if I come across it I'll try getting it to work Ubuntu 9.10 to Ubuntu 9.10.

---

### Post by kkfok1 on 2010-09-07
HI,

I am looking for a usb-to-usb cable to transfer data between Ubuntu 10.04 and MacBook pro OSX 10.6.3.
 
There is one on startech.com which can only support PC-Mac, not Ubuntu :(
Can anyone please help ?

Thanks

---

