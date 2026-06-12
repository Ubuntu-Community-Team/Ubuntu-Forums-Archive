---
title: "Wireless RTL8191SEvA: card ok, can't scan, can't connect"
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by bbukh on 2012-11-11
I have RTL8191SEvA wireless card, and as far as I cannot connect to wireless. Any help is appreciated. My attempts at diagnostics are documented below.

Output of **sudo iwconfig wlan0**:
```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off

```

Output of **rfkill list all**:
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Output of **sudo iwlist wlan0 scan** (about 10cm from the working router, as tested from another computer):
```
wlan0     No scan results
```

Output of **sudo lsmod**:
```
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
rfcomm                 38408  0 
nvidia              10390874  33 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
snd_hda_codec_hdmi     31426  4 
joydev                 17393  0 
arc4                   12473  2 
sparse_keymap          13658  0 
snd_hda_codec_idt      60049  1 
snd_hda_intel          24262  3 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
usbhid                 41905  0 
hid                    77367  1 usbhid
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
rtl8192se              92551  0 
snd_seq_midi_event     14475  1 snd_seq_midi
pcspkr                 12614  0 
rtlwifi               107538  1 rtl8192se
psmouse                73673  0 
serio_raw              12990  0 
mac80211              272785  2 rtl8192se,rtlwifi
cfg80211              172392  2 rtlwifi,mac80211
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
jmb38x_ms              17406  0 
binfmt_misc            17292  1 
memstick               15857  1 jmb38x_ms
video                  18908  0 
snd                    55902  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    18744  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
jme                    40330  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci

```

The output of **sudo lshw -C network**:
```
  *-network
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: e0:91:53:2d:c6:8a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192se driverversion=3.0.0-12-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:e800(size=256) memory:febfc000-febfffff
```

Output of **dmesg | grep wlan0**
```
3.964388] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```


The computer is Shuttle XS35GTV2. I ensured that in the BIOS setting the "Wireless Power Control" is set to "Disabled" (so that BIOS does not turn off wireless card off). I even tried to reinstall the drivers from RealTek website, to no avail (nothing changes).

Any troubleshooting ideas are much appreciated!

---

### Post by ahallubuntu on 2012-11-11
Yes, there are unfortunately issues with the rtl8192xx driver built into the 12.04 and 12.10 kernels.  Your card is currently using the rtl8192se driver.  You can download a newer version of this driver from Realtek's website and try building it for yourself.  Others here have tried with mixed results.  


[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

Through ("Communications Network ICs" - "Wireless LAN ICs" - "WLAN NIC" - "IEEE 802.11b/g/n Single-Chip", "Software,") check the box next to "RTL8192SE," click "Go," and download the Linux/Unix driver from there. I chose the "HK1" link to get the above. Make sure the page says "8192se" at the top before downloading.

I have built the 8192CU driver successfully from Realtek's site but I don't have a card to try building the 8192SE driver on.  There are other threads here about building for that card.

---

### Post by bbukh on 2012-11-11
> **ahallubuntu said:**
>  You can download a newer version of this driver from Realtek's website and try building it for yourself.  

I have done that. The data I posted in the original post was after I have done it. I followed "readme" in the download file, and I did not get any error message during the compilation and installation.

---

### Post by bbukh on 2012-11-17
I gave up, and bought a 50ft Ethernet cable.

---

### Post by gratefulfrog on 2012-12-18
I'm facing the same problem, b ut don't want to go the 50m cable route...  Anyone have any solutions?

All help would be great?

I am prepared to try to build the driver, but I wonder if it is not already included in the 3.2 kernel?

Thanks,
Bob

---

