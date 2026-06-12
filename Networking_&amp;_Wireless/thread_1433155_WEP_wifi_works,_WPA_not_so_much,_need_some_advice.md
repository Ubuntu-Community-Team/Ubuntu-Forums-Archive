---
title: "WEP wifi works, WPA not so much, need some advice"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by bushmaster2000 on 2010-03-18
I've been using ubuntu 9.10 on my Sony vaio laptop connected at my house for some time. At home I have a dlink with wep security.
 
However now at work we have a Cisco wifi access point and they're using WPA1 with TKIP. I can't get my laptop to connect to this. I did some searching and it seems like the solution people went with that fixed the problem was to install wcid, so i did and it didn't help although I do get more info now.
 
So here's what happens in wcid
-The SSID is in the list so i click properties, put in the key, set tcp/ip stuff for automatic
-I click the Use Encryption checkbox, select WPA 1/2 Passphrase and type the key in.
-under wcid Prefs>Advanced i have WPA driver set to wext and backend to external
 
Wheni click connect it says
 
SSID Validating authentication then after a few seconds it changes to
none Validating authentication then a minute passes by and i get
obtaining IP address then another long delay and an error, unable to get IP address.
 
Now I assume when it switches to 'none' that it's no longer connecting to my SSID and it's just trying to connect to an open access point ? 
 
To troubleshoot i've done things like manually setup the tcp/ip information and i've changed some of the drivers in prefs>advanced but I still keep getting the same pattern of events.
 
