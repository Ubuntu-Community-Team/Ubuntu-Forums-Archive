---
title: "HP G42, natty, Broadcom BCM4313 cannot connect to any network"
date: 2011-12-24
forum: Networking &amp; Wireless
---

### Post by jujiyangasli on 2011-12-24
i'm a begginer in ubuntu.

HP g42
Ubuntu 11.04

please help me..
my wireless adapter can scan for networks.
but can't seem to connect to any of them.

lspci | grep Network
```
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

```

lspci -vv -s 02:00.0
```

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 1483
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at d3000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: wl
	Kernel modules: wl, brcm80211

```



I googled my problem. Some folks seems to have to "modprobe" the wl module to make their wifi works.
my wl module seems to be loaded. So i really don't have a clue.

below is the information regarding my driver and connection (that i know of):


lsmod | grep wl

```

wl                   2568244  0 
lib80211               14991  2 lib80211_crypt_tkip,wl

```


iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:169
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```


lshw -C network

```

 *-network               
       description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 70:f3:95:ae:0a:48
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:d3000000-d3003fff

```




if this helps, my last attempt to connect to a wifi-network (innewifi):

cat /var/log/syslog | grep "Dec 24 20:02"

[HTML]Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Activation (eth1) starting connection 'Auto innewifi'
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> (eth1): device state change: 3 -> 4 (reason 0)
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Activation (eth1/wireless): access point 'Auto innewifi' has security, but secrets are required.
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> (eth1): device state change: 5 -> 6 (reason 0)
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> (eth1): device state change: 6 -> 4 (reason 0)
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> (eth1): device state change: 4 -> 5 (reason 0)
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Activation (eth1/wireless): connection 'Auto innewifi' has security, and secrets exist.  No new secrets needed.
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Config: added 'ssid' value 'innewifi'
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Config: added 'scan_ssid' value '1'
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Config: added 'psk' value '<omitted>'
Dec 24 20:02:07 (none) NetworkManager[1006]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 24 20:02:07 (none) NetworkManager[1006]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> Config: set interface ap_scan to 1
Dec 24 20:02:07 (none) NetworkManager[1006]: <info> (eth1): supplicant connection state:  inactive -> scanning
Dec 24 20:02:08 (none) wpa_supplicant[1110]: Trying to associate with d0:c1:b1:23:3d:21 (SSID='innewifi' freq=2437 MHz)
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> (eth1): supplicant connection state:  scanning -> associating
Dec 24 20:02:08 (none) wpa_supplicant[1110]: Association request to the driver failed
Dec 24 20:02:08 (none) wpa_supplicant[1110]: Associated with d0:c1:b1:23:3d:21
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> (eth1): supplicant connection state:  associating -> associated
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> (eth1): supplicant connection state:  associated -> 4-way handshake
Dec 24 20:02:08 (none) wpa_supplicant[1110]: WPA: Key negotiation completed with d0:c1:b1:23:3d:21 [PTK=CCMP GTK=CCMP]
Dec 24 20:02:08 (none) wpa_supplicant[1110]: CTRL-EVENT-CONNECTED - Connection to d0:c1:b1:23:3d:21 completed (auth) [id=0 id_str=]
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> (eth1): supplicant connection state:  4-way handshake -> group handshake
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> (eth1): supplicant connection state:  group handshake -> completed
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> Activation (eth1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'innewifi'.
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> (eth1): device state change: 5 -> 7 (reason 0)
Dec 24 20:02:08 (none) NetworkManager[1006]: client_start: assertion `priv->client_type != 0' failed
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> (eth1): device state change: 7 -> 9 (reason 15)
Dec 24 20:02:08 (none) NetworkManager[1006]: <warn> Activation (eth1) failed for access point (innewifi)
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> Marking connection 'Auto innewifi' invalid.
Dec 24 20:02:08 (none) NetworkManager[1006]: <warn> Activation (eth1) failed.
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> (eth1): device state change: 9 -> 3 (reason 0)
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> (eth1): deactivating device (reason: 0).
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> Policy set 'Esia connection' (ppp0) as default for IPv4 routing and DNS.
Dec 24 20:02:08 (none) NetworkManager[1006]: <info> Policy set 'Esia connection' (ppp0) as default for IPv4 routing and DNS.
Dec 24 20:02:09 (none) wpa_supplicant[1110]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0
[/HTML]

---

### Post by praseodym on 2011-12-24
Hi,

please show:

```
rfkill list
lsmod
```

---

### Post by jujiyangasli on 2011-12-24
hai praseodym,

thanks for replying.. :)



