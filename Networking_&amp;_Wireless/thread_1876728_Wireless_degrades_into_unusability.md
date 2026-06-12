---
title: "Wireless degrades into unusability"
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by jmknsd on 2011-11-06
Howdy,

I have a Lenovo T420, with a realtek wireless adapter(RTL8188CE 802.11b/g/n WiFi Adapter) and the wireless works great for about 3 minutes, gets slow, and eventually it can't maintain a connection.

My google searches have led similar problems with no answers that have worked.

I'm running 11.10, and am using the rtl8195 driver. I'm going to try  building the driver from realtek, but I think it is the same driver, and it probably won't work.

Thanks for any help,
    Jeremy

---

### Post by maddog39 on 2011-11-06
For what its worth, I've had very similar problems with Ubuntu (and other distros) in the past using a Broadcom chipset. After much research it turned out to be most likely related to a change in the kernel which caused a regression with certain drivers/firmware and was never resolved as far as I know. I gave up trying to fix it and bought a USB-type wireless adapter with a better supported chipset and that was the end of it.

---

### Post by jmknsd on 2011-11-07
Still haven't gotten it working, do you have a recommended brand of usb wifi adapter that will work well?

---

### Post by maddog39 on 2011-11-07
The particular USB wireless adapter which I used was based on the ZyDAS ZD1211 802.11b/g USB WLAN chipset and used the zd1211rw driver. However, your mileage may vary. Also, finding adapters with compatible chipsets is quite challenging so a lot of research is necessary.

[http://linux-wless.passys.nl/](http://linux-wless.passys.nl/)
[http://www.linuxquestions.org/hcl/index.php?cat=10](http://www.linuxquestions.org/hcl/index.php?cat=10)

Those are some good references for wireless adapter compatability. Good luck!

---

### Post by joshron on 2011-11-20
I'm having the same problem with 11.10 on a T420. When I connect initially, speeds are what I see on other computers on the network (around 6 mb/s). After a bit of browsing the speed drops to ~0.4 mb/s.


Here's what I've got:
```

joshron@joshron-ThinkPad-T420:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation QM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
0d:00.0 System peripheral: Ricoh Co Ltd Device e823 (rev 05)
0d:00.3 FireWire (IEEE 1394): Ricoh Co Ltd FireWire Host Controller (rev 04)

```here's what I get with iwconfig: 

```

joshron@joshron-ThinkPad-T420:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"aquanet2"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 40:4A:03:E0:16:D2   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2085   Missed beacon:0

```and here is the result for lsmod:

```

joshron@joshron-ThinkPad-T420:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
joydev                 17393  0 
binfmt_misc            17292  1 
arc4                   12473  2 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
rtl8192ce             127398  0 
rtlwifi               102641  1 rtl8192ce
thinkpad_acpi          73942  0 
nvram                  14029  1 thinkpad_acpi
wmi                    18744  0 
tpm_tis                14002  0 
snd                    55902  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
mac80211              272785  2 rtl8192ce,rtlwifi
i915                  505108  3 
psmouse                73673  0 
serio_raw              12990  0 
cfg80211              172392  2 rtlwifi,mac80211
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
mei                    36466  0 
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
ahci                   21634  2 
libahci                25727  1 ahci
e1000e                139775  0 

```Thanks for any help anyone can give. I downloaded the Realtek RTL8192CE driver, and ran make and make install without error, with no change in symptoms. I've also swapped out the router to no avail.

-josh

---

### Post by TheSluiceGate on 2011-11-21
Have a read of my thread - skip the first long post, to where you will see how and why to switch off power management of your wireless card....

[http://ubuntuforums.org/showthread.php?t=1881969](http://ubuntuforums.org/showthread.php?t=1881969)

It's worth a try.

---

### Post by joshron on 2011-11-21
I had already switched power management off during the course of trying to figure this out. Thanks for the suggestion, though. 

```

wlan0     IEEE 802.11bgn  ESSID:"aquanet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:6A:7F:29   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:272   Missed beacon:0

```I've also unsuccessfully tried to figure out how to disable 802.11n, but then realized my router doesn't broadcast 802.11n, so I think that means 802.11n isn't the source of my problem?

Thanks for any help anyone can offer.

-josh

---

### Post by joshron on 2011-11-21
I've noticed the "invalid misc" count in iwconfig increases rapidly, is it possible this is the source of my problems?

```

joshron@joshron-ThinkPad-T420:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"aquanet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:6A:7F:29   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:6300   Missed beacon:0

```I disconnected from the network and reconnected maybe 5 minutes ago.

-josh

---

### Post by joshron on 2011-11-22
My problem seems to be solved. Per advice I received on launchpad at this thread:

([https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/179591/+index](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/179591/+index)) 

I ran this code:

```

echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf . /dev/null

```When I ran the code it gave me what appeared to be an error message, but it still may have worked? I have been browsing for about 30 minutes without the connection getting slow, it used to happen in one or two minutes of browsing.

```

joshron@joshron-ThinkPad-T420:~$ echo "nameserver 8.8.8.8" | sudo tee /etc/resolv.conf . /dev/null
[sudo] password for joshron:
tee: .: Is a directory
nameserver 8.8.8.8
joshron@joshron-ThinkPad-T420:~$

```Last night I tried changing the DNS server through network manager to google's 8.8.8.8 last night without any success, maybe I was doing it wrong? 

Here is the info I was using to change the DNS:
[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

I hope one of these works for you, OP

-josh

---

