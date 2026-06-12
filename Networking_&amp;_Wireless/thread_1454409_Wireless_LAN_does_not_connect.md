---
title: "Wireless LAN does not connect"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by ve7mdl on 2010-04-14
Scenario:

Installed Ubuntu 10.4 Beta on my Asus Eee 901 (the old Windows XP got tired...)

Nice install, BTW, but Networking does not work.  I have a very run-of-the-mill Linksys wireless router, which uses WPA2 passord authentication on the wireless side.  Ubuntu clearly does try to connect, but then asks me for the password again, repeated a few times and then gives up.

The SSID is OK (same I use on my Windows machines) and the same for the password, so it must be something Ubuntu does to the password.  Bug or operator error?

....Erik.

---

### Post by Crafty Kisses on 2010-04-14
Can I get some more information?

```
lspci
lsusb
lshw -C network
```

---

### Post by lwaldo on 2010-04-15
I am having the same problem with 10.4b2 on an Eee PC 1000.  Wireless will not connect at all. Locked or other wise.

---

### Post by ve7mdl on 2010-04-16
Hello Crafty,

I am back looking at this.  Here is what I did:

root@Ubuntu-Eee:~# tail /var/log/syslog
Apr 14 16:08:45 Ubuntu-Eee NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Apr 14 16:08:55 Ubuntu-Eee NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Apr 14 16:08:55 Ubuntu-Eee NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Apr 14 16:08:55 Ubuntu-Eee NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Apr 14 16:08:55 Ubuntu-Eee kernel: [  889.129076] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
Apr 14 16:08:55 Ubuntu-Eee wpa_supplicant[663]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Apr 14 16:08:55 Ubuntu-Eee wpa_supplicant[663]: last message repeated 2 times
Apr 14 16:08:55 Ubuntu-Eee NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Apr 14 16:08:55 Ubuntu-Eee wpa_supplicant[663]: Authentication with 00:00:00:00:00:00 timed out.
Apr 14 16:09:10 Ubuntu-Eee NetworkManager: <info>  wlan0: link timed out.
root@Ubuntu-Eee:~# 

root@Ubuntu-Eee:~# lshw -C Network
  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:22:15:30:41:ca
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:fe8c0000-fe8fffff ioport:dc80(size=128)
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       serial: 00:15:af:bb:be:a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:19 memory:fa7f0000-fa7fffff
root@Ubuntu-Eee:~# 

root@Ubuntu-Eee:~# iwconfig wlan0
wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.457 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=91/100  Signal level:-70 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


root@Ubuntu-Eee:~# lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203169  1 
joydev                  8708  0 
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
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282124  3 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29297  1 i915
uvcvideo               56990  0 
psmouse                63245  0 
drm                   162567  4 i915,drm_kms_helper
intel_agp              24177  2 i915
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
serio_raw               3978  0 
soundcore               6620  1 snd
rt2860sta             481849  1 
i2c_algo_bit            5028  1 i915
agpgart                31724  2 drm,intel_agp
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
output                  1871  1 video
eeepc_laptop           12847  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
atl1e                  28146  0 

******* From dmesg: **********

[  752.600048] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[  757.612313] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 171
[  757.612859] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=10)
[  767.653070] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[  772.654636] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 171
[  772.655152] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=10)
[  782.128991] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[  782.130172] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[  834.133412] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 171
[  834.134017] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=10)
[  844.260451] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[  849.263102] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 171
[  849.263850] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=10)
[  859.313646] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[  864.319768] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 171
[  864.320370] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=10)
[  874.364637] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!
[  879.366050] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 350
[  879.366825] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=10)
[  889.129076] ERROR!!! RTMPCancelTimer failed, Timer hasn't been initialize!


root@Ubuntu-Eee:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:23:69:A6:76:D1
                    Protocol:802.11b/g
                    ESSID:"BCG"
                    Mode:Managed
                    Channel:10
                    Quality:44/100  Signal level:-72 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

root@Ubuntu-Eee:~# uname -mr
2.6.32-20-generic i686

root@Ubuntu-Eee:/etc# modinfo rt2860sta
filename:       /lib/modules/2.6.32-20-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        1.8.1.1
license:        GPL
srcversion:     CAEA506C88572D233F96224
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        
staging:        Y
vermagic:       2.6.32-20-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)

***** Not one to give up easily, I added wpa_supplicant.conf: ***

network={
	ssid="BCG"
	proto=WPA
	scan_ssid=1
	key_mgmt=WPA-PSK
	psk="mysecretkey"
}
 .... and here is what I got after restart:


root@Ubuntu-Eee:~# tail /var/log/syslog
Apr 14 17:23:43 Ubuntu-Eee NetworkManager: <info>  Activation (wlan0/wireless): connection 'BC Girl' has security, and secrets exist.  No new secrets needed.
Apr 14 17:23:43 Ubuntu-Eee NetworkManager: <info>  Config: added 'ssid' value 'BCG'
Apr 14 17:23:43 Ubuntu-Eee NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Apr 14 17:23:43 Ubuntu-Eee NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Apr 14 17:23:43 Ubuntu-Eee NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Apr 14 17:23:43 Ubuntu-Eee NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 14 17:23:43 Ubuntu-Eee NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Apr 14 17:23:43 Ubuntu-Eee NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 14 17:23:43 Ubuntu-Eee NetworkManager: <info>  Config: set interface ap_scan to 1
Apr 14 17:23:43 Ubuntu-Eee NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning

... It clearly processes the file, but still, no joy.

Cheers,           ....Erik.

---

