---
title: "Intel PRO/Wireless 3945ABG works intermittently since Jaunty upgrade"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by RyanGT on 2009-05-07
I have a Dell Latitude D820 with an Intel 3945ABG wireless card.  I just upgrade to Jaunty Jackolope (9.04) and am having trouble (I have had issues with this laptop and linux for as long as I have had it).  I am at home and the wireless connection is currently intermittent.  Actually, I have a script that I wrote to run at login when I was running Hardy Heron.  If I run this script in Jaunty, the wireless works for a few minutes.  Then something happens and I loose the connection.  If I re-run the script, I re-connect.  Here is the script:


#!/bin/bash
ifconfig wlan0 up
iwlist wlan0 scanning
iwconfig wlan0 essid MercyNet
iwconfig wlan0 key s:eZWha870-23:@
dhclient
#this script is called by /etc/rc.local

I assume some wireless manager in Jaunty is messing with the connection.

Here is the output of commands recommended to provide info for wireless posts:

>> lspci -nn | grep 'Intel'

0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

>> ifconfig

wlan0     Link encap:Ethernet  HWaddr 00:19:d2:bb:c7:b8  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d2ff:febb:c7b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1113 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1128790 (1.1 MB)  TX bytes:206392 (206.3 KB)

>> iwconfig

wlan0     IEEE 802.11abg  ESSID:"MercyNet"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:1D:5A:C2:2A:A1   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=85/100  Signal level:-48 dBm  Noise level=-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

>> lsmod | grep "iwl3945"

iwl3945                97912  0 
mac80211              217208  1 iwl3945
led_class              12036  1 iwl3945
cfg80211               38032  2 iwl3945,mac80211

!!!  This one seems most helpful !!!
>> dmesg | grep "wlan0"

[   17.484777] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.061788] wlan0: authenticate with AP 00:1d:5a:c2:2a:a1
[   20.063442] wlan0: authenticated
[   20.063447] wlan0: associate with AP 00:1d:5a:c2:2a:a1
[   20.065404] wlan0: RX AssocResp from 00:1d:5a:c2:2a:a1 (capab=0x431 status=0 aid=1)
[   20.065408] wlan0: associated
[   20.075346] wlan0: authenticate with AP 00:1d:5a:c2:2a:a1
[   20.075371] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   20.077871] wlan0: authenticated
[   20.077879] wlan0: associate with AP 00:1d:5a:c2:2a:a1
[   20.077885] wlan0: mismatch in privacy configuration and mixed-cell disabled - abort association
[   20.272062] wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate
[   39.384321] wlan0: authenticate with AP 00:1d:5a:c2:2a:a1
[   39.386133] wlan0: authenticate with AP 00:1d:5a:c2:2a:a1
[   39.386143] wlan0: authenticated
[   39.386146] wlan0: associate with AP 00:1d:5a:c2:2a:a1
[   39.391365] wlan0: RX AssocResp from 00:1d:5a:c2:2a:a1 (capab=0x431 status=0 aid=1)
[   39.391371] wlan0: associated
[   39.393826] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   49.400036] wlan0: no IPv6 routers present
[   79.495453] wlan0: authenticate with AP 00:1d:5a:c2:2a:a1
[   79.497017] wlan0: authenticated
[   79.497025] wlan0: associate with AP 00:1d:5a:c2:2a:a1
[   79.498896] wlan0: RX ReassocResp from 00:1d:5a:c2:2a:a1 (capab=0x431 status=0 aid=1)
[   79.498901] wlan0: associated
[  804.457425] wlan0: authenticate with AP 00:1d:5a:c2:2a:a1
[  804.460454] wlan0: authenticated
[  804.460461] wlan0: associate with AP 00:1d:5a:c2:2a:a1
[  804.462163] wlan0: RX ReassocResp from 00:1d:5a:c2:2a:a1 (capab=0x431 status=0 aid=1)
[  804.462167] wlan0: associated
[  832.251074] wlan0: direct probe to AP 00:1d:5a:c2:2a:a1 try 1
[  832.267527] wlan0 direct probe responded
[  832.267536] wlan0: authenticate with AP 00:1d:5a:c2:2a:a1
[  832.268975] wlan0: authenticated
[  832.268983] wlan0: associate with AP 00:1d:5a:c2:2a:a1
[  832.270633] wlan0: RX AssocResp from 00:1d:5a:c2:2a:a1 (capab=0x431 status=0 aid=1)
[  832.270639] wlan0: associated
[  832.273001] wlan0: disassociating by local choice (reason=3)
[  844.591698] wlan0: deauthenticated
[  844.593808] wlan0: authenticate with AP 00:1d:5a:c2:2a:a1
[  844.595248] wlan0: authenticated
[  844.595254] wlan0: associate with AP 00:1d:5a:c2:2a:a1
[  844.597092] wlan0: RX ReassocResp from 00:1d:5a:c2:2a:a1 (capab=0x431 status=0 aid=1)
[  844.597097] wlan0: associated
[  883.645266] wlan0: authenticate with AP 00:1d:5a:c2:2a:a1
[  883.646701] wlan0: authenticated
[  883.646706] wlan0: associate with AP 00:1d:5a:c2:2a:a1
[  883.650075] wlan0: RX ReassocResp from 00:1d:5a:c2:2a:a1 (capab=0x431 status=0 aid=1)
[  883.650081] wlan0: associated
[ 1147.252690] wlan0: authenticate with AP 00:1d:5a:c2:2a:a1
[ 1147.254114] wlan0: authenticated
[ 1147.254121] wlan0: associate with AP 00:1d:5a:c2:2a:a1
[ 1147.255862] wlan0: RX ReassocResp from 00:1d:5a:c2:2a:a1 (capab=0x431 status=0 aid=1)
[ 1147.255867] wlan0: associated
[ 1263.150624] wlan0: authenticate with AP 00:1d:5a:c2:2a:a1
[ 1263.152109] wlan0: authenticated
[ 1263.152115] wlan0: associate with AP 00:1d:5a:c2:2a:a1
[ 1263.153889] wlan0: RX ReassocResp from 00:1d:5a:c2:2a:a1 (capab=0x431 status=0 aid=1)
[ 1263.153895] wlan0: associated
[ 1502.283306] wlan0: authenticate with AP 00:1d:5a:c2:2a:a1
[ 1502.284744] wlan0: authenticated
[ 1502.284750] wlan0: associate with AP 00:1d:5a:c2:2a:a1
[ 1502.290339] wlan0: RX ReassocResp from 00:1d:5a:c2:2a:a1 (capab=0x431 status=0 aid=1)
[ 1502.290346] wlan0: associated
[ 1686.780939] wlan0: authenticate with AP 00:1d:5a:c2:2a:a1
[ 1686.782364] wlan0: authenticated
[ 1686.782371] wlan0: associate with AP 00:1d:5a:c2:2a:a1
[ 1686.784700] wlan0: RX ReassocResp from 00:1d:5a:c2:2a:a1 (capab=0x431 status=0 aid=1)
[ 1686.784706] wlan0: associated


