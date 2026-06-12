---
title: "Problems connecting to secure wireless AP in Jaunty"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by HarrisonFan on 2010-01-13
Hi,

My brother is trying to connect his laptop to his university's secure wireless network and is running into some problems.

He is receiving the following error messages with private info removed:

kern.log
=========
```
Jan 13 09:42:52 laptop kernel: [   91.744131] wlan0: associate with AP
Jan 13 09:42:52 laptop kernel: [   91.746454] wlan0: RX AssocResp from REMOVED (capab=0x421 status=12 aid=0)
Jan 13 09:42:52 laptop kernel: [   91.746466] wlan0: AP denied association (code=12)
```

wpa_supplicant.log
==================
```
Trying to associate with REMOVED (SSID='Secure Network')
Associated with REMOVED
CTRL-EVENT-EAP-STARTED EAP authentication started
OpenSSL: pending error: error:0D06C03A:asn1 encoding routines:ASN1_D2I_EX_PRIMITIVE:nested asn1 error
OpenSSL: pending error: error:0D08303A:asn1 encoding routines:ASN1_TEMPLATE_NOEXP_D2I:nested asn1 error
OpenSSL: pending error: error:0D09A00D:asn1 encoding routines:d2i_PrivateKey:ASN1 lib
OpenSSL: pending error: error:140CA00D:SSL routines:SSL_use_PrivateKey_ASN1:ASN1 lib
OpenSSL: pending error: error:0D06C03A:asn1 encoding routines:ASN1_D2I_EX_PRIMITIVE:nested asn1 error
OpenSSL: pending error: error:0D08303A:asn1 encoding routines:ASN1_TEMPLATE_NOEXP_D2I:nested asn1 error
OpenSSL: pending error: error:0D09A00D:asn1 encoding routines:d2i_PrivateKey:ASN1 lib
OpenSSL: pending error: error:140CA00D:SSL routines:SSL_use_PrivateKey_ASN1:ASN1 lib
OpenSSL: pending error: error:0D06C03A:asn1 encoding routines:ASN1_D2I_EX_PRIMITIVE:nested asn1 error
OpenSSL: pending error: error:0D08303A:asn1 encoding routines:ASN1_TEMPLATE_NOEXP_D2I:nested asn1 error
OpenSSL: pending error: error:140CD00D:SSL routines:SSL_use_RSAPrivateKey_ASN1:ASN1 lib
CTRL-EVENT-EAP-METHOD EAP vendor 0 method 13 (TLS) selected
CTRL-EVENT-EAP-FAILURE EAP authentication failed
Authentication with REMOVED timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```

Are these OpenSSL errors related to not being able to authenticate to the Server, or can these errors be ignored? Any ideas?

Also, in my research it appears that people that have Wireless problems often install the linux-backports to see if this fixes the issue.  Is this recommended?  

Thanks!

---

### Post by changingstate on 2010-01-13
There's some very interesting info here : [https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/377227](https://bugs.launchpad.net/ubuntu/+source/wpasupplicant/+bug/377227)

This should give you a few ideas.

---

### Post by HarrisonFan on 2010-01-13
changingstate,

Thanks for the link.  I saw that before as well and I think I dismissed it thinking it might be a different issue as my brother is unable to connect at all whereas the bug report mentions frequent disconnects.  However, I suppose I could have him try out the ideas mentioned in the thread.

Thanks,
Zac

---

