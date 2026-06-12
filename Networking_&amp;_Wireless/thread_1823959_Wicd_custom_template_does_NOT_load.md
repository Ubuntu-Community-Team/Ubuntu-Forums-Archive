---
title: "Wicd: custom template does NOT load"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by acimmarusti on 2011-08-12
My university has a secure wireless network that has the following specs: WPA2, 1st Authentication TTLS, 2nd Authentication PAP, Encryption CCMP or AES, Thawte_Premium_Server_CA certificate and username and password.

I have never gotten this to work with wicd. First of all, wicd does not have a default template for this configuration. This led me in the past to quickly install Network-Manager (on top of XFCE...). While this has worked for me just fine. Recently I found out that this functionality is possible in wicd by creating your own template. So I did and here it is! 

```

name = WPA2 Enterprise TTLS
author = Andres Cimmarusti
version = 1
require identity *Identity anonymous_identity *Anonymous_identity  password *Password auth *Authentication  ca_cert *Path_to_CA_Cert
-----
ctrl_interface=/var/run/wpa_supplicant
network={
   ssid="$_ESSID"
   scan_ssid=$_SCAN
   proto=WPA2
   key-mgmt=WPA-EAP
   pairwise=CCMP TKIP
   group=CCMP TKIP
   eap=TTLS
   anonymous_identity="$_ANONYMOUS_IDENTITY"
   ca_cert="$_CA_CERT"
   phase2="auth=$_AUTH"
   identity="$_IDENTITY"
   password="$_PASSWORD"
}

```

I did everything outlined here: [http://wicd.net/templates.php](http://wicd.net/templates.php) (that is I saved the file as wpa2-ttls and then added this entry to the active file in /etc/wicd/encryption/templates/).

Sadly wicd's gui does not load my template!, the logs show no errors!...it simply refuses to take it. I cannot see any mistake in the above... do you?

Is this some debian bug perhaps?

This is the most important issue for me, before accepting to use wicd instead of NM.

---

### Post by acimmarusti on 2011-08-13
It appears wicd is rather finicky about white spaces when specifying the required and optional fields.... I had sometimes 2 spaces in between each field. By correcting this, it worked! (by that I mean just having one white-space)

---

