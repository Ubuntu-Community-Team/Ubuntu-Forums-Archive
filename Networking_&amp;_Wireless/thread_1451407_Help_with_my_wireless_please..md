---
title: "Help with my wireless please."
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by cubanito52 on 2010-04-10
[FONT=Arial][SIZE=3]Hi to everyone, i am using dual boot i have Windows 7 and Ubuntu 9.10 , everything works fine except i can't[/SIZE][/FONT][FONT=Arial][SIZE=3] connect to the internet in Ubuntu. i am using a wireless USB adapter on my desktop.  is a NETGEAR WN111 USB WIRELESS ADAPTER. Can  anyone please tell me step by step how to successfully install the driver or get it to work for Ubuntu :confused:   Thank you in advance, if any other information about my pc is needed please ask me.

Once again Thanks ill be waiting[/SIZE][/FONT]. :KS

---

### Post by chili555 on 2010-04-10
There are three versions of this device. Please open a terminal and do:```
lsusb
```Post the result and we will learn which device you have.

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

---

### Post by cubanito52 on 2010-04-10
thanks for the reply. Is just the **WN111**  (not the v2 with Atheros arg9170) so i would need the ndiswrapper ? how can i get and install this ?

---

### Post by chili555 on 2010-04-10
How do you know this without consulting *lsusb*? Wouldn't you like to confirm before we install ndiswrapper and possibly find out we don't need it and it doesn't work?

You can omit the parts that deal with 'root hub' and your mouse and anything that is clearly not your wireless device.

---

### Post by cubanito52 on 2010-04-10
sorry about that.. this is what i get. 



administrator@ubuntu:~$ *lsusb*
Bus 001 Device 007: ID 0951:1603 Kingston Technology Data Traveler 1GB/2GB Pen Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 413c:3016 Dell Computer Corp. Optical 5-Button Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by chili555 on 2010-04-10
I don't see a Netgear wireless adapter here. Was it inserted at the time?

---

### Post by cubanito52 on 2010-04-10
Yes, it was inserted. That's why i said that i think it is the WN111. because it doesn't show in the *lsusb *command. is there anything i can do ? like try all the setups? any suggestions?

---

### Post by chili555 on 2010-04-10
Remove it from the slot and open a terminal and do:```
sudo tail -f /var/log/messages
```Leave the terminal open and insert the device. Look for any indication from the kernel that it recognizes the device. Try all of your USB slots. If there is any indication, write down all the details or copy it to your pen drive and post it here. We are especially interested in the usb.id, something like 123a:456b or 0x123a 0x456b.

---

### Post by cubanito52 on 2010-04-10
ok i did what you told me, by any luck is this what we are looking for ? [B]"Bus 001 device 003: ID 0486:9000 Netgear inc
WN111(v1) RangeMax Next Wireless"[/B]  i disconnected the USB and connected it onto other usb ports i don't know if that helped. after i did that i did the *lsusb* in terminal. 

administrator@ubuntu:~$ sudo tail -f /var/log/messages
[sudo] password for administrator: 
Apr 10 18:28:12 ubuntu kernel: [   17.453531] type=1505 audit(1270938492.038:14): operation="profile_replace" pid=852 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Apr 10 18:28:12 ubuntu kernel: [   17.453668] type=1505 audit(1270938492.038:15): operation="profile_replace" pid=852 name=/usr/lib/connman/scripts/dhclient-script
Apr 10 18:28:12 ubuntu kernel: [   17.458005] type=1505 audit(1270938492.042:16): operation="profile_replace" pid=853 name=/usr/bin/evince
Apr 10 18:28:12 ubuntu kernel: [   17.462070] type=1505 audit(1270938492.046:17): operation="profile_replace" pid=853 name=/usr/bin/evince-previewer
Apr 10 18:28:12 ubuntu kernel: [   17.464369] type=1505 audit(1270938492.050:18): operation="profile_replace" pid=853 name=/usr/bin/evince-thumbnailer
Apr 10 18:28:12 ubuntu kernel: [   17.470472] type=1505 audit(1270938492.054:19): operation="profile_replace" pid=857 name=/usr/lib/cups/backend/cups-pdf
Apr 10 18:28:12 ubuntu kernel: [   17.470772] type=1505 audit(1270938492.054:20): operation="profile_replace" pid=857 name=/usr/sbin/cupsd
Apr 10 18:28:12 ubuntu kernel: [   17.472581] type=1505 audit(1270938492.058:21): operation="profile_replace" pid=858 name=/usr/sbin/tcpdump
Apr 10 18:28:12 ubuntu kernel: [   18.050144] ppdev: user-space parallel port driver
Apr 10 18:29:14 ubuntu kernel: [   79.500016] Clocksource tsc unstable (delta = -275631385 ns)
Apr 10 18:29:36 ubuntu kernel: [  101.412028] usb 1-4: new high speed USB device using ehci_hcd and address 5
Apr 10 18:29:36 ubuntu kernel: [  101.549107] usb 1-4: configuration #1 chosen from 1 choice
Apr 10 18:30:36 ubuntu kernel: [  161.853321] usb 1-4: USB disconnect, address 5
Apr 10 18:30:44 ubuntu kernel: [  169.484027] usb 1-5: new high speed USB device using ehci_hcd and address 6
Apr 10 18:30:44 ubuntu kernel: [  169.620968] usb 1-5: configuration #1 chosen from 1 choice

---

### Post by chili555 on 2010-04-10
> [COLOR="Red"]0486:9000[/COLOR] Netgear inc WN111(v1)Yes, indeed!

Post #8 here describes the process:  [http://www.uluga.ubuntuforums.org/showthread.php?p=5470466#post5470466](http://www.uluga.ubuntuforums.org/showthread.php?p=5470466#post5470466)

First, let's install ndiswrapper. It's on your Ubuntu install CD. Drop the CD in the tray and open System > Administration > Synaptic and open Settings > Repostitories and select Other Software. Make sure the CD is selected. Then press Reload and let Synaptic index all the software on the CD. Search for ndiswrapper and install ndiswrapper-common and ndiswrapper-utils-1.9.

Next, download the file referred to in the post, netmw245.tar.gz. Drag and drop it from your pen drive to your desktop. Right click it and select Extract Here. A folder will be created called 'netmw245.'

Now follow the instructions in the post, except start with this command:```
cd Desktop/netmw245
```Post back and report your success.

---

### Post by cubanito52 on 2010-04-12
Sorry, i didn't provide you with enough information.. but i did not use an installation CD i downloaded the  ubuntu-9.10-desktop-i386 which is an .ISO , i used Daemon Tools Lite to mount the image and installed Ubuntu this way.

---

### Post by chili555 on 2010-04-12
It seems that we have three options. First you could burn the .iso image to CD and use it to get the packages as I described above.

Second, you could get the packages from Ubuntu package search on a USB key and transfer them to your Ubuntu computer.

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.54-2ubuntu1_all.deb)

[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb)

Third, if I scratched my white beard long enough, I think we might be able to mount your .iso and get the packages.

By far, I think the USB key option is the easiest.

---

### Post by cubanito52 on 2010-04-12
**SUCCESS  **:KS I'm connected to my wireless network,  Thank you very much for you're help Chili555.

---

### Post by chili555 on 2010-04-13
Great work! I am glad it's working.

---

