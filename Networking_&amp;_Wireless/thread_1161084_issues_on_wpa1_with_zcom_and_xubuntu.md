---
title: "issues on wpa1 with zcom and xubuntu"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by boehser on 2009-05-16
hi dear ubuntu members

last days i downloaded xubuntu 9.04 and installed, looks great ! so today i tried to get my wlan running. my hardware:
pcmcia card, zcom XI 325 hp+ with psim 2.5 chipset (so hostap ?) like this [one]("http://http://cgi.ebay.de/Zcom-Zcomax-Z-Com-XI-325HP-300mW-Linux-Wardriving_W0QQitemZ370201916674QQcmdZViewItemQQptZDE_Computer_Peripherie_Netzwerk?hash=item370201916674&_trksid=p3286.c0.m14&_trkparms=72%3A1229%7C66%3A2%7C65%3A12%7C39%3A1%7C240%3A1318%7C301%3A1%7C293%3A1%7C294%3A50") 
ibm thinkpad t23
wpa1

my essid: WLAN-8C7F52

i ran this card on this laptop under debian lenny (it is still running) with this interfaces list

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-ssid WLAN-8C7F52 
wpa-psk mypassphrase in plaintext

#iface wlan0 inet dhcp
#wireless_mode managed


my /etc/network/interfaces:


>                                         [LEFT]auto lo[/LEFT]
    [LEFT]iface lo inet loopback[/LEFT]
    [LEFT]auto eth1[/LEFT]
    [LEFT]iface eth1 inet static [/LEFT]
    [LEFT]address 192.168.168.40[/LEFT]
    [LEFT]gateway 192.168.168.230[/LEFT]
    [LEFT]dns-nameservers 192.168.168.230 [/LEFT]
    [LEFT]netmask 255.255.255.0[/LEFT]
    [LEFT]wpa-driver wext[/LEFT]
    [LEFT]wpa-ssid WLAN-8C7F52[/LEFT]
    [LEFT]wpa-ap-scan 1[/LEFT]
    [LEFT]wpa-proto WPA[/LEFT]
    [LEFT]wpa-pairwise TKIP[/LEFT]
    [LEFT]wpa-group TKIP[/LEFT]
    [LEFT]wpa-key-mgmt WPA-PSK[/LEFT]
    [LEFT]wpa-psk my passphrase crypted via tutorial
[/LEFT]
               
  

if i try to get eth1 (under debian lenny it is wlan0) running following happensifup: > couldn't read interfaces file "/etc/network/interfaces"

what can i do to get this running ? :(:(

please help me :)


[FONT=Arial]****[/FONT]

---

