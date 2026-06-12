---
title: "Network manager doesn't work   =("
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by csykim on 2006-07-11
Hello, I am new to Ubuntu (switching from Fedora).  I was able to get my Dell Truemobile 1390 (Broadcom 4311) wifi card working using ndiswrapper (apparently the bcm43xx driver doesn't work for 4311).

Anyways, I was trying to get nm-applet working but I can't seem to get connected.  The clicking the icon on the upper toolbar shows my wireless network along with some others.  I click on my network and it asks for my wep code which I enter in (64bit hex open code), and then it never seems to be able to connect.  Anyone have the same problem or an idea on how to make it work?

Using iwconfig to manually set my essid/key and dhclient to connect work fine, but then even after I'm connected, nm-applet does not show that I am connected.  Help anyone?

---

### Post by tbdombrosky on 2006-07-12
I have the same problem.  Haven't been able to fix it.

---

### Post by jenred on 2006-07-12
Make sure you disable all of your network interfaces and THEN run network-manager.

---

### Post by tbdombrosky on 2006-07-13
OK!  I got it working without Network Manager.  Here's what my /etc/network/interfaces file looks like:

> auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf


And here's what my /etc/wpa_supplicant/wpa_supplicant.conf file looks like:

> ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
# Example blocks:

# Simple case: WPA-PSK, PSK as an ASCII passphrase, allow all valid ciphers
network={
        ssid="PUTSSIDHERE"
        psk="PUTKEYHERE"
        priority=5
}


---

### Post by csykim on 2006-07-13
> **jenred said:**
> Make sure you disable all of your network interfaces and THEN run network-manager.


Still no luck  =(.  I did a manual disable of all interfaces (using e.g ifconfig eth0 down) but I'm getting the same result.  It's detecting all the wireless networks just fine, just can't connect to any of them.  After I enter in my key, it just tries to connect for about a minute and gives up. I even tried connecting to my neighbor's unsecured network and it still can't establish connection.

Could the problem have something to do with me using ndiswrapper rather than a built in driver?  I have no problems with connecting when I use:

iwconfig wlan0 key open XXXXXXX
iwconfig wlan0 essid XXXXXXX
dhclient wlan0

It also works on boot when plug in my key and essid into my /etc/network/interfaces file.  Just no luck with nm-applet so it makes using my laptop wireless a pain when I go to work or school.

---

### Post by jenred on 2006-07-14
I had almost the exact problem.  Tried manually disabling the interfaces via ifup and ifdown, tried deactivating the interfaces via the network gui.  The lack of easy wifi was also driving me nuts.

FINALLY what worked for me was to use the System | Network gui to disable the interfaces.  Select each interface, go to properties, remove the enable check marks, and then run network-manager.  Make sure network-manager isn't running when you disable the interfaces.  

Have you tried using disabling via the gui yet?

---

### Post by jakemikey on 2006-07-17
I've been having this problem with network-manager since the dapper alphas, and it still hasn't been fixed.  Using ndiswrapper as the driver I *cannot* connect to unsecured networks with network-manager.  Killing network-manager and uncommenting the appropriate lines in /etc/network/interfaces and using ifup eth1 works.  Why doesn't network-manager work when the command line clearly works?  I also have *everything* in the interfaces file commented out when running network-manager.  Does anyone know where I should look to see if there's an open bug on this?

PS - just wanted to mention that nm works just fine with my home WPA2 network - it's the unencrypted campus network that gives grief.

---

