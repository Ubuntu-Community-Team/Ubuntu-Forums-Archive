---
title: "Lucid Lynx Network-Manager and WPA Enterprise PEAP / MSCHAPv2"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by Sunseeker.ch on 2010-08-09
Hi Folks,

my Wireless Network is secured by freeradius with peap/mschapv2. Until now I just had xp-clients and one smartphone. All worked well. Trying my kubuntu installation get working is a little frustrating.

I've configured the connection via network-manager-applet. CA-Cert, username, password. Establishing the connection fails. The nm-applet pops up again and requests new credentials (username, password).

The radius.log shows the following:
```

Mon Aug  9 11:31:01 2010 : Auth: Login incorrect: [anon] (from client 192.168.0.3 port 0 cli 00-12-6E-7A-6E-FF)

```The daemon.log on the kubuntu client shows this:
```

Aug  9 11:55:55 lrrr NetworkManager: <info>  Activation (eth1) starting connection 'connection-name'
Aug  9 11:55:55 lrrr NetworkManager: <info>  (eth1): device state change: 3 -> 4 (reason 0)
Aug  9 11:55:55 lrrr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Aug  9 11:55:55 lrrr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Aug  9 11:55:55 lrrr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Aug  9 11:55:55 lrrr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Aug  9 11:55:55 lrrr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Aug  9 11:55:55 lrrr NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Aug  9 11:55:55 lrrr NetworkManager: <info>  Activation (eth1/wireless): access point 'connection-name' has security, but secrets are required.
Aug  9 11:55:55 lrrr NetworkManager: <info>  (eth1): device state change: 5 -> 6 (reason 0)
Aug  9 11:55:55 lrrr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Aug  9 11:55:55 lrrr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Aug  9 11:55:55 lrrr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Aug  9 11:55:55 lrrr NetworkManager: <info>  (eth1): device state change: 6 -> 4 (reason 0)
Aug  9 11:55:55 lrrr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Aug  9 11:55:55 lrrr NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Aug  9 11:55:55 lrrr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Aug  9 11:55:55 lrrr NetworkManager: <info>  (eth1): device state change: 4 -> 5 (reason 0)
Aug  9 11:55:55 lrrr NetworkManager: <info>  Activation (eth1/wireless): connection 'connection-name' has security, and secrets exist.  No new secrets needed.
Aug  9 11:55:55 lrrr NetworkManager: <info>  Config: added 'ssid' value 'Planetexpress'
Aug  9 11:55:55 lrrr NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug  9 11:55:55 lrrr NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-EAP'
Aug  9 11:55:55 lrrr NetworkManager: <info>  Config: added 'password' value '<omitted>'
Aug  9 11:55:55 lrrr NetworkManager: <info>  Config: added 'eap' value 'PEAP'
Aug  9 11:55:55 lrrr NetworkManager: <info>  Config: added 'fragment_size' value '1300'
Aug  9 11:55:55 lrrr NetworkManager: <info>  Config: added 'phase2' value 'auth=MSCHAPV2'
Aug  9 11:55:55 lrrr NetworkManager: <info>  Config: added 'ca_path' value '/home/user/ovpn/my-ca.pem'
Aug  9 11:55:55 lrrr NetworkManager: <info>  Config: added 'ca_cert' value 'blob://-org-freedesktop-NetworkManagerSettings-1-ca_cert'
Aug  9 11:55:55 lrrr NetworkManager: <info>  Config: added 'identity' value 'username'
Aug  9 11:55:55 lrrr NetworkManager: <info>  Config: added 'anonymous_identity' value 'anon'
Aug  9 11:55:55 lrrr NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Aug  9 11:55:55 lrrr NetworkManager: <info>  Config: set interface ap_scan to 1
Aug  9 11:55:55 lrrr NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Aug  9 11:55:55 lrrr wpa_supplicant[784]: Trying to associate with ap-mac (SSID='ssid' freq=2412 MHz)
Aug  9 11:55:55 lrrr NetworkManager: <info>  (eth1): supplicant connection state:  scanning -> associating
Aug  9 11:55:55 lrrr wpa_supplicant[784]: Association request to the driver failed
Aug  9 11:55:55 lrrr wpa_supplicant[784]: Associated with ap-mac
Aug  9 11:55:55 lrrr NetworkManager: <info>  (eth1): supplicant connection state:  associating -> associated
Aug  9 11:55:56 lrrr wpa_supplicant[784]: CTRL-EVENT-EAP-STARTED EAP authentication started
**Aug  9 11:55:56 lrrr wpa_supplicant[784]: OpenSSL: tls_connection_ca_cert - Failed to parse ca_cert_blob error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag**
Aug  9 11:55:56 lrrr wpa_supplicant[784]: OpenSSL: pending error: error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
Aug  9 11:55:56 lrrr wpa_supplicant[784]: TLS: Failed to set TLS connection parameters
Aug  9 11:55:56 lrrr wpa_supplicant[784]: EAP-PEAP: Failed to initialize SSL.
Aug  9 11:55:56 lrrr wpa_supplicant[784]: EAP: Failed to initialize EAP method: vendor 0 method 25 (PEAP)
Aug  9 11:55:57 lrrr wpa_supplicant[784]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug  9 11:55:57 lrrr NetworkManager: <info>  (eth1): supplicant connection state:  associated -> disconnected
Aug  9 11:55:57 lrrr wpa_supplicant[784]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug  9 11:55:57 lrrr NetworkManager: <info>  (eth1): supplicant connection state:  disconnected -> scanning
Aug  9 11:55:58 lrrr wpa_supplicant[784]: Trying to associate with ap-mac (SSID='SSID' freq=2412 MHz)
Aug  9 11:55:58 lrrr wpa_supplicant[784]: Association request to the driver failed

```Now a look in the connection-file ~/.kde/[...]/connections shows, that not the path to the ca-cert-file is written in the config but the contend (not /home/user/my-ca.crt but something like: ----- BEGIN CERTIFICATE ------  and so on.)
This looks odd to me.

