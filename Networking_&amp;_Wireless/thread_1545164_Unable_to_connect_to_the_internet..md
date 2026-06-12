---
title: "Unable to connect to the internet."
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by Captain Alex on 2010-08-03
I've been trying for 3 days now, gone to a couple of ubuntu sites, asked some friends who unfortunately don't have the time to assist me, and gone through several forum responses on here to try to find the solution to my problem.

The problem is my inability to connect to my wireless network.

I have a linksys USB device for my wireless, and the wireless router is literally right next door to my room. I am able to find my router and my neighbor's router from my computer. However I can not connect to my router. It is WPA enabled, and I have the correct password.

It is just unable to connect to the network, it tries for a few minutes then doesn't connect at all and says wireless network disconnected.

I am currently hooked up to an unsecured wireless network, but I can't connect to the internet. I am using firefox, but it doesn't seem to connect to any site I try.

Here is the lspci
```
captain@The-Ship-Of-Capn-Alex:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:08.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 05)
00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)
```

and the lsusb

```
captain@The-Ship-Of-Capn-Alex:~$ lsusb
Bus 004 Device 002: ID 04f3:0212 Elan Microelectronics Corp. Laser Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

and when I ping
I type in "ping www.google.com" in the terminal and all that comes up is

```
ping: unknown host www.google.com
```

Am I not pinging properly?

Please help if at all possible. I appreciate any response to this thread.

---

### Post by chili555 on 2010-08-03
May I please see:```
lsmod
```Thanks.

---

### Post by Captain Alex on 2010-08-03
```
Module                  Size  Used by
nls_iso8859_1           3249  0 
nls_cp437               4919  0 
vfat                    8901  0 
fat                    47767  1 vfat
usb_storage            39425  0 
nls_utf8                1069  1 
isofs                  29250  1 
ipt_MASQUERADE          1407  1 
xt_state                1098  1 
ipt_REJECT              1928  2 
xt_tcpudp               2011  4 
iptable_filter          2271  1 
nf_nat_h323             5077  0 
nf_conntrack_h323      46926  1 nf_nat_h323
nf_nat_pptp             1920  0 
nf_conntrack_pptp       4413  1 nf_nat_pptp
nf_conntrack_proto_gre     4021  1 nf_conntrack_pptp
nf_nat_proto_gre        1259  1 nf_nat_pptp
nf_nat_tftp              716  0 
nf_conntrack_tftp       2893  1 nf_nat_tftp
nf_nat_sip              5108  0 
nf_conntrack_sip       15389  1 nf_nat_sip
nf_nat_irc              1124  0 
nf_conntrack_irc        3332  1 nf_nat_irc
nf_nat_ftp              1836  0 
nf_conntrack_ftp        5381  1 nf_nat_ftp
iptable_nat             4414  1 
nf_nat                 15735  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      10672  4 iptable_nat,nf_nat
nf_conntrack           61583  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ip_tables               9991  2 iptable_filter,iptable_nat
x_tables               14299  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
binfmt_misc             6587  1 
snd_via82xx            20058  2 
gameport                9089  1 snd_via82xx
snd_ac97_codec        100646  1 snd_via82xx
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc          7076  2 snd_via82xx,snd_pcm
arc4                    1153  2 
snd_mpu401_uart         5617  1 snd_via82xx
fbcon                  35102  72 
tileblit                2031  1 fbcon
snd_seq_dummy           1338  0 
font                    7557  1 fbcon
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
rt73usb                22434  0 
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_rawmidi            19056  2 snd_mpu401_uart,snd_seq_midi
crc_itu_t               1371  1 rt73usb
vga16fb                11385  0 
i2c_viapro              5573  0 
rt2x00usb               9703  1 rt73usb
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
vgastate                8961  1 vga16fb
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
rt2x00lib              27509  2 rt73usb,rt2x00usb
nouveau               467048  2 
led_class               2864  1 rt2x00lib
snd_timer              19098  2 snd_pcm,snd_seq
via_ircc               21745  0 
ttm                    49943  1 nouveau
drm_kms_helper         29297  1 nouveau
mac80211              204922  2 rt2x00usb,rt2x00lib
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
irda                  186556  1 via_ircc
psmouse                63245  0 
drm                   162471  4 nouveau,ttm,drm_kms_helper
snd                    54148  15 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               3978  0 
joydev                  8708  0 
via_agp                 5310  1 
i2c_algo_bit            5028  1 nouveau
crc_ccitt               1339  1 irda
cfg80211              126485  2 rt2x00lib,mac80211
soundcore               6620  1 snd
ppdev                   5259  0 
agpgart                31724  3 ttm,drm,via_agp
lp                      7028  0 
parport_pc             25962  1 
shpchp                 28820  0 
parport                32635  3 ppdev,lp,parport_pc
8139too                18545  0 
usbhid                 36110  0 
hid                    67032  1 usbhid
ohci1394               26950  0 
8139cp                 16186  0 
pata_via                7272  3 
ieee1394               81181  1 ohci1394
mii                     4381  2 8139too,8139cp
floppy                 53016  0 

