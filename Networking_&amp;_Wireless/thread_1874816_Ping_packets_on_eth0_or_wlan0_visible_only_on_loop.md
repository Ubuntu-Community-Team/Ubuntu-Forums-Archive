---
title: "Ping packets on eth0 or wlan0 visible only on loopback"
date: 2011-11-03
forum: Networking &amp; Wireless
---

### Post by bert_greenIT on 2011-11-03
Hi,

When I ping my own Ip address on eth0 or wlan0, icmp echo and requests are only visible on loopback with tcpdump. 

Is it normal ? why ?

Any explanation would be great. 
Here is my configuration :
[FONT=Courier New]Asus N53Jg Laptop
Linux N53Jg 2.6.38-12-generic #51-Ubuntu SMP Wed Sep 28 14:27:32 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux[/FONT]
Ubuntu 10.04 Gnome Desktop

[FONT=Courier New]$ lspci
...
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
...[/FONT]

[FONT=Courier New]$ lsmod
iptable_filter         12810  0 
ip_tables              27456  1 iptable_filter
x_tables               29581  2 iptable_filter,ip_tables
cryptd                 20510  0 
aes_x86_64             17208  1 
aes_generic            38279  1 aes_x86_64
binfmt_misc            17565  1 
pci_stub               12622  1 
vboxpci                23190  0 
vboxnetadp             13382  0 
vboxnetflt             23435  0 
vboxdrv               286726  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_realtek   336771  1 
joydev                 17606  0 
nvidia              10709116  0 
snd_hda_intel          33176  2 
snd_hda_codec         103804  2 snd_hda_codec_realtek,snd_hda_intel
usbhid                 46956  0 
snd_hwdep              13604  1 snd_hda_codec
arc4                   12529  2 
hid                    91020  1 usbhid
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
uvcvideo               72195  0 
ath9k                 118238  0 
snd_seq_midi_event     14899  1 snd_seq_midi
videodev               82052  1 uvcvideo
mac80211              294370  1 ath9k
i915                  515078  7 
v4l2_compat_ioctl32    17078  1 videodev
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           13851  1 ath9k
psmouse                73535  0 
ath9k_hw              323077  2 ath9k,ath9k_common
asus_laptop            24173  0 
drm_kms_helper         42394  1 i915
intel_ips              18097  0 
serio_raw              13166  0 
ath                    23773  2 ath9k,ath9k_hw
snd                    67382  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   227534  3 i915,drm_kms_helper
sparse_keymap          13898  1 asus_laptop
cfg80211              178528  3 ath9k,mac80211,ath
i2c_algo_bit           13400  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  4 
libahci                26642  1 ahci
atl1c                  41171  0 

$ ifconfig
eth0      Link encap:Ethernet HWaddr bc:ae:c5:0a:4a:2d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:48 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:2538 erreurs:0 :0 overruns:0 frame:0
          TX packets:2538 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:212808 (212.8 KB) Octets transmis:212808 (212.8 KB)

wlan0     Link encap:Ethernet  HWaddr 48:5d:60:67:4e:36  
          inet adr:192.168.0.15  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::4a5d:60ff:fe67:4e36/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:21832 erreurs:0 :0 overruns:0 frame:0
          TX packets:19265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:22465316 (22.4 MB) Octets transmis:4084647 (4.0 MB)

$ ping 192.168.0.15
PING 192.168.0.15 (192.168.0.15) 56(84) bytes of data.
64 bytes from 192.168.0.15: icmp_req=1 ttl=64 time=0.034 ms
64 bytes from 192.168.0.15: icmp_req=2 ttl=64 time=0.031 ms
64 bytes from 192.168.0.15: icmp_req=3 ttl=64 time=0.034 ms
64 bytes from 192.168.0.15: icmp_req=4 ttl=64 time=0.043 ms
64 bytes from 192.168.0.15: icmp_req=5 ttl=64 time=0.038 ms
64 bytes from 192.168.0.15: icmp_req=6 ttl=64 time=0.035 ms
64 bytes from 192.168.0.15: icmp_req=7 ttl=64 time=0.035 ms
64 bytes from 192.168.0.15: icmp_req=8 ttl=64 time=0.038 ms
--- 192.168.0.15 ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 6998ms
rtt min/avg/max/mdev = 0.031/0.036/0.043/0.003 ms

$ tcpdump -ni lo icmp
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on lo, link-type EN10MB (Ethernet), capture size 65535 bytes
01:41:52.572953 IP 192.168.0.15 > 192.168.0.15: ICMP echo request, id 2671, seq 49, length 64
01:41:52.572978 IP 192.168.0.15 > 192.168.0.15: ICMP echo reply, id 2671, seq 49, length 64
01:41:53.572937 IP 192.168.0.15 > 192.168.0.15: ICMP echo request, id 2671, seq 50, length 64
01:41:53.572962 IP 192.168.0.15 > 192.168.0.15: ICMP echo reply, id 2671, seq 50, length 64
01:41:54.572936 IP 192.168.0.15 > 192.168.0.15: ICMP echo request, id 2671, seq 51, length 64
01:41:54.572955 IP 192.168.0.15 > 192.168.0.15: ICMP echo reply, id 2671, seq 51, length 64
01:41:55.572905 IP 192.168.0.15 > 192.168.0.15: ICMP echo request, id 2671, seq 52, length 64
01:41:55.572926 IP 192.168.0.15 > 192.168.0.15: ICMP echo reply, id 2671, seq 52, length 64
01:41:56.572933 IP 192.168.0.15 > 192.168.0.15: ICMP echo request, id 2671, seq 53, length 64
01:41:56.572956 IP 192.168.0.15 > 192.168.0.15: ICMP echo reply, id 2671, seq 53, length 64
10 packets captured
20 packets received by filter
0 packets dropped by kernel

$ tcpdump -ni wlan0 icmp
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on wlan0, link-type EN10MB (Ethernet), capture size 65535 bytes
^C
0 packets captured
0 packets received by filter
0 packets dropped by kernel

[/FONT]

---

