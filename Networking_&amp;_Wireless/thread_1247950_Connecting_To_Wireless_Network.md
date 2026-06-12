---
title: "Connecting To Wireless Network"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by pratiks19 on 2009-08-23
I want to connect to my university wireless network, without using the NetworkManager.

The Following are the configurations for wpa_supplicant.
(Please help me with these for ubuntu 9.04.):

1)Network Authentication = WPA2

2)Data Encryption = AES

3)Authentication Type = Protected EAP (PEAP)

4)When connecting validate server certificate:
  Connect to: aaa.bbb.edu (not the real address)

5)Note: I've got the required certificates

6)Authentication Method = EAP-MSCHAP v2

7)Also, I will have to use my university username and password to login to the network.

I've tried configuring with reference to this link:
[http://ubuntuforums.org/showthread.php?t=571188]("http://ubuntuforums.org/showthread.php?t=571188")
But it does not connect.

my current wpa config:
```

ctrl_interface=/var/run/wpa_supplicant
ap_scan=1

network={
        ssid="net"

        scan_ssid=1
        key_mgmt=WPA-EAP
        eap=PEAP
        identity="abc"
        password="xxxxxxxx"
        phase1="peaplabel=0"
        phase2="auth=MSCHAPV2"

        ca_cert="/etc/ssl/certs/entrust_ssl_ca.pem"
}

```


Also the following:
```

wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -ddd
```

gives a "stack smashing" error.
I have got wpa_supplicant version 0.6.9 installed.

---

### Post by kevdog on 2009-08-23
Dont know much about peap -- sorry

---

### Post by RedSingularity on 2009-08-23
What about something similar to Network Manager?  Say.....WICD?

---

### Post by pratiks19 on 2009-08-24
Will try WICD....
but any method for connecting using the terminal ?

---

### Post by pratiks19 on 2009-08-26
WiCD worked beautifully. 

I guess there is a problem with wpa supplicant in jaunty.
anyways, thank you folks...

---

### Post by RedSingularity on 2009-08-26
No problem.  Glad it worked out:)

---

### Post by josephmc on 2009-11-20
I'm in the same boat. Trying to connect to a university wireless with the same settings. I am usig WICD. **what settings did you use?** 

There is no AES option for me in wicd when I open the dropdown.

---

