---
title: "WPA Problems with 10.4 and a Sony Vaio laptop"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by dafreak on 2010-05-12
Well this one is driving me nuts. I've been searching through the forums for a while and it seems that a number of folks have similar issues but the solutions used don't look like they apply to me. so without further ado here are the outputs typically requested:

lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

```

lsmod

```

Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
usb_storage            39425  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
pcmcia                 33024  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
joydev                  8708  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  3 
tifm_sd                 7863  0 
drm_kms_helper         29297  1 i915
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           20408  1 
ipw2200               135216  0 
drm                   162471  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
tifm_7xx1               3690  0 
rsrc_nonstatic         10015  1 yenta_socket
libipw                 39896  1 ipw2200
intel_agp              24177  2 i915
soundcore               6620  1 snd
tifm_core               6045  2 tifm_sd,tifm_7xx1
sony_laptop            28248  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
lib80211                5046  2 ipw2200,libipw
psmouse                63245  0 
serio_raw               3978  0 
video                  17375  1 i915
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
ohci1394               26950  0 
e100                   28211  0 
mii                     4381  1 e100
ieee1394               81181  1 ohci1394

```

wicd.log 

```

2010/05/12 19:01:36 :: Connecting to wireless network EchoWireless
2010/05/12 19:01:36 :: attempting to set hostname with dhclient
2010/05/12 19:01:36 :: using dhcpcd or another supported client may work better
2010/05/12 19:01:36 :: attempting to set hostname with dhclient
2010/05/12 19:01:36 :: using dhcpcd or another supported client may work better
2010/05/12 19:01:37 :: Putting interface down
2010/05/12 19:01:37 :: Releasing DHCP leases...
2010/05/12 19:01:37 :: attempting to set hostname with dhclient
2010/05/12 19:01:37 :: using dhcpcd or another supported client may work better
2010/05/12 19:01:37 :: Setting false IP...
2010/05/12 19:01:37 :: Stopping wpa_supplicant
2010/05/12 19:01:37 :: Flushing the routing table...
2010/05/12 19:01:37 :: Putting interface up...
2010/05/12 19:01:39 :: Generating psk...
2010/05/12 19:01:39 :: Attempting to authenticate...
2010/05/12 19:01:54 :: wpa_supplicant rescan forced...
2010/05/12 19:02:19 :: wpa_supplicant authentication may have failed.
2010/05/12 19:02:19 :: connect result is Failed
2010/05/12 19:02:19 :: exiting connection thread
2010/05/12 19:02:19 :: Sending connection attempt result bad_pass
2010/05/12 19:02:19 :: attempting to set hostname with dhclient
2010/05/12 19:02:19 :: using dhcpcd or another supported client may work better
2010/05/12 19:02:19 :: attempting to set hostname with dhclient
2010/05/12 19:02:19 :: using dhcpcd or another supported client may work better
2010/05/12 19:03:14 :: Connecting to wireless network EchoWireless
2010/05/12 19:03:14 :: attempting to set hostname with dhclient
2010/05/12 19:03:14 :: using dhcpcd or another supported client may work better
2010/05/12 19:03:14 :: attempting to set hostname with dhclient
2010/05/12 19:03:14 :: using dhcpcd or another supported client may work better
2010/05/12 19:03:15 :: Putting interface down
2010/05/12 19:03:15 :: Releasing DHCP leases...
2010/05/12 19:03:15 :: attempting to set hostname with dhclient
2010/05/12 19:03:15 :: using dhcpcd or another supported client may work better
2010/05/12 19:03:15 :: Setting false IP...
2010/05/12 19:03:15 :: Stopping wpa_supplicant
2010/05/12 19:03:15 :: Flushing the routing table...
2010/05/12 19:03:15 :: Putting interface up...
2010/05/12 19:03:17 :: Generating psk...
2010/05/12 19:03:17 :: Attempting to authenticate...
2010/05/12 19:03:52 :: wpa_supplicant authentication may have failed.
2010/05/12 19:03:52 :: connect result is Failed
2010/05/12 19:03:52 :: exiting connection thread
2010/05/12 19:03:52 :: Sending connection attempt result bad_pass

```

rfkill list returns nothing

sudo lshw -C network

```


  *-network:0 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:06:04.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:3c:0b:84
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:22 memory:b0106000-b0106fff
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:01:4a:c1:77:0a
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:b0107000-b0107fff ioport:2000(size=64)

