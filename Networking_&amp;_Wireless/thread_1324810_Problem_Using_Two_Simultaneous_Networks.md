---
title: "Problem Using Two Simultaneous Networks"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by b.bhargav on 2009-11-12
Hi Friends,
I'm in to a small problem.

I use two networks to connect to the Internet.

One is an Ethernet network with the IP address 10.35.XXX.XXX. (For my Office & Highspeed internet). It connects to the internet through a proxy server/firewall. I configured it through "System >> Preferences >> Network Proxy".

And the other is my personal Wifi Network. IP address 192.168.1.1 (Low Speed personal network). 

Initially I've configured ubuntu to connect using ethernet connection and it is working fine.

My proxy server blocks some websites like facebook/gmail etc and for this purpose I need the Wifi network. I've successfully connected to the Wifi network.But I'm unable to access the Internet. I've removed the proxy server settings from "System >> Preferences >> Network Proxy" which are not required by the Wifi Network.

Please help me with this Issue.
Thank you,
Regards
Bhargav

---

### Post by efflandt on 2009-11-12
Depending upon how you have the network connections configured, you likely have 2 default routes, and unless an IP is specific to one LAN or the other, it will use the first default route it finds (to 10.35.x.x network).

You need more specific routing to route desired public IP ranges to your 192.168.1.x gateway.  **man route**

Or you can add routes with Networks Connections tool.

---

### Post by b.bhargav on 2009-11-13
Hi, Thank you.
But I'm a bit new to linux and I'm not sure how to do it.
I've entered the command "route" in terminal and here is the output
```

souji@BSNL-PC25:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
10.34.129.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 wlan0

```

I want to switch entirely to my wifi connection. I've removed my ethernet cable, switched back the proxy settings in the network manager. 

I can open my router home page @ 192.168.1.1 But I'm unable to access any websites.

Please help me and direct me further as what should be done.

Thank you,
Regards
Bhargav

---

### Post by b.bhargav on 2009-11-13
Here is the complete Information in my situation :
```
$lspci
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


``````

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:a9:c2:6a:ea  
          inet addr:10.34.129.250  Bcast:10.34.129.255  Mask:255.255.255.0
          inet6 addr: fe80::213:a9ff:fec2:6aea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:107755 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32007 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70827709 (70.8 MB)  TX bytes:4419745 (4.4 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:150 errors:0 dropped:0 overruns:0 frame:0
          TX packets:150 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18902 (18.9 KB)  TX bytes:18902 (18.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:be:55:ee  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:77ff:febe:55ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1170310 (1.1 MB)  TX bytes:9791462 (9.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-BE-55-EE-62-65-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


``````
$iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Wiii"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:50:F1:12:12:10   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


``````

$ lsmod
Module                  Size  Used by
nvidia               8873700  0 
nls_iso8859_1           3740  0 
nls_cp437               5372  0 
vfat                   10716  0 
fat                    51452  1 vfat
usb_storage            52544  0 
ndiswrapper           185404  0 
binfmt_misc             8356  1 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
ppdev                   6688  0 
snd_hda_codec_idt      59844  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
arc4                    1660  2 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
ecb                     2524  2 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
iwl3945                77212  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwlcore               112508  1 iwl3945
pcmcia                 36808  0 
snd                    59204  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
joydev                 10272  0 
iptable_filter          3100  0 
soundcore               7264  1 snd
mac80211              181236  2 iwl3945,iwlcore
ip_tables              11692  1 iptable_filter
led_class               4096  2 iwl3945,iwlcore
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
x_tables               16544  1 ip_tables
psmouse                56180  0 
serio_raw               5280  0 
sony_laptop            31972  0 
yenta_socket           24200  1 
tifm_7xx1               5372  0 
cfg80211               93052  3 iwl3945,iwlcore,mac80211
tifm_core               7832  1 tifm_7xx1
lp                      8964  0 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
parport                35340  2 ppdev,lp
btusb                  11856  2 
usbhid                 38208  0 
sky2                   46560  0 
video                  19380  0 
output                  2780  1 video
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
intel_agp              27484  0 
agpgart                34988  2 nvidia,intel_agp


``````

$ sudo lshw -C network

  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1b:77:be:55:ee
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.2 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:31 memory:fa000000-fa000fff
  *-network
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 16
       serial: 00:13:a9:c2:6a:ea
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=10.34.129.250 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:fc000000-fc003fff ioport:6000(size=256)


``````

$uname -mr
2.6.31-14-generic i686

``````

$sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                         Ignoring unknown interface eth0=eth0.
Ignoring unknown interface wlan0=wlan0.


```

---

### Post by Iowan on 2009-11-13
A few things: 
Are your addresses DHCP or static?
Your **route** shows no default gateway (**man route** can provide some information) You should be able to set one up for static address - DHCP should provide the address.
What are you using for DNS? Information should be in */etc/resolv.conf*. Again, DHCP should provide it - static address will need to have it set up.

---

### Post by b.bhargav on 2009-11-14
> **Iowan said:**
> A few things: 
Are your addresses DHCP or static?
Your **route** shows no default gateway (**man route** can provide some information) You should be able to set one up for static address - DHCP should provide the address.
What are you using for DNS? Information should be in */etc/resolv.conf*. Again, DHCP should provide it - static address will need to have it set up.

For the Ethernet connection the IP address is static.

For the Wifi its DHCP.

I've switched back to Ubuntu 9.04 and I've had a bit of success with it.

Is there any stability / security problem sticking to 9.04 cause I've heard a lot of bad reviews about 9.10 and 9.04 is working fine for me now ?

Thank you :)

---

### Post by Iowan on 2009-11-14
Until earlier this week, this machine still ran Gutsy (7.10), now it's been upgraded to Hardy. My laptop will probably stay Jaunty (9.04) until a few more of Karmic's rough edges are polished...

---

### Post by b.bhargav on 2009-11-26
> **Iowan said:**
> Until earlier this week, this machine still ran Gutsy (7.10), now it's been upgraded to Hardy. My laptop will probably stay Jaunty (9.04) until a few more of Karmic's rough edges are polished...

I think 9.04 is fine for me as of now...
I'm a Linux noob but I'm picking up the essence of Ubuntu now... I feel its better than win in most of the cases.

Many thanks to all those people who are coming forward to help noobs like me in here...:popcorn::popcorn:

I like this community friends...

Have a good day

---

