---
title: "Master mode on AR928X."
date: 2009-09-18
forum: Networking &amp; Wireless
---

### Post by Jophish on 2009-09-18
Hi all

EDIT
Turns out I was running a really old version of ath9k. compiling the newest version worked great.
/EDIT

I am trying to get my wireless card working in master mode. I am running Jaunty server 2.6.28-11 x86_64.
I have compiled hostapd with nl80211 enabled. The interface is using ath9k. 

I have tried to compile compat-wireless with [this]("https://dev.openwrt.org/browser/trunk/package/mac80211/patches/004-allow-ap-vlan-modes.patch?rev=12299") patch. However IEEE80211_IF_TYPE_AP was undefined along with IEEE80211_IF_TYPE_VLAN. In addition the latest version of compat-wireless needs to be patched for kernels < 2.6.31 with [this]("http://www.mail-archive.com/bcm43xx-dev@lists.berlios.de/msg08726.html"). However when using this patch IRQ_WAKE_THREAD is still undefined.

I have got to this message:
```
$ sudo hostapd /home/jophish/.hostapd.conf 
Configuration file: /home/jophish/.hostapd.conf
Failed to set interface wlan0 to master mode.
nl80211 driver initialization failed.
ELOOP: remaining socket: sock=5 eloop_data=0xe05040 user_data=(nil) handler=0x433350

```

.hostapd.conf:
```
interface=wlan0
driver=nl80211
ssid=Testnet
channel=1
hw_mode=g
auth_algs=1
wpa=3
wpa_passphrase=1234567890
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP

```

Thanks

Joe

Some useful information:

$ sudo lshw -C Network
```
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:01:2e:27:58:15
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.0.3 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 01
       serial: 00:25:d3:3d:9b:19
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn

```

