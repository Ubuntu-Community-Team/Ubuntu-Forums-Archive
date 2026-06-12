---
title: "Atheros AR242x and Xubuntu"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by hobbsc on 2008-12-20
Greetings -

I've got an HP dv6915nr laptop and I've tried to install Xubuntu 8.10.  

So far, everything but my wireless card works.  It worked under 8.04 with ndiswrapper and it works out of the box using openSUSE 11.0 and 11.1.  I'm sure I'm just having some sort of driver issue here.

'lspci' tells me that I have an Atheros AR242x chipset.  System -> Hardware Drivers says that Atheros 802.11 support is enabled.   However, when I click the network manager, I don't see any wireless networks and if I right click it, I don't get an "Enable Wireless" option.

'ifconfig' and 'wiconfig' do not report any sort of wireless card attached to the system.

What steps do I need to take to get this card working?

Thank you!

---

### Post by hobbsc on 2008-12-20
In addition to this, running 'lshw -C Network' shows me that my wireless card is "unclaimed" and has no driver listed on the configuration line.

---

### Post by rienriscos on 2008-12-20
I am having the same problem with Ubuntu 8.10 on a asus laptop X59SL
Atheros website points me to asus, but I do not find any download of a driver for this AR242x from Atheros there.

The wlan switch does switch on the led for a very short flash and the led goes out right away.

I have tried switching the driver on in Windows Vista but that does not help for Ubuntu.
Any help appreciated!

---

### Post by ugm6hr on 2008-12-20
Your options are either ndiswrapper (as in Hardy), or the new ath5k driver.
 
Read this: [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros) ath5k wireless driver not enabled by default.

The [linux-backports-modules-intrepid-generic]("apt:linux-backports-modules-intrepid-generic") package will install ath5k, if you enable the backports repo.

---

### Post by iBurger on 2009-03-02
> **rienriscos said:**
> I am having the same problem with Ubuntu 8.10 on a asus laptop X59SL
Atheros website points me to asus, but I do not find any download of a driver for this AR242x from Atheros there.

The wlan switch does switch on the led for a very short flash and the led goes out right away.

I have tried switching the driver on in Windows Vista but that does not help for Ubuntu.
Any help appreciated!

I run Ubuntu 8.04 on my Asus X59SL with wireless enabled. I have the AR5007EG Wireless on my asus.

Installing the Madwifi drivers: (I take no credit for the solution, just made the notes how to do it)
#################################
[SIZE="2"]
1. Under System/Administration/HarwareDrivers disable "Support for Atheros 802.11 wireless LAN cards

2. Reboot

3. The kernel headers and the compiler are needed to build this driver so install build-essential. In a terminal window (Applications/Accessories/Terminal) enter:

```
$ sudo apt-get install build-essential

```
4. Install Subversion

```
$ sudo apt-get install subversion

```
5. Checkout the Madwifi drivers to a directory on your local disk

```
$ cd~
$ mkdir madwifi
$ cd madwifi
$ svn co [https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6](https://svn.madwifi.org/madwifi/branches/madwifi-hal-0.10.5.6)

```
6. Build the drivers
```

$ cd madwifi-hal-0.10.5.6
$ make

```
7. Install the drivers

```
$ make install

```
8. Add the Atheros kernel module to the list of modules to be automatically loaded at boot by adding "ath_pci" (without the quotes) to the end of the /etc/modules file and save the file

```
$ sudo gedit /etc/modules

```
9. Now you can reboot and it should work.[/SIZE]

---