Furthermore I've tried the PEM- as well as the DER-format for the ca-file with no change.

Maybe someone can help me with that issue?

---

### Post by happysam on 2010-08-18
I'm having the same problem... Just switched out my old Ubuntu 10.04 NBR to Kubuntu 10.04 netbook and now I can't connect to QUT wifi (my university).

ubuntu NBR worked without a hitch, so i'm well confused.

---

### Post by jatoo on 2010-09-10
happysam, i am having problems wiht QUT wireless as well! i'm not on kubuntu though, just ubuntu netbook 10.04.

any luck with it yet, or anyone have any ideas?

---

### Post by dannelb on 2010-09-12
I had the same problem connecting to a Wifi with the WPA Enterprise settings.
I installed Lucid Lynx (10.4) on my Samsung NC10 netbook. I upgraded the NetworkManager to 0.8.1 to fix the problem connecting to Mobile Broadband with my Huawei modem (EC1261). It did fix that problem beautifully. But, for some reason, I was not able to connect to the WPA Enterprise Wifi. I downgraded to NetworkManager 0.8.0 (from the Ubuntu canonical source) and all worked fine to connect to the WPA Enterprise Wifi.
I now have to use usb modeswitch and wvdial to connect to my Mobile Broadband connection, but the Wifi is working fine with NetworkManager 0.8.0

Check which version of NetworkManager you have installed.

I hope that in a future release everything can work properly.

Hope this helps.

---

### Post by Sunseeker.ch on 2010-09-29
I've just configured my Freeradius to work with certificate-based authentication as well.
The same problem here.

I have installed:
network-manager 0.8.0ubuntu3

OpenVPN doesn't work as well, when the private key is password protected.

---

### Post by chandra on 2010-09-29
Has anyone on this thread tried wicd?

```
sudo apt-get install wicd
```

Although I have no experience with this specific setup, I think it might not hurt to try it.

---

