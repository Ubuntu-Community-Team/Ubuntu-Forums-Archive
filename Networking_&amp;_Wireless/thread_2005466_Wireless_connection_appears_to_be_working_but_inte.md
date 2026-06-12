---
title: "Wireless connection appears to be working but internet randomly stops"
date: 2012-06-17
forum: Networking &amp; Wireless
---

### Post by AnotherMuggle on 2012-06-17
Hi,

I have a Virgin Media Super Hub and two very different Ubuntu machines experiencing the same, very strange, symptoms.  One machine is a HP Mini 210 using the Linux STA driver installed through Additional Drivers the other machine is a custom build desktop with a Netgear W111v3 wireless dongle.

The issue is that after some indeterminate amount of time the internet "just stops".  Pages start saying "Problem loading page" and I cannot ping either the router or any external sites, either by name or IP.  The strange thing is Ubuntu seems to think it is still connected to the router and the router still thinks the Ubuntu machine is connected to it.  It just happened this evening after 4hr 44mins of trouble free surfing.  I can always get it working again by simply disconnecting from the network and reconnecting.

Wireless signal is strong and stable before, during and after the strange stop.  I have already switched the router from Mixed Mode to WPA2[AES] only.

Below is some information obtained amid a stopped internet episode.  If anyone can shed any light then I'd be very happy.  

```
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```
NOTE: The above hardware is my netbook, but I get the same symptoms on the desktop machine.

```
Linux UbuBook 3.2.0-25-generic-pae #40-Ubuntu SMP Wed May 23 22:11:24 UTC 2012 i686 i686 i386 GNU/Linux
```

```
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
8: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

```
======================================================================================
                                NetworkManager status
======================================================================================
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
--------------------------------------------------------------------------------------
running         connected       enabled         enabled    enabled         enabled   
```

```

NetworkManager Tool

State: connected (global)

- Device: eth1  [virginmedia1810478] -------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        90:4C:E5:3D:59:C3

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    SKYD8620:        Infra, 4C:17:EB:4D:86:21, Freq 2462 MHz, Rate 54 Mb/s, Strength 94 WPA WPA2
    BradyInside:     Infra, A0:21:B7:5B:BA:61, Freq 2462 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    *virginmedia1810478: Infra, 74:44:01:F4:E4:0C, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    remington:       Infra, 00:24:17:88:69:CB, Freq 2437 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    BTOpenzone-H:    Infra, 02:24:17:F6:97:20, Freq 2442 MHz, Rate 54 Mb/s, Strength 19
    BTHomeHub2-6M9C: Infra, 00:24:17:F6:97:1F, Freq 2442 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    BTFON:           Infra, 02:24:17:F6:97:21, Freq 2442 MHz, Rate 54 Mb/s, Strength 17
    BTHub3-6G5X:     Infra, AC:E8:7B:4D:C4:4B, Freq 2462 MHz, Rate 0 Mb/s, Strength 24 WPA WPA2
    BTFON:           Infra, 8A:E8:7B:4D:C4:4D, Freq 2462 MHz, Rate 0 Mb/s, Strength 22
    BTOpenzone-H:    Infra, 8A:E8:7B:4D:C4:4C, Freq 2462 MHz, Rate 54 Mb/s, Strength 24

  IPv4 Settings:
    Address:         192.168.0.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             194.168.4.100
    DNS:             194.168.8.100


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:26:9E:C3:37:8A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

---

### Post by matt_symes on 2012-06-17
Hi

Is there anything in /var/log/syslog or dmesg after you lose connectivity ?

Post the relevant parts of the logs back here.

Do you still get any problems if you switch encryption off for a while ? (Hide your esid to give at least some (minimal) protection and monitor connections if you do this)

Can you test with a phone or a different computer. Does that lose connectivity at the same time.

Do both machines lose connectivity at the same time ?

Kind regards

---

### Post by AnotherMuggle on 2012-06-18
> **matt_symes said:**
> Hi

Is there anything in /var/log/syslog or dmesg after you lose connectivity ?

Post the relevant parts of the logs back here.

Do you still get any problems if you switch encryption off for a while ? (Hide your esid to give at least some (minimal) protection and monitor connections if you do this)

Can you test with a phone or a different computer. Does that lose connectivity at the same time.

Do both machines lose connectivity at the same time ?

