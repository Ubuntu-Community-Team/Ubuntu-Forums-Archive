---
title: "HOWTO - Join ubuntu to AD domain, and perform wired 802.1x MACHINE AUTHENTICATION."
date: 2013-05-03
forum: Networking &amp; Wireless
---

### Post by macarthor on 2013-05-03
Hi all,

Many corporation deploy 802.1x machine authentication, because it's more secure than username authentication. Here's a guide of how to do such authentication.

The basic idea is that when a machine joins an AD domain, DC generates a password corresponding to that machine name. The password is transparent to administrators, but an open source software "likewise open" can get this password. So we can use machine name and password to do a 802.1x machine authentication, with PEAP-MSCHAPV2, other than EAP-TLS certificate.

1. Suppose that you'd setup a valid 802.1x machine authentication environment, including switch, AD domain and NPS server.

2. Join ubuntu to AD domain (quite simple):
2.a ```
apt-get install likewise-open
```
2.b ```
domainjoin-cli join <domain dns name> <domain account that has join-domain right>
```, and password will be prompted.

3. Get machine password, and do 802.1x machine authentication:
3.a.1 ```
lw-lsa ad-get-machine password <domain dns name>
```, and record the last output line "password". This is command is for ubuntu 11.04 and later version.
3.a.2 ```
lw-dump-machine-acct <domain dns name>
```. This command is for ubuntu before 11.04.
3.b open network manager, select your wired connection, edit its 802.1x options as following: Authentication - PEAP, PEAP Version - Automatic, Inner authentication - MSCHAPV2, Username - "host/<full computer dns name>" or "<domain dns name>/computers/<computer hostname>", Password - what you got at 3.a.
3.c Save everything, and you will get a valid IP address later. What's more, machine authentication will be done on every reboot.
3.d Besides network manager, you can also use another build-in software "wpa_supplicant". Edit a configuration file "/etc/wpa_supplicant/config.conf" with content:
```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0
eapol_version=1
ap_scan=0
network={
ssid="what ever you like, does not matter"
key_mgmt=IEEE8021X
eap=PEAP
identity="host/<computer full dns name>" or "<domain dns name>/computers/<computer hostname>"
password=&#8221;xxxxxx&#8221;
}
```
and then use the following command to do machine authentication:
```
wpa_supplicant -Dwired -ieth0 -c/etc/wpa_supplicant/config.conf
```

---

### Post by mdalacu on 2014-03-11
Thank you very much for this. You are a life saver.
But i have a small question, what will happen when computer password will expire (in our AD  it is set to 21 days)? On windows this is done transparently by the os. It will be updated automatically or i will be left without network connection?
Thank you very much.

---