Any help would be appreciated. Like i said, i take the same laptop home every night and connect to my home Dlink/Wep wifi with no issues. It's just this Cisco/Wpa setup at work I can't get on for some reason (they don't use mac address filtering either, i should just need to provide the correct key which I have and get on).

---

### Post by bushmaster2000 on 2010-03-19
up....   hoping someone sees this today who might be able to advise ??

---

### Post by aeiah on 2010-03-19
have you tried the other WPA methods other than wext?

incidentally, when you do get WPA working you should really think about moving away from WEP at home. its not very secure and the methods used to hack WEP are very well known.

---

### Post by aeiah on 2010-03-19
also, you should probably detail what wireless card you have and what modules you're using. you can find them in the relevant areas of 
```

lspci

```
and
```

lsmod

```

---

### Post by bushmaster2000 on 2010-03-19
Ya, i know WEP's not great for security, i have some legacy WEP only devices though which is why i'm stuck for now.  I also do mac filtering to at least try and add another layer of security.

Anyway, yes i've tried some of the other options besides wext.  I haven't tried them all though, i've tired hostap, madwifi and ipw.  

The results for LSPCI are:
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
02:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

and LSMOD 

Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
arc4                    1660  0 
ecb                     2524  0 
lib80211_crypt_wep      3708  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
vboxnetflt             84840  0 
vboxnetadp             78344  0 
vboxdrv               121160  1 vboxnetflt
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
btusb                  11856  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
pcmcia                 36808  0 
sbp2                   22888  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
yenta_socket           24296  2 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
tifm_sd                 9284  0 
joydev                 10240  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tifm_7xx1               5372  0 
rsrc_nonstatic         11644  1 yenta_socket
snd_timer              22276  2 snd_pcm,snd_seq
tifm_core               7832  2 tifm_sd,tifm_7xx1
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
ipw2200               140292  0 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
lp                      8964  0 
libipw                 43148  1 ipw2200
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                56500  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
lib80211                6432  3 lib80211_crypt_wep,ipw2200,libipw
serio_raw               5280  0 
shpchp                 32272  0 
parport                35340  2 ppdev,lp
sony_laptop            31972  0 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
radeon                636000  2 
ttm                    36212  1 radeon
drm                   160032  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
ohci1394               29900  0 
ieee1394               86596  2 sbp2,ohci1394
e100                   32420  0 
mii                     5212  1 e100
intel_agp              27676  1 
agpgart                34988  3 ttm,drm,intel_agp

---

### Post by chili555 on 2010-03-19
Are you sure your Intel 2200 does WPA? Mine didn't. What does this tell us?```
sudo iwlist eth1 auth
```It might look like this if WPA is supported:> eth1      Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP
          Current WPA version :
		Unknown
          Current Key management :
		Unknown
          Current Pairwise cipher :
		Unknown
          Current Pairwise cipher :
		Unknown
          Current TKIP countermeasures : yes
          Current Drop unencrypted : yes
          Current Authentication algorithm :
          Current Receive unencrypted EAPOL : no
          Current Roaming control : yes
          Current Privacy invoked : yes

---

### Post by bushmaster2000 on 2010-03-19
yes it appears to support WPA, here are the results of iwlist:
 
eth1 authentication capabilities :
WAP
WAP2
CIPHER-TKIP
CIPHER-CCMP
Current WAP version unknown
Current key managment unknown
Current pairwise cipher unknown
Current tkip countermeasures : yes
current drop unencrypted no
current authentication algorithm: <blank>
Current receive unencrypted eapol yes
current roaming control yes
current privacy invoked yes
 
 
So it looks like it shouldn't have any issues.  Actually i just booted up into the WindowsXP partition i have on there and connect to the wpa network just fine.  So that would seem to confirm that the issue is Ubuntu.

---

### Post by bushmaster2000 on 2010-03-23
Anyone else have any ideas?  

In summary i can't connect to a WPA-TKIP network in the office but can connect to a wep network in my house just fine. Further, I can connect to the WPA-TKIP network if i boot my Ubuntu 9.10 laptop into windows XP instead and try and connect, it connects up ok.  So that seems to isolate the issue to Ubu9.10

The nic is a 02:0b.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

It does support wpa:
eth1 authentication capabilities :
WAP
WAP2
CIPHER-TKIP
CIPHER-CCMP

And i've changed my network tool to wcid which seemed to be the recommend 'solution' to the problem but it obviously hasn't worked in my case for some reason.

The access point is a Cisco brand air-ap1131ag  .

---

### Post by chili555 on 2010-03-23
Please try:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200 hwcrypto=1
```You might also check:```
sudo less /var/log/wicd/wicd.log
```The file will be quite long, so you might have to PgDn to the end or close to it. Copy and paste the ten or so lines leading up to its failure to connect into a text document and post it here.

You might also change the WPA driver in Wicd to *ipw*. Please see attached.

---

### Post by bushmaster2000 on 2010-03-24
Ok here's the wicd.log file , all these events start from the connect through to the error.  Seems like for whatever reason it's not picking up any dhcp info but it is being handed out since i can connect if i boot into windows.  So I don't believe it's a dhcp server issue.

2010/03/24 13:21:46 :: Connecting to wireless network Metro2
2010/03/24 13:21:46 :: Putting interface down
2010/03/24 13:21:46 :: Releasing DHCP leases...
2010/03/24 13:21:46 :: Setting false IP...
2010/03/24 13:21:46 :: Stopping wpa_supplicant
2010/03/24 13:21:47 :: Flushing the routing table...
2010/03/24 13:21:47 :: Putting interface up...
2010/03/24 13:21:47 :: Generating psk...
2010/03/24 13:21:47 :: Attempting to authenticate...
2010/03/24 13:21:47 :: Running DHCP
2010/03/24 13:21:47 :: Internet Systems Consortium DHCP Client V3.1.2
2010/03/24 13:21:47 :: Copyright 2004-2008 Internet Systems Consortium.
2010/03/24 13:21:47 :: All rights reserved.
2010/03/24 13:21:47 :: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
2010/03/24 13:21:47 :: 
2010/03/24 13:21:48 :: Listening on LPF/eth1/00:0e:35:4b:95:27
2010/03/24 13:21:48 :: Sending on   LPF/eth1/00:0e:35:4b:95:27
2010/03/24 13:21:48 :: Sending on   Socket/fallback
2010/03/24 13:21:52 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
2010/03/24 13:21:57 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
2010/03/24 13:22:05 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
2010/03/24 13:22:19 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
2010/03/24 13:22:39 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
2010/03/24 13:22:51 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
2010/03/24 13:22:53 :: No DHCPOFFERS received.
2010/03/24 13:22:53 :: No working leases in persistent database - sleeping.
2010/03/24 13:23:01 :: DHCP connection failed
2010/03/24 13:23:01 :: exiting connection thread
2010/03/24 13:23:01 :: Sending connection attempt result dhcp_failed

---

### Post by chili555 on 2010-03-24
Is /etc/network/interfaces empty except for the loopback stanzas? If not, would you comment out any lines except loopback?```
auto lo
iface lo inet loopback

#auto wlan0
#iface wlan0 inet dhcp

#auto eth0
#iface eth0 inet dhcp
```Reboot and see if Wicd is more cooperative.

---