Kind regards

Hi matt_symes,

Thanks for responding.

I have checked dmesg and syslog after connectivity loss and neither seems to have logged anything interesting around that time.

I've not tried turning encryption off, but may try that at some point.  The problem is this issue is seriously intermittent, sometimes it happens shortly after connecting, sometimes after many hours, sometimes not at all.

We have two Android phones in the house and two Windows 7 machines.  We have not noticed this issue with any of those devices.  They continue to work even when one of the Ubuntu machines mysteriously stops.

I'm stumped ](*,)

---

### Post by josephmills on 2012-06-18
> **AnotherMuggle said:**
> Hi,


```
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g [COLOR="Red"]LP-PHY[/COLOR] (rev 01)
```





lets see three things 

```
lspci -nn | grep 14e4 
```
```
lsmod
```
and 
```
apt-cache policy firmware-b43-lpphy-installer firmware-b43-installer firmware-b43legacy-installer 
```
thanks

---

### Post by AnotherMuggle on 2012-06-18
> **josephmills said:**
> lets see three things 

```
lspci -nn | grep 14e4 
```
```
lsmod
```
and 
```
apt-cache policy firmware-b43-lpphy-installer firmware-b43-installer firmware-b43legacy-installer 
```
thanks

Thanks josephmills,

I am in work so I will get the output of those commands this evening.

EDIT: I will get the output from both Ubuntu machines, since they are very different machines but exhibiting the same symptoms.

---

### Post by AnotherMuggle on 2012-06-18
Ok, this problem has occured twice already this evening on my netbook and once on my desktop.

Here is the output of the requested commands, from my netbook:

```
thomas@UbuBook:~$ lspci -nn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

```
thomas@UbuBook:~$ lsmod
Module                  Size  Used by
rfcomm                 38139  12 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
ip6t_LOG               16846  4 
snd_hda_codec_idt      60251  1 
xt_hl                  12465  6 
ip6t_rt                12473  3 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_multiport           12533  2 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
xt_limit               12541  12 
psmouse                71180  0 
xt_tcpudp              12531  18 
btusb                  17912  2 
snd_seq_midi           13132  0 
bluetooth             158438  23 rfcomm,bnep,btusb
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
xt_addrtype            12596  4 
lib80211_crypt_tkip    17275  0 
wl                   2646601  0 
snd_seq_midi_event     14475  1 snd_seq_midi
xt_state               12514  14 
ip6table_filter        12711  1 
ip6_tables             18432  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21974  14 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  1 hp_wmi
i915                  414663  3 
lib80211               14040  2 lib80211_crypt_tkip,wl
snd_timer              28931  2 snd_pcm,snd_seq
mac_hid                13077  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 

```

```
thomas@UbuBook:~$ apt-cache policy firmware-b43-lpphy-installer firmware-b43-installer firmware-b43legacy-installer
firmware-b43-lpphy-installer:
  Installed: (none)
  Candidate: 1:015-9
  Version table:
     1:015-9 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/multiverse i386 Packages
firmware-b43-installer:
  Installed: (none)
  Candidate: 1:015-9
  Version table:
     1:015-9 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/multiverse i386 Packages
firmware-b43legacy-installer:
  Installed: (none)
  Candidate: 1:015-9
  Version table:
     1:015-9 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/multiverse i386 Packages

```

I will get the same information from the desktop if need be.  But as I say they are two very different machines with the same symptoms.

Cheers,
TK

---

### Post by josephmills on 2012-06-19
> **AnotherMuggle said:**
> Ok, this problem has occured twice already this evening on my netbook and once on my desktop.

Here is the output of the requested commands, from my netbook:

```
thomas@UbuBook:~$ lspci -nn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

```
thomas@UbuBook:~$ lsmod
Module                  Size  Used by
rfcomm                 38139  12 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
ip6t_LOG               16846  4 
snd_hda_codec_idt      60251  1 
xt_hl                  12465  6 
ip6t_rt                12473  3 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_multiport           12533  2 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
xt_limit               12541  12 
psmouse                71180  0 
xt_tcpudp              12531  18 
btusb                  17912  2 
snd_seq_midi           13132  0 
bluetooth             158438  23 rfcomm,bnep,btusb
serio_raw              13027  0 
snd_rawmidi            25424  1 snd_seq_midi
xt_addrtype            12596  4 
lib80211_crypt_tkip    17275  0 
wl                   2646601  0 
snd_seq_midi_event     14475  1 snd_seq_midi
xt_state               12514  14 
ip6table_filter        12711  1 
ip6_tables             18432  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21974  14 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
wmi                    18744  1 hp_wmi
i915                  414663  3 
lib80211               14040  2 lib80211_crypt_tkip,wl
snd_timer              28931  2 snd_pcm,snd_seq
mac_hid                13077  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56321  0 

```

