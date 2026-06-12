---
title: "Broadcom BCM4312 802.11b/g LP-PHY [14e4:4315] no connectivity"
date: 2011-10-31
forum: Networking &amp; Wireless
---

### Post by johndoe31415 on 2011-10-31
Hi forum,

I have a Lenovo S12 Netbook with a BCM4312 network adapter. That thing worked fine with Ubuntu LTS. A week ago I've decided to upgrade to Oneiric. Since I also wanted to repartition the hard drive, I did a clean install. I've not gotten the Wifi to work since.

Here's the problem: I've installed the proprietary drivers in the bcmwl-kernel-source package. The firmware (that dmesg complained about not finding at first) is also there:

```

julbook [/proc]: ls /lib/firmware/b43/*ucode15*
-rw-r--r-- 1 root root 34K   31.10.2011 18:39:51 /lib/firmware/b43/ucode15.fw

```I've tried reinstalling and dpkg reconfigure for the bcmwl-package, to no avail. If I select "Enable wireless" in Network Manager, it gives me a checkmark which then disappears after about 10 seonds again, with no message whatsoever.

When trying on the command line, I can get the wifi adapter to scan the network:

```

julbook [/proc]: iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: xx:xx:xx:xx:xx:xx
                    ESSID:"WLAN-7C9542"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
...

```But when trying to get it to associate it to ANYTHING, this just silently fails:

```

julbook [~]: ifconfig eth1
eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet6 addr: fe80::xxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

julbook [~]: iwconfig eth1
eth1      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

julbook [~]: iwconfig eth1 essid WLAN-7C9542
julbook [~]: iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```Also, the packet RX/TX count shown by ifconfig is always zero.

Then I checked the original Broadcom readme from [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

It says to check that neither the ssb, bcma nor b43 modules are loaded. Neither are:

```

julbook [~]: lsmod  | grep "b43\|ssb\|bcma"

```Only the propietary driver is loaded:

```

julbook [~]: lsmod  | grep wl
wl                   2646601  0 
lib80211               14570  2 wl,lib80211_crypt_tkip

```A thing that struck me as strange is that the use count of the module is zero. This might be a bug in the driver itself, I don't know if it has any special meaning. The device is DEFINITELY the one that is connected to eth1 in my case, as:

```

julbook [~]: ifconfig eth1 >/dev/null
julbook [~]: rmmod wl
julbook [~]: ifconfig eth1 >/dev/null
eth1: error fetching interface information: Device not found

```

Reinserting the module does not give any error message of any kind:

```

julbook [~]: modprobe wl
julbook [~]: dmesg
[ 2647.751031] wl 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 2647.751063] wl 0000:03:00.0: setting latency timer to 64
[ 2648.104442] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.38

```To sum it all up: I'm REALLY puzzled here. Any ideas are greatly appreciated.

Best regards,
Joe

---

### Post by praseodym on 2011-10-31
Hi,

please show the complete output of

lsmod

---

### Post by johndoe31415 on 2011-11-01
Hi,

```

Module                  Size  Used by
rfcomm                 38408  12 
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  3 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
joydev                 17393  0 
snd_seq_midi           13132  0 
acer_wmi               23302  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
btusb                  18160  2 
bluetooth             148839  23 rfcomm,bnep,btusb
lib80211_crypt_tkip    17240  0 
wl                   2646601  0 
uvcvideo               67271  0 
psmouse                73673  0 
snd                    55902  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              12990  0 
videodev               85626  1 uvcvideo
i915                  505108  2 
drm_kms_helper         32889  1 i915
drm                   192226  3 i915,drm_kms_helper
ideapad_laptop         13575  0 
i2c_algo_bit           13199  1 i915
sparse_keymap          13658  2 acer_wmi,ideapad_laptop
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lib80211               14570  2 lib80211_crypt_tkip,wl
video                  18908  1 i915
wmi                    18744  1 acer_wmi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
reiserfs              230932  3 
ahci                   21634  4 
libahci                25727  1 ahci
tg3                   132972  0 

```

---

### Post by praseodym on 2011-11-01
Unload this module:

```
sudo rmmod acer_wmi
```
If it is loaded again at boot-up, put it onto the blacklist:

```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
I recommend pure WPA2-AES encryption for stability reasons

---

### Post by johndoe31415 on 2011-11-01
You, Sir, are a genius! The acer_wmi module really was causing the problem. After removing & blacklisting it, everything works as expected. Thank you so much!

If by any chance (cause you're in Berlin) you attend the CCC next month maybe we can meet up and I'll buy you a beer (or Club Mate) :-)

Best regards,
Joe

---

