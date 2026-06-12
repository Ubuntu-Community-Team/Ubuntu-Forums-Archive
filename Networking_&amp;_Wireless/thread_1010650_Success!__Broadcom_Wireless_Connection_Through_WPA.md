---
title: "Success!  Broadcom Wireless Connection Through WPA2"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by Favux on 2008-12-14
**Note:  Bug reported fixed!** for NM 0.8 in Karmic per Tony Espy (9-7-09):  [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/377643](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/377643)  They will try to make NM 0.8 available for Jaunty via the Network Manager PPA.  No mention of Intrepid.

This solution was suggested by flatline (and Geof) at:
```
   [http://ubuntuforums.org/showthread.php?t=1009180]("http://ubuntuforums.org/showthread.php?t=1009180")
Then flatline cross-posted on this thread:
  [http://ubuntuforums.org/showthread.php?t=963379&page=10]("http://ubuntuforums.org/showthread.php?t=963379&page=10")
post #97 and I answered starting post #100.

```
Broadcom BCM 4328 a/b/g/draft-n Wi-Fi Adaptor connected through WPA2 TKIP to a Linksys Wireless-N Router WRT160N using Broadcom proprietary "wl" driver (in Hardware Drivers:  Broadcom STA wireless driver).

For the first time since updating to Intrepid I have wireless!

**I'm am one of those experiencing the password box filled with hex after a connection attempt through NetworkManager using WPA2-TKIP encryption. Then over and over again NetworkManager asks for a password and reconnection.  I had decided this was a wpa_supplicant certificate issue (and was hoping for a network manager update that would fix it).  But it is not.** 

I went to gconf editor Applications>System Tools>Configuration Editor. Then I went to system>networking>connections>1>802-11-wireless-security.

There I saw:
```
group       [wep40,wep104,tkip,ccmp]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise    [tkip,ccmp]
proto       [wpa,rsn]
```
I edited it to look like:
```
group       [tkip]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise    [tkip]
proto       [wpa]
```
And tried to connect, and it did! I rebooted and tried to connect again. And it did.  I guessed at the parameters, knowing what I had set up in my router.

I right clicked on the NetworkManager applet and went to Edit Connections. I then deleted a duplicate entry and checked the box for automatically connect, since the connection now worked again. I rebooted and the connection failed. Again the password box filled with hex. Again the asking for a password and reconnection. I went back to Gconf editor and found:
```
group       [wep40,wep104,tkip,ccmp]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise    [tkip,ccmp]
proto       [wpa,rsn]
```
I again started editing, and after correcting the second line it automatically connected and so I was left with:
Code:
```
group       [tkip]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise    [tkip]
proto       [wpa,rsn]
```
I rebooted and it connected automatically and flawlessly.

**Think about it for a minute.** Just going into Edit Connections and checking the auto-connect box was enough for NetworkManager to re-add the extraneous, and some clearly erroneous, entries.

So as long as I don't use NetworkManager to edit connections I'm good to go? I suppose I could experiment further and find out just which of the extraneous entries are the erroneous ones.

Inspired by the Launchpad bug #78181:  [https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/78181]("https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/78181")  (Pay particular attention to the posts by manu and Loye Young towards the bottom. Also see bug link by Loye Young:  [https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/192258]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/192258")  (Note:  Avahi-autoipd & avahi-etc. along with ifupdown were installed on my system.  But dhcdbd (available) and dhclient (not available) were not installed on my system.))  I decided to see if I could narrow down the "erroneous" entries. "Erroneous" at least in my case. Thanks to manu my prime suspect was CCMP.

I right clicked on the NetworkManager applet and went to Edit Connections. I then selected edit of my wireless connection. I did not change anything, just clicked on OK. I turned off wireless in NM and then turned it back on and the connection failed. Again the password box filled with hex. Again the asking for a password and reconnection.

I went to gconf editor Applications>System Tools>Configuration Editor. Then I went to system>networking>connections>1>802-11-wireless-security. There I found:
```
group       [wep40,wep104,tkip,ccmp]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise    [tkip,ccmp]
proto       [wpa,rsn]
```
Looks familiar, hmm? So I went to the first line and removed ccmp. Lo and behold the keys mutated into:
```
auth-alg    <no value>
group       [wep40,wep104,tkip]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise    [tkip,ccmp]
proto       [wpa,rsn]
wep-tx-key-idx  <no value>
```
and wireless connection was made! So I rebooted. Again wireless connected automatically. I went to gconf editor again and found:
```
group       [wep40,wep104,tkip]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise    [tkip,ccmp]
proto       [wpa,rsn]

```
So deleting ccmp from the group key seems to be the minimum necessary step, at least for me.

In Gconf editor if you right click on a key there are several options. Among them are "set as default" and "set as mandatory". If one of these two options was selected for the keys that NetworkManager is messing up would this prevent it? In other words could one or the other of these settings block NetworkManager from altering the key? If so which one?

