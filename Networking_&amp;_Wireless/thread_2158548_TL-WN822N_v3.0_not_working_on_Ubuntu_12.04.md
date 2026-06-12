---
title: "TL-WN822N v3.0 not working on Ubuntu 12.04"
date: 2013-06-29
forum: Networking &amp; Wireless
---

### Post by londontechie on 2013-06-29
Hi All, 
I'm facing a strange problem.
I just bought TP-Link TL-WN822N v3.0 USB adapter and have been trying to make it work with Ubuntu 12.04.

I can see loads of wirless networks except my own wireless sky router. This is really weird. How come it doesn't show up my own wireless network but shows others?

This works perfectly fine on Windows 7.

I've Windows 7 and Ubuntu on HP Compaw dc7900.

I tried to manually add wireless network by entering SSID, MAC etc but it still doesn't work.

Am I missing something?

Following are some useful command outputs:

root@HP-Compaq-dc7900:~# lsusb 
Bus 002 Device 003: ID 0bda:8178 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

root@HP-Compaq-dc7900:~# rfkill list
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

root@HP-Compaq-dc7900:~# lsmod
Module                  Size  Used by
ath9k_htc              90845  0 
ath9k_common           13782  1 ath9k_htc
ath9k_hw              384090  2 ath9k_htc,ath9k_common
ath                    19436  3 ath9k_htc,ath9k_common,ath9k_hw
joydev                 17394  0 
dm_crypt               22572  1 
rfcomm                 38104  0 
parport_pc             32115  0 
bnep                   17791  2 
ppdev                  12850  0 
bluetooth             189585  10 rfcomm,bnep
arc4                   12474  2 
rtl8192cu              67480  0 
rtl8192c_common        47696  1 rtl8192cu
rtlwifi                65304  1 rtl8192cu
mac80211              475546  4 ath9k_htc,rtl8192cu,rtl8192c_common,rtlwifi
snd_hda_codec_analog    75324  1 
cfg80211              181041  4 ath9k_htc,ath,rtlwifi,mac80211
coretemp               13362  0 
kvm                   365588  0 
tpm_infineon           17297  0 
hp_wmi                 13653  0 
gpio_ich               13160  0 
sparse_keymap          13659  1 hp_wmi
snd_hda_intel          32983  0 
snd_hda_codec         116477  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13277  1 snd_hda_codec
snd_pcm                81124  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13133  0 
snd_rawmidi            25426  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
microcode              18396  0 
snd_seq                51594  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
tpm_tis                18279  0 
snd                    62675  9 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                91381  0 
serio_raw              13032  0 
soundcore              14636  1 snd
lpc_ich                16993  0 
snd_page_alloc         14109  2 snd_hda_intel,snd_pcm
mei                    36404  0 
mac_hid                13078  0 
lp                     17456  0 
parport                40931  3 parport_pc,ppdev,lp
floppy                 60214  0 
wmi                    18745  1 hp_wmi
i915                  479235  3 
drm_kms_helper         47459  1 i915
drm                   239971  4 i915,drm_kms_helper
ahci                   25621  4 
libahci                26166  1 ahci
i2c_algo_bit           13317  1 i915
video                  19117  1 i915
e1000e                177679  0 

root@HP-Compaq-dc7900:~# iwconfig
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by londontechie on 2013-06-29
I followed instructions on this post [http://ubuntuforums.org/showthread.php?t=1905813](http://ubuntuforums.org/showthread.php?t=1905813) and various other forum posts but none seem to work.

modprobe ath9k_htc -> rebooting doesn't help.

---

### Post by londontechie on 2013-06-29
Some more useful details. Just checked dmesg output and it does recognizes the usb wifi adapter? But it doesn't show up in lsusb?

[  729.020031] usb 2-5: new high-speed USB device number 3 using ehci_hcd
[  729.153475] usb 2-5: New USB device found, idVendor=0bda, idProduct=8178
[  729.153479] usb 2-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  729.153482] usb 2-5: Product: USB WLAN
[  729.153485] usb 2-5: Manufacturer: 802.11n
[  729.153488] usb 2-5: SerialNumber: 00e04c000001
[  729.153972] rtl8192cu: Chip version 0x11
[  729.230473] rtl8192cu: MAC address: f8:1a:67:08:c1:94
[  729.230477] rtl8192cu: Board Type 0
[  729.230720] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[  729.230724] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  729.230727] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  729.230729] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[  729.230731] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  729.230734] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[  729.230736] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  729.230738] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[  729.230740] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  729.230742] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[  729.230745] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  729.230747] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[  729.230749] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  729.230751] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[  729.230753] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  729.230756] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[  729.230758] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  729.230760] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[  729.230762] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  729.230764] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[  729.230767] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  729.230769] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[  729.230771] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[  729.230773] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[  729.230775] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[  729.230777] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[  729.230813] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[  729.233357] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[  729.233469] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[  729.234353] rtlwifi: wireless switch is on
[  729.247716] rtl8192cu: MAC auto ON okay!
[  729.280359] rtl8192cu: Tx queue select: 0x05
[  729.649911] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  729.650135] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