What does "disassociating by local choice (reason=3)" mean?



More commands:

>> sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:bb:c7:b8
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.107 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg


>> iwlist scan

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:5A:C2:2A:A1
                    ESSID:"MercyNet"
                    Mode:Master
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=87/100  Signal level:-46 dBm  Noise level=-85 dBm
                    Encryption key:on
                    IE: Unknown: 00084D657263794E6574
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030103
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000071e72e181
                    Extra: Last beacon: 4ms ago


>> lsb_release -d

Description:	Ubuntu 9.04

>> uname -mr

2.6.28-11-generic i686

>> sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                                                                                  Ignoring unknown interface wlan0=wlan0.

(after re-running my script)

>> sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...          [ OK ]


Any help would be appreciated.  I don't really want to have to go back to Hardy, but I can't re-run my script every 3 minutes to get an internet connection either.

Thanks,

Ryan

---

### Post by coffeeaddict22 on 2009-05-07
In lshw -C network you've got a logical name of wmaster0; this is a "dummy name" the kernel uses to pass messages.  Usually you get this if there's two drivers; in the upgrade scenario often your ndiswrapper driver from Intrepid is still lying around somewhere.  There's more to your output from lshw; look through it for where the wlan is getting its logical name.
You're going to have to find the other driver and disable it.

---

### Post by RyanGT on 2009-05-07
Thanks for the reply.  I actually did a fresh install from a CD, so my old install should have been completely wiped out.  But, the rest of what you are saying makes sense.  Is lshw the best way to find the other driver?

---

### Post by RyanGT on 2009-05-07
I removed ndiswrapper and blacklisted ipw3945 (the only other driver I remember using).  Still no luck.  Any ideas?

---

