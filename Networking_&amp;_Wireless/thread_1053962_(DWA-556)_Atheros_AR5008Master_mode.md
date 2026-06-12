---
title: "(DWA-556) Atheros AR5008/Master mode"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by sanemanmad on 2009-01-29
Hello All,

Thank you for viewing this post. I am in need of some help with setting up my Linux Access Point using the D-Link DWA-556 PCIe 802.11b/g/n card.

Here is some relevant information:

*lspci|grep "Network controller"*
```
[SIZE="1"]04:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)[/SIZE]
```

*lsmod|grep "ath"*
```
[SIZE="1"]ath9k                 296248  0
mac80211              253440  1 ath9k[/SIZE]
```

*iwconfig*

[SIZE="1"]```
wlan1     IEEE 802.11bgn  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=27 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```[/SIZE]

```
wlanconfig wifi0 create wlandev wlan1 wlanmode ap
wlanconfig: ioctl: Operation not supported
```

As you can see I do already have the Ath9k drivers installed and I can confirm connection to my existing AP. My problem here is setting this device to "Master"/"AP" mode.

I was had tried current setup with Kernel-2.6.27-7-server, right now I am running most current Kernel-2.6.27-11-generic


----------------------------------

[From the driver vendor themselves:]("http://linuxwireless.org/en/users/Drivers")

> 
Working
Modes of operation
    *
      Station Mode
    *
      AP Mode
    *
      IBSS Mode
    *
      AHB and PCI bus


> 
DWA-556 Xtreme N PCIe Desktop Adapter 

ath9k (Atheros devices)
	
yes --> AP
yes --> Ad-Hoc	
no --> Mesh
yes --> Full-Monitor
A/B/G/N --> Modes this drivers supports


---

### Post by sanemanmad on 2009-01-31
I know these drivers should support this card in AP mode however there has got to be something i am overlooking. 

*BUMP*

---