$ dmesg | grep -e ath -e wlan
```
[   15.371737] ath9k: 0.1
[   15.373213] ath9k 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
[   15.373232] ath9k 0000:04:00.0: setting latency timer to 64
[   15.800779] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   15.842715] Registered led device: ath9k-phy0:radio
[   15.842758] Registered led device: ath9k-phy0:assoc
[   15.842796] Registered led device: ath9k-phy0:tx
[   15.842833] Registered led device: ath9k-phy0:rx
[ 3704.324281] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6377.225165] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[67178.380725] ath_hal: module license 'Proprietary' taints kernel.
[67178.383995] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[67178.415378] wlan: 0.9.4
[67178.434237] ath_pci: 0.9.4
[67189.736303] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[67617.963271] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[68301.016316] ath_pci: driver unloaded
[68306.091446] ath9k 0000:04:00.0: PCI INT A disabled
[68306.091527] ath9k: driver unloaded
[68316.125010] ath_hal: driver unloaded
[68355.378628] ath9k: 0.1
[68355.378715] ath9k 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
[68355.378732] ath9k 0000:04:00.0: setting latency timer to 64
[68355.812298] phy1: Selected rate control algorithm 'ath9k_rate_control'
[68355.814239] Registered led device: ath9k-phy1:radio
[68355.814304] Registered led device: ath9k-phy1:assoc
[68355.814358] Registered led device: ath9k-phy1:tx
[68355.814420] Registered led device: ath9k-phy1:rx
[71192.024009] ath9k 0000:04:00.0: PCI INT A disabled
[71192.024096] ath9k: driver unloaded
[71208.671421] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[71208.687656] ath_pci: 0.9.4
[71232.363604] ath_pci: driver unloaded
[71236.845164] ath9k: 0.1
[71236.845261] ath9k 0000:04:00.0: PCI INT A -> Link[LN3A] -> GSI 19 (level, low) -> IRQ 19
[71236.845282] ath9k 0000:04:00.0: setting latency timer to 64
[71237.277830] phy2: Selected rate control algorithm 'ath9k_rate_control'
[71237.279894] Registered led device: ath9k-phy2:radio
[71237.279949] Registered led device: ath9k-phy2:assoc
[71237.280065] Registered led device: ath9k-phy2:tx
[71237.280131] Registered led device: ath9k-phy2:rx
[72341.584129] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

$ iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

$ sudo iwconfig wlan0 mode master
```
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
```

---

### Post by rossmoore on 2009-12-06
Hi,

I have the same chipset, and am also wanting to create an AP with it. You say you realised you were using an old version of the ath9k driver - I'm just using whatever came with karmic. Are you saying you downloaded the tarball from here:
[http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)
and then compiled it into your kernel somehow?

I'd love some pointers if you have time.
Thanks,
Ross

---

### Post by rossmoore on 2009-12-14
I tried compiling those drivers but didn't get anywhere with hostapd - I continue to get the errors you list above (Failed to set interface wlan0 to master mode.)

Could you can give me any insight into how you got this working?

---

### Post by raz-berry on 2009-12-14
Once you installed hostapd (like sudo apt-get install hostapd)
you need to make a hostapd.config file with settings like 

interface=wlan0
bridge=br0
driver=nl80211
ssid=xxxx
channel=1
hw_mode=g
ieee80211n=1
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=xxxxx
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP

more about this settings here [http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd)

once this is done you have to run
sudo hostapd hostapd.config
and wireless interface goes into master mode
you cannot put in in master mode with iwconfig wlan0 mode master

---

### Post by rossmoore on 2009-12-18
Hey, raz-berry, that's great! Thanks.

I read the example hostapd.conf that came with the install, but obviously I couldn't understand it well enough or I missed something. Your simplified file definitely gets me up and running - I just need to re-read the tutorials on bridging and I think I'll be there.

Thanks again,
Ross

---

### Post by rossmoore on 2009-12-19
Yup, that's done it. I had to set up dhcpd and firestarter as well to get it all working together, but getting this hostapd.conf file right was the key step I was missing.

Thank you again (from my laptop, connected to my server by wifi, which is in turn connected by pppoe). Hurrah!

---

### Post by bruceschaller on 2010-05-28
This setup works great for me, now I just need to learn how to bridge the wifi card with a NIC and I'll be good to go.  

My ideal setup will be like on in this unsolved post:

[http://ubuntuforums.org/showthread.php?t=698695&highlight=bridged+wireless+access+point]("http://ubuntuforums.org/showthread.php?t=698695&highlight=bridged+wireless+access+point")

Fantastic thread!  Even easier than other 'master mode' cards it seems.

---

### Post by irose123 on 2010-06-15
> **raz-berry said:**
> Once you installed hostapd (like sudo apt-get install hostapd)
you need to make a hostapd.config file with settings like 

interface=wlan0
bridge=br0
driver=nl80211
ssid=xxxx
channel=1
hw_mode=g
ieee80211n=1
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=xxxxx
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP

more about this settings here [http://linuxwireless.org/en/users/Documentation/hostapd](http://linuxwireless.org/en/users/Documentation/hostapd)

once this is done you have to run
sudo hostapd hostapd.config
and wireless interface goes into master mode
you cannot put in in master mode with iwconfig wlan0 mode master
Can confirm works in lucid lynx too (using drivers shipped with release!), just remember backports before installing hostapd:

sudo aptitude install linux-backports-modules-wireless-lucid-generic

---

### Post by ZioNemo on 2010-10-14
Hi, I have the same problem under Lucid.
I need to use my desktop as router:
[LIST]
[*]it has two net cards + AR928X
[*]it is connected to ISP with eth2
[*]it is connected to LAN with eth3
[*]sharing connection on copper works (including firewall)
[*]I need to enable sharing connection over WiFi.
[*]hostapd seems to work, but I'm unsure of what *else* I need to setup
[/LIST]
Pointers, please?

TiA
ZioNemo

---

### Post by rossmoore on 2010-10-14
Well, I guess it depends on exactly what you want to achieve with all those networks interfaces.

If you think hostapd is up and running (if you run it from the command line rather than as a service, does it give good-looking output?) then I guess the next thing you're likely to want is a dhcp server. You can find it synaptic (dhcp3 I think). Set it to bind only to your wlan interface (or whichever interfaces you want it work on).

Have you set that up? Or do you intend to use fixed IP addresses? Then you'll need to set ip_forward on in sysctl probably so that you can act as a router, and definitely set your firewall (I use firestarter, although I had to get familiar a little with iptables too).

Let me know how you get on

---

### Post by ZioNemo on 2010-10-14
Situation is a bit more complex, unfortunately.
Let me explain:

This machine is my home server.

I have ubuntu 10.04 LTS installed and, maybe that has been a mistake, because I have also NetworkManager installed and I cannot remove it.
Anyways:

[LIST]
[*]I also have VirtualBox installed with two Virtual machines:
[*]One VM is an IPCop firewall that has exclusive use of eth3 and connects to ISP.
[*]The Other VM is my www/mail server and sits in a VirtualBox-managed virtual net where just the two VMs see each other.
[*]A third net is connected to eth2 and bridged to the firewall VM.
[/LIST]

This setup works since a long time and I can share my Internet connection (on eth3) with all computers connected to my GREEN (eth2).
I can also do port-forwarding, dhcp, transparent-proxy, etc. All this is handled by the firewall (IPCop).

Now I want to add a Wireless LAN, so I would think I must just bring up my card in AP-mode and bridge it to a fourth virtual interface to the firewall (once there I know how to do the routing).

What is unclear to me is:
[LIST]
[*]What should I write in /etc/network/interfaces (if anything)?
[*]What should I use to bring up wlan2?
[*]IPCop can act as DHCP server also for the wireless (BLUE) interface, but, for it to see it I must tell VirtualBox to bridge it, i.e.: the interface must exist, even if unconfigured.
[*]I have a fair knowledge of Ethernet, but wireless is relatively new to me.
[/LIST]

Can You help me? please?
Regards
ZioNemo

---

### Post by rossmoore on 2010-10-14
Here's my /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider


auto wlan0
iface wlan0 inet manual
up /usr/sbin/service hostapd start
up /sbin/ifconfig wlan0 192.168.3.1 netmask 255.255.255.0 broadcast 192.168.3.255
#up /sbin/ifconfig $IFACE 0.0.0.0
#up /sbin/ip link set $IFACE promisc on
post-up /etc/init.d/dhcp3-server start
post-up /sbin/sysctl -w net.ipv4.ip_forward=1
post-up /etc/init.d/firestarter start
#down /sbin/ip link set $IFACE promisc off
down /usr/sbin/service firestarter stop
down /usr/sbin/service dhcp3-server stop
down/usr/sbin/service hostapd stop
down /usr/bin/poff

```