David-emm on this thread:  [http://ubuntuforums.org/showthread.php?t=1018168]("http://ubuntuforums.org/showthread.php?t=1018168")  tried setting the keys in Gconf to "default" and "mandatory". Unfortunately it was a no go. Intrepid/NM objected to his attempts.  At this point bab1 joined us and pointed to:  [http://www.arachnoid.com/linux/NetworkManager/index.html]("http://www.arachnoid.com/linux/NetworkManager/index.html")  At this URL Paul Lutus goes through an explanation of NM's architecture and rationale (distribution agnostic).  bab1 then explains that NM is not very flexible at this point and it's algorithm (creating values "on the fly" from HAL and dBus inputs) doesn't accept all user input.

The upshot, for us, of all this is that this workaround using Gconf editor is the best we're going to do for now. We will have to wait for another version of NM that is more flexible and accepts more user input. Maybe inputs through dBus editing? We may be waiting a while.

**Addendum 1**:
For those of you who's issues look more like timing issues, check out this bug report:
   [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/263963]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/263963")
At the bottom, Alexander Sack points you to the latest NM PPA packages (0.7 final) that address some driver timing issues at:
   [https://edge.launchpad.net/~network-manager/+archive]("https://edge.launchpad.net/~network-manager/+archive")

**Addendum 2**:
I feel compelled to report other strange behavior I have observed.  This may bear on the fundamental problem of networkmanager and be related to the bug reports above.  After the system is up a while I can no longer grep useful information from dmesg.  Instead dmesg in a terminal yields:
```
[31195.841730] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ffff8800a44c8840
[31197.992106] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ffff8800a44c8840
[31199.937654] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ffff8800a44c8840
[31202.087989] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ffff8800a44c8840
[31204.135831] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ffff8800a44c8840
[31206.286186] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ffff8800a44c8840
[31208.231779] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ffff8800a44c8840
[31210.382003] TKIP: RX tkey->key_idx=1 frame keyidx=2 priv=ffff8800a44c8840

```
going on and on and filling terminal.  Looking in System Log shows the same thing filling both kern.log and syslog.  You get to watch the output into them real time.  A treat.  No idea what's causing this behavior.  Wireless is working fine.

**Addendum 3**:
As juanhm correctly points out there are additional conditions I neglected to mention:
> When the password is stored in the keyring and network-manager is authorized to access it, the connection works flawlessly after rebooting.
juanhm's bug link:
   [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/263963]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/263963")
Bug closed with status changed to:  Won't Fix.  New bug report opened.  The link:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/377643](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/377643)

Note:  Vista says it's a Broadcom 4321AG a/b/g/draft-n Wi-Fi Adaptor.

---

### Post by saywot on 2008-12-14
> I went to gconf editor Applications>System Tools>Configuration Editor. Then I went to system>networking>connections>1>802-11-wireless-security.

this would be super to try to get this wireless networking working

except

when I run gconf-editor
and scroll to >system ..
there is no 'networking' to edit

---

### Post by saywot on 2008-12-14
OK here's what I can see in the configuration editor

System
- dns_sd
- gstreamer
- http_proxy
- pkcs11
- proxy
- smb
- storage

so unless it's because I am used to other distros that allow me to login as 'root' and I'm locked into looking at the options available as 'user' I'm at a loss to see how I can edit this file.

I did run gconf-editor as 'sudo' but it doesn't provide any more options other than those I have above

---

### Post by saywot on 2008-12-14
right, I give up !
where does this file actually live ?

If I can find it I can edit it

I was hoping for a better outcome since last having a run with dapper drake, but Intrepid isn't doing me any 'straight out of the box' favours

---

### Post by Favux on 2008-12-14
Hi saywot,

I'm sorry, I had the entry in gconf editor just like flatline did.  I don't know why you don't have it.  As you can see I'm no Gconf editor expert, that's why I'm asking for help on the set as default or mandatory key options.

> OK here's what I can see in the configuration editor

System
- dns_sd
- gstreamer
- http_proxy
- pkcs11
- proxy
- smb
- storage
I have networking right between http_proxy and pkcs11.

You are running Ubuntu 8.10?  Have you installed a firewall?  Do you have the Broadcom proprietary driver installed in System>Administration>Hardware Drivers?  It's called Broadcom STA wireless driver.  I don't know if Ndiswrapper would be different, but it's worth eliminating a variable to find out.

In Synaptic Package Manager when you do a search on gconf-editor is the box next too it greened, ie installed?  You have wireless turned on?  It is detecting the signal from your wireless router?  You tried to connect to the router through NetworkManager 0.7?  You got the kind of message I talked about in the first post about password box filled with hex and asking for password, etc.?

That's all I can think of off the top of my head.  Good luck.  I'm so happy to finally again be connected wirelessly, I hope you can join me.

---

### Post by theozzlives on 2008-12-14
> **Favux said:**
> Do you have the Broadcom proprietary driver installed in System>Administration>Hardware Drivers?  It's called Broadcom STA wireless driver.  I don't know if Ndiswrapper would be different, but it's worth eliminating a variable to find out.


I only needed ndiswrapper before 8.10 on my Brodcomm 43xx card. 8.10 solved all my wireless problems. I do have the w|, however.

---

### Post by Favux on 2008-12-14
Hi theozzlives,

When the Broadcom proprietary driver came out, that's when I was finally able to connect wirelessly in Hardy.  I didn't bother with ndiswrapper because I saw "wl" was in pre-release and I just waited for it.  It took longer than I had hoped for though.

When I upgraded to 8.10 Intrepid, that's when I lost wireless.  I spent a lot of time and effort and got nowhere, including installing Wicd etc.  Like I said in my first post I finally decided it was a wpa_supplicant certificate issue and decided to wait for a NetworkManager update that would fix it.

So I was surprised this worked.  I think it shows it was a NetworkManager 0.7 problem all along.  I saw in a Launchpad bug report where one of the Ubuntu developers had miscommunicated with another one and they had accidently merged two different versions of NetworkManager.  I probably should have paid more attention to that report.

---

### Post by saywot on 2008-12-14
> You are running Ubuntu 8.10? Have you installed a firewall? Do you have the Broadcom proprietary driver installed in System>Administration>Hardware Drivers? It's called Broadcom STA wireless driver. I don't know if Ndiswrapper would be different, but it's worth eliminating a variable to find out.

In Synaptic Package Manager when you do a search on gconf-editor is the box next too it greened, ie installed? You have wireless turned on? It is detecting the signal from your wireless router? You tried to connect to the router through NetworkManager 0.7? You got the kind of message I talked about in the first post about password box filled with hex and asking for password, etc.?

- Yes it is Intrepid Ibex
- No I don't run a local (software) firewall
- Yes I have activated the Broadcom Drivers
- Yes the 'light' on the laptop that indicates wireless is on, is on
- I have only run gconf-edotor from a terminal as the SU so since I get it to open I am assuming that it's installed
- I am using whatever version of NetworkManager came installed on the 8.10 disc (the installation is a day old)
- I'm pretty sure that when you enter a 'human-readable' passkey it is translated into a 'machine-readable' hex key otherwise the passwords would be as easy to crack as lower levels of wireless security

---

### Post by saywot on 2008-12-14
I might ask the network manager (the person, not the programme) if they'll accept tkip **AND** AES cerification

---

### Post by Favux on 2008-12-14
Hi saywot,

> - I have only run gconf-edotor from a terminal as the SU so since I get it to open I am assuming that it's installed
Why?  When it is clear from context that both flatline and I are talking about using it through the Ubuntu gui?  Are you running a server install?
> - I'm pretty sure that when you enter a 'human-readable' passkey it is translated into a 'machine-readable' hex key otherwise the passwords would be as easy to crack as lower levels of wireless security
Sure, when transmitted.  Not when authorized user looking at it on gui.  Then should be blanked out like standard password, and the # of blanked out digits shoould be the same as the password's.  I don't think you're talking about the same bug as I am, because you should have instantly recognized the description.  There are multiple posts on the forum reporting the same bug.  The bug I've seen posted involves WPA2 and often WPA2-TKIP

I'm thinking there isn't a "networking" in gconf because you haven't really established an attempt to connect to the router that's been recognized by networkmanager.  Either through networkmanager's edit connections or network configuration.

---

### Post by saywot on 2008-12-14
> In Synaptic Package Manager when you do a search on gconf-editor is the box next too it greened,

yes it is 'greened'
 
- Here we go again

I hope this *isn't* annoying you as much as it is me Favux

---

### Post by saywot on 2008-12-14
this may be a daft question
- but
wpa-supplicant is installed by default isn't it ?

I don't have it in my list of 'services' 

could this be a problem ?

---

### Post by Favux on 2008-12-14
Hi saywot,

Yes wpa_supplicant is suppose to be installed.  But I have seen posts by folks who didn't have it so it isn't a daft question.  I believe you may have solved the mystery.  Networkmanager hasn't recognized an attempt at connection because you may not have wpa_supplicant installed.  Load it through Synaptics and then see where you are.

> By the way, saywot, you need to run gconf-editor as user.

I don't actually know how to use gconf-editor, but I found that if you run it as root, you won't see the network configs.
This is from James_xxx in the other thread.

---

### Post by saywot on 2008-12-14
it's installed :(

editing the keys didn't work

the card uses a BCM4309 chip-set, the 'Hardware Driver' (System->Administration->HardwareDrivers) is telling me I have the Broadcom B43 wireless driver installed
So now I'm guessing that Ubuntu has picked the wrong driver for me at installation

Can I de-activate that and get another ?

---

### Post by Favux on 2008-12-14
Sure.

---

### Post by saywot on 2008-12-14
From [http://bcm43xx.berlios.de/?go=devices]("http://bcm43xx.berlios.de/?go=devices")

> 4309  	PCI/Cardbus  	Unstable (802.11a unsupported, work in progress)

it should work on b/g though

---

### Post by Favux on 2008-12-14
Hi saywot,

That's a shame.  I hope you get n support soon.

> it should work on b/g though
Could this be why you didn't get wpa_supplicant?  Ubuntu, because of the driver, didn't think your card supported WPA encryption?

---

### Post by Ayuthia on 2008-12-14
> **saywot said:**
> From [http://bcm43xx.berlios.de/?go=devices]("http://bcm43xx.berlios.de/?go=devices")



it should work on b/g though

You are using the b43/b43legacy module instead of the Broadcom STA (wl)module.  Your card is not supported by the Broadcom STA module so you will not be able to use that one.  If you want to see if you can use WPA with your card, you can try:
```
sudo iwlist auth
```and it should show WPA as an option if it can use it.

EDIT: The b43 driver does have the options listed in gconf-editor.  I did not try changing it though, but I also have not had problems connecting with WPA2 through Intrepid.

---

### Post by saywot on 2008-12-15
```
$ sudo iwlist auth

wlan0  Authentication capabilities:

WPA
WPA2
CIPHER-TKIP
CIPHER-CCMP
Current Authentication algorithm:
open
shared key
$_
```

so the card, though useless, is capable of WPA

I've tried just about everything in this, and everything that is linked to from this thread and am becoming convinced that Ubuntu 8.10 is *_**far**_* less fun than Fedora (which this was intended to replace) Whoever said that this was some sort of 'human' distribution and that it will work straight out of the box needs to be pelted with livestock - 2 days now and no network connection !

to recap, I have a Broadcom bcm4309 card, I have followed the instructions to install the b43-fw cutter AND the appropriate firmware that was in ... [http://ubuntuforums.org/showpost.php?p=6077792&postcount=72]("http://ubuntuforums.org/showpost.php?p=6077792&postcount=72")
  
 I have re-booted umpteen times and have edited the 'network' section using gconf-editor

and nothing, zilch,
I deleted all wireless connections, re-created my connection at least 6 times and It seems to be trying to create the connection and then asks me for the pass-key again. and again, and again until I get the 'network disconnected' message

---

### Post by Ayuthia on 2008-12-15
> **saywot said:**
> ```
$ sudo iwlist auth

wlan0  Authentication capabilities:

WPA
WPA2
CIPHER-TKIP
CIPHER-CCMP
Current Authentication algorithm:
open
shared key
$_
```

so the card, though useless, is capable of WPA

I've tried just about everything in this, and everything that is linked to from this thread and am becoming convinced that Ubuntu 8.10 is *_**far**_* less fun than Fedora (which this was intended to replace) Whoever said that this was some sort of 'human' distribution and that it will work straight out of the box needs to be pelted with livestock - 2 days now and no network connection !

to recap, I have a Broadcom bcm4309 card, I have followed the instructions to install the b43-fw cutter AND the appropriate firmware that was in ... [http://ubuntuforums.org/showpost.php?p=6077792&postcount=72]("http://ubuntuforums.org/showpost.php?p=6077792&postcount=72")
  
 I have re-booted umpteen times and have edited the 'network' section using gconf-editor

and nothing, zilch,
I deleted all wireless connections, re-created mt connection at least 6 times zand It seems to be trying to create the connection and then asks me for the pass-key again. and again, and again until I get the 'network disconnected' message

You  might try this link:
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)
It will show you how to connect via wpa_supplicant in the Terminal.  It might help.

---

### Post by saywot on 2008-12-15
Right - back to it (day 3)

that guide says check that the correct driver/firmware is applied for the right card so ...
> 
~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:08:4f:6d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.29a latency=0 module=tg3 multicast=yes
  *-network
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:7d:23:28:11
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

as far as I can tell from the above output I have confirmed that I have a Broadcom BCM4309 with what seems to be the only driver available -the 'b43' applied

There was no wpa_supplicant.conf file so, I created one from the guide linked to above

> ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="ESSID_IN_QUOTES"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="ASCII PSK Password in Quotes"
        pairwise=TKIP
        group=TKIP
}

so now I thought it time to issue the commands to manually start the wireless connection and - drum roll please ...

> ~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:0b:7d:23:28:11
Sending on   LPF/wlan0/00:0b:7d:23:28:11
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

- stop the drum-rolling, it flopped like a fish on a boat's deck !

---

### Post by Ayuthia on 2008-12-15
Can you post the results of:
```
sudo iwlist scan
```
Also, can you post the results of:
```
sudo wpa_supplicant -D wext -i wlan0 -c/etc/wpa_supplicant.conf -dd 
```

---

### Post by saywot on 2008-12-15
> ~$ sudo iwlist scan
lo  Interface doesn't support scanning

eth0 Interface doesn't support scanning

wmaster0 Interface doesn't support scanning

wlan0 No scan results

so the wireless card isn't scanning
> 
~$ sudo wpa_supplicant -D wext -i wlan0 -c/etc/wpa_supplicant.conf -dd
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ap_scan=1
ctrl_interface='var/run/wpa_supplicant'
Line: 4 - start of a new network block
ssid - hexdump_ascii(len=6):
     4d 65 4d 65 4d 65                                 MeMeMe          
scan_ssid=0 (0x0)
proto: 0x1
key_mgmt: 0x2
PSK (ASCII passphrase) - hexdump_ascii(len=9): [REMOVED]
pairwise: 0x8
group: 0x8
PSK (from passphrase) - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='My ESSID'
Initializing interface (2) 'wlan0'
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:0b:7d:23:28:11
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
mkdir[ctrl_interface]: No such file or directory
Failed to initialize control interface 'var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

Failed to add interface wlan0
State: DISCONNECTED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6


some thing is a miss

---

### Post by saywot on 2008-12-15
> Failed to initialize control interface 'var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

Huh ?


that wouldn't be the wpa_supplicant file I just created would it ??

---

### Post by Ayuthia on 2008-12-15
You have two things not going quite right.  You are not getting a response from dhclient because you are not getting any scan results.

The other part is that wpa_supplicant is already running, but that might just be because you started it last time.  If you do:
```
ps -ef|grep wpa
```
You should see the wpa_supplicant process running, you can kill the process:
```
sudo killall wpa_supplicant
```and that will end the process.

Can you post the results of:
```
ls /lib/firmware
lsmod|grep b43
```
Have you been able to see any wireless sites at all?

---

### Post by saywot on 2008-12-15
>  Have you been able to see any wireless sites at all?

nothing, nowhere, not a cracker, not a bean

> ~$ ls /lib/firmware
2.6.27-7-generic                    dvb-usb-umt-010-02.fw
2.6.27-9-generic                    dvb-usb-vp702x-01.fw
acx                                 dvb-usb-vp7045-01.fw
aic94xx-seq.fw                      dvb-usb-wt220u-02.fw
atmel_at76c502_3com.bin             dvb-usb-wt220u-fc03.fw
atmel_at76c502_3com-wpa.bin         dvb-usb-wt220u-zl0353-01.fw
atmel_at76c502.bin                  ipw2100-1.3.fw
atmel_at76c502d.bin                 ipw2100-1.3-i.fw
atmel_at76c502d-wpa.bin             ipw2100-1.3-p.fw
atmel_at76c502e.bin                 ipw2200-bss.fw
atmel_at76c502e-wpa.bin             ipw2200-ibss.fw
atmel_at76c502-wpa.bin              ipw2200-sniffer.fw
atmel_at76c503-i3861.bin            isl3877
atmel_at76c503-i3863.bin            isl3886
atmel_at76c503-rfmd-0.90.2-140.bin  isl3887usb_bare
atmel_at76c503-rfmd-acc.bin         isl3890
atmel_at76c503-rfmd.bin             isl3890usb
atmel_at76c504_2958-wpa.bin         iwlwifi-3945-1.ucode
atmel_at76c504a_2958-wpa.bin        iwlwifi-4965-1.ucode
atmel_at76c504.bin                  iwlwifi-4965-2.ucode
atmel_at76c504c-wpa.bin             iwlwifi-5000-1.ucode
atmel_at76c505a-rfmd2958.bin        ql2100_fw.bin
atmel_at76c505-rfmd2958.bin         ql2200_fw.bin
atmel_at76c505-rfmd.bin             ql2300_fw.bin
atmel_at76c506.bin                  ql2322_fw.bin
atmel_at76c506-wpa.bin              ql2400_fw.bin
b43                                 rt2561.bin
b43legacy                           rt2561s.bin
bcm2033-fw.bin                      rt2661.bin
bcm2033-md.bin                      rt73.bin
dvb-fe-or51132-qam.fw               v4l-cx23418-apu.fw
dvb-fe-or51132-vsb.fw               v4l-cx23418-cpu.fw
dvb-fe-or51211.fw                   v4l-cx23418-dig.fw
dvb-fe-tda10046.fw                  v4l-cx2341x-dec.fw
dvb-ttpci-01.fw                     v4l-cx2341x-enc.fw
dvb-usb-avertv-a800-02.fw           v4l-cx2341x-init.mpg
dvb-usb-bluebird-01.fw              v4l-cx25840.fw
dvb-usb-dib0700-1.10.fw             v4l-pvrusb2-24xxx-01.fw
dvb-usb-dibusb-5.0.0.11.fw          v4l-pvrusb2-29xxx-01.fw
dvb-usb-dibusb-6.0.0.8.fw           zd1201-ap.fw
dvb-usb-dtt200u-01.fw               zd1201.fw
dvb-usb-tvwalkert.fw                zd1211

---

### Post by saywot on 2008-12-15
and finally 

> ~$ lsmod | grep b43
b43           131356  0
rfkill         17176  3 rfkill_input, b43
mac80211      216820  1 b43
led_class      12164  1 b43
input_polldev  11912  1 b43
ssb            40580  1 b43

---

### Post by Ayuthia on 2008-12-15
The 4309 card can either be a b43 or b43legacy based on the MAC core revision.  Of course, I forgot what that means or how to find out.  We can just try it the easy way:
```
sudo modprobe -r b43 b43legacy ssb
sudo modprobe b43legacy
sudo iwlist scan
```
If it is able to see wireless sites, then we know that something odd happened with the system selecting the incorrect module.  This will only work for this session.

EDIT:To find out the the MAC core revision, type in the Terminal:
```
dmesg|grep ssb
```
You will find that it will return something like:
```
ssb: SPROM revision X detected
```

---

### Post by saywot on 2008-12-15
```
 sudo modprobe -r b43 b43legacy ssb
sudo modprobe b43legacy
sudo iwlist scan
```

> wlan0  No scan results

---

### Post by saywot on 2008-12-15
> **Ayuthia said:**
> The 4309 card can either be a b43 or b43legacy based on the MAC core revision. 

EDIT:To find out the the MAC core revision, type in the Terminal:
```
dmesg|grep ssb
```
You will find that it will return something like:
```
ssb: SPROM revision X detected
```

[B][     3.717636] ssb: Sonics Silicon Backplane found on PCI device 0000:03:03.0
[  1989.612044] ssb: Sonics Silicon Backplane found on PCI device 0000:03:03.0[/B]

---

### Post by Ayuthia on 2008-12-15
Sorry about that.  I just realized that I am currently in Gentoo and I compiled the b43 kernel module with debug enabled so I was able to see more info.

The only thing that I can think of at this point is to try ndiswrapper.  I am not for sure why you are not getting any wireless sites.  The info that you have provided looks ok but for some reason your card doesn't see the wireless sites.

---

### Post by saywot on 2008-12-15
O God !

- start all over again :(

---

### Post by saywot on 2008-12-15
> **Ayuthia said:**
> 
The only thing that I can think of at this point is to try ndiswrapper.  I am not for sure why you are not getting any wireless sites.  The info that you have provided looks ok but for some reason your card doesn't see the wireless sites.

I think maybe Ubuntu wasn't the distro for me after all, however buggy Fedora 10 was on this laptop at least it would connect me to the 'world' wirelessly :confused:

---

### Post by juanhm on 2008-12-17
Favux, you're a genious!

I've been messing with this problem since I upgraded to Ubuntu 8.10 and after following your suggestions my wireless connection is working again.

There is an open bug in Launchpad related to this problem and Intel cards (bug #263963) so I'm going to append a link to this thread. 

After some tries I agree with you that it seems is network-manager that overwrites again and again the registry keys you mention when it needs to ask for a password. On the other hand, when the password is stored in the keyring and network-manager is authorized to access it, the connection works flawlessly after rebooting.

---

### Post by Favux on 2008-12-17
Great jaunhm,

I'm glad you're back to wireless!  Good idea to link to the launchpad bug.  Why didn't I think of that?

> After some tries I agree with you that it seems is network-manager that overwrites again and again the registry keys you mention when it needs to ask for a password. On the other hand, when the password is stored in the keyring and network-manager is authorized to access it, the connection works flawlessly after rebooting.
Right, and like I mentioned, if you edit with networkmanager, be prepared to go to gconf editor again.

---

### Post by Favux on 2008-12-22
Hi everyone,

Inspired by the Launchpad bug #78181:
   [https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/78181]("https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/78181")
Pay particular attention to the posts by manu and Loye Young towards the bottom.  Also see bug link by Loye Young:
   [https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/192258]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/192258")
I decided to see if I could narrow down the "erroneous" entries.  "Erroneous" at least in my case.  Thanks to manu my prime suspect was CCMP.

I right clicked on the NetworkManager applet and went to Edit Connections. I then selected edit of my wireless connection.  I did not change anything, just clicked on OK.  I turned off wireless in NM and then turned it back on and the connection failed. Again the password box filled with hex. Again the asking for a password and reconnection.

I went to gconf editor Applications>System Tools>Configuration Editor. Then I went to system>networking>connections>1>802-11-wireless-security.  There I found:
```
group       [wep40,wep104,tkip,ccmp]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise    [tkip,ccmp]
proto       [wpa,rsn]

```

Looks familiar, hmm?  So I went to the first line and removed ccmp.  Low and behold the keys mutated into:
```
auth-alg    <no value>
group       [wep40,wep104,tkip]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise    [tkip,ccmp]
proto       [wpa,rsn]
wep-tx-key-idx  <no value>

```
and wireless connection was made!  So I rebooted.  Again wireless connected automatically.  I went to gconf editor again and found:
```
group       [wep40,wep104,tkip]
key-mgmt    wpa-psk
name        802-11-wireless-security
pairwise    [tkip,ccmp]
proto       [wpa,rsn]

```
So deleting ccmp from the group key seems to be the minimum necessary step.  If the connection stays stable I'll add this to the "demo" later.

Kind of interesting, isn't it?

---

### Post by rmcd on 2008-12-22
I'm one of the people who doesn't see a networking entry in gconf-editor (I run it from the command line, it's not in my Applications menu). 

Has anyone resolved the question of how to access wireless networking properties without gconf-editor, or alternatively how to get networking to show up in gconf-editor?

Thanks.

Bob

---

### Post by Favux on 2008-12-22
Hi rmcd,
  
The networking entry and the keys in it appear to be local.  You won't see them if you "sudo".  Apparently you can only see them if you are logged in the gui and in "/home/username".  If you learn more/or differently please post.

Use System>Preferences>Main Menu to add it to your menu.  Mine ended up in Applications>System Tools>Configuration Editor.

---

### Post by Favux on 2008-12-24
I thought I would go ahead and quote Loye Young from the bug report above:

[https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/78181]("https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/78181")

> avahi-autoipd, dhcdbd, and network-manager don't play well with wpa_supplicant. If I uninstall avahi-autoipd, dhcdbd, and network-manager and use instead network-config and wlassistant, I don't have problems.

The basic problem is that wpa_supplicant's architechture expects to works with ifupdown and dhclient, not dhcdbd and avahi. (See the first sentence of /usr/share/doc/wpasupplicant/README.Debian. ) The default install seems to work fine as long as you aren't using WPA encryption and you don't use static IP addresses.

I should note that avahi-autoipd & avahi-etc. along with ifupdown were installed on my system. But dhcdbd (available) and dhclient (not available) were not installed on my system.

---

### Post by loyeyoung on 2008-12-30
At IYCC, we've made several changes to the networking stack to make it "just work".

[LIST][*] Migrated to using wicd as the front-end to handle networking.
[*] Added "conflicts" dependencies to the iycc-blacklist package, which prevents the installation of: avahi-autoipd, avahi-daemon, avahi-utils, dhcdbd, libavahi-core5, libnss-mdns, and network-manager.
[*] Added ifmetric to resolve 
[*] Changed udev rules to require wireless network cards use wlan* as device name. (work in progress)
[/LIST]

See our repository at [http://archive.iycc.net](http://archive.iycc.net).

Happy Trails,

Loye Young
Isaac & Young Computer Company
Laredo, Texas
[http://start.iycc.net](http://start.iycc.net)

---

### Post by Favux on 2008-12-30
Hi loyeyoung,

Thanks for the useful post.  So technically there can be a working stack without issues.

Unfortunately, aside from wicd, which I've already tried, the rest of your stack looks beyond my capabilities.  Unless I chose to invest a lot of time.  Your repository, thanks for the link, might make it doable but I'm on AMD-64 architecture.

This gconf workaround, while being a total kludge, works for me.  I know its worked for others.  Meanwhile I'm hoping Ubuntu sorts the issues out for Jaunty, and backports them to Intrepid.

---

### Post by HowHardCanItBe on 2009-01-02
Wow!!!!

I've been trying to get my ubuntu (intrepid) box onto my WPA network for close to a week. I just stumbled onto this post tonight and tried it. Wow!!!! 

I'm admittedly a newby - not to Unix (as a user) but to Linux. I decided to put **ubuntu** on a Dell PIII that I got from the dumpster at work. I had a Dynex DX-WGPUSB (BestBuy cheapo) dongle laying around and figured that was my connection to the internet - it works flawlessly with Windoze, why shouldn't it work with the first Linux distro that I've actually successfully installed on a computer of any kind? For a week I've been able to see practically everybody in my neighborhood and connect to anybody that wasn't secure, but I haven't been able to connect to my own WPA-protected home wireless network. I could have gone out and bought wireless card X.. but Linux (to me) is all about the journey and making hardware that Windows has rendered useless valuable again. 

Well, tonight I'm on my own network!!

Gotta thank ya. Seriously! THANK YOU for this post!

---

### Post by Favux on 2009-01-03
Hi HowHardCanItBe,

Good! Thanks for the thanks.  Nice to have wireless, isn't it?

In the meanwhile learned a bunch of new information on david-emm's thread:

[http://ubuntuforums.org/showthread.php?t=1018168]("http://ubuntuforums.org/showthread.php?t=1018168")

We've been messing around with NM.  He was brave enough to try setting the keys in Gconf to "default" and "mandatory".  Unfortunately it was a no go.  Intrepid/NM objected strenuously to his attempts.

I speculated that if we could find NM's master "default" file maybe we could edit it.  But maybe NM was generating the values "on the fly" from other scripts.  At this point bab1 (20 yr.s experience Solaris/Linux administrator) joined us and pointed to:

[http://www.arachnoid.com/linux/NetworkManager/index.html]("http://www.arachnoid.com/linux/NetworkManager/index.html")

At this URL Paul Lutus goes through an explanation of NM's architecture and rationale (distribution agnostic).  He creates Ruby scripts to feed NM through Gconf his network's state and discovers to his amazement that NM ignores all of it.

bab1 then explains that NM is not very flexible at this point and it's algorithm (creating values "on the fly" from HAL and dBus inputs) doesn't accept user input.

The upshot, for us, of all this is that the "demo" of the workaround using Gconf editor at the start of this thread is the best we're going to do.  We're going to have to wait for another version of NM that is more flexible and accepts user inputs.  Maybe inputs through dBus editing?  We may be waiting a while.

But, for those of you who's issues look more like timing issues, check out this bug report:

[https://bugs.launchpad.net/ubuntu/+s...er/+bug/263963]("https://bugs.launchpad.net/ubuntu/+s...er/+bug/263963")

At the bottom, Alexander Sack (a NM developer?) points you to the latest NM PPA packages (0.7 final) that address some driver timing issues at:

[https://edge.launchpad.net/~network-manager/+archive]("https://edge.launchpad.net/~network-manager/+archive")

Now how do I add all this stuff to the "demo"?  It is getting kind of unwieldy.

---

### Post by Coombabah on 2009-01-07
Thanks Favux.
This workaround fixed wpa enterprise with tkip via Network-manager 0.7 on my eeePC with an RT2860 wireless card.
Previously wpa enterprise with tkip would only work in earlier versions of network-manager like the version in Hardy.

---

### Post by HDave on 2009-01-07
Thank you very much for this fix.  I have been unable to connect to a WPA network at work now for over a year.  :(

I did have to invent my own sequence of gconf-edits in order to get it to work in my case.  I learned this:

1) The minute you touch the connection in NM, it adds the ccmp garbage.
2) If you go into the NM and manually try to connect, it adds the ccmp garbage, so auto-connect is the only way to go here.

...and most importantly...

3) If it prompts you for a password, it adds the ccmp garbage.

In my case, the SSID of my network was hidden, so that could have made a difference, but here is the sequence of events that worked for me.

a) delete the network in NM
b) re-add the network in NM, being EXTREMELY careful to uncheck the auto-connect box and type in the correct password.
c) go into gconf-editor and do the following:
    i.    find the connection (mine was #10)
    ii.   delete the ccmp garbage from the security folder
    iii.  add the BOOLEAN key "autoconnect" to the "connection" folder
    iv.   set autoconnect to true

As soon as you do step c-iv, NM will connect you and you can see if it works.  If something goes wrong, you HAVE to start all over.  You can't fix it without having NM trash your connection every time you go to connect.  At least I couldn't.

---

### Post by juanhm on 2009-01-08
Hi HDave.

A little correction: in my case, I´m using CCMP as the encryption algorithm in the AP and that´s the value I have to use in then "group" and "pairwase" keys for the network to connect.

What I need to remove from gconf are the references to "wep40" and "wep104", so you can´t talk about the "CCMP" garbage as it depends on the algorithm used by for AP.

Not a very useful POST, just for establishing the real situation.

---

### Post by hasinasi on 2009-01-08
Any ideas yet, how to implement this in KDE (kubuntu)? 
I know that nm-applet (network-manager-gnome) can be used instead of knetworkmanager in kubuntu. But would I also have gconf-editor in this case? 

--hasi

---

### Post by HDave on 2009-01-08
> **juanhm said:**
> Hi HDave.

A little correction: in my case, I´m using CCMP as the encryption algorithm in the AP and that´s the value I have to use in then "group" and "pairwase" keys for the network to connect.

What I need to remove from gconf are the references to "wep40" and "wep104", so you can´t talk about the "CCMP" garbage as it depends on the algorithm used by for AP.

Not a very useful POST, just for establishing the real situation.

You are of course correct.  One man's garbage is another man's treasure.  In my case, my company was using TKIP instead of CCMP, but that was just for me.

---

### Post by HDave on 2009-01-08
> **hasinasi said:**
> But would I also have gconf-editor in this case?

I don't know squat about KDE, but the "g" in gconf-manager stands for "Gnome" and I am sure that knetwork-manager doesn't use the gnome standard for editing config keys.

You need to find out where knetwork-manager stores its info.

---

### Post by Favux on 2009-01-08
Hi everybody,

jaunhm, while you make a valid, important and correct point, surely HDave is entitled to blow off a little steam.  A whole year without being able to connect!


Hi hasinasi,

You're the first KDE user to post.  Since I have never used KDE I do not know the KDE equivalent of gconf editor.  If search or google search doesn't help, why not start a thread on the appropriate forum and ask?  I would appreciate hearing from you if you learn anything.  Sorry I can't be more helpful.  Also to be honest I thought Knetworkmanager was essentially the same as networkmanager, just renamed.

---

### Post by juanhm on 2009-01-09
Hi hasinasi.

Even using KDE you could try to install gconf-editor by APT (if it isn´t installed by default) and see if network-manager uses gconf keys to store its configuration.

I guess that being a Gnome application, network-manager could still rely in gconf despite the type of session you select when login (KDE session in your case)

Give it a try.

---

### Post by Aearenda on 2009-01-09
You should be able to tell just by looking for a .gconf/system/networking/ folder in your home directory, no need to install anything! The settings are all stored as XML.

---

### Post by hasinasi on 2009-01-17
All my WPA2 connection problems are now solved. I followed a workaround posted by Dan Bracey: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272185/comments/174]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272185/comments/174").

This basically fixes it by using some newer packages from jaunty. Since I am running kubuntu, I now have to use nm-applet instead of knetworkmanager, which is no problem. (I also disabled autostart for knetworkmanager, and I enabled autostart for nm-applet at the beginning of every session. It is totally seamless.)

I hope this helps. I am not sure everyone here suffers from the same bug. Let me know if you need more details to get it to work. It may also be interesting to look at the entire bug listed on launchpad: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272185]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272185")

---

### Post by Favux on 2009-01-17
Hi hasinasi,

Thank you very much for posting the Jaunty ppa's for NM.  Glad they worked for you.  The bug on the bug report doesn't appear to be the same as what I had.  Since wireless is working great for me right now I think I'll hold off.  Meanwhile I'll keep reading the bug report (about 1/3 through).

Do you know what version of NM the ppa's give?  The link on the "demo" (first post) gives Alexander Sack's 0.7 final.  This is a newer version?

I think I'll wait to I see how NM is doing in final beta or a couple weeks into Jaunty release before I upgrade.

---

### Post by hasinasi on 2009-01-18
Favux, 
after applying the workaround I have the following  versions: network-manager, network-manager-gnome, libnm-glib0, and libnm-util1 are 0.7-0ubuntu1~nm1~intrepid1. The version of libnm-util0 is 0.7~~svn20081018t105859-0ubuntu2.
Hope this helps. 
--hasi

---

### Post by beyboo on 2009-01-27
Favux, I must really thank you for the brilliant post where you have gathered thought from all over. Personally I am happy with Intel 3954 wireless card, but someone I know uses a Dell with one of the Broadcom wireless cards which dint work. He was a newbie to Ubuntu and this was the last hour that he was going to try out things (after a whole week of looking up) and I found ur thread. It just added a new Ubuntu user !!!

---

### Post by Favux on 2009-01-27
Hi beyboo,

That's a great story.  It would have been tragic to loose a new Ubuntu user over this silly wireless thing.  Thank you for tracking down the "demo" for him!

Hi hasinasi,

Thank you (I would have used forums thanks if it was available) for posting those updated NM version numbers.

---

### Post by kevdog on 2009-01-27
Ive got a beef with that launchpad bug stating wrong information.  Although NWM communicates with wpa_supplicant through a library file, it doesn't do it directly through the wpa_supplicant binary.  The wpa_supplicant package does not need to be exclusively installed on any ubuntu machine in order to get WPA access using network manager.

---

### Post by Favux on 2009-01-27
Hi kevdog,

OK, good to know.  Are you going to take that up on the lauchpad bug's page?

---

### Post by kevdog on 2009-01-27
There wasn't a place to post the comment that I'm aware of, so I thought I would just complain (and educate others) here! :)

---

### Post by Rich99 on 2009-03-08
I have the exact same problems as everyone else here (<rant> it seems incredible to me that anyone could claim linux is ready for the average home user when wireless is completely broken for 4 months & no-one appears interested in fixing it!! </rant>) but I can't get your solution to work.  The clearest instructions were from HDave on page 5 (#45) so I tried to follow those.

My router uses AES, so in gconf I deleted everything except CCMP in the group & pairwise folders.  After adding the 'autoconnect' entry, NM showed it was trying to connect, but it still failed & gave the long hex string as the password.  Any ideas what I might have done wrong?  Using an intel 3945 wireless card, and a fresh install of Intrepid.

*edit* I should say that I'm usinhg WPA-Personal here, but all symptoms & problems are identical. I put in the password in NM, then after a while the prompt comes back but this time the password hash is there instead of the password.  In syslog I see it attempting to authenticate, then 'AP denied association'.

---

### Post by saywot on 2009-03-08
Rich99 
I think that the reason the password isn't the same string of letters/numbers is that it has been translated from human-readable to machine-readable.
But if you're sure that everything is correct and have, maybe, right-clicked the NM icon and created a new connection (which is the same as the old connection) selected the correct security protocol and then got the "spinning, trying to connect, spinning, trying to connect" activity indicator with no success, you may need to experiment with the security your router is demanding like swith it over to WPA2-PSK.

I had a broadcom chip and eventually after applying the correct firmware for the card and re-booting I got a connection almost immediately

---

### Post by Favux on 2009-03-08
Hi Rich99,

I'm really not sure.  Perhaps removing everything is the problem?  Why don't you try just removing tkip and see what happens.

Regarding your rant:
> I have the exact same problems as everyone else here (<rant> it seems incredible to me that anyone could claim linux is ready for the average home user when wireless is completely broken for 4 months & no-one appears interested in fixing it!! </rant>) but I can't get your solution to work. The clearest instructions were from HDave on page 5 (#45) so I tried to follow those.
It might give you a chuckle to go to the bug link from juanhm at the bottom of the first post.  In an effort to be efficient and spare the reader they left only the first eighty posts visible and then the next 26, now 27 since Rich posted, posts are hidden.  Of course the hidden posts include the link to this work around by jaunhm and a number of posts by users who said the work around worked for them!

Also you could try installing the PPA's (if it's a newer version of NM than you have) from Alexander Sack (on the first post) and see if that helps.  And of course where Alexander posted the link is on the hidden posts section too!

---

### Post by Rich99 on 2009-03-09
Thanks for all the suggestions - my router is already the latest firmware & is currently set to WPA2-PSK using AES.  After playing for a couple of hours & fighting with NM's attempts to reset those gconf keys, I've simply settled on using wpa_supplicant & editing /etc/network/interfaces for now.  In the conf file for wpa_supplicant I just used ccmp in the group & pairwise statments, and that worked perfectly.  It's the same settings as I tried for the gconf keys, but it didn't appear to work there. Wpa_supplicant is nowhere near as convenient as NM for when you're roaming, but it's better than wireless not working atall.

---

### Post by kevdog on 2009-03-09
Rich99

Install WICD instead of NetworkManager.  This program uses the exact same methods as the wpa_supplicant/dhclient command line options (although it is slightly more complex), offers a GUI, and makes it convenient to browse and connect to networks.

---

### Post by Rich99 on 2009-03-09
> **kevdog said:**
> Rich99

Install WICD instead of NetworkManager.  This program uses the exact same methods as the wpa_supplicant/dhclient command line options (although it is slightly more complex), offers a GUI, and makes it convenient to browse and connect to networks.

Looks like it might do the trick, I remember seeing some other posts suggesting this but I didn't really pay too much attention. They even have a repository for ubuntu.  Thanks!

---

### Post by smalldog on 2009-05-03
> **rmcd said:**
> I'm one of the people who doesn't see a networking entry in gconf-editor (I run it from the command line, it's not in my Applications menu). 

Has anyone resolved the question of how to access wireless networking properties without gconf-editor, or alternatively how to get networking to show up in gconf-editor?

Thanks.

Bob

I was asking this question myself. But I have to admit that I was overlook the preceding message. The gconf-editor content is changing according to the user's profile. Therefore, you must using the desired user account to run the gconf-editor instead of "root" user. Good luck

---

### Post by rvgsd on 2009-05-13
Hi All,
I am using wpa2 security in my network and unable to connect. (Ubuntu 9.04, BCM 4306, Using drivers installed through b43-fwcutter by Ubuntu ). The wireless connects to unsecured networks immediately.

I tried doing the steps given on the first page.
In my **gconf**, in the **system>networking>connections>1>802-11-wireless-security**, there are only two entries:
```

key-mgmt    wpa-psk 
name            802-11-wireless-security

```

I tried adding the other entries, but nothing works. The Network Manager keeps displaying the password window with the Hex-Key and quits after like three times. 
**Help!!!!!!!!**

Thanks.
rvgsd.

---

### Post by Favux on 2009-05-14
Hi rvgsd,

Not sure what's going on.  You have WPA2 enabled on your router obviously.  Do you have wpa_supplicant installed?

In NM when you edit Wireless what do you see?  Does it allow you to set security etc.?  Also check Seahorse (Applications>Accessories>Passwords and Encryption Keys).  Check on Passwords and see if your wireless Password is in there.  After you've done all that then go back to gconf and see if the other entries are present.

---

### Post by rvgsd on 2009-05-15
Hello Favux,

wpa_supplicant is installed.

In NM I can edit the connection to which I am trying to connect to, and set the security etc. 

In the 'Passwords and Encryption Keys' the password which I enter to connect is present. And the entries in gcong also seem fine. 

So far nothing works!!! The connection used to work fine in Ubuntu 8.04 and 8.10, with the exact same settings. 

Any help is appreciated!

Thanks.

---

### Post by Favux on 2009-05-15
Hi rvgsd,

I'd go ahead and remove wpa_supplicant reboot and then reinstall it and reboot.  Is your SSID on?  NM can have trouble if it's hidden.

That's about the end of my advice.  The demo is about a "trick" using gconf to get around some problems with NM's algorithms.  You need a wireless guru, there are several out there who maintain threads.  Like kevdog above and wiemanO1.

Sorry.  Good luck!  Hang in there, it took me at least four weeks to find this fix.  Tethered by an ethernet cable the whole time.

---

### Post by tad1073 on 2009-05-15
do you know if this will work with 9.04?

I tried and had to add:
```

group       [tkip]
pairwise    [tkip]
proto       [wpa]

```

those three keys.

by the way, my wireless card uses ath9k driver from madwifi

here is my post about my prblems
[http://ubuntuforums.org/showthread.php?t=1139001&page=3](http://ubuntuforums.org/showthread.php?t=1139001&page=3)

---

### Post by Favux on 2009-05-15
Hi tad1073,

I'm not sure.  I don't think anyone with Jaunty has posted a success yet.  NM hasn't changed that much I don't think.  It's gone from the unofficial 0.70 they were using in Intrepid to the official final 0.70.  Or maybe they updated it a little since the alphas.

But the rest of the infrastructure has changed some.  For example Gnome is updated.

So if you have the same problem I had with NM constantly asking you for the password and returning hex in the password box and when you use gconf editor you find similar entries to the ones I (and the other posters) found it should work.

---

### Post by tad1073 on 2009-05-15
```

NM constantly asking you for the password and returning hex in the password box

```

Yes

I think it is my router though. I had a D-Link router but it died. The new router is a Linksys WRT160n which is g+n.

I have it running in mixed mode

---

### Post by Favux on 2009-05-15
Hi tad1073,

I'm sure you noticed we have the same/similar router.  I don't think it's in mixed mode though, just n.  Different wifi chipset though.  In my case the NM algorithm was choking on ccmp in the group key.  Once I removed that with gconf editor the Broadcom chipset was able to connect to the Linksys router.  So I never tried adding keys, just subtracting entries from them.

---

### Post by tad1073 on 2009-05-16
I guess it is my card then. AR5008 driver for a d-link dwa-552 wireless b+g+n

---

### Post by AJack10600 on 2009-06-23
Hm... this is pretty much how my problem looks.... but can it be a router problem when it works fine with my Windows PC ? 
 
When using NM in Ubuntu 9.04  get exactly what you subscribe, I get promted again and again for a Key for the WLan and when I go to see key I see massive Hex code in there..  where does that come from ? What and who generates it? 
 
It clearly prevents any connection to the Router...  this is silly especially since this problem seems to be pretty old ... if it's been around since release 8 ...

---

### Post by Favux on 2009-06-23
Hi AJack10600,

I assume the hex hash is coming from the Message Digest algorithm 5 (MD5) of the password.  I think MD5 is in common use in the distributions.

Does your router have hidden ESSID like mine did?  I found a link to some new patches for Broadcom to handle hidden ESSID the other day.  I haven't looked at them at all.  Ayuthia found them and describes them on posts #7 and #9 here:  [http://ubuntuforums.org/showthread.php?t=1187656](http://ubuntuforums.org/showthread.php?t=1187656)  Maybe they will be of some use to you.

Good luck!

---

### Post by ewanaunf6 on 2011-01-13
> **Favux said:**
> **Note: Bug reported fixed!** for NM 0.8 in Karmic per Tony Espy (9-7-09): [https://bugs.launchpad.net/ubuntu/+s...er/+bug/377643](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/377643) They will try to make NM 0.8 available for Jaunty via the Network Manager PPA. No mention of Intrepid.This solution was suggested by flatline (and Geof) at:```
http://ubuntuforums.org/showthread.php?t=1009180[/url]Then flatline cross-posted on this thread:  [http://ubuntuforums.org/showthread.php?t=963379&page=10](http://ubuntuforums.org/showthread.php?t=963379&page=10)post #97 and I answered starting post #100.
```Broadcom BCM 4328 a/b/g/draft-n Wi-Fi Adaptor connected through WPA2 TKIP to a Linksys Wireless-N Router WRT160N using Broadcom proprietary "wl" driver (in Hardware Drivers: Broadcom STA wireless driver).For the first time since updating to Intrepid I have wireless!**I'm am one of those experiencing the password box filled with hex after a connection attempt through NetworkManager using WPA2-TKIP encryption. Then over and over again NetworkManager asks for a password and reconnection. I had decided this was a wpa_supplicant certificate issue (and was hoping for a network manager update that would fix it). But it is not.** I went to gconf editor Applications>System Tools>Configuration Editor. Then I went to system>networking>connections>1>802-11-wireless-security.There I saw:```
I edited it to look like:[code]And tried to connect, and it did! I rebooted and tried to connect again. And it did. I guessed at the parameters, knowing what I had set up in my router.I right clicked on the NetworkManager applet and went to Edit Connections. I then deleted a duplicate entry and checked the box for automatically connect, since the connection now worked again. I rebooted and the connection failed. Again the password box filled with hex. Again the asking for a password and reconnection. I went back to Gconf editor and found:[code]I again started editing, and after correcting the second line it automatically connected and so I was left with:Code:[code]I rebooted and it connected automatically and flawlessly.**Think about it for a minute.** Just going into Edit Connections and checking the auto-connect box was enough for NetworkManager to re-add the extraneous, and some clearly erroneous, entries.So as long as I don't use NetworkManager to edit connections I'm good to go? I suppose I could experiment further and find out just which of the extraneous entries are the erroneous ones.Inspired by the Launchpad bug #78181: [https://bugs.launchpad.net/ubuntu/+s...ger/+bug/78181](https://bugs.launchpad.net/ubuntu/+source/knetworkmanager/+bug/78181) (Pay particular attention to the posts by manu and Loye Young towards the bottom. Also see bug link by Loye Young: [https://bugs.launchpad.net/ubuntu/+s...ta/+bug/192258](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/192258) (Note: Avahi-autoipd & avahi-etc. along with ifupdown were installed on my system. But dhcdbd (available) and dhclient (not available) were not installed on my system.)) I decided to see if I could narrow down the "erroneous" entries. "Erroneous" at least in my case. Thanks to manu my prime suspect was CCMP.I right clicked on the NetworkManager applet and went to Edit Connections. I then selected edit of my wireless connection. I did not change anything, just clicked on OK. I turned off wireless in NM and then turned it back on and the connection failed. Again the password box filled with hex. Again the asking for a password and reconnection.I went to gconf editor Applications>System Tools>Configuration Editor. Then I went to system>networking>connections>1>802-11-wireless-security. There I found:[code]Looks familiar, hmm? So I went to the first line and removed ccmp. Lo and behold the keys mutated into:[code]group       [wep40,wep104,tkip]key-mgmt    wpa-pskname        802-11-wireless-securitypairwise    [tkip,ccmp]proto       [wpa,rsn]wep-tx-key-idx  
```and wireless connection was made! So I rebooted. Again wireless connected automatically. I went to gconf editor again and found:[code]So deleting ccmp from the group key seems to be the minimum necessary step, at least for me.In Gconf editor if you right click on a key there are several options. Among them are "set as default" and "set as mandatory". If one of these two options was selected for the keys that NetworkManager is messing up would this prevent it? In other words could one or the other of these settings block NetworkManager from altering the key? If so which one?David-emm on this thread: [http://ubuntuforums.org/showthread.php?t=1018168](http://ubuntuforums.org/showthread.php?t=1018168) tried setting the keys in Gconf to "default" and "mandatory". Unfortunately it was a no go. Intrepid/NM objected to his attempts. At this point bab1 joined us and pointed to: [http://www.arachnoid.com/linux/Netwo...ger/index.html](http://www.arachnoid.com/linux/NetworkManager/index.html) At this URL Paul Lutus goes through an explanation of NM's architecture and rationale (distribution agnostic). bab1 then explains that NM is not very flexible at this point and it's algorithm (creating values "on the fly" from HAL and dBus inputs) doesn't accept all user input.The upshot, for us, of all this is that this workaround using Gconf editor is the best we're going to do for now. We will have to wait for another [[COLOR=#000000]version[/COLOR]](http://www.****************.com/wmv-video-format/convert-xvid-avi-video-to-wmv-format.html) of NM that is more flexible and accepts more user input. Maybe inputs through dBus editing? We may be waiting a while.**Addendum 1**:For those of you who's issues look more like timing issues, check out this bug report:[https://bugs.launchpad.net/ubuntu/+s...er/+bug/263963](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/263963)At the bottom, Alexander Sack points you to the latest NM PPA packages (0.7 final) that address some driver timing issues at:[https://edge.launchpad.net/~network-manager/+archive](https://edge.launchpad.net/~network-manager/+archive)**Addendum 2**:I feel compelled to report other strange behavior I have observed. This may bear on the fundamental problem of networkmanager and be related to the bug reports above. After the system is up a while I can no longer grep useful information from dmesg. Instead dmesg in a terminal yields:[code]going on and on and filling terminal. Looking in System Log shows the same thing filling both kern.log and syslog. You get to watch the output into them real time. A treat. No idea what's causing this behavior. Wireless is working fine.**Addendum 3**:As juanhm correctly points out there are additional conditions I neglected to mention:  juanhm's bug link:[https://bugs.launchpad.net/ubuntu/+s...er/+bug/263963](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/263963)Bug closed with status changed to: Won't Fix. New bug report opened. The link:[https://bugs.launchpad.net/ubuntu/+s...er/+bug/377643](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/377643)Note: Vista says it's a Broadcom 4321AG a/b/g/draft-n Wi-Fi Adaptor.Thanks for your explanation! It's very detailed, Now I got it.

---

