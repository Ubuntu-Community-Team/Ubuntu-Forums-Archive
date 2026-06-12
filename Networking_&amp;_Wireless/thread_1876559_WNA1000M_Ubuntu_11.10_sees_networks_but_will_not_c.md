---
title: "WNA1000M Ubuntu 11.10 sees networks but will not connect and authenticate."
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by Ahnakel on 2011-11-06
lsusb:
Bus 001 Device 003: ID 0846:9041 NetGear, Inc. 

iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          
lsmod:
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61475  1 vfat
parport_pc             36962  0 
ppdev                  17113  0 
snd_hda_codec_realtek   330769  1 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
arc4                   12529  2 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
rtl8192cu             102029  0 
rtl8192c_common        74576  1 rtl8192cu
snd_seq_midi_event     14899  1 snd_seq_midi
rtlwifi               105583  1 rtl8192cu
mac80211              319649  3 rtl8192cu,rtl8192c_common,rtlwifi
binfmt_misc            17540  1 
cfg80211              203978  2 rtlwifi,mac80211
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
psmouse                73882  0 
serio_raw              13166  0 
nouveau               728662  3 
ttm                    76805  1 nouveau
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         42558  1 nouveau
drm                   236330  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13423  1 nouveau
mxm_wmi                12979  1 nouveau
wmi                    19256  1 mxm_wmi
video                  19412  1 nouveau
edac_core              53746  0 
edac_mce_amd           23709  0 
k10temp                13166  0 
snd                    68266  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            57901  1 
usbhid                 47198  0 
hid                    95463  1 usbhid
uas                    18027  0 
r8169                  52788  0 
sata_nv                32305  2 
pata_amd               14121  0

sudo lshw -C network
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@1:4
       logical name: wlan0
       serial: c4:3d:c7:77:91:75
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192cu driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bgn


iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

lsb_release -d
Description:	Ubuntu 11.10

uname -mr
3.0.0-12-generic x86_64

 sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by Ahnakel on 2011-11-12
Bump :)

---

### Post by Ahnakel on 2011-11-23
Ok, I was able to get the computer online using NDISwrapper and assigning DCHP(address only). But now the connection will work for a while, but then after using apt-get to get a package or 2 installed it drops connection again. Any idea of a package i need to update? Do I have something set wrong in the network settings? 

It should also be stated that when I am kicked off it asks me to re-enter my network key.(Which it doesn't accept)
I have also tried updating wpasupplicant, but this hasn't really helped any.

---

### Post by WasMeHere on 2011-11-23
Hello Ahnakel,

I have found that support of wireless equipment is one of the weak spots of linux. Some chips/cards are supported out of the box, but some have to be run via ndiswrapper and a windows driver. Sometimes this works well, sometimes not.

[COLOR="Red"]If you are lucky, someone with experience of your wireless equipment will show up and help.[/COLOR]

You can start browsing the internet to find out what is expected to work. See for example the following link
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

Have fun finding out :-)
Olle

---

### Post by gordintoronto on 2011-11-23
Have a look at this thread: 
[http://ubuntuforums.org/archive/index.php/t-1806839.html](http://ubuntuforums.org/archive/index.php/t-1806839.html)

---

### Post by Ahnakel on 2011-12-02
I have tried many things in the forums that I have found but i really can't get it to work. I will continue to play around with it but for now I have bought a cisco wifi card and it worked as soon as I plugged it in. Thanks for the help and references but it looks like this may just not happen.

---

### Post by CableCat on 2012-02-28
Mini USB wifi adaptor that work in Ubuntu:
* Buffalo AirStation N-Technology 150Mbps USB 2.0 Client [WLI-UC-GNM-EU]

Mini USB wifi adaptors that do not work in Ubuntu:
* NETGEAR G54/N150 Wireless USB Micro Adapter WNA1000M [WNA1000M-100PES]
* TRENDnet TEW 648UBM [TEW-648UBM]
* D-Link Wireless N 150 Micro USB Adapter DWA-121 [DWA-121]
* Belkin N150 Micro Wireless USB Adapter [F7D1102AZ]

Tested at 2012-02-28 in Ubuntu 11.10 and Daily Live.
Connecting to WPA2 enterprise network fails most times.

[IMG]http://kom.aau.dk/~pmr/www/mini_USB_WIFI/Mini_USB_WIFI_in_Ubuntu_550px.png[/IMG]

---

### Post by skud78 on 2012-08-02
Wish I had seen this before I went out to buy my D-Link N 150 DWA-121 adapter.  Been searching and tried to install the linux driver downloaded at [http://www.dlink.com/ca/en/home-solutions/connect/adapters/dwa-121-wireless-n-150-pico-usb-adapter](http://www.dlink.com/ca/en/home-solutions/connect/adapters/dwa-121-wireless-n-150-pico-usb-adapter)
but getting an error: "fatal error: linux/smp_lock.h" - the search continues

---

### Post by skud78 on 2012-09-20
So problem solved by going out and buying the D-Link DWA 160 which works out of the box with Ubuntu 11.10 - "plug and play".   Only catch is DWA 160 is more than twice the price of DWA 121 which works "plug and play" on Windows 7.  

The not so cheap "free" O/S

---