### Post by Crafty Kisses on 2010-04-19
Hello,

Check this out: [http://wiki.debian.org/DebianEeePC/Model/901](http://wiki.debian.org/DebianEeePC/Model/901). Then you can run:
```
sudo apt-get install firmware-iwlwifi
```
See if that gets you up and running.

---

### Post by ve7mdl on 2010-04-19
"Crafty",

Thanks, I will try that when I get home (I'm located in Vancouver, so the work day has just started).

Cheers,           ....Erik.

---

### Post by ve7mdl on 2010-04-19
Hello again, Montana,

I'm not having much luck.

I first updated the repository list per eeepc.debian.net, then tried to install eeepc-acpi-scripts, but it reports that packages are broken.

Next, tried to install firmware-iwlwifi.  No can't do.  The package cannot be found.

I am really puzzled here.  I though that netbook support was introduced as of 9.10?  Is there something or some step that I am missing?

Cheers,               ....Erik.

---

### Post by ve7mdl on 2010-04-20
Well, some additional experimentation bore fruit.

I took the Eee 901 very close to the access point (a Linksys wireless router) and re-booted.  This time I got connected.

When I moved away from the router, I guess it temporarily lost signal and would not recover - even though auto connect is on.

I decided to try some different setting on the router just for fun.  The encryption scheme was set to TKIP+AES, which works fine for all the other machines and did work fine for another Ubuntu installation I had (9.10) at some point.  Anyway, I changed it to AES and now the 901 connects!

I use WPA2 and a password, BTW.

I hope this information is useful for other people.

Cheers,      ....Erik.

---

### Post by Crafty Kisses on 2010-04-20
Hey Erik,

Sorry I was about to give you more instructions about installing the driver, but this is great news! I'm so glad you fixed the problem. ;-)

---

### Post by ve7mdl on 2010-04-22
Montana,

Yes, thanks for all your suggestions.  I learned a lot!

Cheers,                ....Erik.

---

### Post by mmaia on 2010-04-30
Hi I have the same problem. My wireless connection does not work. 

Dell Inspiron 

*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation


any suggestions? I'm lost here.

---

### Post by overlord404 on 2010-05-01
> **mmaia said:**
> Hi I have the same problem. My wireless connection does not work. 

Dell Inspiron 

*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation


any suggestions? I'm lost here.

I've had this problem ever since 9.04 (possibly earlier) - there were a couple of suggestions mentioned here that may help: -

[http://forum.eeeuser.com/viewtopic.php?id=68388](http://forum.eeeuser.com/viewtopic.php?id=68388)

I've also had this problem with Fedora but another kernel worked fine for me on both occasions (with ubuntu and fedora).

Wish Canonical would sort this as they are pushing an 'Easy to Use" OS but this aspect is still not fixed "out of the box".

Really I would have thought the combination of EEE PC 1000 + Ubuntu would be a popular one - had this netbook now 18 months but still no success at having Wireless 'just work' straight after installation with any of the mainstream linux disties...

If anyone has an easy to follow guide on manually sorting this without having to use a different kernel then I'm all ears!

;-)

---

### Post by 1BUBA on 2010-05-01
> **ve7mdl said:**
> Well, some additional experimentation bore fruit.

I took the Eee 901 very close to the access point (a Linksys wireless router) and re-booted.  This time I got connected.

When I moved away from the router, I guess it temporarily lost signal and would not recover - even though auto connect is on.

I decided to try some different setting on the router just for fun.  The encryption scheme was set to TKIP+AES, which works fine for all the other machines and did work fine for another Ubuntu installation I had (9.10) at some point.  Anyway, I changed it to AES and now the 901 connects!

I use WPA2 and a password, BTW.

I hope this information is useful for other people.

Cheers,      ....Erik.


Just a confirmation.
I'm running an EEE, WPA2 Personal, TKIP+AES and password...  Could get no connection.
Changed from TKIP+AES to AES, and all is good.

Thanks Erik!

---

### Post by nyarnon on 2010-05-01
Great solution if you can access the router, but many of us can't so it's no solution at all.

---

### Post by Strange_Movement on 2010-05-02
Crafty Kisses I would be really grateful if you would post whatever information you were going to post before ve7mdl got the wireless connection going. I'm still having problems getting my eee 901 running 10.04 to connect to my hidden SSID access point using WPA/WPA2 TKIP/AES 

Thanks

---

### Post by pete_m on 2010-08-21
Happy to report a successful fix on eee pc 1000 

Starting from a 2.6.32 kernel  which could see the wireless card and networks but not log on to a wireless network.

After a kernel upgrade-> 2.35 from Maverick none of the previously mentioned  firmware issues were in evidence, iwconfig seemd ok and accepted ESSID directive but not key s:my_password

I don't use network-manager as it depends on upstart. 
My upgraded system uses sysv-init, and will continue to until upstart is part of Sid - seemingly on its way since last year.

Hence I needed a non-NetworkManager solution.

Seems wpa-supplicant is needed to WPA so unless you can find the Hex key by logging to that router from a different install/ machine and running iwconfig there. . .

I came across wicd on a Debian forum and located the package in Maverick Universe - installed and all was well to connect and re-connect

If this solution doesn't suit I guess you'll need to investigate wpa-supplicant in more detail.

Hope this helps,

Viva Sid, Viva Linux, Viva FOSS . . .

---

### Post by Scotsman268 on 2010-08-22
Came up against this very problem...this thread solved it! Router settings needed to be configured ditto to yours...WPA2 + password + AES encryption. Thx for the SUPER info!

---

