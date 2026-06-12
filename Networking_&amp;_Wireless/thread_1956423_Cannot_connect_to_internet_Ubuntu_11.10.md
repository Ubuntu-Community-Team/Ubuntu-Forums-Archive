---
title: "Cannot connect to internet Ubuntu 11.10"
date: 2012-04-10
forum: Networking &amp; Wireless
---

### Post by emerson1234567890 on 2012-04-10
OK, I mentioned a long time ago that Ubuntu installations kept failing on my computer.  Now It didn't.

After I installed Ubuntu 11.10, the computer freezes after I turned on the computer.  So I forced-quit my computer by pressing the power button for 8 seconds.

Then I turned on my computer again.  This time Ubuntu didn't freeze, but I can't connect to the internet!

First I clicked the network-applet and chose my home wireless network.  I typed the RIGHT password and it kept asking for the password.

Then I typed ```
sudo lshw -C network
``` into the terminal.  Ubuntu recognized the wireless adapter and the driver is there.  I tried connecting again but it didn't work.

Next, I turne the wireless adapter off and on using the terminal.  I tried again and it didn't work either.

What's the problem here???  I desperately need to use the internet because I can't install any software and drivers.

Any help will be appreciated.

Specs: ASUS F81Se, Windows 7 Dual-boot, Card: Atheros AR928X, 4GB RAM

---

### Post by roelforg on 2012-04-11
Run this:
```

sudo lshw -C network
sudo lspci
sudo ifconfig -a
sudo cat /etc/network/interfaces

```
Post the output.
 