$ rfkill list

```

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```




$ lsmod

```

Module                  Size  Used by
ppp_deflate            12990  0 
zlib_deflate           27074  1 ppp_deflate
bsd_comp               12913  0 
ppp_async              17540  1 
crc_ccitt              12667  1 ppp_async
michael_mic            12612  0 
arc4                   12529  0 
hidp                   22572  0 
hid                    91020  1 hidp
snd_hrtimer            12784  1 
binfmt_misc            17565  1 
rfcomm                 47694  8 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53610  17 hidp,rfcomm,bnep
pci_stub               12622  1 
vboxpci                23190  0 
vboxnetadp             13382  0 
vboxnetflt             23435  0 
vboxdrv               286917  3 vboxpci,vboxnetadp,vboxnetflt
nfsd                  316512  11 
lockd                  85732  1 nfsd
nfs_acl                12883  1 nfsd
auth_rpcgss            52881  1 nfsd
sunrpc                234297  12 nfsd,lockd,nfs_acl,auth_rpcgss
exportfs               12998  1 nfsd
dm_crypt               22993  0 
parport_pc             36959  0 
ppdev                  17113  0 
vesafb                 13761  1 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
snd_hda_codec_hdmi     28167  1 
vfat                   21708  1 
fat                    61374  1 vfat
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
lib80211_crypt_tkip    17387  0 
snd_seq                61621  3 snd_seq_midi,snd_seq_midi_event
wl                   2568244  0 
snd_timer              29602  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17606  0 
fglrx                2739144  102 
snd                    67382  15 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
option                 25285  3 
coretemp               13490  0 
usb_wwan               20407  1 option
soundcore              12680  1 snd
usbserial              42908  9 option,usb_wwan
uvcvideo               72195  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
btusb                  18600  2 
lp                     17825  0 
bluetooth              72320  10 hidp,rfcomm,sco,bnep,l2cap,btusb
psmouse                73535  0 
parport                46458  3 parport_pc,ppdev,lp
hp_wmi                 13706  0 
intel_ips              18097  0 
sparse_keymap          13898  1 hp_wmi
serio_raw              13166  0 
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  5 
r8169                  48022  0 
libahci                26642  1 ahci
video                  19438  0 
```

---

### Post by praseodym on 2011-12-24
Blacklist the module
```
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
and reboot. I recommend using pure WPA2-AES encryption

---

### Post by jujiyangasli on 2011-12-24
i added "blacklist brcm80211" to /etc/modprobe.d/blacklist.conf

but that doesn't seem to solve the problem. 
I (still) can't connect to any network.

i check the /etc/modprobe.d/ directory and i found that "blacklist brcm80211" has already in /etc/modprobe.d/blacklist-bcm43.conf

such as:
```
$ cat /etc/modprobe.d/blacklist-bcm43.conf
# Warning: This file is autogenerated by bcmwl. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
```

so i deleted "blacklist brcm80211" from blacklist.conf, reboot and greped brcm80211 from lsmod:

```
$lsmod | grep brcm80211
```

to no result.


below is the content of my blacklist.conf

```
$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
#blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
```

btw, 
thank you for staying with me.. :)


ooo, and one more question please:
> I recommend using pure WPA2-AES encryption
How can i do this?

---

### Post by praseodym on 2011-12-24
Connect via cable to the router and type in the IP address of it into your browser. You should be able to have access to the router interface and change the encryption mode. Check also if the firmware is up-to-date and if a MAC-address filter is activated.

---

### Post by jujiyangasli on 2011-12-24
hmmm...
i don't think i can do that..

my router only support wep, and wpa2-psk.
(it's a mobile phone)

but thx anyway, i'm sure wpa2-aes is better than wpa2-psk :)


about the wireless connection problem..
do you have any other solution besides blacklisting brcm80211 module?

in addition,

two days ago, my friend were trying to share my pp0 connection via wifi (using my computer)
he installed something like:
dhcp3-server
hostapd
dnsmaq

after that, my wireles connecting just goes out of the window.
i've tried to unistall the packages to no avail.

i'm really stressed-out right now, because i can't seem to connect normally to ANY wireless network T_T

---

### Post by praseodym on 2011-12-24
Can you show completely:

> iwlist chan
sudo iwlist scan
and mark the NW you want to connect to.

---

### Post by jujiyangasli on 2011-12-24
the network is "juji-wifi" (mark in red)

```
$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

ppp0      no frequency information.

eth1      no frequency information.