```
thomas@UbuBook:~$ apt-cache policy firmware-b43-lpphy-installer firmware-b43-installer firmware-b43legacy-installer
firmware-b43-lpphy-installer:
  Installed: (none)
  Candidate: 1:015-9
  Version table:
     1:015-9 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/multiverse i386 Packages
firmware-b43-installer:
  Installed: (none)
  Candidate: 1:015-9
  Version table:
     1:015-9 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/multiverse i386 Packages
firmware-b43legacy-installer:
  Installed: (none)
  Candidate: 1:015-9
  Version table:
     1:015-9 0
        500 http://gb.archive.ubuntu.com/ubuntu/ precise/multiverse i386 Packages

```

I will get the same information from the desktop if need be.  But as I say they are two very different machines with the same symptoms.

Cheers,
TK

 [COLOR="Red"]LP-PHY [14e4:4315]
hp_wmi                 13652  0 
firmware-b43-lpphy-installer:
  Installed: (none)[/COLOR]


```
 sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```

Then 
```
sudo modprobe b43 
```


Do you have Wireless ?

---

### Post by AnotherMuggle on 2012-06-19
> **josephmills said:**
> [COLOR="Red"]LP-PHY [14e4:4315]
hp_wmi                 13652  0 
firmware-b43-lpphy-installer:
  Installed: (none)[/COLOR]


```
 sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```

Then 
```
sudo modprobe b43 
```


Do you have Wireless ?

Hi josephmills,

What exactly is your line of thinking here?  It looks like these commands are very specific to the broadcom hardware in my netbook but I have a desktop machine which exhibits the exact same symptoms but doesn't use a broadcom wireless card.

Cheers,
TK

---

### Post by josephmills on 2012-06-19
> **AnotherMuggle said:**
> Hi josephmills,

What exactly is your line of thinking here?  It looks like these commands are very specific to the broadcom hardware in my netbook but I have a desktop machine which exhibits the exact same symptoms but doesn't use a broadcom wireless card.

Cheers,
TK

well I do not know what other cards you have on other  machines because you have not posted that. 

if you are unsure about why you should install the drivers that are for you card ON THE machine that you gave info for. 
Please read this 

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Hopes this helps and please give us the info on the other machine so we can see what kinda card that is. 

thanks

---

### Post by AnotherMuggle on 2012-06-19
> **josephmills said:**
> well I do not know what other cards you have on other  machines because you have not posted that. 

if you are unsure about why you should install the drivers that are for you card ON THE machine that you gave info for. 
Please read this 

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

Hopes this helps and please give us the info on the other machine so we can see what kinda card that is. 

thanks

Sorry, I don't mean to challenge you, I'm just not convinced this will help.  Of course, I could be wrong, but I just wanted to be sure you are understanding my problem fully.

Tonight I have used the netbook for a few hours without a signal loss of internet.  And when I do loose internet, the connection to the router still appears to be active, I just can't "use" the connection.  The router thinks the machine is still connected and NetworkManager thinks it's still connected to the router.  Identical symptoms on both machines.

---

### Post by josephmills on 2012-06-19
On the box that you posted for you have the wl or broadcom sta loaded This is the wrong driver for your card 

you need the b43 ([14e4:[COLOR="DarkRed"]4315[/COLOR]])but here is the catch You have a [COLOR="Red"]LP-PHY[/COLOR]  This means that you have a low powered card meaning that you need a different firmware that is not installed. 
([COLOR="red"]firmware-b43-lpphy-installer:
Installed: (none)[/COLOR])

So you need to remove the wl (broadcom sta) and install the correct drivers for you card then file a bug. 

```
ubuntu-bug jockey-gtk 
```
When you get to launchpad and it asks for a summary enter in 
"additional drivers  installed wrong wireless driver"