I suspect your /etc/network/interfaces reads this:
```

auto lo
iface lo inet loopback

```
Append this to the file and reboot:
```

auto eth0
iface eth0 inet dhcp

```
That should work for wired nics (i assume you don't use wireless).

---

### Post by Bucky Ball on 2012-04-11
Have you plugged in a cable and gotten updates if you are using wireless? You might try looking in Additional Drivers ...
What is the card?

---

### Post by roelforg on 2012-04-11
> **Bucky Ball said:**
> Have you plugged in a cable and gotten updates if you are using wireless? You might try looking in Additional Drivers ...
What is the card?

Most of the time the problem is a missing entry in /etc/network/interfaces
Had 2cases yesterday.

Edit: oops... didn't see the wireless part.
Still, it's usually a missing entry in /etc/network/interfaces

---

### Post by emerson1234567890 on 2012-04-11
I don't have a Wired connection... :(

Reinstalled Ubuntu today.  Same thing happens again (Installation complete, first bootup, freezes, reboot, login, didn't freeze, no internet)

My card is an Atheros AR928X.


I can't really post the actual outputs in the terminal because I am typing this from another computer that has a working internet connection.  So I'll just post the summary.

sudo lshw-C network :  It shows the product name (Atheros AR928X) and description, and it shows the driver.  The logical name is wlan0.

The output of sudo lspci:  From 00:00.0 to 00:0f.0 it all says "Silicon Integrated Systems".  01:00.0 Audio devices says "ATI Technologies Inc RV710/730".  02:00.0 Network controller shows my wireless card and some extra details about it.

sudo ifconfig -a: The output splits up into 3 parts: eth0, lo, and wlan0.  But I will just post wlan0 since I am using wireless.  Both RX and TX packets show 0 in errors, drops, overruns, frame, and carrier.  And there are many packets.(I don't know what that really means, but I just posted it.)

sudo cat /etc/network/interfaces:  How did you know that?  It really shows auto lo iface lo inet loopback!

And I forgot to mention this:  After I entered the right password, the computer tries to connect, then it kept asking the password over and over.

And Internet worked while I was installing ubuntu.  It also worked when I was using wubi a long time ago.

Help!  And thanks for helping!

---

### Post by Bucky Ball on 2012-04-12
Do you need to enter a DNS address (or two) when right clicking on 'Network' icon and 'Edit Connections'?

If you can get online, even if you need to take the machine elsewhere, Madwifi is what you need over the default Network Manager. It is all about Atheros ...

[http://madwifi-project.org/](http://madwifi-project.org/)

---

### Post by roelforg on 2012-04-12
> **emerson1234567890 said:**
> I don't have a Wired connection... :(
 
Reinstalled Ubuntu today. Same thing happens again (Installation complete, first bootup, freezes, reboot, login, didn't freeze, no internet)
 
My card is an Atheros AR928X.
 
 
I can't really post the actual outputs in the terminal because I am typing this from another computer that has a working internet connection. So I'll just post the summary.
 
sudo lshw-C network : It shows the product name (Atheros AR928X) and description, and it shows the driver. The logical name is wlan0.
 
The output of sudo lspci: From 00:00.0 to 00:0f.0 it all says "Silicon Integrated Systems". 01:00.0 Audio devices says "ATI Technologies Inc RV710/730". 02:00.0 Network controller shows my wireless card and some extra details about it.
 
sudo ifconfig -a: The output splits up into 3 parts: eth0, lo, and wlan0. But I will just post wlan0 since I am using wireless. Both RX and TX packets show 0 in errors, drops, overruns, frame, and carrier. And there are many packets.(I don't know what that really means, but I just posted it.)
 
sudo cat /etc/network/interfaces: How did you know that? It really shows auto lo iface lo inet loopback!
 
And I forgot to mention this: After I entered the right password, the computer tries to connect, then it kept asking the password over and over.
 
And Internet worked while I was installing ubuntu. It also worked when I was using wubi a long time ago.
 
Help! And thanks for helping!
 
I knew cause network manager sometimes messes up and only leaves the lo part in /etc/network/interfaces (you're the 1000'th or something like that).
 
Let me explain what /etc/network/interfaces is (simplified):
the programs ifup and ifdown control what network interface is on (up) or off (down)
They use /etc/network/interfaces to get info about what interfaces to launch, which to configure how.
Those 2 programs are irreplacable for networking.
When you boot a script runs that will run ifup and tells it to up'em all.
ifup up's every interface in /etc/network/interfaces
Network-manager works by overwriting /etc/network/interfaces and running a script that first calls ifdown (turning them off) and then ifup
Only sometimes network manager screws up and erases all except lo in /etc/network/interfaces.
When that happens, you manually edit the file, add the interface and run 
```

sudo /etc/init.d/networking restart

```
 
Anyways...
Read this:
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo#Adding_it_to_.2BAC8-etc.2BAC8-network.2BAC8-interfaces](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo#Adding_it_to_.2BAC8-etc.2BAC8-network.2BAC8-interfaces)
It'll tell you how to add your wifi to /etc/network/interfaces

---

### Post by emerson1234567890 on 2012-04-14
> **roelforg said:**
> 
Anyways...
Read this:
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo#Adding_it_to_.2BAC8-etc.2BAC8-network.2BAC8-interfaces](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo#Adding_it_to_.2BAC8-etc.2BAC8-network.2BAC8-interfaces)
It'll tell you how to add your wifi to /etc/network/interfaces

Thanks!  So do I have to replace MYNETWORK into my network ESSID and FEFEFEFEFE into my internet password to make the internet connection work?

auto wlan0
iface wlan0 inet dhcp
wireless-essid   MYNETWOTK
wireless-key     FEFEFEFEFE
wireless-channel 11
wireless-mode    managed

And how to install madwifi?  I copied the whole tar.gz file to a USB from this laptop that has internet and copied the file from the usb from th eUbuntu Laptop.  But how can I install it?

I really wanted my internet connection because I am SICK of changing the boot options to nolapic everytime I boot.  I really need to install the drivers.   Help!!

---

### Post by roelforg on 2012-04-15
> **emerson1234567890 said:**
> Thanks!  So do I have to replace MYNETWORK into my network ESSID and FEFEFEFEFE into my internet password to make the internet connection work?

auto wlan0
iface wlan0 inet dhcp
wireless-essid   MYNETWOTK
wireless-key     FEFEFEFEFE
wireless-channel 11
wireless-mode    managed

And how to install madwifi?  I copied the whole tar.gz file to a USB from this laptop that has internet and copied the file from the usb from th eUbuntu Laptop.  But how can I install it?

I really wanted my internet connection because I am SICK of changing the boot options to nolapic everytime I boot.  I really need to install the drivers.   Help!!
FEFEFE... needs to be replaced with hex,
[http://www.dolcevie.com/js/converter.html](http://www.dolcevie.com/js/converter.html)
just enter the pass, press ascii to hex
replace the fefefe... with the result and remove the : from it.

---

### Post by Bucky Ball on 2012-04-15
How to install madwifi: Plug in an ethernet cable and install madwifi. Don't bother if you aren't running an Atheros wireless card ...

---

### Post by emerson1234567890 on 2012-04-15
Wow.....  Still didn't work!
 
Should I just keep trying or do a clean install after 11 days (12.04) ?

Thanks for you 2 guys help!

---