$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 78:47:1D:31:03:DB
                    **[COLOR="Red"]ESSID:"juji-wifi"[/COLOR]**
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:5/5  Signal level:-41 dBm  Noise level:-89 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
```

---

### Post by praseodym on 2011-12-24
Have a look at the country code used:

```
dmesg | grep country
```
and set it manually:

```
sudo apt-get install iw
iw reg get
sudo iw reg set DE [COLOR="Red"]# DE for Germany, use your own one[/COLOR]
```

Check:
```
iwlist chan
```

---

### Post by jujiyangasli on 2011-12-24
dmesg shows nothing
```
$ dmesg | grep country
```


when i try to view country by iw:
```
$ iw reg get
nl80211 not found.
```


should i install nl80211 ?

( with apt-get? )

---

### Post by praseodym on 2011-12-24
No, it means, this driver doesnt work with the 80211 subsystem. Try to remove your wireless profile and create a new one. Alternatively try Wicd instead of the NM (remove it after installing Wicd "completely"). Choose **eth1** as interface name and **wext** as driver.

---

### Post by jujiyangasli on 2011-12-25
i've installed WICD. but i can't remove NM because wicd does not support ppp0 (which i am using right now)

after i installed WICD, i try to connect to the wireless network (juji-wifi) twice, with WICD. here are the results:

[LIST]
[*]**juji-wifi (wpa2-psk)**
[COLOR="Red"]Connection failed: bad password[/COLOR]
This is weird because the password is correct.
[/LIST]

[LIST]
[*]**juji-wifi (unsecured)**
[COLOR="red"]Connection failed: Unable to get IP addres[/COLOR]
[/LIST]

Edit:
ooo, btw, i tried to remove my wireless profiles. I still couldn't connect to any network.

---

### Post by praseodym on 2011-12-25
Try
> sudo service network-manager stop
sudo service wicd restart

---

### Post by josephmills on 2011-12-25
I do not mean to jump in but I will :) could we also see a ```
lspci -nn | grep 14e4
``` the -nn stands for name and number of the card

---

### Post by jujiyangasli on 2011-12-25
> **josephmills said:**
> I do not mean to jump in but I will :) could we also see a ```
lspci -nn | grep 14e4
``` the -nn stands for name and number of the card


```
$ lspci -nn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```

be my guest :)

---

### Post by praseodym on 2011-12-25
How many letters does your key have? Any blanks or strange letters in there? Did you:
```
sudo apt-get remove --purge network-manager network-manager-gnome
sudo service wicd restart
```

---

### Post by jujiyangasli on 2011-12-25
> **praseodym said:**
> 
Try:
sudo service network-manager stop
sudo service wicd restart


done that.. 
and tried to connect to "juji-wifi" (unsecured)
with no luck.. :(

---

### Post by jujiyangasli on 2011-12-25
> **praseodym said:**
> How many letters does your key have? Any blanks or strange letters in there? Did you:
```
sudo apt-get remove --purge network-manager network-manager-gnome
sudo service wicd restart
```

no i didn't do that, because i need an internet connection from ppp0 (the type which WICD doesn't support)

So, i can't remove the network manager because i don't know any other way to connect to the internet.

about the password it's a 12 letter word (i verified that the password is correct), and no strange character.

---

### Post by praseodym on 2011-12-25
Try:
```
sudo service network-manager stop
sudo pppoeconf
```
If you are using a single modem with ppp0

---

### Post by jujiyangasli on 2011-12-25
> **praseodym said:**
> Try:
```
sudo service network-manager stop
sudo pppoeconf
```
If you are using a single modem with ppp0

i can't.. i guess because i use a usb stick modem. (cdma)

**addition:**

i would really like to keep relying on the default network-manager...
can i do that?

it worked great a week ago..
now, it doesn't work. I don't know why, but i'm trying to make it work again..

is there any other option to fix my problem besides relying on another end-user interface?

i don't mind some workaround, as long as i can keep my default network manager.. :)

btw, praseodym, thanks for staying with me.. :)

---

### Post by praseodym on 2011-12-25
Here are several other tools for UMTS devices you can use/try:

[http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist](http://ubuntuforums.org/showthread.php?t=1831649&highlight=umts+checklist)

---

### Post by jujiyangasli on 2011-12-27
hey.. sorry, for the late reply..
christmas holiday.. :)

just dropping by to say praseodym's solution work.

in summary:

[LIST=1]
[*]install wicd
[*]instal gnome-ppp (for my ppp0 connection)
[*]uninstall network-manager and gnome-network-manager
[*]my wireless connection works...
[/LIST]

thx for your help.. :)

---

