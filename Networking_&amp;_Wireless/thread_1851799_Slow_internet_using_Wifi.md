---
title: "Slow internet using Wifi"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by parth.s on 2011-09-29
Im using Natty on an Asus laptop with Realtek wireless card. Its been just a couple of weeks since I have started using Natty (and bought this laptop). I have dual booted my laptop with Win7.

Internet connectivity seems to be miserable with Natty. There has been more than one instances of, pages taking a lot of time to load, pages giving session timeout message. Although the wireless connection is established all the time. At the same time switching to win7 gives me uninterrupted connectivity.

Please help.:confused:

---

### Post by parth.s on 2011-09-29
Just keeping the post active...

---

### Post by linuxman94 on 2011-09-29
For future reference, please wait at least 24 hours before bumping your thread.

Can you post the output of these commands?  Run them in the terminal (search in the dash)

```
iwconfig
lspci
lsmod
```

---

### Post by dave01945 on 2011-09-29
what wireless card are you using it might help to get a better idea of whats happening just type in terminal

```
lshw -C network
```

and post the output, also do you know if you are using DHCP or a static ip

---

### Post by parth.s on 2011-09-29
> **linuxman94 said:**
> For future reference, please wait at least 24 hours before bumping your thread.

Can you post the output of these commands?  Run them in the terminal (search in the dash)

```
iwconfig
lspci
lsmod
```

parth@parth-K53E:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"DragonAge"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: E0:46:9A:50:28:C2   
          Bit Rate=45 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:75   Missed beacon:0
-----------------------------------
parth@parth-K53E:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
03:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)
------------------------------------
parth@parth-K53E:~$ lsmod
Module                  Size  Used by
cryptd                 19801  0 
aes_i586               16956  2 
aes_generic            38023  1 aes_i586
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24113  2 
arc4                   12473  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  451033  3 
rtl8192ce             120858  0 
rtlwifi                78961  1 rtl8192ce
mac80211              257001  2 rtl8192ce,rtlwifi
snd_seq_midi           13132  0 
uvcvideo               66851  0 
drm_kms_helper         40745  1 i915
snd_rawmidi            25269  1 snd_seq_midi
drm                   184164  4 i915,drm_kms_helper
sparse_keymap          13666  0 
videodev               75143  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              156212  2 rtlwifi,mac80211
i2c_algo_bit           13184  1 i915
psmouse                73312  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
serio_raw              12990  0 
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  1 
atl1c                  36237  0 
libahci                25548  1 ahci

---

### Post by parth.s on 2011-09-29
> **dave01945 said:**
> what wireless card are you using it might help to get a better idea of whats happening just type in terminal

```
lshw -C network
```and post the output, also do you know if you are using DHCP or a static ip

parth@parth-K53E:~$ sudo lshw -C network
*-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: e0:b9:a5:35:53:de
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=2.6.38-11-generic firmware=N/A ip=192.168.1.42 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:c000(size=256) memory:dea00000-dea03fff
  *-network
       description: Ethernet interface
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: f4:6d:04:50:de:7f
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:de000000-de03ffff ioport:b000(size=128)



I am using DHCP

---

### Post by parth.s on 2011-09-29
Also I dont think this would be a problem but, my router is not broadcasting the SSID...

---

### Post by collisionystm on 2011-09-29
It's probably a power management issue. I would investigate disabling power saving on your wifi card

---

### Post by wildmanne39 on 2011-09-29
Hi, I do not see anything wrong with what you posted and that card and driver usually works pretty well.

I am having the issue you described right now also but it is firefox not working right, have you tried another broswer?
Thank you

---

### Post by linuxman94 on 2011-09-29
> **collisionystm said:**
> It's probably a power management issue. I would investigate disabling power saving on your wifi card

Shouldn't be a power saving issue:

```
Power Management: off
```

OP: I'm thinking you're going to need to install the realtek driver.  Most realtek cards have poor performance with the default kernel driver.  For example, my realtek RTL8168B (ethernet card) had poor performance and connection issues prior to installing the official driver.

I'll post instructions tomorrow, as the installation is rather long, yet easy process.

---

### Post by wildmanne39 on 2011-09-29
Hi, you could also post the results of these commands and they might tell us something.
```
sudo cat /var/log/syslog | grep etwork | tail -n25
```
```
cat /etc/lsb-release; uname -a
```
```
nm-tool
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
iwlist chan
```
```
dmesg | egrep 'rtl|firm|wlan0'
```
```
lsmod | grep rtl
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by parth.s on 2011-09-29
> **wildmanne39 said:**
> Hi, I do not see anything wrong with what you posted and that card and driver usually works pretty well.

I am having the issue you described right now also but it is firefox not working right, have you tried another broswer?
Thank you

Thanks, I ought to have tried that before posting...but im gonna try chrome and see if there is any change...

---

### Post by parth.s on 2011-09-29
> **linuxman94 said:**
> Shouldn't be a power saving issue:

```
Power Management: off
```OP: I'm thinking you're going to need to install the realtek driver.  Most realtek cards have poor performance with the default kernel driver.  For example, my realtek RTL8168B (ethernet card) had poor performance and connection issues prior to installing the official driver.

I'll post instructions tomorrow, as the installation is rather long, yet easy process.


Thanks! do post the instructions...I can wait that much..

---

### Post by parth.s on 2011-09-30
> **parth.s said:**
> Thanks, I ought to have tried that before posting...but im gonna try chrome and see if there is any change...

The problem still persists...chrome randomly takes time to load pages...also when i try to update apt-get it is unable to connect to the server at that instant. 
Again this is completely random and very annoying

---

### Post by linuxman94 on 2011-09-30
Alrighty lets get this thing working.  It's not as long as i previously thought it was.

Step 1: Download the driver at this link: [RTL**92CE Driver]("http://dl.dropbox.com/u/7800678/92ce_se_de_linux_mac80211_0004.0816.2011.tar.gz")

Step 2: Extract the contents into your home directory using archive manager.

3: Time to install.  Fire up a terminal and change to the driver directory:

```
cd rtl92ce
```

Next, you need to install build-essential (may be already installed) so that you can compile the driver.  If you can do it with apt-get, great.  If not, let me know your architecture (32bit or 64bit) and I'll get the appropriate packages for you.

```
sudo apt-get install build-essential
```

Now that you have build-essential installed, run these two commands and reboot.

```
make
sudo make install
```

If any errors occur, post the output here for us to look at.

Verify that the wireless works correctly after reboot.  if it does, you're all set!

---

### Post by parth.s on 2011-10-01
thanks linuxman94 and wildmanne39 for your quick responses. I am not facing that problem anymore.

What i dont understand is that i was using the same driver before...did re-installing the driver make the difference?
=D>

---

### Post by wildmanne39 on 2011-10-01
Hi, I believe it is because the driver you installed from the out side source is a newer and improved driver.
Thank you

---