```

I'm sure that I have the wireless password correct so that should be out of the equation. I know that the wireless works on unsecured networks just fine. At this point I'm  not sure what else to try. I've tried using both the default NetworkManager and WICD. If I use the network manager it can see networks just fine, it's just when I type in my WPA2 password it will not authenticate with my Linksys WRT-54GL router, it keeps prompting for the password. Wicd simply fails to authenticate and doesn't go further. I know the wireless itself works as I can connect to unsecured networks just fine. But I sure as heck am not going to open up my secured network.

---

### Post by dafreak on 2010-05-13
Just ran the update manager to make sure everything was up to date. It did have to update a number of packages but none of them have affected the issue at all. Still quite baffled as to why this wireless card will not authenticate on a WPA secured network.

---

### Post by HedgeBoar on 2010-05-13
Exactly the same issue here, using an edimax 7711UAN usb adapter with rt2870sta driver.  Works fine on unprotected network but WPA doesn't work... was fine with 9.10.

---

### Post by dafreak on 2010-05-14
So does anybody have any suggestions? I'm really not sure what else to try at this point. I even tried installing the latest experimental kernel. That didn't help and actually caused some other issues causing me to re-install 10.04 again.

---

### Post by HedgeBoar on 2010-05-14
I actually got mine to work last night -- I changed the router from using TKIP/AES to just TKIP and it connects fine now!

---

### Post by HedgeBoar on 2010-05-14
I also disabled WCN on the router (something windows specific I think) at the same time... I think it's more likely the AES that was causing the issue though..

---

### Post by warfacegod on 2010-05-14
@ dafreak, your lshw command says that the wireless is disabled. Right click your network icon in the Notification Area and be certain that wireless is enabled.

---

### Post by dafreak on 2010-05-14
@warfacegod

Yeah I had forgotten to unhook the ethernet cable while doing an lshw and ubuntu automatically disables wireless if a wired network is plugged in. I did an lshw again with the wired interface unplugged and it returned the same information with the exception that the adapter shows as enabled ie the DISABLED tag is gone.

---

### Post by dafreak on 2010-05-15
Well I tried the old school way of getting wireless to work on the ipw2200 chipset, no go there either. I followed the instructions here ( [http://ubuntuportal.blogspot.com/2007/03/how-to-get-ipw2200-and-wpa-to-work.html](http://ubuntuportal.blogspot.com/2007/03/how-to-get-ipw2200-and-wpa-to-work.html) ) and it still fails to associate with my wireless router. Here's the detailed debug from a wpa_supplicant connection attempt:

```