### Post by sanemanmad on 2009-02-01
Hmm... Where is the support :( I suppose this has stumped the community also? I have been back and forth to madwifi-project and it confirms these drivers can operate in Master mode (Act as an access point) I could care less for the N speeds, I would like to scratch my existing wifi ap for internal one.

---

### Post by viggeh on 2009-02-07
I'm having the same problems, can't get AP mode working on my DWA-556 card. I've tried using madwifi (trunk, v0.9.4), but the NIC won't send out any packets after a client computer connects to it.

According to [a page](http://wireless.kernel.org/en/users/Documentation/modes) at Linux Wireless hostapd is required for AP mode, but hostapd gives me the following errors when run:
```
# hostapd -dd /etc/hostapd/hostapd.conf
Configuration file: /etc/hostapd/hostapd.conf
ctrl_interface_group=0
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported
Could not enable hostapd mode for interface wlan0
hostap driver initialization failed.
wlan0: Unable to setup interface.
Flushing old station entries
Deauthenticate all stations
```

hostapd.conf:
```
bridge=br0 # eth0 and wlan0 are bridged
interface=wlan0
driver=hostap

ssid="somerouter"

hw_mode=g
channel=7

wpa=3
wpa_psk=xxxxxxxxxxxxxx
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP

logger_syslog=-1
logger_syslog_level=2
logger_stdout=--1
logger_stdout_level=2
debug=0

ctrl_interface_group=0
macaddr_acl=0
deny_mac_file=/etc/hostapd/hostapd.deny
auth_algs=3
eapol_key_index_workaround=0
eap_server=0
dump_file=/tmp/hostap
```

I'm hoping someone can shed some light regarding this, thanks in advance!

---

### Post by beighto on 2009-02-10
I am having the same problem with an Atheros AR5008 Dlink DWA-552.  I am beginning to think the ath9k driver does not support master mode.  I have used this card in master mode before in g mode with ath_pci so I know it is capable.

---

### Post by sanemanmad on 2009-02-10
> **viggeh said:**
> 
According to [a page](http://wireless.kernel.org/en/users/Documentation/modes) at Linux Wireless hostapd is required for AP mode

Ya, I tried using this driver and adapter with hostap and was unsuccessful, So now I am only attempting to get the adapter to function as an AP, I do not need WPA or Radius auth.

---

### Post by zekica on 2009-02-10
I think **wlanconfig** is a part of **madwifi** drivers, and not **ath9k**. **ath9k** should work with [**iw**]("http://wireless.kernel.org/en/users/Documentation/iw") command.

---

### Post by beighto on 2009-02-10
I was able to get mine working again by unloading the ath9k and using ath_pci.  It only works in G mode, but at least it works.  Mostly everything I did was covered here:

[http://www.how2pc.co.il/blog/2009/01/raphael-pinson-setting-up-an-access-point-with-wpa-on-ubuntu-intrepid/](http://www.how2pc.co.il/blog/2009/01/raphael-pinson-setting-up-an-access-point-with-wpa-on-ubuntu-intrepid/)

---

### Post by sanemanmad on 2009-02-13
Hi again and thank you for the help.

So far I had placed this on hold, however I retried this time using a svn of the drivers recommended [[http://madwifi-project.org/ticket/2232]](http://madwifi-project.org/ticket/2232]) for my kernel [2.6.27-11-server]. Again I can load the drivers and connect to my wireless AP, here is my second attempt to set this device as an AP using madwifi's
[
root@server:~# iwconfig wlan0 mode Master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
]





MAN iwconfig -- is from where I copied the syntax from.

---

### Post by areamike on 2009-02-13
I have the same issue with my Atheros Wireless card for my Laptop. 

AR5007EG - Driver shows under System>Administrator>Hardware Drivers
Support for Atheros 802.11 Wireless LAN cards.

However, when I go to System>Preferences>Network Configuration>Wireless, no connections are listed. So I try to ADD and put in all necessary info, yet my Wireless card still will not work.

This is my second install of Ubuntu. The first time I tried so many things to get the wireless to work, I ended up getting pissed off and started over. I tried madwifi drivers, ndiswrapper etc etc etc. This sure seems like a lot of hoops to jump through just to get wireless networking to work on Ubuntu.

Sorry to hijack, but I thought it better to post in this thread since I am having almost exact same problem rather than starting a new thread.

---

### Post by sanemanmad on 2009-02-13
Sure, Let's see iwconfig

Then look for wlan0 or ath0
then in terminal, which is where you will use those other commands;

iwlist "wlan0/ath0" scanning

---

### Post by areamike on 2009-02-13
#iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.

#iwlist "wlan0/ath0" scanning
wlan0/ath0  Interface doesn't support scanning.

Funny thing also is in my /etc/network/interfaces file, there is nothign listed about ath0.

---

### Post by sanemanmad on 2009-02-13
I do recommend for a much faster resolution, you should open a new thread. [It will show up as a new post and will receive many more views and responses]

---

### Post by sanemanmad on 2009-02-13
> **areamike said:**
> #iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.

#iwlist "wlan0/ath0" scanning
wlan0/ath0  Interface doesn't support scanning.

Funny thing also is in my /etc/network/interfaces file, there is nothign listed about ath0.

Are you sure the drivers are loaded? Also I meant for only one option wlan0 *or* ath0 :P

"lsmod|grep ath"

---

### Post by areamike on 2009-02-13
> **sanemanmad said:**
> Are you sure the drivers are loaded? Also I meant for only one option wlan0 *or* ath0 :P

"lsmod|grep ath"

I'll start another thread. 


New thread started here:
[http://ubuntuforums.org/showthread.php?t=1068917](http://ubuntuforums.org/showthread.php?t=1068917)

---

### Post by sanemanmad on 2009-02-23
[SIZE="2"]Ok I have managed to get this adapter to work in Master mode using the standard madwifi drivers "ath". [/SIZE]

[SIZE="1"]_**Do the following:**_

**sudo vi /etc/modprobe.d/madwifi**

add this line **options ath_pci autocreate=ap**

[B]sudo modprobe ath_pci
sudo ifconfig ath0 up
iwconfig ath0[/B] *should show "mode: Master"*
**sudo iwconfig ath0 essid "YOUR_WIRELESS_NAME" key "0123456789"**

Otherwise you will want to reboot. If needing to adjoin multiple networks, the use of bridge-utils may be required also.[/SIZE]

---

### Post by Brezhonneg on 2009-03-04
Hi there,

For the record, I just managed to set this board up (DWA-556) as an AP using hostapd and ath9k. This required bleeding edge packages, but if anyone is interested, here is how I did:

1/ I used a fresh and updated Jaunty alpha 5 server install
2/ The wireless-crda package comes installed by default and you need to take care of [this bug]("https://bugs.launchpad.net/ubuntu/+source/wireless-crda/+bug/336915") if you have version <=1.6 for this package. I guess that should be fixed with next versions.
3/ I installed the [Debian sid iw]("http://packages.debian.org/unstable/main/iw") package, since an iw package is [not provided by Ubuntu]("https://bugs.launchpad.net/ubuntu/+bug/321630") yet. So wget and 'dpkg -i' are your friends here.
4/ I installed libln1 (this one is in the repos)
5/ I also needed a fresh ath9k provided by the linux-backports-modules-`uname -r` package. Make sure to reboot after this installation (or to play with modprobe a bit).
6/ And last but not least, I grabbed a recent hostapd packaged in [this ppa]("https://edge.launchpad.net/~hermansson-per/+archive/ppa").

I actually found the list of required packages on [this page]("http://acx100.erley.org/stable.html"), but managed to avoid the 'compile them all' approach. As you can see, I only used deb's. The ppa I used for hostapd does not provide the latest hostapd version, but this version seems to be sufficient.

Fiddle with hostapd.conf a little *et voila*. I can see the AP from my eee pc. There is no DHCP server running on that machine yet so I have not tried to connect yet (well, I have and that went well until the point where the eee requested an IP...), so I cannot confirm if this actually works and at what speed but this seems promising.

Cheers

EDIT: the hostapd package provided by the PPA I mentioned did not fire up the daemon at boot for me. This is because the init script refers to a $RUN_DAEMON variable that was not defined in my environment. Anyways, if you have this problem, just edit /etc/init.d/hostapd and add RUN_DAEMON=yes below the INIT INFO block.

EDIT2: next time I will open my eyes and read... the correct way to make the daemoon start at boot is to edit /etc/default/hostapd and uncomment the RUN_DAEMON=yes line. D'uh

---

### Post by Brezhonneg on 2009-03-14
Alright, I am back to complete my report...

Since my first post, iw has been included in Jaunty repos, the crda bug was fixed and the ppa was updated to the latest hostapd (0.6.8). So any fresh install should be just smooth and easy now.

Everything works very well for me, and I can connect with WPA2 and MAC filtering, everything I wanted. My download speed from my eee is capped at 13-14 Mbps (1.7MB/s) on FTP, but then I am not sure if the AP is limiting, or if the limit is reached on the eee (which is still drived by ath5k on crunchbang 8.10). I'll know more when I upgrade the eee to Jaunty, but till then, I can do with what I have.

I hope this can help anybody who would like to go down this road.

Have fun!

---

### Post by bastler on 2009-06-05
Hi There!

I too am in the middle of setting up an AP with an Atheros AR5008 card on Jaunty using Ath9k, and I've run into a strange problem.

Thanks to your posts here I managed to get hostapd up and running, it detects the card, puts it in access point mode, fires it up, handles encryption and everything. Both ifconfig and iwconfig output look normal (I don't see an essid in iwconfig output any more, but I'm told that's by design when using the 80211-driver).

when looking at the logs I can see the card receiving probe requests for SSID broadcasts from my laptop. The only problem is it cannot connect!

no matter wether I tell hostapd to show or hide the ssid, the network does not appear in the list of available networks on the stations, and when manually connecting to the access point it just times out...

Has anyone else ever had this problem and knows a solution to it?


running jaunty stable on 2-6-28.11-generic x86_64 with the newest packages I could get my hands on...

---

### Post by Brezhonneg on 2009-06-08
Hi Bastler,

There are dozens of different issues that could give these symptoms... It could be related to hostapd, to your dhcp config, to your AP firewall, to your client firewall, to your client WiFi driver...

I guess you should first try to disable any security or encryption protocols in hostapd, go for a static IP (no dhcp), shut down your firewalls and investigate from here. If you get a connexion, then turn those components back on one by one. Otherwise, run hostapd in verbose mode and see if you can spot any useful message.

In any event, I am affraid that nobody will really be able to provide you with valuable advice until you narrow down the source of your problem a little.

Best of luck!

---

### Post by berland on 2009-09-12
I have an AR5008 (on a DWA-547) running on Ubuntu Karmic Alpha 5. 

Using the Ubuntu-supplied hostapd and ath9k, I have got this card to function (for a few seconds) in AP mode. The card is bridged with LAN so another router hands out DHCP.

But, after a period of time (5 sec to 1 min), I loose connection, and in /var/log/daemon.log I find messages from hostapd:

Sep 11 23:00:50 htpc hostapd: wlan0: STA 00:21:e8:0a:xx:xx IEEE 802.1X: unauthorizing port
Sep 11 23:00:50 htpc hostapd: wlan0: STA 00:21:e8:0a:xx:xx IEEE 802.11: deauthenticated due to local deauth request

After this, rmmod ath9k or reboot seems necessary to get a new connection.

I have reached speeds of 3-4 MB/sec before connection is lost.

---

### Post by Harper04 on 2009-10-13
> **berland said:**
> I have an AR5008 (on a DWA-547) running on Ubuntu Karmic Alpha 5. 

Using the Ubuntu-supplied hostapd and ath9k, I have got this card to function (for a few seconds) in AP mode. The card is bridged with LAN so another router hands out DHCP.

But, after a period of time (5 sec to 1 min), I loose connection, and in /var/log/daemon.log I find messages from hostapd:

Sep 11 23:00:50 htpc hostapd: wlan0: STA 00:21:e8:0a:xx:xx IEEE 802.1X: unauthorizing port
Sep 11 23:00:50 htpc hostapd: wlan0: STA 00:21:e8:0a:xx:xx IEEE 802.11: deauthenticated due to local deauth request

After this, rmmod ath9k or reboot seems necessary to get a new connection.

I have reached speeds of 3-4 MB/sec before connection is lost.


Hi, i am on Karmic Beta with latest updates and i am experiencing the same Problem!
The Connections stays online as long i try to reconnect to Wlan AP, then i have to restart HostAP!

Did you solve this Problem? Do you have this Problem under Jaunty?

PLEASE Responsd :)

greetings harper

---

### Post by timeking on 2009-10-19
[COLOR=red]**SORRY FOR MISLEADING! Karmic dev edition doesn't work with the config below, I was too optimistic and did too little testing.**[/COLOR]
[COLOR=red][/COLOR] 
DWA-552 with AR9223 inside works fine on Karmic Beta Server. The machine is a router: ath9k + hostapd + iptables forwarding + dnsmasq. On the upstream side is a 3Com wired card, connected to another router.
Connections are stable in N mode. I tested stability by listening to online radio for hours on my ASUS 1005HAB netbook.
When I tried this same setup with Karmic Desktop, wireless networking hangs. Sometimes at connection, sometimes later; ath9k rmmod/insmod or reboot is required. 
Looks like NetworkManager is involved, and the related GUI in paticular.
Try to put your wireless card into "interfaces" to prevent NetworkManager from controlling it.
Interesting, but everything works fine on 9.04 desktop. OOB in station mode with or without NetworkManager and in master mode with hostapd backported from 9.10.

---

### Post by neffer on 2009-10-26
Hey

I have tried for a long time to get my Ubuntu box to work as an Access point - but newer succeed. 

My configuration:
Intel motherboard: D945GCLF2
With Wireless PCI card: Linksys WMP300Nv2 (Atheros chipset: AR5416+AR2133)

timeking - you are claiming, that you have got i to work in N-mode. Could I get you to write in detail how you manage to so? From a claen install of Ubuntu and in step by step?

Any other help are also most welkome

Best regards
Steffen Rasmussen

---

### Post by C4colo on 2010-02-25
I don't think this applies to just Ubuntu.  This is probably an ath9k issue or something stupid with the card itself.  I have experienced this same behavior in Vyatta VC6-alpha which now supports Wi-Fi interfaces including master/AP mode.  It is based on Debian (I don't know if that is significant).

I was hoping to get the card working on my ubuntu desktop in Master/AP mode to "prove" that it works, and in searching I found this thread.  I just wanted to let people know that this is not just an issue with Ubuntu but it seems to be pretty wide-spread.

I will let you guys know if I find anything or if I figure it out on my own.

EDIT: I forgot to mention that I'm using the DWA-552 version of the card (PCI instead of PCIe) but it is the same chipset, just different interface.

---

### Post by ben@kietzman.org on 2010-05-22
I have been unable to configure my DWA-552 AR5008 wireless card as an AP in master mode.  I have primarily been using the ath_pci driver, but I have also tried using ath9k.

I am using dhcp3-server, firehol and hostapd.  I have tried all sorts of different configurations, but nothing seems to work.  Any help would be appreciated.

lspci
```

01:08.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)

```

ifconfig
```

ath0      Link encap:Ethernet  HWaddr 06:22:b0:bd:a4:f5  
          inet6 addr: fe80::422:b0ff:febd:a4f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:2290  Metric:1
          RX packets:365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20770 (20.7 KB)  TX bytes:4617 (4.6 KB)

br0       Link encap:Ethernet  HWaddr 00:a0:c9:13:c7:38  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2001:4978:1fa:0:2a0:c9ff:fe13:c738/64 Scope:Global
          inet6 addr: fe80::2a0:c9ff:fe13:c738/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:14942 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1774229 (1.7 MB)  TX bytes:3672799 (3.6 MB)

eth0      Link encap:Ethernet  HWaddr 00:a0:c9:13:c7:38  
          inet6 addr: 2001:4978:1fa::1/64 Scope:Global
          inet6 addr: fe80::2a0:c9ff:fe13:c738/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9556 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2017558 (2.0 MB)  TX bytes:3673007 (3.6 MB)

eth1      Link encap:Ethernet  HWaddr 00:50:bf:39:fa:43  
          inet6 addr: fe80::250:bfff:fe39:fa43/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13406 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3638682 (3.6 MB)  TX bytes:1937336 (1.9 MB)
          Interrupt:10 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:500 (500.0 B)  TX bytes:500 (500.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:70.226.205.196  P-t-P:70.226.207.254  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:9380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3427539 (3.4 MB)  TX bytes:1640374 (1.6 MB)

sixxs     Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet6 addr: 2001:4978:f:252::2/64 Scope:Global
          inet6 addr: fe80::4878:f:252:2/64 Scope:Link
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1280  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:144 (144.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-22-B0-BD-A4-F5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:384 errors:0 dropped:0 overruns:0 frame:51
          TX packets:239 errors:204 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:23360 (23.3 KB)  TX bytes:45719 (45.7 KB)
          Interrupt:9 

```

iwconfig
```

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"kietzman"  
          Mode:Master  Frequency:2.442 GHz  Access Point: 06:22:B0:BD:A4:F5   
          Bit Rate=54 Mb/s   Tx-Power:19 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:174  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

hostapd -dd /etc/hostapd/hostapd.conf
```

Configuration file: /etc/hostapd/hostapd.conf
Configure bridge br0 for EAPOL traffic.
madwifi_set_iface_flags: dev_up=0
madwifi_set_privacy: enabled=0
madwifi_receive_probe_req Enter
BSS count 1, BSSID mask ff:ff:ff:ff:ff:ff (0 bits)
SIOCGIWRANGE: WE(compiled)=22 WE(source)=18 enc_capa=0xf
ath0: IEEE 802.11 Fetching hardware channel/rate support not supported.
Flushing old station entries
madwifi_sta_deauth: addr=ff:ff:ff:ff:ff:ff reason_code=3
Deauthenticate all stations
madwifi_sta_deauth: addr=ff:ff:ff:ff:ff:ff reason_code=2
madwifi_set_privacy: enabled=0
madwifi_del_key: addr=00:00:00:00:00:00 key_idx=0
madwifi_del_key: addr=00:00:00:00:00:00 key_idx=1
madwifi_del_key: addr=00:00:00:00:00:00 key_idx=2
madwifi_del_key: addr=00:00:00:00:00:00 key_idx=3
Using interface ath0 with hwaddr 06:22:b0:bd:a4:f5 and ssid 'kietzman'
madwifi_set_wps_ie buflen = 0
madwifi_set_wps_ie buflen = 0
madwifi_set_iface_flags: dev_up=1
ath0: Setup of interface done.
l2_packet_receive - recvfrom: Network is down
l2_packet_receive - recvfrom: Network is down
l2_packet_receive - recvfrom: Network is down

```

/etc/dhcp3/dhcpd.conf
```

authoritative;
ddns-update-style interim;
ignore client-updates;

subnet 192.168.0.0 netmask 255.255.255.0 {
        option routers 192.168.0.4;
        option subnet-mask 255.255.255.0;
        option domain-name-servers 68.94.156.1,68.94.157.1;
        option ip-forwarding off;
        range dynamic-bootp 192.168.0.5 192.168.0.254;
        default-lease-time 21600;
        max-lease-time 43200;
}

```

/etc/firehol/firehol.conf
```

#!/sbin/firehol
version 5

home_ips="192.168.0.0/24"
vpn_ips="10.8.0.0/24"

client_httpalt_ports="8089"
client_httpslfm_ports="4443"
client_openvpn_ports="1194"
client_tor_ports="9050"
client_torcontrol_ports="9051"
client_tormirror_ports="9030"
client_torrelay_ports="9001"

server_httpalt_ports="tcp/8089"
server_httpslfm_ports="tcp/4443"
server_openvpn_ports="tcp/1194"
server_tor_ports="tcp/9050"
server_torcontrol_ports="tcp/9051"
server_tormirror_ports="tcp/9030"
server_torrelay_ports="tcp/9001"

interface br0 home src "${home_ips}"
  server all accept
  client all accept

interface tun0 interface3 src "${vpn_ips}"
  server all accept
  client all accept

interface ppp0 internet src not "${home_ips} ${vpn_ips} ${UNROUTABLE_IPS}"
  protection strong 10/sec 10
  server "emule http https httpslfm ping rtp openvpn sip squid ssh tor torcontrol tormirror torrelay" accept
  server ident reject with tcp-reset
  client all accept

```

/etc/hostapd/hostapd.conf
```

interface=ath0
bridge=br0
driver=madwifi
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
dump_file=/tmp/hostapd.dump
ssid=kietzman
hw_mode=g

```

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

iface eth0 inet6 static
  address 2001:4978:1fa::1
  netmask 64

auto ath0
iface ath0 inet manual
  pre-up wlanconfig ath0 destroy
  pre-up wlanconfig ath0 create wlandev wifi0 wlanmode ap
  post-down wlanconfig ath0 destroy
  wireless-mode master
  wireless-essid kietzman
  wireless-channel 7
  wireless-rate 54M

auto br0
iface br0 inet static
  address 192.168.0.4
  network 192.168.0.0
  netmask 255.255.255.0
  broadcast 192.168.0.255
  bridge-ports eth0 ath0

auto dsl-provider
  iface dsl-provider inet ppp
  pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
  provider dsl-provider

auto eth1
iface eth1 inet manual

```

/etc/modprobe.d/blacklist-ath_pci.conf
```

#blacklist ath_pci

```

/etc/modprobe.d/blacklist.conf
```

blacklist ath9k
blacklist ath5k

```

/etc/modprobe.d/options.conf
```

options ath_pci autocreate=ap

```

---

### Post by rotten777 on 2010-09-06
I'm in the same boat as many. Trying to setup AR5008 in master mode and no dice.

Is this a dead issue or is there hardware that would better fit this? 

802.11n speed would be nice but I'm only spending the money if it works with linux (specifically deb/ubu).

---

### Post by ben@kietzman.org on 2010-09-07
It's a dead issue for me.  I returned the wireless card and bought a simple wireless router instead.  Except I disabled the router aspect of the wireless router.  It works like a wireless switch now.  The Ubuntu server still serves as the primary router.

---

### Post by b0bbykey on 2010-09-19
I have set up DWA-552 + ath9k + hostapd to work in master mode on 10.04, all software from official repository, everything works fine in G mode but won't go to 802.11n mode. Guys if you have this card working in 802.11N mode pls share your confs maybe I'm missing smth

---

### Post by nemo136 on 2011-12-07
I know this subject is quite old. Still, the card now works perfectly using ath9k and hostapd. Here is my config file for people who might be interested :

```

interface=wlan0
bridge=br0
driver=nl80211
ssid=yourssid
hw_mode=g
ieee80211n=1
auth_algs=1
channel=1
ignore_broadcast_ssid=0
macaddr_acl=0
wpa=2
wpa_passphrase=yourpasswordhere
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP


```

The only thing left is using power saving, which did not work for me.

---

