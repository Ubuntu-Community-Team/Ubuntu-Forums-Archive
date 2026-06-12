---
title: "Linux chalanged need help"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by yellowsnow55 on 2010-09-09
Help, can no longer access the internet,Deleted Network Manager thinking I could reinstall it and it would be back to its default settings. Had not been able to get online for days. Offcourse now I can't get Network manager back as I have to be online for that. I think I had stuffed up the proxy settings but can't work out how to get that back to default either.
What do I do now and how do I do it?:rolleyes:

---

### Post by Cabalbl4 on 2010-09-09
Download the debs for network manager and nm-applet from here [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and install them )
This thread is also useful: [http://ubuntuforums.org/archive/index.php/t-1005244.html](http://ubuntuforums.org/archive/index.php/t-1005244.html)

---

### Post by jeight on 2010-09-09
First of all you don't need network manager to get online. Try the steps from the Arch linux beginners install guide.  Use the appropriate option for your network.
[http://wiki.archlinux.org/index.php/Beginners%27_Guide#Step_1:_Configuring_the_network_.28if_necessary.29](http://wiki.archlinux.org/index.php/Beginners%27_Guide#Step_1:_Configuring_the_network_.28if_necessary.29)

** Wired LAN**

 Check your Ethernet with 
 # ifconfig -a
All interfaces will be listed. You should see an entry for eth0, or perhaps eth1.  
 
[LIST]
[*]**Static IP**
[/LIST]
 If required, you can set a new static IP with: 
 # ifconfig eth0 <ip address> netmask <netmask> up 
and the default gateway with 
 # route add default gw <ip address of the gateway>
Verify that /etc/resolv.conf contains your DNS server and add it if  it is missing.  Check your network again with ping [www.google.com](www.google.com). If everything is  working now, adjust /etc/rc.conf as described above for static IP.  
 
[LIST]
[*]**DHCP**
[/LIST]
 If you have a DHCP server/router in your network try: 
 # dhcpcd eth0
If this is working, adjust /etc/rc.conf as described above, for dynamic IP. 
 ** Wireless LAN**

 
[LIST]
[*] Ensure the driver has created a usable interface:
[/LIST]
 # iwconfig

[LIST]
[*] Bring the interface up with ifconfig <interface> up. e.g.:
[/LIST]
 # ifconfig wlan0 up
** Note: **If you get this error message: SIOCSIFFLAGS: No such file or directory  it most certainly means your wireless chipset requires a firmware to  function, which you forgot to install during package selection. See [Does the Wireless Chipset require Firmware?]("http://wiki.archlinux.org/index.php/Beginners%27_Guide#Does_the_Wireless_Chipset_require_Firmware.3F") and [Select Packages]("http://wiki.archlinux.org/index.php/Beginners%27_Guide#D:_Select_Packages").
 
[LIST]
[*] Associate your wireless device with the access point you want  to use. Depending on the encryption (none, WEP, or WPA), the procedure  may differ. You need to know the name of the chosen wireless network  (ESSID), e.g. 'linksys' in the following examples:
[*] An example using a *non-encrypted* network:
[/LIST]
 # iwconfig wlan0 essid "linksys"

[LIST]
[*] An example using *WEP and a hexadecimal key*:
[/LIST]
 # iwconfig wlan0 essid "linksys" key 0241baf34c

[LIST]
[*] An example using *WEP and an ASCII passphrase*:
[/LIST]
 # iwconfig wlan0 essid "linksys" key s:pass1

[LIST]
[*] Using *WPA*, the procedure requires a bit more work. Check [WPA supplicant]("http://wiki.archlinux.org/index.php/WPA_Supplicant") for more information and troubleshooting:
[/LIST]
 # wpa_passphrase linksys "secretpassphrase" > /etc/wpa_supplicant.conf
# wpa_supplicant -B -Dwext -i wlan0 -c /etc/wpa_supplicant.conf

[LIST]
[*] Check you have successfully associated to the access point before continuing:
[/LIST]
 # iwconfig wlan0

[LIST]
[*] Request an IP address with /sbin/dhcpcd <interface> . e.g.:
[/LIST]
 # dhcpcd wlan0

[LIST]
[*] Ensure you can route using /bin/ping:
[/LIST]
 # ping -c 3 [www.google.com](www.google.com)

---