Try to find WPA-enabled AP
0: 00:0f:66:d2:af:65 ssid='EchoWireless' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:0f:66:d2:af:65 ssid='EchoWireless'
Trying to associate with 00:0f:66:d2:af:65 (SSID='EchoWireless' freq=2432 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: using IEEE 802.11i/D3.0
WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto 1
WPA: set AP WPA IE - hexdump(len=26): dd 18 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02 00 00
WPA: clearing AP RSN IE
WPA: using GTK TKIP
WPA: using PTK TKIP
WPA: using KEY_MGMT WPA-PSK
WPA: not using MGMT group cipher
WPA: Set own WPA IE default - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: DISCONNECTED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Association request to the driver failed
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'eth1' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Added BSSID 00:0f:66:d2:af:65 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: ASSOCIATING -> DISCONNECTED

```

This is what's in my wpa_supplicant.conf file:

network={
     ssid="EchoWireless"
     scan_ssid=1
     proto=WPA RSN
     key_mgmt=WPA-PSK
     pairwise=TKIP
     group=TKIP
     psk=mypsk
}
[/code]

My psk is different than what's shown obviously. I'm running out of things to try short of downgrading to 9.04 and hoping for the best.

---

### Post by HedgeBoar on 2010-05-15
Did you try disabling AES on your router?

---

### Post by dafreak on 2010-05-15
Yep I tried setting it to TKIP only, no change.

---

### Post by warfacegod on 2010-05-15
I  have read threads on a *few* people getting wpa2 working by changing their password to only lowercase letters. I have no idea if that will work for wpa but it might be worth a shot.

---

### Post by dafreak on 2010-05-15
> **warfacegod said:**
> I  have read threads on a *few* people getting wpa2 working by changing their password to only lowercase letters. I have no idea if that will work for wpa but it might be worth a shot.

I'm willing to try close to anything at this point. I'll give it a shot and report the results shortly.

---

### Post by dafreak on 2010-05-15
Well I tried with an all lowercase WPA2 key, no dice :(

---

### Post by warfacegod on 2010-05-15
My fault, I thought this was about wpa, its been awhile since I've read the OP. Not that wpa or wpa2 matters at this point.

Are your sure your actually getting any signal?

Does ```
sudo iwlist scanning
``` produce any results?

Can you connect with security turned off?

---

### Post by dafreak on 2010-05-15
> **warfacegod said:**
> My fault, I thought this was about wpa, its been awhile since I've read the OP. Not that wpa or wpa2 matters at this point.

Are your sure your actually getting any signal?

Does ```
sudo iwlist scanning
``` produce any results?

Can you connect with security turned off?

Here's the output of sudo iwlist scanning:

```

eth1      Scan completed :
          Cell 01 - Address: 00:26:F2:97:70:FB
                    ESSID:"NETGEAR"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=58/100  Signal level=-66 dBm  
                    Extra: Last beacon: 800ms ago
          Cell 02 - Address: 00:1E:C7:8E:22:E9
                    ESSID:"2WIRE192"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=86/100  Signal level=-44 dBm  
                    Extra: Last beacon: 372ms ago
          Cell 03 - Address: 00:00:00:00:00:00
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=55/100  Signal level=-68 dBm  
                    Extra: Last beacon: 428ms ago
          Cell 04 - Address: 00:0F:66:D2:AF:65
                    ESSID:"EchoWireless"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.432 GHz (Channel 5)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=62/100  Signal level=-63 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 104ms ago
          Cell 05 - Address: 00:24:37:31:F4:00
                    ESSID:"qwest3264"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=64/100  Signal level=-62 dBm  
                    Extra: Last beacon: 52ms ago
          Cell 06 - Address: 00:22:3F:8B:C9:C9
                    ESSID:"CBC"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=85/100  Signal level=-45 dBm  
                    Extra: Last beacon: 228ms ago
          Cell 07 - Address: 00:1C:10:BD:DF:16
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=85/100  Signal level=-45 dBm  
                    Extra: Last beacon: 148ms ago
          Cell 08 - Address: 00:00:00:00:00:00
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=59/100  Signal level=-65 dBm  
                    Extra: Last beacon: 164ms ago
          Cell 09 - Address: 00:24:7B:03:FE:30
                    ESSID:"myqwest1679"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 4592ms ago
          Cell 10 - Address: 00:24:7B:82:B3:5C
                    ESSID:"FORDJOUR"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=56/100  Signal level=-67 dBm  
                    Extra: Last beacon: 1604ms ago
          Cell 11 - Address: 00:24:7B:03:46:46
                    ESSID:"myqwest4597"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=55/100  Signal level=-68 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 396ms ago
          Cell 12 - Address: 00:16:38:C8:16:F3
                    ESSID:"Vicki"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=59/100  Signal level=-65 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 56ms ago
          Cell 13 - Address: 00:23:33:79:37:21
                    ESSID:"MemoPrivate"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm  
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 6412ms ago
          Cell 14 - Address: 00:22:75:5C:69:5C
                    ESSID:"BLOWURWOD"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=64/100  Signal level=-62 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 160ms ago
          Cell 15 - Address: 00:22:6B:83:8F:0F
                    ESSID:"Mriposa"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-73 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 300ms ago
          Cell 16 - Address: 00:24:7B:29:07:8E
                    ESSID:"beetlejuice"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=58/100  Signal level=-66 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 160ms ago
          Cell 17 - Address: 00:23:33:79:37:20
                    ESSID:"MemoPublic"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 7180ms ago
          Cell 18 - Address: 00:24:36:A9:BB:41
                    ESSID:"WKA Wifi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-81 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 7192ms ago
          Cell 19 - Address: C0:3F:0E:0C:91:F8
                    ESSID:"Tabnate"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=61/100  Signal level=-64 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 2736ms ago
          Cell 20 - Address: C2:3F:0E:0C:91:F9
                    ESSID:"NETGEAR_Guest1"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=61/100  Signal level=-64 dBm  
                    Extra: Last beacon: 2716ms ago
          Cell 21 - Address: 06:90:7F:26:96:7C
                    ESSID:"RUNNINGGURU"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=29/100  Signal level=-82 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 396ms ago
          Cell 22 - Address: 00:24:7B:FB:03:70
                    ESSID:"myqwest0673"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=46/100  Signal level=-73 dBm  
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 2844ms ago
          Cell 23 - Address: 00:0B:85:58:07:1B
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=44/100  Signal level=-74 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 5440ms ago
          Cell 24 - Address: 00:1D:71:E0:E0:91
                    ESSID:"marconi"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=51/100  Signal level=-70 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : 802.1x
                    Extra: Last beacon: 452ms ago
          Cell 25 - Address: 00:1D:71:E0:E0:90
                    ESSID:"JEDunn_GuestWifi"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality=55/100  Signal level=-68 dBm  
                    Extra: Last beacon: 916ms ago
          Cell 26 - Address: 00:0B:85:58:07:1C
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=27/100  Signal level=-83 dBm  
                    Extra: Last beacon: 6976ms ago
          Cell 27 - Address: 00:13:10:FA:24:CC
                    ESSID:"Cherry_Plaza_2"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=25/100  Signal level=-84 dBm  
                    Extra: Last beacon: 8476ms ago
          Cell 28 - Address: 00:0C:41:FC:36:43
                    ESSID:"linksys"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=33/100  Signal level=-80 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 3756ms ago

```

What's really interesting though is I decided to turn off security and see if I could connect and I still could not. Which is very interesting. Because I have been able to connect to other unsecured networks and as such suggests that there is a different issue. Not sure if it's an issue with my configuration elsewhere or the wireless router itself. Quick note that iwlist was before I turned off security on my router, another scan shows it with key disabled.

---

### Post by warfacegod on 2010-05-15
When you turned security off, did you also clear the passkey text box in the Connection Manager?

---

### Post by bkratz on 2010-05-15
If you are trying to connect to one of the ones on channel 1--you have a lot of competition! You might want to change channels.

---

### Post by dafreak on 2010-05-15
When I disabled security on the router it simply showed up on the list as an unsecured router and I clicked on it to connect. It didn't ask for a password but it also was not able to connect.

---

### Post by dafreak on 2010-05-15
> **bkratz said:**
> If you are trying to connect to one of the ones on channel 1--you have a lot of competition! You might want to change channels.

Nope mine is set to channel 5 which doesn't have any (or much at least) competition.

---

### Post by warfacegod on 2010-05-15
> **dafreak said:**
> When I disabled security on the router it simply showed up on the list as an unsecured router and I clicked on it to connect. It didn't ask for a password but it also was not able to connect.

That may be but the Network Manager may still be trying to use the passkey entered for that signal even though an unsecured network won't ask for a passkey. However, if you can't connect to the network and assuming the above isn't the issue, then you likely have a problem with the driver.

This may have nothing to do with Ubuntu at all. If this is a Windows (especially 7) managed network, you may need to manually add your computer to the network either through Windows or through the Network Summary.

---

### Post by dafreak on 2010-05-15
> **warfacegod said:**
> That may be but the Network Manager may still be trying to use the passkey entered for that signal even though an unsecured network won't ask for a passkey. However, if you can't connect to the network and assuming the above isn't the issue, then you likely have a problem with the driver.

This may have nothing to do with Ubuntu at all. If this is a Windows (especially 7) managed network, you may need to manually add your computer to the network either through Windows or through the Network Summary.

Wait, what?

I do have Windows 7 on the network yes, and I do also have a Windows 2000 Server on the network as well. However no system that connects to the network is required to authenticate with them to obtain an IP address. The IP address handling is done purely by the router.

---

### Post by dafreak on 2010-05-15
Ok, I did a reinstall of 10.04 and I can now connect to my network if it is not secured. I must've messed up something in my network settings on the previous install and a fresh install fixed it. Still cannot connect to a WPA secured network though. If it wasn't so dang insecure I'd leave it unsecured and just enable MAC filtering, but that's a laughable attempt at security.

---

### Post by warfacegod on 2010-05-15
Insecure would be the definition of Unsecured, sort of.:P

I've had my laptop try to connect to several networks with 7 machines on them. On all of them, the guy on the 7 machine had to manually add me to the network before I could connect even with the correct  passkey. Although, now that I think about it, all of them where on Comcast Cable Internet and it may have been a Comcast thing.

---

### Post by dafreak on 2010-05-15
> **warfacegod said:**
> Insecure would be the definition of Unsecured, sort of.:P

I've had my laptop try to connect to several networks with 7 machines on them. On all of them, the guy on the 7 machine had to manually add me to the network before I could connect even with the correct  passkey. Although, now that I think about it, all of them where on Comcast Cable Internet and it may have been a Comcast thing.


Well like I said before I'm willing to try anything. When you say add you to the network are you talking about adding your system to the windows homegroup? Not sure how that would affect DHCP but we'll give it a shot.

---

### Post by warfacegod on 2010-05-15
I'm pretty sure they where using some program that accessed the router's Network Summary directly. I know very little about Vista or 7 and wish I didn't know what I do. I can't even tell the difference between the two by looking at them. My apologies for giving you so little to go on and also if this ends up being a Red Herring.

---

### Post by dafreak on 2010-05-15
Thanks for helping anyways :). I'll keep reading forum posts and looking for possible solutions to the problem. I think their router may have allowed direct interaction through Windows 7, mine does not support that functionality. If all else fails I may just turn on AP Isolation on my router and set it to MAC secured, but I'm going to keep trying a good long time before I do something like that.

---

### Post by warfacegod on 2010-05-16
Perseverance.

---

### Post by dafreak on 2010-05-16
Just thought I'd give a quick update to this thread. Still not able to connect to a WPA encrypted network. At the suggestion of the #ubuntu chatroom I tried installing the wpa_gui tool. It installs and runs but does not display any network cards on its dropdown. What that's indicative of (if anything) I'm not sure though.

---

### Post by warfacegod on 2010-05-16
Probably nothing. Its likely that the GUI just isn't seeing your card and/or driver.

---

### Post by dafreak on 2010-05-17
Curiousity rears its ugly head. Is there any possibility that for some reason WPA is disabled on the driver/kernel level? When I check to see what my wireless is capable of it shows wpa & wpa2 but it's just a niggling question that's bothering me. Sorry for asking silly questions. I really want to use Ubuntu on this laptop, especially as quickly as it has been performing with the exception of wireless. It's just that the Windows XP license that came with this laptop is tempting me to go digging for my Windows XP CD again :( . Any other suggestions are welcome of course.

---

### Post by dafreak on 2010-05-17
Bumping this up to see if anybody else has any ideas. Still plugging away. Tried the latest experimental kernal from mainline, still no go.

---

### Post by warfacegod on 2010-05-17
> Curiousity rears its ugly head. Is there any possibility that for some reason WPA is disabled on the driver/kernel level?

That would be totally idiotic to have a driver or anything setup that way. But not outside the realm of possibility. Not a stupid question either.

---

### Post by dafreak on 2010-05-17
*shakes head* The easiest solutions are what I should always try first and I forgot to try this one. Turns out that doing a hard reset on my Linksys WRT54G was all that was needed. Once it rebooted I connected again with my WPA2 passphrase and it let me hookup without a hitch. Will mark this as solved.

---

### Post by warfacegod on 2010-05-18
Glad to hear it.

---

### Post by clarkac on 2010-06-11
I have a similar setup - Sony laptop, BG2200 wireless - and my problem is that I cannot make a wireless connection reliably.  It will connect, then drop, then reconnect and so on.  Last 3/4 mins max.  I have reset my router, and now changed it to no effect.  W7 works perfectly...
Ubuntu 10.04, Sony VAIO FS415B, Intel BG2200 wireless.

Any ideas?

Andy

---

### Post by cheway on 2010-08-07
> **HedgeBoar said:**
> I actually got mine to work last night -- I changed the router from using TKIP/AES to just TKIP and it connects fine now!

If you change it to just AES, it will also work fine. That way you don't need to use a weaker encryption method. It's just when you have TKIP/AES at the same time.

Thanks for your post though, I wouldn't have been able to sort out my network problems without it.

---

### Post by ricardisimo on 2011-03-29
I'm staring at my parents' Sony Vaio, which is running 10.10, fully updated, and using a "PRO/Wireless 2200BG [Calexico2] Network Connection" as per lshw. It is having the exact same problem I have had with every Ubuntu laptop I have looked at for almost two years now: the "Enable Wireless" option in Network Manager is grayed out and cannot be selected or modified.

On all of my desktops (you know, the machines I have connected by ethernet cable) the wireless works just fine, of course. But not a single laptop has wireless since at least Karmic. What the hell is going on?

---

