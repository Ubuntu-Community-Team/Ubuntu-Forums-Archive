---
title: "new USB Wifi..."
date: 2011-01-15
forum: Networking &amp; Wireless
---

### Post by Shadyboy on 2011-01-15
I recently bought myself an Trendnet usb wifi ( TEW-648UBM )
and at the store they told me that it "should" work under linux.

Wich it did not when I opened it up and pluged it into my labtop running ubuntu 10.10 ( 64 version )

Just wondering on if there is anyone else who has the same usb wifi as me? and / or have a sollution so that I can get it to work?

---

### Post by MooPi on 2011-01-15
Can you give us some details please. From a terminal type separately 
```
lsusb
iwconfig
lsmod
```

---

### Post by Zaffzaff on 2011-03-01
I'm having the same exact issue as it were. 10.10 with the 648ubm, and the cd doesnt support linux

Anywhere I can find the drivers?

---

### Post by Zaffzaff on 2011-03-01
rob@Citadel:~$ lsusb
Bus 004 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 062a:0001 Creative Labs Notebook Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 04f2:b016 Chicony Electronics Co., Ltd VGA 30fps UVC Webcam
Bus 001 Device 003: ID 20f4:648b  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
rob@Citadel:~$ lsmod
Module                  Size  Used by
rfcomm                 33811  4 
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
sco                     7998  2 
bnep                    9542  2 
l2cap                  37008  16 rfcomm,bnep
nvidia               9329739  40 
snd_hda_codec_conexant    30003  1 
joydev                  8767  0 
snd_hda_intel          22203  2 
snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip     7736  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   1959533  0 
btusb                  10969  2 
usbhid                 36882  0 
uvcvideo               55847  0 
hp_wmi                  5223  0 
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
hid                    67742  1 usbhid
snd                    49038  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r852                    9536  0 
sm_common               3285  1 r852
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
lib80211                5058  2 lib80211_crypt_tkip,wl
psmouse                59033  0 
serio_raw               4022  0 
mtd                    18877  2 sm_common,nand
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  1 nvidia
video                  18712  0 
output                  1883  1 video
k8temp                  3228  0 
i2c_nforce2             5179  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
firewire_ohci          21234  0 
firewire_core          46643  1 firewire_ohci
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
forcedeth              49433  0 
led_class               2633  1 sdhci
crc_itu_t               1383  1 firewire_core
ahci                   19198  2 
libahci                21728  1 ahci
pata_amd                8746  0 
rob@Citadel:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

rob@Citadel:~$

---

### Post by Cloudy Brain on 2011-06-23
Don't know if this helps, I've had some luck with the Realtek 8192cu driver on 32bit Natty:

[http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true&SortByDesc=1#2772]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true&SortByDesc=1#2772")

(Don't know if it compiles to 64bit, I may try it one day)

I'd googled the usb id 20f4 648b and found the chipset from the LKDDb:

[http://cateee.net/lkddb/web-lkddb/RTLWIFI.html]("http://cateee.net/lkddb/web-lkddb/RTLWIFI.html")

The driver compile/install is very easy as there's a script in the download that does the lot:

```
sudo ./install.sh
```

There's also some reasonable example documentation on wpa_supplicant too to get it to connect with WPA.

The GUI Network Manager stuff doesn't work though, I have to scan and connect to networks on the command line. A few useful commands (the TEW-648UBM is wlan1 on my laptop):

```

sudo ifconfig wlan1 up
sudo iwlist scan
sudo wpa_supplicant -Dwexp -iwlan1 -c ~/wpa.conf
sudo dhclient wlan1

```
where wpa.conf has the details of my wireless router; ssid and key.

I'm new to Ubuntu so I've still a lot to learn, maybe there's an easy way to fix the GUI side of things? For now I'm just pleased that I can connect at all :)

---

### Post by jedibrand on 2011-07-11
> **Cloudy Brain said:**
> Don't know if this helps, I've had some luck with the Realtek 8192cu driver on 32bit Natty:

[http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true&SortByDesc=1#2772]("http://218.210.127.131/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true&SortByDesc=1#2772")

(Don't know if it compiles to 64bit, I may try it one day)

I'd googled the usb id 20f4 648b and found the chipset from the LKDDb:

[http://cateee.net/lkddb/web-lkddb/RTLWIFI.html]("http://cateee.net/lkddb/web-lkddb/RTLWIFI.html")

The driver compile/install is very easy as there's a script in the download that does the lot:

```
sudo ./install.sh
```

There's also some reasonable example documentation on wpa_supplicant too to get it to connect with WPA.

The GUI Network Manager stuff doesn't work though, I have to scan and connect to networks on the command line. A few useful commands (the TEW-648UBM is wlan1 on my laptop):

```

sudo ifconfig wlan1 up
sudo iwlist scan
sudo wpa_supplicant -Dwexp -iwlan1 -c ~/wpa.conf
sudo dhclient wlan1

```
where wpa.conf has the details of my wireless router; ssid and key.

I'm new to Ubuntu so I've still a lot to learn, maybe there's an easy way to fix the GUI side of things? For now I'm just pleased that I can connect at all :)

Hey Cloudy, that's very helpful! I can report the drivers compile for 64-bit natty. Also, network manager is able to scan properly for APs (did it scan for you?). However, I cannot make a connection via network manager to a wpa2-psk authenticated AP, It simply does not succeed. Open AP's connect just fine via network manager, however. I might try wicd next.

In the meantime, could you share any more details about how you got yours to work with wpa_supplicant? Like maybe post your wpa_supplicant config? I can't even get mine to scan via iwlist. Granted, I removed Network manager before attempting to do anything on the command line (since the docs for the drivers you pointed to advise us to do so).  here's my wpa_supplicant config (WPA2 Personal TKIP):

```

ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
ap_scan=1
fast_reauth=1

network={
ssid="myssid"
proto=RSN
key_mgmt=WPA-PSK
pairwise=CCMP TKIP
group=CCMP TKIP
psk="mysecretpsk"
}

```

Another related issue is that sudo iwlist scan does not produce any results. However, I reinstalled network manager and reattempt, this time it does list results. Then again, I cannot seem to get wpa_supplicant to connect to my AP. The error I see is:

Associated with my-wireless-router's-mac-address
CTRL-EVENT-DISCONNECTED bssid=my-wireless-router's-mac-address reason=0 

Anywho, any insights would be much appreciated!

---

### Post by jedibrand on 2011-07-23
FYI, there's new drivers available (as of 7/20) for the RTL8192cu chipset.

Anyone care to offer some input on the issues I reported above?

---

### Post by Cloudy Brain on 2011-07-24
Hi jedibrand, thanks for the heads-up on the new drivers and confirmation of 64bit compile! I've not had chance to look at either but one day I will!

As for your request, here's my wpa_supplicant.conf

```

ctrl_interface=/var/run/wpa_supplicant
network={
    ssid="myssid"
    proto=WPA WPA2
    key_mgmt=WPA-PSK
    pairwise=CCMP TKIP
    group=CCMP TKIP
    psk="mypsk"
    #psk=mypskdigest
    priority=2
}
network={
  ssid="workssid"
  key_mgmt=NONE
  wep_key0=12345...
  wep_tx_keyidx=0
  priority=5
}

```

Biggest difference between mine and yours that I see is I've got proto=WPA WPA2 and you're RSN. The second network is for my office where we're using WEP, that connects fine for me too. I had tried using the pre-digested key with my WPA2 AP but that didn't seem to work and I can't remember where I'd read about that, will have to ask Mr Google.

Didn't have the patience to fight with the gui stuff so I ended up writing a noddy script that I leave on the desktop to make turning the radio on and connecting easier... (don't laugh!)

```

#!/bin/bash
gksudo ifconfig wlan1 up
sleep 5
gksudo wpa_supplicant Dwext -c/etc/wpa_supplicant/wpa_supplicant.conf -iwlan1 -B -s
sleep 5
gksudo dhclient wlan1

```

Not sure if all the sleeps are strictly necessary! Hope you have some better luck soon.

---

### Post by Cloudy Brain on 2011-07-26
Hi again jedibrand,

Just as a quick update, I reinstalled 11.04 on my laptop with the 64bit version last night. Compiled and installed the (older) RTL8192CU driver, slapped in the wpa_supplicant.conf and could connect to my AP with the 3 sudoed command line calls. That allowed me to get all the updates and download the latest r8192cu driver you pointed to. After rebooting from the kernel update and compile/install the latest driver I was up and running again. "sudo iwlist scan" scans all the AP's around just fine.

I didn't bother with uninstalling the Network Manager. The Software Centre doesn't think there's a network connection (i.e. for more info/reviews) but will happily download and install stuff.

I didn't use anything of wpa_supplicant that comes with the driver download, just the 'vanilla' one from the Ubuntu install. If you're still getting the CTRL-EVENT-DISCONNECTED 'errors' maybe try running wpa_supplicant in the foreground without the -B switch and maybe throw in a debug switch -d or -dd

One thing I forgot to mention before, I didn't have any luck with starting the wpa_supplicant daemon with the wait -W flag, which is what lead me to just scripting something.

---

### Post by melissaMontanano92 on 2011-07-26
my usb wi-fi working fine, but my venus evdo modem not working.

---

### Post by jedibrand on 2011-08-15
> **Cloudy Brain said:**
> Hi again jedibrand,

Just as a quick update, I reinstalled 11.04 on my laptop with the 64bit version last night. Compiled and installed the (older) RTL8192CU driver, slapped in the wpa_supplicant.conf and could connect to my AP with the 3 sudoed command line calls. That allowed me to get all the updates and download the latest r8192cu driver you pointed to. After rebooting from the kernel update and compile/install the latest driver I was up and running again. "sudo iwlist scan" scans all the AP's around just fine.

I didn't bother with uninstalling the Network Manager. The Software Centre doesn't think there's a network connection (i.e. for more info/reviews) but will happily download and install stuff.

I didn't use anything of wpa_supplicant that comes with the driver download, just the 'vanilla' one from the Ubuntu install. If you're still getting the CTRL-EVENT-DISCONNECTED 'errors' maybe try running wpa_supplicant in the foreground without the -B switch and maybe throw in a debug switch -d or -dd

One thing I forgot to mention before, I didn't have any luck with starting the wpa_supplicant daemon with the wait -W flag, which is what lead me to just scripting something.

My apologies for the late reply! I've been on vacation, and busy with life ;).

I've re-tried connecting to my AP with the new information you've provided. Unfortuantely, still no success. I should say that I am doing all of this on a Macbook Pro 8,1, though I doubt there would be any issues related tot he particular machine harware that the usb wireless dongle is on.

I will have to try connecting to another AP to see if there's any difference. Thanks again!

---

### Post by robolange on 2011-09-05
Just bought the Trendnet TEW-648UBM for use on Ubuntu 11.04 Natty.  I used the drivers from:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

That seemed less suspicious than downloading them from an unknown IP address, even if it is probably the same server.

Unlike apparently everyone else, I have had good results with Network Manager, so I never disable it.  I prefer to use it rather than the command line arguments and supplicant config files, which I find hard to get right.

And my approach paid off.  I installed the driver and rebooted.  Network Manager immediately detected the interface.  I was able to use it to associate with my personal network, which is protected by WPA2-Enterprise with EAP-TLS.  This setup is usually more involved than the less secure network types, so I will assume that those will work as well.

Note that I was using a vanilla Ubuntu install.  I had *not* disabled Network Manager or otherwise messed with it.  I have found that most of the directions on the Web to disable it cause lasting harm to its configuration.  If you have disabled Network Manager, later re-enabled it, and find that it is just not working right, I recommend a re-install unless you are *extremely* good at properly restoring configurations.  I also recommend ignoring instructions online that tell you to disable it and use manual configuration for end-user systems; more often than not they cause more harm than good.

Anyway, A+ to Realtek for its Linux support and Trendnet for using Realtek's chipset to make a neat little Wifi connector.

---

### Post by CableCat on 2012-02-29
I tried to install the lates driver from Realtek on Ubuntu 11.10 AMD64. It did not work.

I have bought 5 different mini USB wifi adaptors, to see if any would work. Only one did: Buffalo WLI-UC-GNM-EU.

Adaptor that worked:
* Buffalo AirStation N-Technology 150Mbps USB 2.0 Client [WLI-UC-GNM-EU]

Adaptors that did not work:
* NETGEAR G54/N150 Wireless USB Micro Adapter WNA1000M [WNA1000M-100PES]
* TRENDnet TEW 648UBM [TEW-648UBM]
* D-Link Wireless N 150 Micro USB Adapter DWA-121 [DWA-121]
* Belkin N150 Micro Wireless USB Adapter [F7D1102AZ]

Tested at 2012-02-28 in Ubuntu 11.10 and Daily Live.

---