I also would like to say that I did not think that you where challenging me :) It is good to know why you are typing things into you computer.

---

### Post by AnotherMuggle on 2012-06-20
> **josephmills said:**
> On the box that you posted for you have the wl or broadcom sta loaded This is the wrong driver for your card 

you need the b43 ([14e4:[COLOR="DarkRed"]4315[/COLOR]])but here is the catch You have a [COLOR="Red"]LP-PHY[/COLOR]  This means that you have a low powered card meaning that you need a different firmware that is not installed. 
([COLOR="red"]firmware-b43-lpphy-installer:
Installed: (none)[/COLOR])

So you need to remove the wl (broadcom sta) and install the correct drivers for you card then file a bug. 

```
ubuntu-bug jockey-gtk 
```
When you get to launchpad and it asks for a summary enter in 
"additional drivers  installed wrong wireless driver"

I also would like to say that I did not think that you where challenging me :) It is good to know why you are typing things into you computer.

Ok, thanks, I will try this tonight and report how I get on.  If it cures my netbook I will post details of my desktop.

Cheers,
TK

---

### Post by AnotherMuggle on 2012-06-20
> **AnotherMuggle said:**
> Ok, thanks, I will try this tonight and report how I get on.  If it cures my netbook I will post details of my desktop.

Cheers,
TK

I have installed b43-fwcutter and firmware-b43-lpphy-installer and removed the sta driver and rebooted.  It looks like the b43 driver is in use and everything appears to be working OK.  I think it may have improved network performance aswell, but it may just be my imagination.  Anyway so far, so good, I will give it a week to be certain the strange problem is gone.

Please can you take a look at my desktop information to see if you can see anything strange going on there. 

Thanks again, Tom.

This is the wireless dongle I am currently using:

```
thomas@UbuTop:~$ lsusb | grep -i net
Bus 002 Device 003: ID 0846:4260 NetGear, Inc. WG111v3 54 Mbps Wireless [realtek RTL8187B]

```

```
thomas@UbuTop:~$ lsmod
Module                  Size  Used by
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               252188  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17830  2 
rfcomm                 38139  0 
bluetooth             158438  10 bnep,rfcomm
binfmt_misc            17292  1 
vesafb                 13516  1 
snd_hda_codec_hdmi     31775  4 
arc4                   12473  2 
hid_microsoft          12760  0 
ip6t_LOG               16846  4 
xt_hl                  12465  6 
ip6t_rt                12473  3 
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13139  1 nf_conntrack_ipv6
ipt_REJECT             12512  1 
ipt_LOG                12783  5 
xt_multiport           12533  2 
ppdev                  12849  0 
xt_limit               12541  12 
xt_tcpudp              12531  18 
xt_addrtype            12596  4 
xt_state               12514  14 
ip6table_filter        12711  1 
ip6_tables             18432  3 ip6t_LOG,ip6t_rt,ip6table_filter
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               21974  14 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_multiport,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
rtl8187                56323  0 
mac80211              436455  1 rtl8187
snd_hda_codec_via      46138  1 
cfg80211              178679  2 rtl8187,mac80211
eeprom_93cx6           12653  1 rtl8187
joydev                 17393  0 
nvidia              10962290  40 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
psmouse                72919  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32114  1 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13027  0 
asus_atk0110           17742  0 
mac_hid                13077  0 
snd                    62064  20 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    36570  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0 
hid                    77367  2 hid_microsoft,usbhid

```

This machine also has the following internal network card, but it freezes the system as soon as it connects to a network.  This freeze has occured in every distro I've tried right from way old through to current kernel versions:

```
thomas@UbuTop:~$ lspci -nn | grep -i net
03:01.0 Network controller [0280]: Atheros Communications Inc. AR9227 Wireless Network Adapter [168c:002d] (rev 01)

```

---

### Post by AnotherMuggle on 2012-07-01
I still seem to be intermittently struggling with this issue.  I had another internet disspearance on my desktop machine. It seems totally and utterly random.

Again, everything appears normal except no internet, no ability to ping etc.  Disconnect and reconnect sorts the issue.

Are there any commands I can run when this problem occurs to test what is stopping the connection?

---

### Post by Onesimus on 2012-07-01
@AnotherMuggle
I am experiencing exactly the same symptons as yourself.  

