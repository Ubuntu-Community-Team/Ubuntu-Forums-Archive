---
title: "WPA enterprise"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by Nonno Bassotto on 2009-11-16
Hello, I'm trying to connect to a WPA enterprise at my institute. I was given 3 pem certificates which look like
```

myname.pem
instituteca.pem
myname.key.pem

```
and the key password.

I try to connect through network manager. When I select a WPA/WPA2 enterprise connection with TLS I'm asked for:
```

Identity
User certificate
CA certificate
Private key
Private key password

```

The problem is that when I supply all this information, the Connect button remains inactive. That is, I don't even get any error trying to connect, I simply cannot push the confirm button. What can I try?

By the way, I'd want to use Network manager if possible: I'm already connecting to other networks using it, so I'd rather not have it disabled.

---

### Post by AGFApan on 2009-11-25
I'm not sure why, but Networkmanager 0.7.1-8 seems to be the last version that supports WPA Enterprise, or the EAP/TLS version anyway.

---

### Post by Nonno Bassotto on 2009-11-25
Is that based on your opinion or do you have a reference for that?

---

### Post by AGFApan on 2009-11-26
It is based on my own experience after upgrading to Fedora 12, and following the NetworkManager mailing list. 

[http://mail.gnome.org/archives/networkmanager-list/2009-November/msg00301.html](http://mail.gnome.org/archives/networkmanager-list/2009-November/msg00301.html)


Edit: If you are feeling adventurous, you could try the  Wicd network manager. It is available in Ubuntu's Universe repository. Myself, I've had no luck getting the RPM and source to work with Fedora,

---

### Post by Nonno Bassotto on 2009-11-27
Thank you for the reference. I've tried WICD, but it was not able to obtain an address from DCHP. I also tried to connect manually (i.e. on the command line), without any useful results.

---

### Post by AGFApan on 2009-11-27
Unfortunately, I've also had no luck trying to connect old school with WPA_supplicant. I've never been good with WPA Supplicant, so it is very posible I'm doing something wrong, but it looks like it may be a problem with OpenSSL. If that is the case there may not be a way around it.

For any who may understand it, here is what I'm getting from the client:

```

Trying to associate with 00:14:bf:b9:b4:3d (SSID='UNIVAC' freq=2462 MHz)
Associated with 00:14:bf:b9:b4:3d
CTRL-EVENT-EAP-STARTED EAP authentication started
OpenSSL: pending error: error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
OpenSSL: pending error: error:140C800D:SSL routines:SSL_use_certificate_file:ASN1 lib
OpenSSL: pending error: error:0D08303A:asn1 encoding routines:ASN1_TEMPLATE_NOEXP_D2I:nested asn1 error
OpenSSL: pending error: error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
OpenSSL: pending error: error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
OpenSSL: pending error: error:04093004:rsa routines:OLD_RSA_PRIV_DECODE:RSA lib
OpenSSL: pending error: error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
OpenSSL: pending error: error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
OpenSSL: pending error: error:140CB00D:SSL routines:SSL_use_PrivateKey_file:ASN1 lib
CTRL-EVENT-EAP-METHOD EAP vendor 0 method 13 (TLS) selected
OpenSSL: tls_connection_handshake - Failed to read possible Application Data error:00000000:lib(0):func(0):reason(0)
CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
WPA: Key negotiation completed with 00:14:bf:b9:b4:3d [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:14:bf:b9:b4:3d completed (auth) [id=0 id_str=]
^CCTRL-EVENT-TERMINATING - signal 2 received

```

And the Radius server:

```
rad_recv: Access-Request packet from host 192.168.1.1 port 3414, id=0, length=143
	User-Name = "vaio_laptop"
	NAS-IP-Address = 192.168.1.1
	Called-Station-Id = "0014bfb9b43d"
	Calling-Station-Id = "00166f075918"
	NAS-Identifier = "0014bfb9b43d"
	NAS-Port = 6
	Framed-MTU = 1400
	State = 0x679f3e1a6299330c6ba8cc01c6b2731f
	NAS-Port-Type = Wireless-802.11
	EAP-Message = 0x020600060d00
	Message-Authenticator = 0xc4d801b62e15445cda0f88e650507896
+- entering group authorize {...}
++[preprocess] returns ok
++[chap] returns noop
++[mschap] returns noop
[suffix] No '@' in User-Name = "vaio_laptop", looking up realm NULL
[suffix] No such realm "NULL"
++[suffix] returns noop
[eap] EAP packet type response id 6 length 6
[eap] No EAP Start, assuming it's an on-going EAP conversation
++[eap] returns updated
++[unix] returns notfound
[files] users: Matched entry vaio_laptop at line 50
++[files] returns ok
++[expiration] returns noop
++[logintime] returns noop
++[pap] returns noop
Found Auth-Type = EAP
+- entering group authenticate {...}
[eap] Request found, released from the list
[eap] EAP/tls
[eap] processing type tls
[tls] Authenticate
[tls] processing EAP-TLS
[tls] Received TLS ACK
[tls] ACK handshake is finished
[tls] eaptls_verify returned 3 
[tls] eaptls_process returned 3 
[tls] Adding user data to cached session
[eap] Freeing handler
++[eap] returns ok
+- entering group post-auth {...}
++[exec] returns noop
Sending Access-Accept of id 0 to 192.168.1.1 port 3414
	MS-MPPE-Recv-Key = 0xfcc3dc51b37484faeeea83c1ffcadcd7520da190dc75209599d42b2569a65a14
	MS-MPPE-Send-Key = 0x499c6b7d723e67c2891b1447b194c4ac6927dff4ce1afe0e623c818ac4a93c23
	EAP-Message = 0x03060004
	Message-Authenticator = 0x00000000000000000000000000000000
	User-Name = "vaio_laptop"
Finished request 20.
Going to the next request
Waking up in 4.9 seconds.
Cleaning up request 14 ID 0 with timestamp +65464
Cleaning up request 15 ID 0 with timestamp +65464
Cleaning up request 16 ID 0 with timestamp +65464
Cleaning up request 17 ID 0 with timestamp +65464
Cleaning up request 18 ID 0 with timestamp +65464
Cleaning up request 19 ID 0 with timestamp +65464
Cleaning up request 20 ID 0 with timestamp +65464
Ready to process requests.

```

And my WPA Supplicant configuration file:

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=wheel
network={
	ssid="UNIVAC"
	scan_ssid=1
	key_mgmt=WPA-EAP
	pairwise=CCMP TKIP
      	group=CCMP TKIP
      	eap=TLS
	identity="vaio_laptop"
	ca_cert="/etc/UNIVAC/cacert.pem"
	client_cert="/etc/UNIVAC/vaio_laptop_cert.pem"
	private_key="/etc/UNIVAC/vaio_laptop_key.pem"
	private_key_passwd="xxxxxxxx"
}
```

---

### Post by AGFApan on 2009-11-28
Please disregard the above. After some more work at it, I was able to get WPA Supplicant to connect to my WPA enterprise network. NetworkManager, however is still not working. 

Anyway, it apears that connecting to a WPA Enterprise network can still be done, but not in a user friendly way.

---

### Post by Nonno Bassotto on 2009-12-01
Do you have any more details on what you did to be able to connect?

---

### Post by AGFApan on 2009-12-01
Unfortunately, it is an ugly way to connect. But it does seem to work consistently with Fedora 12. However, I have not tried it on my Kubuntu laptop yet. File locations for Ubuntu may be different and sudo will likely have to appended to when using the command line.

Edit /etc/wpa_supplicant/wpa_supplicant.conf

Mine looks like this: 


```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=wheel
network={
	ssid="UNIVAC"
	scan_ssid=1
	key_mgmt=WPA-EAP
	pairwise=CCMP TKIP
      	group=CCMP TKIP
      	eap=TLS
	identity="vaio_laptop"
	ca_cert="/home/Jeff/certs/cacert.pem"
	client_cert="/home/Jeff/certs/vaio_laptop_cert.pem"
	private_key="/home/Jeff/certs/vaio_laptop_key.pem"
	private_key_passwd="xxxxxxx"
}
```

Replace the ssid, identity, keys and password with your own and save.


The commands to get it running are:

service NetworkManager stop
service network stop
service network start
chkconfig wpa_supplicant
wpa_supplicant -B -i eth1 -c/etc/wpa_supplicant/wpa_supplicant.conf
dhclient eth1

I'm not sure all the commands are necessary, but it works for me. 

As for the second last command (wpa_supplicant -B -i eth1 -c/etc/wpa_supplicant/wpa_supplicant.conf) replace eth1 with your device name, and you may want to leave off the -B option the first time, which starts it as a daemon. That way all the messages will be visible if there is an error. However, dhclient eth1 will need to be run in another terminal window, or you will have a connection only with no IP, gateway, or DNS server. 

Anyway, good luck!

---

### Post by Nonno Bassotto on 2009-12-02
Thank you!!! It finally works. :D
These are more or less the steps I already tried, but I didn't stop network manager before connecting. So finally I have a connection

---

### Post by AGFApan on 2009-12-02
Glad it worked! It is nice to actually be helpful on one of these forums.:)

You may already know. but should the connection drop, the commands:

service wpa_supplicant stop
dhclient -r
wpa_supplicant -B -i eth1 -c/etc/wpa_supplicant/wpa_supplicant.conf
dhclient eht1

Should bring it back up.


Anyway, hopefully NetworkManger gets fixed before I have to write all this in a script.

---

