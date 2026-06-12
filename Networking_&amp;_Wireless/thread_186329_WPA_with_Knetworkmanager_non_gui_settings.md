---
title: "WPA with Knetworkmanager: non gui settings"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by lexxonnet on 2006-06-01
Hey everyone,
 
I'm using Kubuntu Dapper and have tried to get Network Manager working with my University's Wireless Network. I recently did manage to get wpasupplicant working, but its a bit of a chore, cos everytime I move hotspots, I need to look for an ip again, and also, a lot of issues switching between a wired and a wireless network.
 
KNetworkmanager(or Network-manager-gnome) seems to be a much better solution, but it doesn't seem to allow all the options for configuring a WPA network. I just wanted to ask if there's any way to get all the wpasupplicant options working with network manager, such as specifing a wpasupplicant config file in network manager and so on... I'm attaching my wpasupplicant config file for reference.
 
Cheers
Lex

```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=2
ap_scan=2
fast_reauth=0

network={
        ssid="ACHERNAR-BG"
        key_mgmt=WPA-EAP
        proto=WPA
        eap=PEAP
        pairwise=TKIP
        group=TKIP
        identity="********"
        password="********"
        ca_cert="/etc/ssl/certs/Thawte_Premium_Server_CA.pem"
        phase1="peaplabel=0 include_tls_length=1"
        phase2="auth=MSCHAPV2"
        priority=1
}

```

---

### Post by lexxonnet on 2006-06-04
anyone?? :(

---

### Post by timmir on 2006-09-05
I'm having the same problems.  I'm using gnome and nm-applet.  my university also uses the same type of connection.  were you able to find anything out?

---

### Post by ltmon on 2006-09-05
Hi,

I'm using knetworkmanager with a WPA network at work.  When you try to connect to the network for the first time it comes up with a configuration screen for that network, where I was able to enter all the WPA settings I needed.

Have you gotten to this stage?  Or is there something more you need to configure?

L.

---

