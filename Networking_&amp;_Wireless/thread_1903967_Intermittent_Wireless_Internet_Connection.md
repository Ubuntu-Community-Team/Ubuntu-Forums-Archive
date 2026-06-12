---
title: "Intermittent Wireless Internet Connection"
date: 2012-01-03
forum: Networking &amp; Wireless
---

### Post by mspalt on 2012-01-03
Greeting all,
I would like to declare an issue I'm having with Ubuntu 11.10 with regards to my wireless connection. It seems as though it's seldomly connecting to the access point. I loaded the latest drivers from Realtek's website and disabled my onboard wired lan interface.
 
Reading the logs w/in my router I can see the MAC address trying to connect, but with deauthenticated requests from some reason.
 
I'm connecting via hidden wireless network (not broadcasting SSID), running WPA2-PSK w/ AES encryption.
 
I've followed along with the instructions along other threads to no avail unfortunately. 
 
Help would be highly appreciated...
 
Thanks...regards

---

### Post by josephmills on 2012-01-03
> **mspalt said:**
> Greeting all,
I would like to declare an issue I'm having with Ubuntu 11.10 with regards to my wireless connection. It seems as though it's seldomly connecting to the access point. I loaded the latest drivers from Realtek's website and disabled my onboard wired lan interface.
 
Reading the logs w/in my router I can see the MAC address trying to connect, but with deauthenticated requests from some reason.
 
I'm connecting via hidden wireless network (not broadcasting SSID), running WPA2-PSK w/ AES encryption.
 
I've followed along with the instructions along other threads to no avail unfortunately. 



 

 
Help would be highly appreciated...
 
Thanks...regards





Hi there I was wondering if we could see more about your card and if you could tell us more about your computer? could you please open your terminal and enter ```
lspci -nn && lsmod && lsusb && 
``` then paste that all here thanks

---

### Post by mspalt on 2012-01-03
Thanks for quick response. Here is the output of the three requested commands.
 
```
mark@BEDROOM1:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
05:00.0 VGA compatible controller: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]
05:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600]
```
&#12288;
 
```
mark@BEDROOM1:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0048 Microsoft Corp. Office Keyboard 1.0A
Bus 002 Device 003: ID 041e:30e0 Creative Technology, Ltd 
```
 
 
&#12288;
```
mark@BEDROOM1:~$ sudo lsmod
Module Size Used by
nls_iso8859_1 12617 1 
nls_cp437 12751 1 
vfat 17308 1 
fat 55577 1 vfat
bnep 17923 2 
rfcomm 38408 0 
bluetooth 148839 10 bnep,rfcomm
arc4 12473 2 
ppdev 12849 0 
rtl8192ce 127361 0 
rtlwifi 107538 1 rtl8192ce
snd_usb_audio 100880 2 
snd_intel8x0 33318 2 
snd_ac97_codec 106082 1 snd_intel8x0
ac97_bus 12642 1 snd_ac97_codec
snd_hwdep 13276 1 snd_usb_audio
snd_usbmidi_lib 24558 1 snd_usb_audio
mac80211 393459 2 rtl8192ce,rtlwifi
snd_pcm 80435 3 snd_usb_audio,snd_intel8x0,snd_ac97_codec
radeon 925193 3 
snd_seq_midi 13132 0 
snd_seq_midi_event 14475 1 snd_seq_midi
psmouse 73673 0 
ttm 65224 1 radeon
drm_kms_helper 32889 1 radeon
usb_storage 44173 1 
snd_seq 51567 2 snd_seq_midi,snd_seq_midi_event
snd_rawmidi 25241 2 snd_usbmidi_lib,snd_seq_midi
serio_raw 12990 0 
drm 192194 5 radeon,ttm,drm_kms_helper
uas 17699 0 
k8temp 12905 0 
cfg80211 172392 2 rtlwifi,mac80211
snd_timer 28932 2 snd_pcm,snd_seq
snd_seq_device 14172 3 snd_seq_midi,snd_rawmidi,snd_seq
snd 55902 18 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit 13199 1 radeon
soundcore 12600 1 snd
snd_page_alloc 14115 2 snd_intel8x0,snd_pcm
i2c_nforce2 12906 0 
binfmt_misc 17292 1 
parport_pc 32114 1 
lp 17455 0 
parport 40930 3 ppdev,parport_pc,lp
usbhid 41905 0 
hid 77367 1 usbhid
sata_nv 23379 2 
pata_amd 13753 0 
floppy 60310 0
```

---

### Post by mspalt on 2012-02-29
I have resolved my issue by properly compiling my drivers.  I blacklisted my current realtek drivers and ran following commands

sudo apt-get install build-essential checkinstall
mkdir /usr/local/src
sudo chown $USER /usr/local/src
sudo chmod u+rwx /usr/local/src
gedit /et/modprobe.d/blacklist.conf (blacklisted by inserting rtl8192ce into blank line)
sudo rmmod rtl8192ce

Downloaded updated unix drivers from:

[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)

And placed them into src where I extracted.  Then within that directory I ran following commands:


make uninstall
make clean
sudo su
make 
make install
reboot

Hope that helps somebody out there with similar issue.  Thanks!!

---

