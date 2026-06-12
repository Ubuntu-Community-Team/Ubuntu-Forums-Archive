---
title: "no wireless connection (ipw+wpa+dapper-beta)"
date: 2006-04-20
forum: Networking &amp; Wireless
---

### Post by Inspector Hector on 2006-04-20
update: AAAAAAAAAAAAAAAHHHHHH! I'am such an idiot. the breezy forum is definitely the wrong forum for dapper related questions. What can i do? taking a rest, good night!

Hi There

I have a pesky problem with my ipw enhancend laptop and a router that accepts only wpa connections. Of course I invested some time before posting, but wether there is no well known solution or i'm just too stupid (which is absolut within possibility). 
[This]("http://www.ubuntuforums.org/showpost.php?p=130227&postcount=1") HowTo solved the problem for breezy (by just showing me, how to configure wpa_supplicant correctly).

However it is not working for my dapper beta installation. So i tried to install Network Manager manually (with dpkg, as there was no connection to use apt-get). Installation seemed to work fine, but starting nm-applet results in an error, and i was not able to figure out why.

So i returned to my old wpa_supplicant friend, to gather some information at least. 
Appending some stuff that could be usefull. I'd be happy about some hints. 
Damn iam so tired! 

wpa_supplicant.conf
```

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=2

network={
       ssid="your_network_name"
       scan_ssid=1
       proto=WPA
       key_mgmt=WPA-PSK
       #pairwise=TKIP
       psk="your_secret_key"
}

```

daemon.log
```
(...)
Apr 21 04:24:08 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr 21 04:24:12 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr 21 04:24:17 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr 21 04:24:23 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Apr 21 04:24:30 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr 21 04:24:39 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
Apr 21 04:24:41 localhost dhclient: No DHCPOFFERS received.
Apr 21 04:24:41 localhost dhclient: No working leases in persistent database - sleeping.
Apr 21 04:24:45 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
Apr 21 04:25:05 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr 21 04:25:13 localhost dhclient: No DHCPOFFERS received.
Apr 21 04:25:13 localhost dhclient: No working leases in persistent database - sleeping.
Apr 21 04:28:09 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Apr 21 04:28:13 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Apr 21 04:28:24 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Apr 21 04:28:32 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Apr 21 04:28:40 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Apr 21 04:28:46 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
Apr 21 04:28:48 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
Apr 21 04:29:00 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Apr 21 04:29:08 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
Apr 21 04:29:10 localhost dhclient: No DHCPOFFERS received.
Apr 21 04:29:10 localhost dhclient: No working leases in persistent database - sleeping.
Apr 21 04:29:16 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr 21 04:29:28 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
Apr 21 04:29:40 localhost dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
Apr 21 04:29:41 localhost dhclient: No DHCPOFFERS received.
Apr 21 04:29:41 localhost dhclient: No working leases in persistent database - sleeping.
```

kern.log
```
(...)
Apr 21 04:20:22 localhost kernel: [4299069.368000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 21 04:22:35 localhost kernel: [4299201.930000] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

C:\ sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -dd
```

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw' ctrl_interface 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=7):
     4b 75 62 72 69 63 6b                              Kubrick
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
pairwise: 0x8
PSK (ASCII passphrase) - hexdump_ascii(len=16): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Line 10: removed CCMP from group cipher list since it was not allowed for pairwise cipher
Priority group 0
   id=0 ssid='Kubrick'
Initializing interface (2) 'eth1'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_ipw_init is called
SIOCGIWRANGE: WE(compiled)=19 WE(source)=18 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
Own MAC address: 00:12:f0:2b:3f:81
wpa_driver_ipw_set_wpa: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_key: alg=none key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_key: alg=none key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Failed to set encryption.
wpa_driver_ipw_set_countermeasures: enabled=0
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
wpa_driver_ipw_set_drop_unencrypted: enabled=1
ioctl[IPW_IOCTL_WPA_SUPPLICANT]: Operation not supported
Setting scan request: 0 sec 100000 usec
Added interface eth1
Daemonize..
```

messages
```

