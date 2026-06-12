---
title: "Dynamic WEP and wpa_supplicant (?)"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by leden on 2009-05-09
Hi! First of all, I'm don't have much knowledge about networking.

My university says it uses 802.1b for wifi.
On my ubuntu laptop I use nm-applet to connect. The only way I managed to connect is with this nm-applet is with Dynamic WEP with PEAP, MSCHAPv2.
However, I heard people have successfully connected using wpa(2)_enterprise.
Is this possible? What is the difference?

Now what I really want to know is how can I configure the whole thing using only wpa_supplicant. The example wap_supplicant.conf file says something about 802.1x with dynamic WEP, but so far I haven't come across a manual/guide for setting it (using MSCHAPv2, PEAP etc.).

This is the extract from this example:
```

# IEEE 802.1X/EAPOL with dynamically generated WEP keys (i.e., no WPA) using
# EAP-TLS for authentication and key generation; require both unicast and
# broadcast WEP keys.
network={
	ssid="1x-test"
	key_mgmt=IEEE8021X
	eap=TLS
	identity="user@example.com"
	ca_cert="/etc/cert/ca.pem"
	client_cert="/etc/cert/user.pem"
	private_key="/etc/cert/user.prv"
	private_key_passwd="password"
	eapol_flags=3
}

```
What should I change here (except ssid, identity, private_key_passwd) to  to set it to use 802.1x with PEAP and MSCHAPv2?

---

