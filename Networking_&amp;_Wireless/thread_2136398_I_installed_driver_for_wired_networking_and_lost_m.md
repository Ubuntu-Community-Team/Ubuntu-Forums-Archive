---
title: "I installed driver for wired networking and lost my WiFi. How can I get it back?"
date: 2013-04-17
forum: Networking &amp; Wireless
---

### Post by alhefner on 2013-04-17
**Admins, I decided to post here and there is an earlier post exactly like it in the beginner's forum. Please delete that one so I'm not cluttering up the system with duplicate posts. Thank you!**

I had **alx** installed before and it worked well with the WiFi. In the mean time, I changed my install to 12.04LTS on an external HDD then again installed **alx** for ethernet.

The only other thing I have done is plug in my mobile broadband adapter and play around in Ubuntu to see if it would connect. I did not download any additional software for that, just followed the networking prompts that Ubuntu presented me to select country and service provider. It didn't work so I didn't worry about it since I felt I would be able to fall back on WiFi which had been doing well enough.

Now, I don't even have the option of looking for available WiFi signals. I would like to get that feature back but don't know how to go about it. I doubt that **alx** is causing a conflict since it was working well with WiFi when I had 12.10 installed as dual boot and WiFi was working on 12.04LTS before I started playing around with the mobile broadband stuff.

Thanks in advance! I know you folks will come through for me!

---

### Post by wildmanne39 on 2013-04-17
Hi, did you shutdown your dongle ad reboot?

Did you install updates?

Copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by alhefner on 2013-04-17
> **Wild Man said:**
> Hi, did you shutdown your dongle ad reboot?

Did you install updates?

Copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```


Yes, I did take out the dongle and reboot.

Unfortunately, in Ubuntu, I'm without internet access. No wired connection at my location right now but windows does let me use my Verizon Mobile Broadband.

I'm looking at the command and it looks like I could download the file while in Windows and put it on a DVD to run. Would that work? Not sure of the exact steps to do that though.

---

### Post by wildmanne39 on 2013-04-17
You can do it this way:
Copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

You need to be where the network is at that you want to connect to so we can see what those settings are when you run the script.
Thanks

---

### Post by alhefner on 2013-04-17
> **Wild Man said:**
> If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)

You need to be where the network is at that you want to connect to so we can see what those settings are when you run the script.
Thanks

Well, I downloaded the script and ran it. Got no output file at all. Several wireless networks are available here if I can get WiFi to work.

Perhaps I need to see what wireless devices are seen by Ubuntu / Linux and go from there. It really was working well at one time but now does not show up at all in the network options.

---

### Post by wildmanne39 on 2013-04-17
It did not create the netinfo.txt file in your home folder?

> Perhaps I need to see what wireless devices are seen by Ubuntu / Linux and go from there.
that is one of the things the wireless script does and so much more.
Thanks

---

### Post by alhefner on 2013-04-17
The script did not generate the file at all. I tried just running it with the "Run" button and got nothing then tried running it in a terminal and only got a flash of terminal and then nothing.

My wireless device is - Realtek RTL8188CE Wireless Lan 802.11n PCI-E NIC -. I did some more searching and found that folks are doing the things below to investigate their system. Maybe the results can help things along.
```
lspci result:

alan@alan-Satellite-C855:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
alan@alan-Satellite-C855:~$ 

lsusb result:

alan@alan-Satellite-C855:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 003: ID 0bc2:5031 Seagate RSS LLC FreeAgent GoFlex USB 3.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 10f1:1a3d Importek 

sudo lshw -C NETWORK result:

alan@alan-Satellite-C855:~$ sudo lshw -C NETWORK
[sudo] password for alan: 
  *-network               
       description: Ethernet interface
       product: AR8162 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 00:26:6c:17:da:3a
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx firmware=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:b8500000-b853ffff ioport:3000(size=128)
  *-network
       description: Network controller
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=rtl8192ce latency=0
       resources: irq:17 ioport:2000(size=256) memory:b8400000-b8403fff