(...)
Apr 21 04:07:23 localhost gconfd (root-8033): Die Adresse Â»xml:readonly:/etc/gconf/gconf.xml.defaultsÂ« wurde an der Position 2 zu einer nur lesbaren Konfigurationsquelle aufgelÃ¶st
Apr 21 04:07:23 localhost gconfd (root-8033): Die Adresse Â»xml:readonly:/var/lib/gconf/debian.defaultsÂ« wurde an der Position 3 zu einer nur lesbaren Konfigurationsquelle aufgelÃ¶st
Apr 21 04:07:23 localhost gconfd (root-8033): Die Adresse Â»xml:readonly:/var/lib/gconf/defaultsÂ« wurde an der Position 4 zu einer nur lesbaren Konfigurationsquelle aufgelÃ¶st
Apr 21 04:07:39 localhost kernel: [4298306.095000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 21 04:08:07 localhost kernel: [4298334.505000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
Apr 21 04:08:13 localhost kernel: [4298339.978000] cdrom: This disc doesn't have any tracks I recognize!
Apr 21 04:10:23 localhost gconfd (root-8033): Der GConf-Server wird nicht verwendet und daher beendet.
Apr 21 04:10:23 localhost gconfd (root-8033): Beenden
Apr 21 04:17:04 localhost kernel: [4298870.812000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 21 04:19:22 localhost gconfd (root-8738): (Version 2.14.0) wird gestartet, Prozesskennung 8738, Benutzer Â»rootÂ«
Apr 21 04:19:22 localhost gconfd (root-8738): Die Adresse Â»xml:readonly:/etc/gconf/gconf.xml.mandatoryÂ« wurde an der Position 0 zu einer nur lesbaren Konfigurationsquelle aufgelÃ¶st
Apr 21 04:19:22 localhost gconfd (root-8738): Die Adresse Â»xml:readwrite:/root/.gconfÂ« wurde an der Position 1 zu einer schreibbaren Konfigurationsquelle aufgelÃ¶st
Apr 21 04:19:22 localhost gconfd (root-8738): Die Adresse Â»xml:readonly:/etc/gconf/gconf.xml.defaultsÂ« wurde an der Position 2 zu einer nur lesbaren Konfigurationsquelle aufgelÃ¶st
Apr 21 04:19:22 localhost gconfd (root-8738): Die Adresse Â»xml:readonly:/var/lib/gconf/debian.defaultsÂ« wurde an der Position 3 zu einer nur lesbaren Konfigurationsquelle aufgelÃ¶st
Apr 21 04:19:22 localhost gconfd (root-8738): Die Adresse Â»xml:readonly:/var/lib/gconf/defaultsÂ« wurde an der Position 4 zu einer nur lesbaren Konfigurationsquelle aufgelÃ¶st
Apr 21 04:20:22 localhost gconfd (root-8738): Der GConf-Server wird nicht verwendet und daher beendet.
Apr 21 04:20:22 localhost gconfd (root-8738): Beenden
Apr 21 04:20:22 localhost kernel: [4299069.368000] ADDRCONF(NETDEV_UP): eth1: link is not ready
Apr 21 04:22:35 localhost kernel: [4299201.930000] ADDRCONF(NETDEV_UP): eth1: link is not ready
```

---

### Post by Inspector Hector on 2006-04-21
I solved it now, wasn't that hard. Sorry for the post.
And hey Breezy Users, Dapper is really cool at all. Give it a try

... still tired ...

---

### Post by garbage_ on 2006-04-22
[QUOTE=Inspector Hector]I solved it now, wasn't that hard. Sorry for the post.
And hey Breezy Users, Dapper is really cool at all. Give it a try

... still tired ...[/QUOTE]

So if it wasn't that hard - why don't you share it with us?
(so others won't get angry so late in the night ...)

---

### Post by Inspector Hector on 2006-04-22
I had to delete /etc/network/interfaces to let network manager work properly. Why wpa_supplicant didn't worked is still a mystery too me. I'am not a crack, but i think i tried a lot. Indeed it seems that my netgear router is also damaged somehow, network manager isn't able to locate him so i have to type in the SSID and the passphrase manually on every startup. The router will be replaced soon, so i may give it another try afterwards. At this time i'am just happy that i don't have to run a 10m wire trough the rooms.

---

