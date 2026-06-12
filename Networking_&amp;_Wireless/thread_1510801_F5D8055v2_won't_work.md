---
title: "F5D8055v2 won't work"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by brendon423 on 2010-06-16
I've used the ndiswrapper to install the driver of my wireless adapter and it says the driver is installed, but when I go to connect to a wireless network there's nothing there. Any help at all would be much appreciated

---

### Post by b k on 2010-06-16
> **brendon423 said:**
> I've used the ndiswrapper to install the driver of my wireless adapter and it says the driver is installed, but when I go to connect to a wireless network there's nothing there. Any help at all would be much appreciated
 
Hi there, I believe that you do not need the ndiswrapper to get your wireless adapter to work.
 
I am assuming that you have a reasonably fresh install of Ubuntu 10.04 LTS
 
Go to System > *Application > Synaptic Package Manager*
 
and mark the following packages f**or removal** (you need to first mark for removal and then click apply):
 
[COLOR=red]ndisgtk[COLOR=black] ;[/COLOR] ndiswrapper-utils-1.9 [COLOR=black];[/COLOR] ndiswrapper-common[/COLOR]
 
 
We will use the native rt2870 driver (within Ubuntu 10.04 LTS)
 
It is strongly recommended that you copy the code that needs to be executed (from a Terminal window) below to a .txt file to your Ubuntu machine via a usb dongle to miminise human typo errors.
Open this .txt file and copy and paste the code into the Terminal window of the Ubuntu machine (with the wireless adapter problem).
 
Go to : *Applications, Accessories, Terminal*
 
```
lsusb
```Check the output to make sure that your device ID is:
 
[COLOR=red]050d:825b[/COLOR]
 
**_If it matches_**, do this:
 
```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```
 
Put in/add [COLOR=red]one[/COLOR] long line [COLOR=black]in the opened file[/COLOR]
 
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="825b", RUN+="/sbin/modprobe -qba rt2870sta"
```
 
Proofread carefully (ensuring that the opened file will be saved in the /etc/udev/rules.d directory), [COLOR=red]save[/COLOR] and close gedit.
 
Next do this:
 
```
sudo gedit /etc/modprobe.d/network_drivers.conf
```
 
Put in/add [COLOR=red]one[/COLOR] long line [COLOR=black]in the opened file[/COLOR]
 
```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "050d 825b
" > /sys/bus/usb/drivers/rt2870/new_id

```
 
Proofread carefully (ensuring that the opened file will be saved in the /etc/modprobe.d directory), [COLOR=red]save[/COLOR] and close gedit
 
Reboot
 
Good luck and let us know if it works.
 
The above procedure can be 'undone' if necessary by executing the codes again and removing the code lines that were previously added into the two files.
 
PS: most of the above info is modified from this link posts #32 and #58 [http://ubuntuforums.org/showthread.php?t=1419504&page=6](http://ubuntuforums.org/showthread.php?t=1419504&page=6)
 
Also see post #2 of this link (although it is for a different Belkin model) [http://ubuntuforums.org/showthread.php?t=1509403](http://ubuntuforums.org/showthread.php?t=1509403)

---

### Post by brendon423 on 2010-06-16
I did all that you said, proofread my directories and everything but still no connections showing up. I'll look through the links you posted and see if I can find anything

---

### Post by b k on 2010-06-16
> **brendon423 said:**
> I did all that you said, proofread my directories and everything but still no connections showing up. I'll look through the links you posted and see if I can find anything
 
See section 5 of this link for some help in uninstalling ndiswrapper [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Hi, perhaps post the output of the following commands:
 
```
 
lsmod

``````
 
lshw -C network

```I assume that you did remove ndiswrapper before executing the other commands.
 
You did use copy and paste technique for those commands to prevent typo errors I hope.
 
Thanks

---

### Post by jazmin on 2010-07-04
Hi there,

I have searched around through the forums quite a bit regarding this issue and this thread seems most relevant to my situation, the material being most fresh.

Post #2 in reply to the OPs problem states that with a recent install of 10.04 that the "native rt2870sta" driver can be made to work with the Belkin Wireless N+ USB adaptor (F5D8055V2).

I did the steps as mentioned (the lsusb) to confirm my vendor and device IDs and everything is fine.  Also, this is a brand new installation of 10.04 and my hardware is without any doubt the F5D8055V2 (VendorID: 050d, ProductID: 825b)

So I carried out the steps exactly as described in post #2.  After rebooting the box, the blue LED flickers on and then goes steady.  The ifconfig -a shows the device at interface wlan0.  An lsmod shows the rt2870sta driver is loaded and in use.  

The problem is trying to configure the WiFi connection.  The wireless network is seen and its SSID is listed with a lock icon (WPA2 configured on the Belkin Wireless N+ router).  When I add a new wireless network configuration, I am unable to connect to the network.  I have tried multiple methods of making the connection, static IP, gateway, subnet mask assignment, DHCP, etc, etc, but I am having no luck.  I have double and triple checked all of my connection params including the WPA PSK but nothing, I cannot connect.  dmesg and /var/log/messages shows nothing useful.  I have even tried manually adding routing table entries and confirmed them with netstat.  Am I missing something here?  Has anyone else had any problems with this?  I am able to connect to this network on another system (Mac OS X), so it is a working network configuration.

Also, the poster (post #2) references some older posts which use a method that uses the driver from ralink.  This is a bit odd as this completely changes the game, so I am not clear why these are referenced.  Some others seemed to have success with this linked method however when I took a look at the 3070 driver code from ralink, there are no USB_DEVICE entries in the source file as is claimed in the procedure (this might be due to the fact that the driver on the ralink site is 3 months newer than the posted procedure and the source might have undergone a redesign).

Perhaps there is a manual way I can try and enter my wireless LAN settings? 

Thanks for any input!

jazminder

[COLOR=Navy]**Edit** - **Problem Resolution**[/COLOR]

Post #2 was correct except the rt2870sta driver is the incorrect driver for this chip.  It does provide some wifi functionality, name the ability to see the SSID broadcast, however I was unable to join except for one time where I was knocked back into adhoc mode with a link-local configured IP address.

The proper driver is the rt3070sta so the above method initially posted in post #2 is sound, just make some swaps as follows:

In */etc/udev/rules.d/network_drivers.rules*

```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="825b", RUN+="/sbin/modprobe -qba rt3070sta"
```And finally in */etc/modprobe.d/network_drivers.conf*

```
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "050d 825b" > /sys/bus/usb/drivers/rt2870/new_id
```A reboot should bring you back up with the proper driver loaded (confirm with an lsmod) and there should be no problems with accessing your network now.

J

---

