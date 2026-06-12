---
title: "Slow login after activating wlan0"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by hanslammerts on 2011-04-01
Hi,
 
I have a strange issue that I cannot put my finger on.
Recently,I installed a new Ubuntu 10.04 server. No extra software yet, apart from
openssh-server. The wired connection (eth1) works fine. I then added a wireless card with chipset p54pci, which appears to work with the wext driver.
Configured /etc/wpa_supplicant, and /etc/network/interfaces as well:
 
This is wpa_supplicant:
```
 
ap_scan=1 
ctrl_interface=/var/run/wpa_supplicant 
network={ 
ssid="LaoKhao"           #very strong Thai rice whisky \\:D/
scan_ssid=0 
proto=WPA 
key_mgmt=WPA-PSK 
psk=longstringwithnumbersandletters
pairwise=TKIP 
group=TKIP 
}

```

[SIZE=1]This is interfaces:[/SIZE]
```
 
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2][FONT=Verdana][SIZE=1]auto lo[/SIZE][/FONT][/SIZE][/FONT][/SIZE][/FONT]
[SIZE=1]iface lo inet loopback [/SIZE]
 
[SIZE=1]# The primary network interface [/SIZE]
[SIZE=1]auto eth1 [/SIZE]
[SIZE=1]iface eth1 inet static [/SIZE]
[SIZE=1]address 192.168.2.100 [/SIZE]
[SIZE=1]netmask 255.255.255.0 [/SIZE]
[SIZE=1]network 192.168.2.0 [/SIZE]
[SIZE=1]broadcast 192.168.2.255 [/SIZE]
[SIZE=1]gateway 192.168.2.1 [/SIZE]
 
[SIZE=1]auto wlan0 [/SIZE]
[SIZE=1]iface wlan0 inet static [/SIZE]
[SIZE=1]address 192.168.2.97 [/SIZE]
[SIZE=1]netmask 255.255.255.0 [/SIZE]
[SIZE=1]wireless-essid LaoKhao [/SIZE]
[SIZE=1]gateway 192.168.2.1 [/SIZE]
[SIZE=1]wpa-driver wext [/SIZE]
[FONT=Helv][SIZE=2][FONT=Helv][SIZE=2][FONT=Verdana][SIZE=1]wpa-conf /etc/wpa_supplicant.conf[/SIZE][/FONT]
[/SIZE][/FONT][/SIZE][/FONT]
```

[FONT=Tms Rmn][FONT=Verdana][SIZE=1]After a reboot the machine comes up with both NICs active.[/SIZE][/FONT][/FONT]

[FONT=Tms Rmn][FONT=Verdana][SIZE=1]If I do a ssh from another Ubuntu machine to this machine (to 192.168.2.100, so the wired address) it takes about 30 seconds before I get the login as: prompt.[/SIZE][/FONT][/FONT]
[FONT=Tms Rmn][FONT=Verdana][SIZE=1]If I change the interfaces file so that wlan0 is not started (I comment out the line auto wlan0, and reboot), connecting from another machine with ssh alsmost instantly gives me te login prompt.[/SIZE][/FONT][/FONT]

[FONT=Tms Rmn][FONT=Verdana][SIZE=1]I tried switching the order of both NICs in the interfaces file. Also tried changing the sshd config file so that it only listens on the wired ip address. Both did not help.[/SIZE][/FONT][/FONT]

[FONT=Tms Rmn][FONT=Verdana][SIZE=1]Does anyone have a clue why logging in with ssh from another machine is very much slower in response with wlan0 activated than without ?[/SIZE][/FONT][/FONT]

[FONT=Tms Rmn][FONT=Verdana][SIZE=1]TIA,[/SIZE][/FONT][/FONT]

[FONT=Tms Rmn][FONT=Verdana][SIZE=1]Hans[/SIZE][/FONT]
[/FONT]

---

### Post by hanslammerts on 2011-04-02
Anyone, please ?

---

### Post by hanslammerts on 2011-04-04
The use of "UseDNS no" in the sshd config on the server fixed this...

---

