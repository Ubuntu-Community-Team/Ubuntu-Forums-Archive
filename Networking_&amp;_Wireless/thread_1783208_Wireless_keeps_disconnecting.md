---
title: "Wireless keeps disconnecting"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by FinalLight on 2011-06-15
Hello forum users! I have been using ubuntu now for quite a while with no issues. Until now. Last night, I ran the new update for ubuntu and now I can't seem to connect to my wireless network properly. As soon as I log in, and imput my password to the key ring, it will automatically just disconnect me no matter the network. I'm running a dell duo, 32-bit Ubuntu 11.04 in a Gnome 3 shell. Oh, and I tried booting into my old ubuntu (Non Gnome 3) and that didn't work. Godspeed please!

---

### Post by notcosi on 2011-06-15
I have been having the same problem for weeks - not found a solution yet though - sorry

---

### Post by FinalLight on 2011-06-15
I think I saw someone work around it by logging into root. I tried and failed. But I think theres some work around.

---

### Post by smurphy_it on 2011-06-15
As in doing a "distribution update" ?
I've seen posts around that can point to the wireless drivers going a little sideways.

May have to re-install your wifi drivers to get it to work.  In the past when I've had issues it's usually one of two things:

(1) Wireless Drivers
(2) Network manager

So I'd probably start with the wireless drivers, and then move on to install wicd (and using that instead of Network Manager).

---

### Post by rcktsingh on 2011-06-15
Hi guys,

I was facing the same problem since the past couple of days. and then I did the following. Seems to be working fine with me until now.

```

sudo gedit /etc/NetworkManager/nm-system-settings.conf
Changed the file to:
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

[ifdown]
managed=true

[ifup]
managed=true

```

Source: [http://edtake.wordpress.com/2010/05/10/ubuntu-lucid-lynx-wireless-keep-dropping/]("http://edtake.wordpress.com/2010/05/10/ubuntu-lucid-lynx-wireless-keep-dropping/")

Good luck!

---

### Post by FinalLight on 2011-06-15
> **smurphy_it said:**
> As in doing a "distribution update" ?
I've seen posts around that can point to the wireless drivers going a little sideways.

May have to re-install your wifi drivers to get it to work.  In the past when I've had issues it's usually one of two things:

(1) Wireless Drivers
(2) Network manager

So I'd probably start with the wireless drivers, and then move on to install wicd (and using that instead of Network Manager).

alright, I can't connect to the internet in the first place, so I can't install wcid. I can't reinstall the wireless drivers I can't connect to the internet.

---

### Post by FinalLight on 2011-06-15
> **rcktsingh said:**
> Hi guys,

I was facing the same problem since the past couple of days. and then I did the following. Seems to be working fine with me until now.

```

sudo gedit /etc/NetworkManager/nm-system-settings.conf
Changed the file to:
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

[ifdown]
managed=true

[ifup]
managed=true

```

Source: [http://edtake.wordpress.com/2010/05/10/ubuntu-lucid-lynx-wireless-keep-dropping/]("http://edtake.wordpress.com/2010/05/10/ubuntu-lucid-lynx-wireless-keep-dropping/")

Good luck!

I tried it, it didn't work, let me try a reboot.

---

### Post by FinalLight on 2011-06-15
> **FinalLight said:**
> I tried it, it didn't work, let me try a reboot.

Reboot did nothing.

---

### Post by FinalLight on 2011-06-15
Help please? XD

---

### Post by rcktsingh on 2011-06-15
how about getting on a wired connection and installing wicd to see if that works fine ? 

post your $lspci output. may be someone can help after looking at that.

---

### Post by garvinrick4 on 2011-06-15
It is 99% of the time your wireless device driver problem, is your driver in the kernel or did you have to load a restricted driver to start with? First what is your card and driver?
```
sudo lshw -C network
```or below will give all cards and kernel drivers find your network controller:
```
lspci -k
```Below copy and paste one at a time to start and stop network manager.
```
sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start

```below will tell you what is active and more one at a time:
```

sudo hwinfo --netcard
``` ##Give the users some info to go on and they will get you running in no time. 
Must have your card and drivers to get you going some good network users around these forums.

##There are plenty of commands to get info on network these are just a few above:

---

### Post by AlbertoEdhek on 2011-06-15
I also have experienced this problem. On my UNR, I've installed firewall.
Maybe my brother have changed the network configuration (he has been broken my password). so, I can't access wireless network for a month.
Firstly, you must check your firewall configuration, and your network configuration.

---

### Post by FinalLight on 2011-06-15
> **garvinrick4 said:**
> It is 99% of the time your wireless device driver problem, is your driver in the kernel or did you have to load a restricted driver to start with? First what is your card and driver?
```
sudo lshw -C network
```or below will give all cards and kernel drivers find your network controller:
```
lspci -k
```Below copy and paste one at a time to start and stop network manager.
```
sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start

```below will tell you what is active and more one at a time:
```

sudo hwinfo --netcard
``` ##Give the users some info to go on and they will get you running in no time. 
Must have your card and drivers to get you going some good network users around these forums.

##There are plenty of commands to get info on network these are just a few above:
For the first command, this showed up:
*-network
description: Wireless interface
product: AR9285 Wireless Network Adapter(PCI Express)
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:2:00.0
logical name: wlan0
version: 01
serial: 88::25:2c:c3:e6:74
width:64 bits
clock: 34 MHz
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver= ath9k driverversion= 2.6.37-8-generic firmware=N/A latency=0 link=no multicast=yes wireless= IEEE 802.11bgn recources: irq: 17 memory:97000000-9700ffff

---

### Post by FinalLight on 2011-06-15
Then, I disabled the network manager, then restarted it, then entered the third command, which gave me this:
26: PCI 200.0: 0282 WLAN controller
[Created at pci.318]
UDI: /org/freedesktop/hal/devices/pci_168c_2b
Unique ID: y9sn.FR1No5WFY97
Parent Id: qTvu.kekTNY_Txu1
SysFS ID: /devices/pci0000:00/0000:00:1c.1/0000:02:00.0
SysFS BusID: 0000:02:00.0
Hardware Class: Network
Model: "Atheros Wlan Controller"
Vendor: pci 0x168c "Atheros Communications Inc."
Device: pci: 0x002b
Subvendor: pci 0x168c "Atheros Communications Inc"
SubDevice: pci 0x0205
.........................
*Theres alot more from there, and I'm typing this on my other computer, not copy and paste, so if you need anything from here, can you ask for it?*

---

### Post by FinalLight on 2011-06-15
Quick note: 
1) It's not my virus detector or firewall.

2) I'm in Gnome-3, so this may impact things (I don't know)

