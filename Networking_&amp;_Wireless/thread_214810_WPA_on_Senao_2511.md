---
title: "WPA on Senao 2511"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by ulukay on 2006-07-13
hello

i've tried to get a wpa connection with my senao 2511 

hostap_diag wlan0
Host AP driver diagnostics information for 'wlan0'

NICID: id=0x800c v1.0.0 (PRISM II (2.5) PCMCIA (SST parallel flash))
PRIID: id=0x0015 v1.1.0
STAID: id=0x001f v1.4.9 (station firmware)

lsmod: 
hostap_cs              64536  1
hostap                119428  1 hostap_cs

but i'm really stuck when configuring/starting the wpa_supplicant 

/etc/wpa_supplicant.conf
 network={
               ssid="lala"
               scan_ssid=1
               key_mgmt=WPA-PSK
               psk="vdmnjkvbfjd"
          }

i've tried to start it with different drivers, but no luck :(

root@note:~# wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dhostap
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
CTRL-EVENT-TERMINATING - signal 2 received
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
Failed to disable WPA in the driver.

root@note:~# wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -Dwext
ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 7 value 0x1 - CTRL-EVENT-TERMINATING - signal 2 received

root@note:~# wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
CTRL-EVENT-TERMINATING - signal 2 received
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
Failed to disable WPA in the driver.

(i have to terminate it with strg+c ...)
any advices?

---

### Post by tturrisi on 2006-07-13
What version is your Seneao 2511?  Cardbus or pcmcia?

---

### Post by ulukay on 2006-07-13
i think pcmcia

---

### Post by tturrisi on 2006-07-13
What version is your Seneao 2511?

---

### Post by yeehawjared on 2006-09-20
does the Seneao 2511 even support WPA?  I have the same card and thought that it was WEP/802.11b only.  Could be wrong.

---