alan@alan-Satellite-C855:~$ 
```

---

### Post by wildmanne39 on 2013-04-17
Hi, please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
nm-tool
sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan -e wpa -e etwork | tail -n50
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by alhefner on 2013-04-17
OK I did all that and below are the results.

```
Results:

alan@alan-Satellite-C855:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux alan-Satellite-C855 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

alan@alan-Satellite-C855:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
	Subsystem: Toshiba America Info Systems Device [1179:ff1e]
	Kernel driver in use: alx
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8211]
	Kernel driver in use: rtl8192ce


alan@alan-Satellite-C855:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 003 Device 003: ID 0bc2:5031 Seagate RSS LLC FreeAgent GoFlex USB 3.0
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 10f1:1a3d Importek 


alan@alan-Satellite-C855:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.


alan@alan-Satellite-C855:~$ rfkill list all
alan@alan-Satellite-C855:~$ 


alan@alan-Satellite-C855:~$ lsmod
Module                  Size  Used by
parport_pc             32867  0 
ppdev                  17114  0 
rfcomm                 47562  0 
bnep                   18240  2 
bluetooth             211812  10 rfcomm,bnep
snd_hda_codec_hdmi     32476  1 
snd_hda_codec_realtek    79756  1 
joydev                 17694  0 
rtl8192ce              58779  0 
rtl8192c_common        49512  1 rtl8192ce
rtlwifi                76086  1 rtl8192ce
alx                    81351  0 
mac80211              555198  3 rtl8192ce,rtl8192c_common,rtlwifi
compat                 13228  1 alx
cfg80211              208382  2 rtlwifi,mac80211
coretemp               13642  0 
kvm_intel             137888  0 
kvm                   422160  1 kvm_intel
ghash_clmulni_intel    13221  0 
cryptd                 20531  1 ghash_clmulni_intel
microcode              23030  0 
snd_hda_intel          34117  3 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
psmouse               102075  0 
serio_raw              13216  0 
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
lpc_ich                17145  0 
snd_seq_midi_event     14900  1 snd_seq_midi
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
rts5139               350620  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
mei                    41410  0 
i915                  530857  3 
drm_kms_helper         49259  1 i915
mac_hid                13254  0 
drm                   290344  4 i915,drm_kms_helper
i2c_algo_bit           13565  1 i915
video                  19598  1 i915
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
hid_logitech_dj        18768  0 
usbhid                 47259  1 hid_logitech_dj
hid                   100815  2 hid_logitech_dj,usbhid
usb_storage            49288  5 


alan@alan-Satellite-C855:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        00:26:6C:17:DA:3A

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



