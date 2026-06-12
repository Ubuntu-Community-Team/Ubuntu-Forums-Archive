---
title: "getting connected to wpa network"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by thejoker810 on 2009-01-06
hi this is my first post on ubuntu forums, or any forum really.
i just recently purchased a dell mini 9 and upgraded to ubuntu 8.10. ive never ran linux before but being a computer science major i thought it would be something get my feet wet in.
(and even tho im computer science major im still doing a lot of learning so please bare with me if it seems i dont know ****).

ive done a lot of looking around on forums and such to solve my problem but i cant figure out exactly what i need to do to get my networks working.

THE PROBLEM:

i can connect to my home wireless network just fine, it uses WEP, no problem there.

my problem (as you may guess) is that i can't get connected to my school's wireless network. it uses WPA Enterprise. Ive installed wpa_supplicant and made my own wpa_supplicant.conf file:

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
ssid='MizzouWireless'
proto=RSN
key_mgmt=WPA-EAP
pairwise=TKIP
eap=PEAP
identity='tigers\pawprint'
password='xxxxxxxx'
phase2='auth=MSCHAPV2'
}

ive also edited my /etc/network/interfaces file:
this is the original:

auto lo
iface lo inet loopback

this is after i edited it:

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
        wpa-driver wext
        wpa-conf /etc/wpa_supplicant.conf

after i edited the interfaces file, my home WEP network stopped working. i have not tested the changed interfaces file with the WPA Enterprise network because i have to drive over to it and i figured it cant be right if my WEP network stopped working.

p.s. WPA Enterprise network uses a certificate, i think this makes a difference

THANK YOU ANY HELP IS MUCH APPRECIATED. i like linux, and am committed to making this work

---

### Post by thejoker810 on 2009-01-08
any help?

---