I have to say I'm not an expert, but it works, and I think I understand 90+% of it...

Basically to get the wlan up as an Access Point I ensure everything's down first, so ifconfig gives nothing (or nothing but loopback). Then bring up hostapd and then give that interface an IP address and subnet. Then bring up firestarter, the dhcp server and anything I need. I also have an openvpn server with its virtual tun device on the network.

Do you need to bridge for your virtual machines? Could the virtual devices just have IP addresses that get routed to? Sorry, I'm even less of an expert on virtual machines and their networking requirements - you'll need someone else to help you out there I'm afraid.

Oh, and one more thing - you mentioned Network Manager. That will only control interfaces not mentioned in your /etc/network/interfaces file. If an interface is mentioned in there, Network Manager automatically just leaves it well alone - which is very polite and well-behaved of it. I have Maverick installed now with Network Manager - but I don't touch it and have everything controlled in Network Manager. I like NM, and use it on my laptop where my networking requirements change frequently. But on a server (or quasi-server) it's better to set everything up in the proper files I think.

---

### Post by ZioNemo on 2010-10-14
Even dumber than expected.
I am not able to follow what You are doing.
I *thought* I understood... but it does not work :(
My current target is to set up this pc to accept connections, forget about sharing, routing, etc.
My /etc/network/interfaces is:
> auto lo
iface lo inet loopback

auto wlan2
iface wlan2 inet manual
    up /usr/sbin/service hostapd start
    up /sbin/ifconfig wlan2 192.168.2.2 netmask 255.255.255.0 broadcast 192.168.2.255
    post-up /etc/init.d/dhcp3-server start
    post-up /sbin/sysctl -w net.ipv4.ip_forward=1
    post-up /etc/init.d/firestarter start
    down /usr/sbin/service firestarter stop
    down /usr/sbin/service dhcp3-server stop
    down /sbin/ifconfig wlan2 down
    down /usr/sbin/service hostapd stop


/etc/hostapd/hostapd.conf (minus comments, mostly unchanged from defaults) is:
> 
interface=wlan2
bridge=br0
driver=nl80211
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
dump_file=/tmp/hostapd.dump
ctrl_interface=/var/run/hostapd
ctrl_interface_group=0
ssid=Atom
country_code=IT
ieee80211d=1
hw_mode=g
channel=2
beacon_int=100
dtim_period=2
max_num_sta=255
rts_threshold=2347
fragm_threshold=2346
auth_algs=3
ignore_broadcast_ssid=0
wme_enabled=1
wme_ac_bk_cwmin=4
wme_ac_bk_cwmax=10
wme_ac_bk_aifs=7
wme_ac_bk_txop_limit=0
wme_ac_bk_acm=0
wme_ac_be_aifs=3
wme_ac_be_cwmin=4
wme_ac_be_cwmax=10
wme_ac_be_txop_limit=0
wme_ac_be_acm=0
wme_ac_vi_aifs=2
wme_ac_vi_cwmin=3
wme_ac_vi_cwmax=4
wme_ac_vi_txop_limit=94
wme_ac_vi_acm=0
wme_ac_vo_aifs=2
wme_ac_vo_cwmin=2
wme_ac_vo_cwmax=3
wme_ac_vo_txop_limit=47
wme_ac_vo_acm=0
wep_default_key=0
wep_key0=123456789a
wep_key1="vwxyz"
wep_key2=0102030405060708090a0b0c0d
wep_key3=".2.4.6.8.0.23"
ieee80211n=1
eapol_key_index_workaround=0
eap_server=0
own_ip_addr=127.0.0.1
wpa=2
wpa_passphrase=mysecretpassphrase
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP


When I start the interface I so not see any evident errors, but another pc simply do not see any AP nearby.

If this is the case I assume it's useless to try something more complex.

What should I check?

TiA

---

### Post by rossmoore on 2010-10-17
OK, hostapd is not good at reporting errors when run as a service. Try this:

```

cd /etc/hostapd
sudo hostapd hostapd.conf

```

Then it should try and start the access point in your terminal and give you some useful denbigh output. Post the results if you can't figure out what to do next.

---

