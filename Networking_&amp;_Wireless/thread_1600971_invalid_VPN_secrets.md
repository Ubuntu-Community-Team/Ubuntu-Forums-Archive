---
title: "invalid VPN secrets"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by mogambo on 2010-10-19
[SIZE=2]Unable to connect to vpn and  along with my thinkpad I am  frustrated, exhausted by multiple restart
installed ubuntu 10.10 on Thinkpad-T410 64 bit [/SIZE]
[SIZE=2][B][U]
Steps[/U][/B][/SIZE]
1. sudo apt-get install network-manager-vpnc
2. sudo apt-get remove resolvconf
3. Import .pcf
4. reboot
5. connect, enter password in password window 
6. error "invalid VPN secrets"

also  tried  enabling/disabling  Dead Peer Detection option but still no success

:confused:

---

### Post by mogambo on 2010-10-21
Solved . but not using  VPN gui client

created a test.config file
IPSec gateway <gateway IP>
IPSec ID <CLIENT ID >
IPSec secret <CLIENT PASSWORD>
Xauth username <user id>

_**to connect**_
sudo vpnc-connect test.config
enter the password

_**to disconnect **_
sudo vpnc-disconnect


:guitar:

---

### Post by deezer on 2010-10-22
Now that you solved it does the GUI client work?

---

### Post by deezer on 2010-10-22
FYI to all - A reboot made the GUI version work for me.  See [http://ubuntuforums.org/showthread.php?t=1564642]("http://ubuntuforums.org/showthread.php?t=1564642")

---