### Post by coffeeaddict22 on 2009-05-07
What you're looking for is the driver that's pinched the wlan0 address.  there's a few ways of doing it; ```
lsmod
``` will list all your running modules; if you have a fair idea of what the problem might be, it can show you modules you thought weren't there (like ndiswrapper).  lshw lists hardware, and is good for showing what's driving it, as well as what the logical name is (which is what looks like part of your problem at present).  

Once you've got the driver sorted, then you can move on to sort out how the PC talks to it.  That's when you can use ifconfig and iwconfig, iwlist and a few other commands.

A fresh install works... but.  If you keep your home folder, or back it up and reinstall, there's a truckload of config files in it.  They start with a . and Linux treats them as hidden files; because they can be referenced by the system in it's startup scripts, the only way to completely start afresh is to explicitly only transfer files you know you want.  Which is a bit of a hassle, so doesn't get done and, well, you can guess what happens if a previous setup for, say, the network settings is inadvertently copied into your new setup.

---

### Post by RyanGT on 2009-05-08
Here is the result of lsmod:

>> lsmod

Module                  Size  Used by
ipt_MASQUERADE         10752  1 
xt_state               10112  1 
ipt_REJECT             11136  2 
xt_tcpudp              11008  4 
iptable_filter         10752  1 
nf_nat_h323            14336  0 
nf_conntrack_h323      56648  1 nf_nat_h323
nf_nat_pptp            11136  0 
nf_conntrack_pptp      14212  1 nf_nat_pptp
nf_conntrack_proto_gre    13572  1 nf_conntrack_pptp
nf_nat_proto_gre       10372  1 nf_nat_pptp
nf_nat_tftp             9600  0 
nf_conntrack_tftp      12308  1 nf_nat_tftp
nf_nat_sip             14976  0 
nf_conntrack_sip       26260  1 nf_nat_sip
nf_nat_irc             10240  0 
nf_conntrack_irc       13220  1 nf_nat_irc
nf_nat_ftp             10752  0 
nf_conntrack_ftp       15652  1 nf_nat_ftp
iptable_nat            13700  1 
nf_nat                 25876  9 ipt_MASQUERADE,nf_nat_h323,nf_nat_pptp,nf_nat_proto_gre,nf_nat_tftp,nf_nat_sip,nf_nat_irc,nf_nat_ftp,iptable_nat
nf_conntrack_ipv4      21388  4 iptable_nat,nf_nat
nf_conntrack           72008  18 ipt_MASQUERADE,xt_state,nf_nat_h323,nf_conntrack_h323,nf_nat_pptp,nf_conntrack_pptp,nf_conntrack_proto_gre,nf_nat_tftp,nf_conntrack_tftp,nf_nat_sip,nf_conntrack_sip,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_conntrack_ftp,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
ip_tables              19472  2 iptable_filter,iptable_nat
x_tables               23044  6 ipt_MASQUERADE,xt_state,ipt_REJECT,xt_tcpudp,iptable_nat,ip_tables
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56340  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
arc4                    9856  2 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
ecb                    10752  2 
pcmcia                 44748  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
psmouse                61972  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iwl3945                97912  0 
intel_agp              34108  0 
yenta_socket           32396  1 
rsrc_nonstatic         19328  1 yenta_socket
mac80211              217208  1 iwl3945
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13316  0 
dcdbas                 15264  0 
agpgart                42696  1 intel_agp
pcmcia_core            43540  3 pcmcia,yenta_socket,rsrc_nonstatic
led_class              12036  1 iwl3945
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
cfg80211               38032  2 iwl3945,mac80211
video                  25360  0 
output                 11008  1 video
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
tg3                   131204  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

I don't know for sure what I am looking for, but I don't see ndiswrapper of ipw3945.  I tried blacklisting mac80211 and cfg80211, but it didn't actually work, i.e. I added:

blacklist mac80211
blacklist cfg80211

to /etc/modprobe.d/blacklist.conf

but when I rebooted, they still showed up in lsmod.  Maybe this is because they are called by iwl3945 and it makes sure they are loaded.

Also, I copied my entire home directory to a USB harddrive, but I have copied back very little of it.  So, while I understand that it is possible that something migrated from 8.04, I really doubt it.

What should I try next?  Any modules that look suspicious to you?

Thanks again,

Ryan

---

### Post by RyanGT on 2009-05-08
I think my problem is solved, though I am not 100% sure what solved it.  I think the biggest issue was an error in converting the ascii WEP key to hex.  There may be a bug in how the gnome network-manager converts ascii keys to hex.  Mine had one wrong digit.  I used this at the terminal instead:

perl -e 'print unpack("H*", "ascii key here"), "\n"'

and when I pasted that output into the gnome network-manager gui, my problems seem to have gone away (I also changed it to use DHCP, which it wasn't doing by default).  My connection has been working for 30 or so minutes now (way longer than before).

---

### Post by coffeeaddict22 on 2009-05-08
Well, on the "if it aint broke don't fix it" principle, leave it like that and enjoy!

---

### Post by chili555 on 2009-05-08
> There may be a bug in how the gnome network-manager converts ascii keys to hex.I suggest you report this to the bug tracker for Network Manager. [https://bugs.launchpad.net/ubuntu/+source/network-manager](https://bugs.launchpad.net/ubuntu/+source/network-manager)

---

### Post by k0d3k on 2009-05-08
I am in a similar situation where my wireless works as previously mentioned.  I have a different set of drivers and I use WPA2, could my issue be somewhat related to this?

---

### Post by RyanGT on 2009-05-08
If you are seeing similar behavior, I would say it is possible.  I would try either converting my keys to hex using the perl line I mentioned (don't know if that is possible with WPA) or varying your security options (assuming you have the authority to do that on your network).  If this is your router, try no security at first (with MAC filtering if possible) and work your way up.  With my router and the iwl3945 driver, I can confirm that static 128 bit WEP is working in Jaunty.

---

### Post by k0d3k on 2009-05-08
nevermind, Wicd fixed me all up :) 

I'm good to go, so easy to do..

---

### Post by CAsurfer on 2009-07-22
I have the same wireless card and the same problem of intermittent connectivity, running Jaunty x64. 

Running iwconfig gives:
"""
lo      no wireless extensions
eth0    no wireless extensions
pan0    no wireless extensions
"""

Is this evidence that some essential piece of software is not loaded, or that I'm simply not connected to a network?

Does anybody have an idea of how I might troubleshoot this?

Thanks!

---