---

### Post by londontechie on 2013-06-29
# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:81:1b:f8:62  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:81ff:fe1b:f862/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21774967 (21.7 MB)  TX bytes:2455375 (2.4 MB)
          Interrupt:19 Memory:f0500000-f0520000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1098 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1098 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123778 (123.7 KB)  TX bytes:123778 (123.7 KB)

wlan0     Link encap:Ethernet  HWaddr f8:1a:67:08:c1:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by londontechie on 2013-06-29
finally figured it out.

---

### Post by wildmanne39 on 2013-06-29
That's great! Please post the solution so everyone can benefit from your experience.
Thanks

---

### Post by londontechie on 2013-06-30
Ended up writing a blog post while I was resolving this issue, it might help if someone is having similar problem as I had.
[http://www.ajaykumarsingh.com/linux/tp-link-tl-wn822n-300mbps-high-gain-wireless-n-usb-adapter-not-working-on-ubuntu-12-04.html](http://www.ajaykumarsingh.com/linux/tp-link-tl-wn822n-300mbps-high-gain-wireless-n-usb-adapter-not-working-on-ubuntu-12-04.html)

Here is the solution
[COLOR=#333333][FONT=Open Sans]**1) Download Realtek driver for Linux from Realtek website **[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans][http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU)[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]If above link doesn’t work then search for RTL8192CU driver on Realtek website.[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]**2) Download and install the driver**[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]After downloading above driver, unzip it.[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]cd to the folder where you unzipped the driver and run following commands. If you are not root then use sudo before these commands where required.[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]*chmod 755 ./install.sh*
*./install.sh*[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]**3) Blacklist existing drivers**[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]*vi /etc/modprobe.d/blacklist.conf*[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]At the end add followings[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]**4) Auto load module**[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]*vi /etc/modules *[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]Add **8192cu** at the end of this file.[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]**5) Reboot**[/FONT][/COLOR]
[COLOR=#333333][FONT=Open Sans]*reboot*[/FONT][/COLOR]

---

### Post by adambh on 2013-12-19
This didn't work for me using 13.10. Initially I had intermittent connection (i.e. would connect and then drop out); interesting, I could see all of my neighbour's wifi networks but not mine.  After blacklisting the drivers I had no wifi at all. Signal strength is not a problem as the wifi works fine under Windows 8. Found gedit much easier to use than vi editor. Still stuck.

---

### Post by praseodym on 2013-12-31
For 13.10 you need a patched driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git 
git clone https://github.com/pvaret/rtl8192cu-fixes.git
sudo dkms add ./rtl8192cu-fixes
sudo dkms install 8192cu/1.7
echo "blacklist rtl8192cu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
Reboot.

---

### Post by Rbazley on 2014-01-08
Just wanted to thank you for this, fixed my problem perfectly.

---

### Post by xp15 on 2014-04-18
I can't clone the git!

```
dvir@Yam:~$ git clone https://github.com/pvaret/rtl8192cu-fixes.git
Cloning into 'rtl8192cu-fixes'...
remote: Reusing existing pack: 366, done.
error: RPC failed; result=56, HTTP code = 200 19.00 KiB/s      
fatal: The remote end hung up unexpectedly
fatal: early EOF
fatal: index-pack failed
dvir@Yam:~$
```

What should I do?
I have TP-LINK TL-WN822N Ver:3.0 Im using Lubuntu 13.10.
Help? Pls help.

---

### Post by praseodym on 2014-04-18
```
git clone https://github.com/pvaret/rtl8192cu-fixes.git
Cloning into 'rtl8192cu-fixes'...
remote: Reusing existing pack: 366, done.
remote: Total 366 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (366/366), 1.74 MiB | 828 KiB/s, done.
Resolving deltas: 100% (186/186), done.
```

Here it works, try it again after removing the folder **rtl8192cu-fixes**

---

### Post by xp15 on 2014-04-18
Well, It worked now, the clone. I will keep fixing it! Thank!
used this, And some how here it worked (I did it from the start):
[http://ubuntuforums.org/showthread.php?t=2208485&p=12944636#post12944636](http://ubuntuforums.org/showthread.php?t=2208485&p=12944636#post12944636)

---

### Post by xp15 on 2014-04-18
> **praseodym said:**
> ```
git clone https://github.com/pvaret/rtl8192cu-fixes.git
Cloning into 'rtl8192cu-fixes'...
remote: Reusing existing pack: 366, done.
remote: Total 366 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (366/366), 1.74 MiB | 828 KiB/s, done.
Resolving deltas: 100% (186/186), done.
```

Here it works, try it again after removing the folder **rtl8192cu-fixes**

Thank for the so quick answer! I have no idea how, but running the commands from the start by the other guide in the link made it working. Is there ant difference between them?

---

### Post by praseodym on 2014-04-18
No, maybe an intermittent connection problem?!

---

### Post by ferdinandvwyk on 2014-08-13
Just wanted to confirm that the instructions found here: [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes) fixed my problems (under 12.04 LTS 64-bit kernel 3.13.0-33). Thanks praseodym!

---