3) I'm on a dell inspiron atom duo, (Dell duo) which doesn't have a ethernet. (It's a tablet pc) 

~Thanks for all the help guy's, keep it comming, I need a solution, if worse comes to worse, I'll reinstall ubuntu and work from there.

---

### Post by garvinrick4 on 2011-06-15
In the third one you ran if you look down farther it will tell you if the driver is active.
ath9k is the driver.

---

### Post by garvinrick4 on 2011-06-15
What is the kernel you are running.
uname -a
Download the kernel you are using from this page to your DESKTOP:
[http://linuxwireless.org/en/users/Download/stable/#compat-wireless_2.6.39_stable_releases](http://linuxwireless.org/en/users/Download/stable/#compat-wireless_2.6.39_stable_releases)
Just change to whatever kernel below you downloaded: Unplug your usb wireless device
Open a terminal and do these one at a time just change to whatever you downloaded:
cd Desktop
ls
tar -xf compat-wireless-2.6.39.tar.bz2
ls
cd compat-wireless-2.6.39
make
sudo make install
sudo make unload                      
Plug in your usb wireless device and reboot:

---

### Post by AlbertoEdhek on 2011-06-15
> **FinalLight said:**
> Quick note: 
1) It's not my virus detector or firewall.

2) I'm in Gnome-3, so this may impact things (I don't know)

3) I'm on a dell inspiron atom duo, (Dell duo) which doesn't have a ethernet. (It's a tablet pc) 

~Thanks for all the help guy's, keep it comming, I need a solution, if worse comes to worse, I'll reinstall ubuntu and work from there.

[SIZE=4]**Don't give up!**[/SIZE]
[SIZE=1]It must have the solution. So, tablet pc. Since I am using Linux, I never meet[/SIZE] this problem.
Sorry, If only I knew.

---

### Post by rcktsingh on 2011-06-16
One more thing I forgot to add: My internet stopped getting disconnected after I stopped using Pidgin Messenger. I know that sounds weird(and I didn't report the problem anywhere), but hey, that worked for me. I figured, I am happy with my usual gmail chat.

---

### Post by garvinrick4 on 2011-06-16
Launchpad kernel fix for ath9k below 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761176/comments/8](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/761176/comments/8)

launchpad bug report below:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/754176](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/754176)

Other thread below:
[http://ubuntuforums.org/showthread.php?p=10929238#post10929238](http://ubuntuforums.org/showthread.php?p=10929238#post10929238)

---

### Post by FinalLight on 2011-06-16
> **garvinrick4 said:**
> In the third one you ran if you look down farther it will tell you if the driver is active.
ath9k is the driver.

Alright, it says my driver status is active:
Driver Status rt2500usb is active

---

### Post by garvinrick4 on 2011-06-16
```
sudo gedit /etc/modprobe.d/blacklist.conf
```
ADD this line below to bottom and hit save in upper left and close.
blacklist rt2500usb

Now reboot and should pick up ath9k driver which is what it should be using.

## All we did was make sure the rt2500usb driver was not used.

---

