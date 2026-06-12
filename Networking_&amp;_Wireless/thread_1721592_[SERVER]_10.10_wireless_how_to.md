---
title: "[SERVER] 10.10 wireless how to"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by lospo on 2011-04-04
hi, i'd like to configure ubuntu server 10.10 as dwnload server, but i cannot find anything on how to configure my wireless connection with wpa encrypted password.

here is some info

login as: lospo
lospo@192.168.2.101's password:
Linux Chester 2.6.35-22-server #33-Ubuntu SMP Sun Sep 19 20:48:58 UTC 2010 x86_64 GNU/Linux
Ubuntu 10.10
```

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc
Last login: Mon Apr  4 23:45:33 2011 from 192.168.2.105
lospo@Chester:~$ uname -r
2.6.35-22-server
lospo@Chester:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

Thanks!

---

### Post by K_Light2003 on 2011-04-05
Hi lospo,

I'm no Linux/Ubuntu expert, but I have managed to get my server wireless at last. However for some reason it will no longer shut down cleanly. I'm using wpa as well.

Maybe my post [here]("http://ubuntuforums.org/showthread.php?t=1717127") will help a little.

---

### Post by lospo on 2011-04-07
ok, wifi card installed and configured, but...

can you take a look here?
[http://ubuntuforums.org/showthread.php?t=1722721](http://ubuntuforums.org/showthread.php?t=1722721)

---

### Post by K_Light2003 on 2011-04-11
> **lospo said:**
> ok, wifi card installed and configured, but...

can you take a look here?
[http://ubuntuforums.org/showthread.php?t=1722721](http://ubuntuforums.org/showthread.php?t=1722721)


I get exactly the same problem as you if I have both configured in  /etc/network/interfaces.
From what I have read, we will have to comment out the eth0 section and add it to the /etc/wpa_supplicant.conf as a second interface. [See here]("http://linux.die.net/man/5/wpa_supplicant.conf")

This is in /usr/share/doc/wpasupplicant/examples/ieee8021x.conf

```
# IEEE 802.1X with dynamic WEP keys using EAP-PEAP/MSCHAPv2

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="example 802.1x network"
        key_mgmt=IEEE8021X
        eap=PEAP
        phase2="auth=MSCHAPV2"
        identity="user name"
        password="password"
        ca_cert="/etc/cert/ca.pem"
}

  
```I think the #priority switch will load the networks in the order you want them. I have not set this up yet, due to my [shutdown issues when using wpasupplicant.]("http://ubuntuforums.org/showthread.php?t=1717127")

---

