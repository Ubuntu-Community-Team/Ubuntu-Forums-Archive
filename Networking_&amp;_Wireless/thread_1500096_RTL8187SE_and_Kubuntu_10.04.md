---
title: "RTL8187SE and Kubuntu 10.04"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by garryknight on 2010-06-02
I recently upgraded my MSI Wind clone netbook to Kubuntu 10.04 from 9.10. Since then my WiFi seems to have stopped working - or the KDE network manager has. I used the "Manage connections" dialog to configure the connection with the correct WPA2/PSK password and using DHCP. I also checked the "Connect automatically" box. Not only does it not connect automatically, I can't manually get it to connect either.

If I left-click the tray icon, my wireless router is listed, but if I click it, it does nothing. If I click "Connect to other network", select mine, then click Connect, nothing seems to happen.

Running 'lsmod | grep rtl" shows this:
rtl8187se             159435 0

Running "sudo /sbin/iwlist scan" shows my router with the correct ESSID and other information.

Running "iwconfig wlan0 essid MYESSID" returns no errors, but "ifup wlan0" shows:
Ignoring unknown interface wlan0=wlan0

Strange. Either it exists or it doesn't. The error message seems to be inconsistent.

Other than telling me to install wicd, can anyone shed any light on what's going on? Is it a fault with the hardware, the kernel module, or knetworkmanager? Or something else?

---

### Post by garryknight on 2010-06-02
Update: I tried installing the wireless backport packages as per [this post]("http://ubuntuforums.org/showpost.php?p=9270508&postcount=3") and it seems to have worked. 

At least, after a reboot I switched the wireless card on and was prompted to enter my password for the KDE Wallet and up came the connection.

In case it helps anyone else with a Realtek RTL8187SE card and Kubuntu 10.04 (possibly the Gnome version, too), here's what I did:

sudo apt-get update && sudo apt-get install linux-backports-modules-wireless-lucid-generic

---

### Post by garryknight on 2010-06-03
I spoke too soon. The connection to my router came up ok but not only can I not get out to the Internet, I don't even get any pings back from my router; I get a "Destination Host Unreachable" message. The route table looks OK to me:

```

Kernel IP routing table
Destination     Gateway         Genmask        Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0  U     2      0      0   wlan0
link-local      *               255.255.0.0    U     1000   0      0   wlan0
default         router.garry.la 0.0.0.0        UG    0      0      0   wlan0

```
The router is router.garry.lan at 192.168.1.1 as defined in /etc/hosts, and my netbook is given 192.168.1.3 by the router. My PC is 192.168.1.2 and if I ping the netbook from the PC, I get the same "Destination Host Unreachable" message, and also if I try pinging the PC from the netbook.

Has anyone got any idea what's going on?

---

### Post by garryknight on 2010-06-06
*Bump*

Has anyone got any ideas about why my RTL8187se connects to my wireless router but won't give me access to the internet, please?

---

### Post by garryknight on 2010-06-06
I really ought to stop talking to myself... :-\"

Right, I seem to have solved it. I uninstalled the KDE front-end to network-manager and installed the Gnome front-end with this command:

sudo aptitude purge network-manager-kde -y ; sudo aptitude install network-manager-gnome

I then added nm-applet to the Autostart in System Settings. Now my wifi seems to work. Hope this helps someone else in the same situation.

---

