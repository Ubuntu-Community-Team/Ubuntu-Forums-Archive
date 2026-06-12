---
title: "PEAP authentication"
date: 2005-12-12
forum: Networking &amp; Wireless
---

### Post by bluedog666 on 2005-12-12
Hello and sorry for the (potentially) nooby question.

I am trying to configure a dell600m with an intel2200 on ubuntu 5.10 to connect to a PEAP wifi. 

The network only offers support for windows, but here are the config options
WEP enabled
key provided authomatically
IEEE 802.1x PEAP enabled
validate server certificate
connect to server ***.******.**
trusted root certification authority:Secuer Server Certification Authority
secuer password EAP-MSCHAPv2

I have installed wpa_suplicant and XSuplicant

i have the following wpa_suplicant.conf file
```

update_config=1
ctrl_interface=/var/run/wpa_suplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

network={
       ssid="something"
       scan_ssid=1
       priority=10
       key_mgmt=IEEE8021X
       auth_alg=OPEN

       eap=PEAP
       identity="something"
       password=something"
       
       phase1="peaplabel=1"
       phase2="auth=MSCHAPV2"
}

```

```
xsupplicant -c /etc/wpa_supplicant.conf -i eth1
```
returns with success but 
```
ifup eht1
```
returns 
```

DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
NO DHCPDISCOVER received.

```

I think one of the problems is the fact that I do not have a client-side certificate and have to obtain it from the server (and have no idea how to do that).
Any ideas/suggestions ?

Thanks,
Alex

---