I have a Dell Laptop, a netbook and a variety of desktops that are all able to connect to the internet, ping each other, (download speed seems to have dropped overall since installing 12.04) but then quite randomly loses the connection (though the system doesn't think it has).

I have to disconnect, then reconnect to remedy the situation.

(I was beginning to think it might be something to do with the router, as it was the only constant in the system).

---

### Post by AnotherMuggle on 2012-07-01
> **Onesimus said:**
> @AnotherMuggle
I am experiencing exactly the same symptons as yourself.  

I have a Dell Laptop, a netbook and a variety of desktops that are all able to connect to the internet, ping each other, (download speed seems to have dropped overall since installing 12.04) but then quite randomly loses the connection (though the system doesn't think it has).

I have to disconnect, then reconnect to remedy the situation.

(I was beginning to think it might be something to do with the router, as it was the only constant in the system).

Well I'm glad I'm not the only person experiencing these symptoms.  However my internet connection is no slower in 12.04 than any previous version of Ubuntu and is the same as in Windows.  I have a 10Mb connection and usually get between 9 and 10.

I too pointed my finger at the router for a while but I don't know... none of the Windows machines have an issue and I've tinkered with just about every setting in the router and the issue persists.  I'm convinced there is some library or program in Ubuntu/Linux to blame but I don't have sufficient knowledge to troubleshoot.

---

### Post by Skybolt83JL on 2012-07-01
FWIW I'm seeing the same symptoms with Mythbuntu 12.04 and either the RTL8192 or RT2860 devices in 802.11n mode. Both NICS fail in the same way. An 802.11g NIC with the RT2561 driver works well. My Ubuntu 12.04 laptop with an AR9285 NIC works fine in 802.11n mode.

---

### Post by AnotherMuggle on 2012-07-02
> **Skybolt83JL said:**
> FWIW I'm seeing the same symptoms with Mythbuntu 12.04 and either the RTL8192 or RT2860 devices in 802.11n mode. Both NICS fail in the same way. An 802.11g NIC with the RT2561 driver works well. My Ubuntu 12.04 laptop with an AR9285 NIC works fine in 802.11n mode.

Interesting to hear another similar report.  I disabled N mode to see if it helped but it made no difference.

---

### Post by matt_symes on 2012-07-02
Hi

> **AnotherMuggle said:**
> Interesting to hear another similar report.  I disabled N mode to see if it helped but it made no difference.

Have you ried changing the channel your router is broadcasting on ? Are there many other routers in the area broadcasting on the same channel as yopur router is currently ?

Maybe that's part of the problem.

Open a terminal and type 

```
nm-tool
```to get a list of the routers and frequencies of those routers your card can see. 

Change your routers frequency so it does not clash with others (or at least with as few others as possible)

Kind regards

---

### Post by AnotherMuggle on 2012-07-03
> **matt_symes said:**
> Hi



Have you ried changing the channel your router is broadcasting on ? Are there many other routers in the area broadcasting on the same channel as yopur router is currently ?

Maybe that's part of the problem.

Open a terminal and type 

```
nm-tool
```to get a list of the routers and frequencies of those routers your card can see. 

Change your routers frequency so it does not clash with others (or at least with as few others as possible)

Kind regards

Hi matt_symes,

There are lots of other routers in the area so this is something I have already tinkered with quite a lot.  By default the router channel is set to Auto but I have used an Android app called Wifi Analyzer which scans wireless networks in the area and chosen a channel which is as far out away from the others as possible.  This didn't make a difference, nor did trying with a number of other channels.  The router is back to Auto because it really made no difference.  Looking at the router channel when set to auto it seems to manage to choose a frequency which is free.

Windows boxes never have an issue, but both Ubuntu machines do.  I'm reluctant to believe it's the quality of the wireless signal itself as it's not a huge house.

Thanks for helping.

---

### Post by Onesimus on 2012-07-03
I have absolutely no routers nearby.  The nearest house is at least 1/2 a mile away and I haven't detected any router whatsoever (even using Android's Wifi Analyser) so that might be a red herring.

---

### Post by matt_symes on 2012-07-03
Hi

After you lose connectivity, take a look at your routing table. Does it look correct ?

```
route -n
```What about you ip address ?

```
ifconfig
```Post back the output of these two commands (especially the last one) anyway {after you lose connectivity}. You can mask out the mac address if you like.

(Hmmm. I really struggling to think of things for you to check :(. You're sure there is nothing in any log files ? )

Have you tried connecting to your access point without using NetworkManager ? Doing it the old command line way ? You can do this with wpa_supplicant if you are using WPA(2).

This will implicate/eliminate Network Manager as a cause. That is one of the things i would be looking at next.

Do you know how to do this ?

Kind regards

---

### Post by AnotherMuggle on 2012-07-05
> **matt_symes said:**
> Hi

After you lose connectivity, take a look at your routing table. Does it look correct ?

```
route -n
```What about you ip address ?

```
ifconfig
```Post back the output of these two commands (especially the last one) anyway {after you lose connectivity}. You can mask out the mac address if you like.

(Hmmm. I really struggling to think of things for you to check :(. You're sure there is nothing in any log files ? )

Have you tried connecting to your access point without using NetworkManager ? Doing it the old command line way ? You can do this with wpa_supplicant if you are using WPA(2).

This will implicate/eliminate Network Manager as a cause. That is one of the things i would be looking at next.

Do you know how to do this ?

Kind regards

Hi matt_symes,

Sorry for the late response, I missed the notification somehow.

I can confirm ifconfig all looks OK, but I have never tried route -n, I will be sure to check it out when I get home and compare the output during the next loss of connectivity.

I am fairly sure nothing is appearing in log files.

I think I know how to use wpa_supplicant on the command line, assuming it is similar/same as the Arch way.

Thanks again,
Tom

---

### Post by matt_symes on 2012-07-06
Hi

> **AnotherMuggle said:**
> Hi matt_symes,

Sorry for the late response, I missed the notification somehow.

I can confirm ifconfig all looks OK, but I have never tried route -n, I will be sure to check it out when I get home and compare the output during the next loss of connectivity.

You're seeing this below ?

```
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
```

Any packets errored, dropped, overrun ?

```
RX packets:2212895 errors:0 dropped:0 overruns:0 frame:0
 TX packets:1454775 errors:0 dropped:0 overruns:0 carrier:0
```

> I am fairly sure nothing is appearing in log files.That's a pain.

> I think I know how to use wpa_supplicant on the command line, assuming it is similar/same as the Arch way.

Thanks again,
TomIt's similar. Just remember to stop network manager.

```
sudo service network-manager stop
```Did you ever check to see if it was a power management issue on the cards ? I know it's unlightly as it's two different cards but try disabling PM (now i'm really am grasping at straws :))

Kind regards

---

### Post by adamdonm on 2012-08-08
I made a similar post a few days ago. I too have a virgin superhub. I can connect to it wirelessly no problem but after a few minutes of browsing the Internet I can't load anymore pages, although it still says I am connected. I have to disconnect and connect again.

I have a small feeling that it's something to do with the superhub. 

I say this because I also have a bt connection at home. It's a bt total broadband hub. I can connect to that perfectly and browse the Internet for hours. I don't lose connection once. So in other words, I get no problem using my bt line, but I get a problem with my virgin line, just like everybody else in this thread. 

I have a wireless router that's not in use. What I will do is turn my superhub into a modem and use the wireless router with it. Hopefully that will sort out the problem. Will let you know how it goes.

---

### Post by omelette on 2012-08-09
> **AnotherMuggle said:**
> Well I'm glad I'm not the only person experiencing these symptoms.  However my internet connection is no slower in 12.04 than any previous version of Ubuntu and is the same as in Windows.  I have a 10Mb connection and usually get between 9 and 10.

I too pointed my finger at the router for a while but I don't know... none of the Windows machines have an issue and I've tinkered with just about every setting in the router and the issue persists.  I'm convinced there is some library or program in Ubuntu/Linux to blame but I don't have sufficient knowledge to troubleshoot.

I hate to admit it,but I too take comfort from hearing others are suffering with this problem. :) I've had just posted about this as well, but it appears that only my Dell laptop suffers from this, a Zotac mini-pc seems symptom-free, and both are being supplied by the same router.

What you might try is giving Ndiswrapper a go with native M$ drivers - my laptop seems perfect now with this installed, although the mini-pc has always worked fine as far as I'm aware and that uses native Linux wireless drivers.

---

