---
title: "No Network Connection Ubuntu 9.1 on dedicated Gateway laptop"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by Lady_With_A_Knife on 2010-04-05
Am new new new to Ubuntu/Linux and am learning as fast I can, but apparently not fast enough.  
Have a Gateway MX6428 laptop (AMD 64, 1.8 GHz, 512 KB L2 cache) with a Broadcom Co. BCM4318 802.11g wireless network controller.
I just installed Ubuntu 9.1 on this computer with no other OS.  When clicking on the network icon, only "VPN connections", "connect to hedden wireless network", and create new wireless network" is highlighted.  Even after adding the requisite info, it will not acknowledge my desktop router/network, even following the rules for new setup in the "Ubuntu Pocket Guide and Reference" and other forum threads.
Thank you in advance for any assistance provided!

---

### Post by Iowan on 2010-04-05
Laptops always seem to be a challenge - especially in the wireless department. **sudo lshw -C network** may provide more information - probably suggesting driver problem...

---

### Post by Lady_With_A_Knife on 2010-04-05
Did what you said, but would have no idea if it indicated problem with driver.  I did dl ndiswrapper under synaptic manager, but don't know enough about Ubuntu to know if it installed automatically or how to install it myself (?).  Sorry, you're working with a real newbie.

---

### Post by Iowan on 2010-04-05
Post results if possible.
(I'm still a rookie with drivers - especially wireless - but there are a few gurus around who might happen by...)

---

### Post by chili555 on 2010-04-05
Oh, I just happened by and Iowan and I will be happy to help. Together, we are one good guru.

---

### Post by Lady_With_A_Knife on 2010-04-05
Thank you!
Where to begin? Been fighting this for several hrs...
Someone had told me to get ndiswrapper from synaptic manager, so I did.  Then I saw somewhere else that the thing to do was this:
**Step 1.** Install the b43/STA hybrid drivers/firmware from the [restricted repository]("http://www.ubuntu.com/community/ubuntustory/components") using the **Synaptic Package Manager** and search for the bcmwl-kernel-source package and install or in a terminal use the aptitude or apt-get commands: 
~$ sudo apt-get update
~$ sudo apt-get install bcmwl-kernel-source**Step 2.** Under the desktop menu **System > Administration > Hardware Drivers**, the drivers can be activated for use. 
**Note:** A computer restart may be required before using the wifi card.  
So I did.
The only thing it said when I went to "hardware drivers" was there was a proprietory software modem available to activate, so I trepidaciously did so.  
NOW I don't even have as a drop down option in the background of my network manager a wireless network AT ALL. (Before it was there but not highlighted).
So here I sit.  In misery.  Wish I were smarter than this, I hate not knowing my way around a system...

---

### Post by Lady_With_A_Knife on 2010-04-05
Addition to last post:
Here is copy of result of entering lshw -C network:

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:e0:b8:8d:a1:0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 multicast=yes
       resources: irq:18 memory:d0200000-d0203fff ioport:a000(size=256)
  *-network UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:d0304000-d0305fff

---

### Post by chili555 on 2010-04-05
I always approach a lady with a knife with caution; unless she's cooking! If you have an ethernet connection, please follow this post: [http://art.ubuntuforums.org/showpost.php?p=8887474&postcount=8](http://art.ubuntuforums.org/showpost.php?p=8887474&postcount=8)

---

### Post by Lady_With_A_Knife on 2010-04-05
lol, strictly a Florida Cracker who does love to cook and, never without a knife on the hip!  I will check this out, thanks so much...

---

### Post by Lady_With_A_Knife on 2010-04-05
It did not ask me to fetch and install. Instead:
sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
  ndiswrapper-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
?????

---

### Post by chili555 on 2010-04-05
Maybe you already have the needed firmware. Please do:```
ls /lib/firmware/b43
```It will either say, 'no sucha file, cracker' or it will spew forth a listing of firmware files it has. If it has the firmware files, then we wonder why your wireless is still asleep. Please run and post:```
dmesg | grep -e firm -e b43
```

I had to move outa Florida when it was fillin' up with them northerners. Keep that knife handy.

---

### Post by Iowan on 2010-04-05
> **chili555 said:**
> Oh, I just happened by and Iowan and I will be happy to help. Together, we are one good guru.I'll just stand back and watch the magic happen... ;)

---

### Post by Lady_With_A_Knife on 2010-04-05
Yeah, I see you're in SC, my sister moved there and loves it.  I like to visit, but too much family here, and besides, I'm way meaner than any Yankee...!

Anyway, here is the code (I'm back on my desktop, so I'm typing by hand):
[    1.033773] ACPI:  EC:  missing confirmations, swith off interrupt mode.

BTW, "firm" in confirmations is in red.

---

### Post by chili555 on 2010-04-05
So, was the firmware there or not? Please post:```
rfkill list
sudo modprobe b43 ssb
dmesg | grep -e b43 -e ssb
```Thanks.

---

### Post by Lady_With_A_Knife on 2010-04-05
There was a huge long list of firmware and when I did the code you asked got this:

[ 2399.978760] b43-pci-bridge 0000:05:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  2400.036114]  ssb:  Sonics Silicon Backplane found on PCI device 0000:05:02.0