alan@alan-Satellite-C855:~$ sudo cat /var/log/syslog | grep -e rtl -e firmware -e wlan -e wpa -e etwork | tail -n50
[sudo] password for alan: 
Apr 17 15:10:38 alan-Satellite-C855 NetworkManager[878]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 17 15:10:38 alan-Satellite-C855 NetworkManager[878]: <info> (eth0): now managed
Apr 17 15:10:38 alan-Satellite-C855 NetworkManager[878]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 17 15:10:38 alan-Satellite-C855 NetworkManager[878]: <info> (eth0): bringing up device.
Apr 17 15:10:38 alan-Satellite-C855 NetworkManager[878]: <info> (eth0): preparing device.
Apr 17 15:10:38 alan-Satellite-C855 NetworkManager[878]: <info> (eth0): deactivating device (reason 'managed') [2]
Apr 17 15:10:38 alan-Satellite-C855 NetworkManager[878]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0
Apr 17 15:56:39 alan-Satellite-C855 kernel: [   17.252106] type=1400 audit(1366239397.183:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=578 comm="apparmor_parser"
Apr 17 15:56:39 alan-Satellite-C855 kernel: [   17.451297] Qualcomm Atheros(R) AR813x/AR815x/AR816x PCI-E Ethernet Network Driver
Apr 17 15:56:39 alan-Satellite-C855 kernel: [   17.454284] alx: Atheros Gigabit Network Connection
Apr 17 15:56:39 alan-Satellite-C855 kernel: [   17.538404] rtl8192ce: ****** This B_CUT device may not work with kernels 3.6 and earlier
Apr 17 15:56:39 alan-Satellite-C855 kernel: [   17.538406] rtl8192ce: Using firmware rtlwifi/rtl8192cfwU_B.bin
Apr 17 15:56:39 alan-Satellite-C855 kernel: [   17.540697] rtlwifi: Firmware rtlwifi/rtl8192cfwU_B.bin not available
Apr 17 15:56:39 alan-Satellite-C855 kernel: [   19.206045] type=1400 audit(1366239399.139:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=863 comm="apparmor_parser"
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> NetworkManager (version 0.9.4.0) is starting...
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> DNS: loaded plugin dnsmasq
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]:    SCPlugin-Ifupdown: init!
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]:    SCPlugin-Ifupdown: update_system_hostname
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]:    SCPluginIfupdown: management mode: unmanaged
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0, iface: eth0)
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]:    SCPlugin-Ifupdown: end _init.
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]:    Ifupdown: get unmanaged devices count: 0
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]:    SCPlugin-Ifupdown: (30989104) ... get_connections.
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]:    SCPlugin-Ifupdown: (30989104) ... get_connections (managed=false): return empty list.
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]:    keyfile: parsing Verizon connection ... 
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]:    keyfile:     read connection 'Verizon connection'
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]:    Ifupdown: get unmanaged devices count: 0
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> modem-manager is now available
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> monitoring kernel firmware directory '/lib/firmware'.
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> WiFi enabled by radio killswitch; enabled by state file
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> WWAN enabled by radio killswitch; enabled by state file
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> WiMAX enabled by radio killswitch; enabled by state file
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> Networking is enabled by state file
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <warn> failed to allocate link cache: (-10) Operation not supported
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> (eth0): carrier is OFF
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> (eth0): new Ethernet device (driver: 'alx' ifindex: 2)
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> (eth0): now managed
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> (eth0): bringing up device.
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> (eth0): preparing device.
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> (eth0): deactivating device (reason 'managed') [2]
Apr 17 15:56:39 alan-Satellite-C855 NetworkManager[872]: <info> Added default wired connection 'Wired connection 1' for /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/eth0
alan@alan-Satellite-C855:~$ 


```

One of these days, I may learn how to interpret all that! Thanks guys!

---

### Post by alhefner on 2013-04-18
I think I got it going! I went to the Realtek site and clicked through to the drivers for my chipset and downloaed that. Then, I booted up in Ubuntu and copied the file to my home directory and extracted it there. Once the new directory was made, one heck of a long name on that one, I opened it and just followed the instructions in the "readme" file.

Right now, I'm using Ubuntu with my wireless connection. If it keeps on working, I'll mark this thread as solved. Thanks for all the work folks! I know you put some time and effort into it all and I never considered going the simple route until tonight.

---

### Post by wildmanne39 on 2013-04-18
That is what I was going to recommend sorry I did not get back to you sooner.

Glad it is working, would you post the directions here so the everyone will benefit?
Thanks

---

### Post by alhefner on 2013-04-18
Here is how I did it:

1. Go to the dowload location for the [Realtek RTL8188CE driver]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true").

2. Choose the most recent version for Linux and download it to your home directory. I had to use Windows to download so I put it in a Windows directory then copied it to my home folder using Ubuntu.

3. Right click on the compressed folder and choose "Extract Here". This will cause a new folder to be created in your home directory named ```
rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013
```

4. Use crtl+alt+t to open a terminal

5. in the terminal, do the following (one command line at a time):

```
cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013
sudo su
make
make install
reboot
```

6. Enjoy using your Realtek 8188CE wireless internet NIC!

If you have some other Realtek Wireless adapter, just go to the [Realtek site]("http://www.realtek.com/downloads/") and using the menu on the left of that page, navigate to it. Wireless adapters are called "Wireless LAN IC's" in that menu system... You may have to experiment with the choices to find the exact one you are looking for.

---

### Post by wildmanne39 on 2013-04-18
Thank you those are excellent direction.:)

---

