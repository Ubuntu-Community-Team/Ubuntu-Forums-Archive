---
title: "arggg WPA_supplicant problem"
date: 2006-01-04
forum: Networking &amp; Wireless
---

### Post by hantzis on 2006-01-04
when running WAP_supplicant in debug mode

sudo wpa_supplicant -B -ieth1 -c/etc/wpa_supplicant.conf -ddDmadwifi

I receive an "Operation not supported" message multiple times:

EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: Operation not supported
SIOCGIWRANGE: WE(compiled)=19 WE(source)=16 enc_capa=0x0
  capabilities: key_mgmt 0x0 enc 0x3
...
wpa_driver_madwifi_del_key: keyidx=0
ioctl[IEEE80211_IOCTL_DELKEY]: Operation not supported
wpa_driver_madwifi_del_key: keyidx=1
ioctl[IEEE80211_IOCTL_DELKEY]: Operation not supported
wpa_driver_madwifi_del_key: keyidx=2
ioctl[IEEE80211_IOCTL_DELKEY]: Operation not supported
wpa_driver_madwifi_del_key: keyidx=3
ioctl[IEEE80211_IOCTL_DELKEY]: Operation not supported


IF I run in debug mode:
sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -dd  

I believe the problem message is "failed to parse WPA IE from associate info"

Automatic auth_alg selection: 0x1
WPA: Failed to parse WPA IE from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 8 pairwise 24 key_mgmt 2
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK CCMP

AND ALSO RECEIVE THIS:
wpa_driver_hostap_associate
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported
Setting authentication timeout: 5 sec 0 usec

EAPOL: External notification - portControl=Auto
Wireless event: cmd=0x8b06 len=8
Wireless event: cmd=0x8b1a len=17
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:00:00:00:00:00 blacklist count incremented to 6


Any ideas? I've followed the install instructions very closely. Thanks.

---

### Post by Lambert on 2006-01-05
Not sure of the answer but this reply will also bump the thread.

> sudo wpa_supplicant -B -ieth1 -c/etc/wpa_supplicant.conf -ddDmadwifi
ioctl[PRISM2_IOCTL_HOSTAPD]: Operation not supported


Showing eth1 and later the prism2 line I take it you're using a device with a prism chipset. The end of the line you have -ddDmadwifi. The madwifi part specifies the madwifi driver which supports devices with the atheros chipset. You might need to specify the correct driver. 

Also the instructions you followed may be to generic for all drivers. Yours may need something more done to use it. I believe you need to install hostapd but not sure. 

Here is a link you might find more information from.

[http://hostap.epitest.fi/](http://hostap.epitest.fi/)

Be patient with this and sooner or later the right person will read and respond  with a better answer.

---

### Post by frank05 on 2006-04-11
It looks to me that you've got the wrong drivers specifed. First time I did this I just typed in what was in the instructions and left the "madwifi" when i should have put "ndiswrapper" :rolleyes: . I subsequently got the same "operation not supported message". 

Once I corrected this there was no error message, only problem now is it cannot detect my AP (which is why I'm back on the forums!).

You can get a list of supported driver options by starting wpa_supplicant with the help option (it's either -h, --help or -help, sorry im on windoz right now :( ).

---

### Post by tungsai on 2007-12-05
the command is indeed "wpa_supplicant -h". I know because I am getting the SAME error! haha.

---

### Post by kevdog on 2007-12-05
What chipset are you running??  How did you install the drivers??  For ndiswrapper with wpasupplicant, the driver should be wext

---

### Post by tungsai on 2007-12-06
Hi... Sorry if I'm hijacking the thread... but I am having the same problem, perhaps the answer will help the other guy. My output:

I probably need to point out that I CAN connect when using the GUI; and my wireless card DOES auto-connect to wireless networks when I'm wandering around. The problem is, here on Purdue Campus, to connect to the real wireless network, I have to provide specific settings & username/password. I want my laptop to auto-connect to THAT network, on login. The local linux user's group has some wiki instructions, but... they're sort of hard to read, and don't address some problems that I'm having. So, I'm having to start from ground zero and learn what wpa_supplicant is, etc. They give three methods to set up Linux to connect to this network. the first, using the GUI, works. the second is to use /etc/networking/interfaces entries; the third is using the wpa_supplicant as a daemon or something. Unfortunately their instructions are for Edgy & Feisty, not Gutsy which is what I'm using. and also, you know, drivers are different for every laptop, and who knows what hardware anybody is using. Oh well, at least I'm learning something.

Without further ado, here's my dump from that command. to me, I can see the actual hardware drivers, but from what I understand, the wpa drivers are different???



```
lshw -C network
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:d3:xx:xx:xx
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI duplex=full firmware=0.5-1 latency=0 link=yes module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 02
       serial: 00:13:02:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=128.211.176.104 latency=0 link=yes module=ipw3945 multicast=yes wireless=IEEE 802.11g

```

---

