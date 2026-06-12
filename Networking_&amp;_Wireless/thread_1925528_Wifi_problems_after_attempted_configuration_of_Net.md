---
title: "Wifi problems after attempted configuration of Netgear g54/n150 USB adapter"
date: 2012-02-14
forum: Networking &amp; Wireless
---

### Post by ams1888 on 2012-02-14
Hello forum,

I recently tried to install drivers for the Netgear g54/n150 usb adapter, and not only did it fail but I seem to have removed/corrupted some general wireless interface configuration settings. As of now, KDE does not show any wireless capabilities (ethernet only). help!

---

### Post by chili555 on 2012-02-15
Please open a terminal and run and post:```
lsusb
sudo modprobe rtl8192cu
```Why did you decide to install this from compat-wireless since it is already installed by default? What didn't work as expected?

---

### Post by ams1888 on 2012-02-15
lsusb shows device is detected:
Bus 002 Device 007: ID 0846:9041 NetGear, Inc. 

modprobe... :
zev@zev-Lenovo-IdeaPad-Y530:~/Downloads$ sudo modprobe rtl8192cu
[sudo] password for zev: 
WARNING: Error inserting rtlwifi (/lib/modules/3.0.0-12-generic/updates/drivers/net/wireless/rtlwifi/rtlwifi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting rtl8192c_common (/lib/modules/3.0.0-12-generic/updates/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting rtl8192cu (/lib/modules/3.0.0-12-generic/updates/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko): Unknown symbol in module, or unknown parameter (see dmesg)

I tried to reinstall the drivers because NetworkManager showed the device but failed to actually connect to any wifi network. I thought that there might be some driver issue, and saw other forums that suggested trying compat.

---

### Post by matbluvenger on 2012-02-15
Interestingly enough I *just* solved this issue from advice on another thread.


> **qkslvrwolf said:**
> Ok, so just in case anyone comes after me.  I was never able to get this working with the open source drivers.  However, I was able to get it working very well with Realtek's proprietary(?) drivers.  (You still have to make/make install them, so they're give you code...maybe they're not proprietary?  Whatever, their install script works really well.)

Anyone, I went to this link:  [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2772](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#2772)

Grabbed the 8192cu linux driver zip, unzipped it, and just ran 

```
chmod +x install.sh
sudo ./install.sh
```

from the directory that was created when I unzipped it, and voila!  I have a working usb wireless nic. 

Ironic, too, considering I spent about 3 hours trying to get the compat stuff to work.  :-)

---

### Post by chili555 on 2012-02-16
rtl8192cu is certainly correct for your device. You'll need to uninstall compat first to get your wireless system going correctly:```
cd Downloads/compat_directory   <--wherever you extracted the files
sudo su
make uninstall
exit
```Now can you modprobe the old in-kernel rtl8192cu correctly?```
sudo modprobe rtl8192cu
```Are there any clues as to why it doesn't connect here?```
sudo cat /var/log/syslog | grep -e etwork -e 819 | tail -n20
```

---

### Post by ams1888 on 2012-02-16
uninstalled compat, then ran:
```
zev@zev-Lenovo-IdeaPad-Y530:~$ sudo modprobe rtl8192cu
WARNING: Error inserting rtlwifi (/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko): Invalid argument
WARNING: Error inserting rtl8192c_common (/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko): Invalid argument
FATAL: Error inserting rtl8192cu (/lib/modules/3.0.0-12-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko): Invalid argument

```


sudo cat /var/log/syslog | grep -e etwork -e 819 | tail -n20  
returns nothing

---

### Post by chili555 on 2012-02-16
Can you temporarily get a wired ethernet connection and do:```
sudo apt-get install --reinstall linux-image-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

Reboot and try again:```
sudo modprobe rtl8192cu
```

---

### Post by ams1888 on 2012-02-16
Wifi works now! 

modprobe rtl8192cu returns nothing.

interestingly, the device now only manages to connect to a network when i unplug and replug it. If i connect/disconnect using network manager it fails. If this doesn't suggest some worrisome underlying problem, I can live with it, and let you get back to being one of the most helpful linux forum members I've ever seen! 

Thanks

---

### Post by chili555 on 2012-02-16
> If i connect/disconnect using network manager it fails.Meaning what? It tries and asks for your WPA2 password and times out...or...what?

Thanks for your kind comments. I appreciate it.

---

### Post by Hihwrya on 2012-11-19
> **matbluvenger said:**
> Interestingly enough I *just* solved this issue from advice on another thread.

Hey thanks for the heads up on Realtek Linux drivers. After many hours fighting drivers trying to get my Gigabyte PCI card to work, this pointed me in the right direction. Just downloaded the script for my particular chipset (RTL8168B) followed the directions in their readme file and viola! Works great. Very much a newbie using Ubuntu 12.10.

---

### Post by ben87naruto on 2013-03-24
hey guys.. i'm new to linux.! and i've been following u're forums on installing this godforsaken router n150 [http://www.netgear.com/home/products/wireless-adapters/simplesharing/WNA1000M.aspx](http://www.netgear.com/home/products/wireless-adapters/simplesharing/WNA1000M.aspx)

for the past few days.. 

i've tried installing the file from the realtek link u'd given previously in some forum.. and still it doesn't connect to the wifi.. Pls help.! The ethernet is fine btw.. 

[COLOR=#333333][FONT=lucida grande]thuthi@thuthi-hp:~$ lsusb[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]Bus 001 Device 002: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS][/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR]
[COLOR=#333333][FONT=lucida grande]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

thuthi@thuthi-hp:~$ lsmod
Module                  Size  Used by
arc4                   12530  2 
joydev                 17458  0 
hp_wmi                 18049  0 
sparse_keymap          13891  1 hp_wmi
snd_hda_codec_conexant    61898  1 
rtl8192cu              67660  0 
rtl8192c_common        48780  1 rtl8192cu
rtlwifi                74749  1 rtl8192cu
mac80211              540032  3 rtl8192cu,rtl8192c_common,rtlwifi
kvm                   414071  0 
cfg80211              206797  2 rtlwifi,mac80211
snd_hda_intel          33492  3 
snd_hda_codec         134213  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
nvidia              11257760  45 
r852                   18282  0 
sm_common              16861  1 r852
nand                   54707  2 r852,sm_common
nand_ids               12724  1 nand
r592                   18020  0 
mtd                    44906  2 sm_common,nand
nand_bch               13148  1 nand
bch                    17435  1 nand_bch
nand_ecc               13274  1 nand
memstick               16555  1 r592
snd                    78921  15 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                95595  0 
serio_raw              13216  0 
edac_core              52452  0 
edac_mce_amd           23304  0 
k8temp                 12979  0 
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
nv_tco                 13565  0 
i2c_nforce2            13014  0 
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
rfcomm                 46620  0 
bluetooth             209249  10 bnep,rfcomm
wmi                    19071  1 hp_wmi
binfmt_misc            17501  1 
mac_hid                13206  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
firewire_ohci          40402  0 
sdhci_pci              18617  0 
firewire_core          64369  1 firewire_ohci
crc_itu_t              12708  1 firewire_core
sdhci                  32646  1 sdhci_pci
video                  19391  0 
forcedeth              67157  0 
pata_amd               14119  0 
sata_nv                31831  2 
thuthi@thuthi-hp:~$ 

thuthi@thuthi-hp:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:64:76:d6  
          inet addr:10.0.0.5  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe64:76d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2454 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3179525 (3.1 MB)  TX bytes:350725 (350.7 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22165 (22.1 KB)  TX bytes:22165 (22.1 KB)


wlan0     Link encap:Ethernet  HWaddr e0:46:9a:28:ff:c2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


thuthi@thuthi-hp:~$ 


Also some kde wallet keeps coming up and asking me for saving password.. would that be interfering maybe..! i'm a noob in linux.. any help wud be appreciated.. thank you..



[/FONT][/COLOR]

---