I entered the codes separately, one after the other to get this response.

---

### Post by chili555 on 2010-04-05
It recognizes and attaches to your card:> [ 2399.978760] b43-pci-bridge 0000:05:02.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 2400.036114] ssb: Sonics Silicon Backplane found on PCI device 0000:[COLOR="Red"]05:02[/COLOR].0> product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 2
bus info: pci@0000:[COLOR="Red"]05:02[/COLOR].0Did it create a wireless interface?```
iwconfig
```Are there any errors that the kernel has to report?```
dmesg | grep -i error
dmesg | grep wlan
```Thanks.

---

### Post by Lady_With_A_Knife on 2010-04-05
Did it create a wireless interface?```
iwconfig
Response it gave:
lo       no wireless extensions.
etho   no wireless extensions.


```Are there any errors that the kernel has to report?
```
dmesg | grep -i error
dmesg | grep wlan
```
Response it gave to both:  nothing!

Aren't you tired yet??!  I may have to give up the good fight til tomorrow...But I do so appreciate all ya'lls help!

---

### Post by chili555 on 2010-04-05
Yes, I am tired. Shout atcha tomorrow.

---

### Post by Lady_With_A_Knife on 2010-04-06
Where is my knight in shining armor?  Where is Chili555?

---

### Post by chili555 on 2010-04-06
Did you get no response at all with:```
rfkill list
```Would you please do:```
dmesg > dmesg.txt
zip dmesg.zip dmesg.txt
```Transfer the dmesg.zip file on a USB key or similar and attach it to your reply.

---

### Post by Lady_With_A_Knife on 2010-04-06
[QUOTE]No response with the rfkill list...
and the the response after typing the other 2 codes:
The first nothing, the second:
adding:  dmesg.txt (deflated 71%)

---

### Post by chili555 on 2010-04-06
Wow! In your attached dmesg, there is no sign of the Broadcom at all...*at all!* Please do:```
sudo su
echo b43 >> /etc/modules
echo ssb >> /etc/modules
exit
```Reboot and do:```
dmesg | grep -e b43 -e ssb
lspci -nn | grep Network
```Post the result.

---

### Post by Lady_With_A_Knife on 2010-04-06
Okay, problem.  After first code, I *thought* I copied info but didn't.  Then I re-booted, and the following is the result, as well as a window popping up saying "authentication required by wireless network".  So something happened!

---

### Post by oleink on 2010-04-06
Make sure your driver is actually still turned on in "Hardware Drivers" you never said it was after your restart.  I had to turn mine back on after restart.  STA Driver.  After that it worked perfectly also in Synaptic it may be helpful to download wine.  For some reason my NIC didn't operate as well without wine working with my driver.

---

### Post by oleink on 2010-04-06
After reading your last post.  If that is the case you need to authenticate your access to the network

---

### Post by Lady_With_A_Knife on 2010-04-06
SUCCESS!!!!
This thread is now closed, because of the amazing-ness of Chili555.  I am now up and running, buzzing around the net and in general making a nuisance of myself (as usual) because he patiently helped me through the wireless issues I was having.

[SIZE=7]Thank you!![/SIZE]

---

