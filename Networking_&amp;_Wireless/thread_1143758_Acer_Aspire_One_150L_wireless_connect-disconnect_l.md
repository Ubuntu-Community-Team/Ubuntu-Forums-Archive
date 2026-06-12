---
title: "Acer Aspire One 150L wireless connect-disconnect loop"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by rotor_of_the_internet on 2009-04-30
I'm new to Linux. I just decided to install the latest Ubuntu Remix on my Netbook (Acer Aspire One 150L). I don't have any experience setting up wireless networks.

My problem is that my wireless connection keeps disconnecting as soon as it has connected.

I enabled my wireless connection in my modem's web interface and I set up the details (SSID, BSSID and password). It seems to establish a connection without any errors but I don't think it truly connects to the modem.

I noticed other Aspire One users blacklisting acer_wmi, but that didn't seem to change anything for me.

Can anyone help me to identify what's going on?

---

### Post by duanedesign on 2009-09-25
I am pretty sure your laptop has the AR242x. You can confirm this by running this command in a Terminal.
Applications > Accessories > Terminal

```
lspci -vnn
```

you should see something like this:

03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

If that is correct you should be using the Ath5k driver. To confirm this you should see in the same stanza as the information above two lines like this:

Kernel driver in use: ath5k
Kernel modules: ath5k

This particular card is not easy to get working. Some have had better luck than others so I dont want to discourage you from trying.
To try the latest ath5k driver run the following in the Terminal:

```
sudo apt-get install linux-backports-modules-jaunty
```

also make sure the ath_pci is blacklisted

```
sudo nano /etc/modprobe.d/blacklist.conf
```
NOTE: your file may or may not have .conf on the end. if you do not find this file try /etc/modprobe.d/blacklist. If this is the case after you are done with it save it with .conf on the end, this is the preferred format.

Look for a line in the file like the one below. If it is not there add it and save the file:
> blacklist ath_pci

Try this newer driver and see if you have any change in performance.

If you do not get any improvement I would try the site below. This will install the ath_pci module. If you are going to try the driver recommended below you need to delete the line you added to /etc/modprobe.d/blacklist.conf that blacklisted this driver. The reason for the blacklisting is to keep the two drivers from conflicting. 

A couple of things not mentioned on this link.
1. If you have never compiled anything on your machine you will need to install the build-essential package. Run the following command before following the link.

```
sudo apt-get install build-essential
```

2. After you install the ath_pci driver 'modprobe ath_pci' you will need to go to System > Administration > Hardware Drivers to enable the new driver and disable the old Atheros one.

[http://adamdotnet.net/2008/08/18/acer-one-wifi-fix/](http://adamdotnet.net/2008/08/18/acer-one-wifi-fix/)
-
-
-

---