```

There you are sir.

---

### Post by chili555 on 2010-08-04
The loaded modules look correct; I don't see any conflicts. Let's look at two things. First, some routers use a mixed WPA and WPA2 mode. Linux, or probably wpa_supplicant, doesn't work and play well with mixed mode. Please be sure your router is set to WPA or WPA2 and not mixed mode.

Second, let's try a module parameter to see if it helps. Please do:```
sudo rmmod -f rt73usb
sudo modprobe rt73usb nohwcrypt=1
```Now are you able to connect?

---

### Post by Captain Alex on 2010-08-04
It still won't connect to the internet.

When I open firefox it gives me the "Server not found" page. So could it maybe be firefox?

I also tried using the email client to send myself an email. That didn't work either.

I forgot to mention, the router we use here is a Wireless-G 2.4GHz Linksys. Comcast is our ISP. I'm not sure if that has any relevance.

---

### Post by chili555 on 2010-08-04
Let's go a bit deeper in diagnostics. Please post:```
iwconfig
cat /etc/resolv.conf
ping -c3 74.125.67.147
```Thanks.

---

### Post by Captain Alex on 2010-08-04
```
captain@The-Ship-Of-Capn-Alex:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Sage house"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:39:80:5D:7E   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



captain@The-Ship-Of-Capn-Alex:~$ cat /etc/resolv.conf
# Generated by NetworkManager



captain@The-Ship-Of-Capn-Alex:~$ ping -c3 74.125.67.147
connect: Network is unreachable

```

---

### Post by chili555 on 2010-08-04
Very mysterious. This looks like you are connected:> wlan0     IEEE 802.11bg  ESSID:"[COLOR="Red"]Sage house[/COLOR]"  
          Mode:Managed  Frequency:2.437 GHz  [COLOR="Red"]Access Point: 00:18:39:80:5D:7E   [/COLOR]
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=66/70  Signal level=-44 dBm But this looks like you are not:> $ ping -c3 74.125.67.147
connect: [COLOR="Red"]Network is unreachable[/COLOR]I wonder if the kernel has any interesting messages. Please post:```
sudo cat /var/log/syslog | grep -e wlan -e Network
```If the output is lengthy, just post the last 25 lines or so.

---

### Post by Captain Alex on 2010-08-04
```
Aug  4 16:14:22 The-Ship-Of-Capn-Alex NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  (wlan0): device state change: 5 -> 3 (reason 38)
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  (wlan0): deactivating device (reason: 38).
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) starting connection 'Sagehouse'
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0/wireless): connection 'Sagehouse' has security, and secrets exist.  No new secrets needed.
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Config: added 'ssid' value 'Sagehouse'
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Config: added 'mode' value '1'
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Config: added 'frequency' value '2412'
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-NONE'
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Config: added 'proto' value 'WPA'
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Config: added 'pairwise' value 'NONE'
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Config: added 'group' value 'TKIP'
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Config: set interface ap_scan to 2
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> completed
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Sagehouse'.
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Aug  4 16:14:49 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol tcp --destination-port 53 --jump ACCEPT
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol udp --destination-port 53 --jump ACCEPT
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol tcp --destination-port 67 --jump ACCEPT
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol udp --destination-port 67 --jump ACCEPT
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --in-interface wlan0 --jump REJECT
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --out-interface wlan0 --jump REJECT
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --in-interface wlan0 --out-interface wlan0 --jump ACCEPT
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --source 10.42.43.0/255.255.255.0 --in-interface wlan0 --jump ACCEPT
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <info>  Executing: /sbin/iptables --table filter --insert FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface wlan0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <info>  Executing: /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! 10.42.43.0/255.255.255.0 --jump MASQUERADE
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <info>  Starting dnsmasq...
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <debug> [1280952890.694445] nm_dnsmasq_manager_start(): Command line: /usr/sbin/dnsmasq --no-hosts --keep-in-foreground --bind-interfaces --except-interface=lo --clear-on-reload --strict-order --listen-address=10.42.43.1 --dhcp-range=10.42.43.10,10.42.43.100,60m --dhcp-option=option:router,10.42.43.1 --dhcp-lease-max=50 --pid-file=/var/run/nm-dnsmasq-wlan0.pid
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <debug> [1280952890.696135] nm_dnsmasq_manager_start(): dnsmasq started with pid 6270
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <debug> [1280952890.696862] periodic_update(): Roamed from BSSID 00:00:00:00:00:00 (Sagehouse) to (none) ((none))
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) successful, device activated.
Aug  4 16:14:50 The-Ship-Of-Capn-Alex NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug  4 16:14:58 The-Ship-Of-Capn-Alex NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> associated
Aug  4 16:14:58 The-Ship-Of-Capn-Alex NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed

```

---

### Post by Captain Alex on 2010-08-04
Also, when I posted the original one where it looks like I was connected, it was still connecting to the network. I should have mentioned that.

---

### Post by Captain Alex on 2010-08-04
Also, important note: I just tried to connect to 127.0.0.1 in Firefox and it says "Unable to connect"

So I believe that is the problem as far as Firefox goes, however it doesn't solve my wireless problem.

---

### Post by chili555 on 2010-08-04
From *iwconfig*: > ESSID:"Sage house"From *syslog*:> Config: added 'ssid' value 'Sagehouse'
Did you specify 'Sage  house' somewhere? Network Manager says it's Sagehouse; they are not the same. If you have specified it, please change it.

> /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! 10.42.43.0/255.255.255.0 --jump MASQUERADEIs this an ad-hoc connection; that is, to another computer? Or are you trying to connect to a router? Please let us see:```
route -n
```> Also, important note: I just tried to connect to 127.0.0.1 in Firefox and it says "Unable to connect"
That's normal. Ping bypasses Firefox, your email client, your instant messaging client and if you can't get ping returns, there are fundamental problems outside Firefox. Can you connect, in Firefox to [http://127.0.0.1:631?](http://127.0.0.1:631?) That's the interface for printing.

---

### Post by Captain Alex on 2010-08-04
I tried to create a connection to 'SageHouse' but the actual network that I'm trying to connect to is 'Sage House'

I just looked at 'SageHouse' and it is set to ad-hoc. However 'Sage House' is set to infrastructure. Which is probably why 'SageHouse' always auto-connects right after 'Sage House' fails to connect.

I tried the printer interface, and it connected properly.

Here is all the settings for 'Sage House'

> Connection Name: Auto Sage House
Connect automatically: Yes
SSID: Sage House
Mode: Infrastructure
BSSID: --
MAC address: --
MTU: automatic
Available to all users: yes

IPv4 Settings:
Method: Automatic (DHCP)
DHCP client ID: --

IPv6 Settings:
Method: Ignore

Wireless Security:
Security WPA & WPA2 Personal


Whenever I try to use route -n it comes up with no data on the kernel IP routing table. just the table names.

It won't connect at all, I deleted the SageHouse ad-hoc network, since all that was doing was connecting me to the ad-hoc.

however when i did try a route -n on the ad hoc 'Sagehouse' thie came up.

```

Destination     Gateway    Genmask  Flags   Metric   Ref    Use   Iface
10.42.43.0   0.0.0.0    255.255.255.0    U   2   0   0   wlan0
169.254.0.0   0.0.0.0   255.255.0.0   U   1000   0   0   wlan0
```

---

### Post by chili555 on 2010-08-04
> Wireless Security:
Security WPA & WPA2 Personal Here's what I said previously:> some routers use a mixed WPA and WPA2 mode. Linux, or probably wpa_supplicant, doesn't work and play well with mixed mode. Please be sure your router is set to WPA or WPA2 and not mixed mode.Can you please check the router and make sure it's set to WPA ***or*** WPA2 and not both?

---

### Post by Captain Alex on 2010-08-05
It's definitely WPA, it's just in my ubuntu version for the wireless connection it has WPA & WPA2 as the type of security. not just WPA or WPA2.

---

### Post by Captain Alex on 2010-08-05
[http://ubuntuforums.org/showthread.php?t=141589](http://ubuntuforums.org/showthread.php?t=141589)

This is pretty much the exact same problem I am having.

So should I try to get a wpasupplicant?

And if so, where do I get one, and what do they do?

---

### Post by DaveVM on 2010-10-31
Folks,

I too am having this problem, New Lenovo G550 with the ill fated Broadcom 4312/4315 chipset. No connection wirelessly.

The router is set for WPA-PSK and the SSID is NOT broadcast. (Too many other networks in neighborhood) Security is key here.

Running 10.10.

I suspect the problem is in authentification with 10.10 as other Win7 wireless computers can connect without problem.

From reading here it seems connections were broke about the time Ubuntu 10 came along. If so what changed?

Looking for a fix to resolve this on the G550. Where do I start?

Please be gentle, while I'm versed, in DOS and Windows, Linux I'm still a NuBee.

Thank You

Dave

1st Edit: I removed v10.10 and installed v10.04 for NetBooks and it works just fine! So it is a Ubuntu v10.10 Desktop issue.

So now I'll try v10.04 LTS because I do not care for the Unity Shell, as there does not at first look seem to be an easy way to adjust the shell icon spacing and so forth.

2nd Edit: Tried 10.04 Desktop LTS and the wireless (bcm4312) is working fine! v10.10 Desktop has a problem.

Hope this helps someone.

---

