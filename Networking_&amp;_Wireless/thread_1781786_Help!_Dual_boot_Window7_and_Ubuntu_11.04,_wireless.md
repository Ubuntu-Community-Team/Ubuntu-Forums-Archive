---
title: "Help! Dual boot Window7 and Ubuntu 11.04, wireless problem"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by thustam on 2011-06-14
Hi, 
I just installed Ubuntu 11.04 on my lenovo U330 last Friday. I'm new to this operating system and having a hard time trying to get it connect to wireless internet. 
The wireless works fine when I boot up Window7, but doesn't work with the Ubuntu. I've tried following steps from a few threads/blogs, but I just cannot get mine to work.

This is what I have:

tam@TamLenovo:~$ sudo lshw -c network
[sudo] password for tam: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:0c:90:a8
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 firmware=sb v3.04 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:95200000-9520ffff
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:d8:f4:a6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:48 memory:94100000-94101fff


tam@TamLenovo:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
06:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
06:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
06:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
06:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)


tam@TamLenovo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by chili555 on 2011-06-14
Please run and post:```
rfkill list all
lsmod
```Since your wireless is disabled, I suspect that the little driver module that translates key presses into usable kernel commands is faulty. I suspect the key combination that controls wireless is not being recognized. I am open to being disproved.

---

### Post by thustam on 2011-06-14
tam@TamLenovo:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes


tam@TamLenovo:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
joydev                 17322  0 
binfmt_misc            13213  1 
arc4                   12473  2 
snd_hda_codec_hdmi     27479  1 
radeon                896428  3 
iwlagn                284569  0 
snd_hda_codec_realtek   255820  1 
snd_usb_audio          91410  1 
snd_usbmidi_lib        24388  1 snd_usb_audio
iwlcore               148965  1 iwlagn
snd_seq_midi           13132  0 
mac80211              257001  2 iwlagn,iwlcore
uvcvideo               66851  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  2 snd_usb_audio,snd_hda_codec
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
r852                   17878  0 
snd_seq_midi_event     14475  1 snd_seq_midi
acer_wmi               23123  0 
videodev               75143  1 uvcvideo
drm                   180037  5 radeon,ttm,drm_kms_helper
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                80244  4 snd_hda_codec_hdmi,snd_usb_audio,snd_hda_intel,snd_hda_codec
psmouse                73312  0 
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
cfg80211              156212  3 iwlagn,iwlcore,mac80211
mtd                    26720  2 sm_common,nand
serio_raw              12990  0 
i2c_algo_bit           13184  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ideapad_laptop         13262  0 
sparse_keymap          13666  2 acer_wmi,ideapad_laptop
video                  18951  0 
snd                    55295  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_usb_audio,snd_usbmidi_lib,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_seq,snd_pcm,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
ahci                   21591  2 
sdhci                  22720  1 sdhci_pci
tg3                   131476  0 
crc_itu_t              12627  1 firewire_core
libahci                25548  1 ahci
tam@TamLenovo:~$

---

### Post by thustam on 2011-06-14
You have any clue what's wrong with my wireless? Sorry to get back with you so late, I didn't have this laptop with me during the day.

---

### Post by chili555 on 2011-06-14
Let's try a temporary experiment. Please do:```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```Now is your wireless working? If so, we can tweak a couple of files and make it permanent.

---

### Post by thustam on 2011-06-14
Am I suppose to get some output? I typed those 2 codes in but nothing happen.

---

### Post by chili555 on 2011-06-14
Now try:```
rfkill list all
```Is blocked = yes now changed to no? Can you now click the Network Manager icon and connect?

---

### Post by thustam on 2011-06-14
tam@TamLenovo:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by thustam on 2011-06-14
I clicked on the network manager. The wireless networks is still in grey.

---

### Post by chili555 on 2011-06-14
> phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]Are you quite sure there is no hardware switch that's moved over to 'Off?' Swear on a stack of Programmer's Bibles??

This could be a bit challenging; it's a known bug:[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/774036](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/774036)> A little more investigation proofed that, alas, this does not solve the problem on the ***Ideapad*** S12, so this bug is mostly invalid.

Still, the acer-wmi module overrides the blockstate after a manual "rfkill" command with the state it expects from the Fn+F5/F6 keyboard combos. I dont think it should do that (rfkill requires root-priviledges after all). Updated title accordingly.


---

### Post by thustam on 2011-06-14
yes it's on. Swear on a stack of Programmer's Bibles (which I don't have) lol. Windows7 connect to the wireless just fine

---

### Post by chili555 on 2011-06-14
I have to take 126 aspirin and get some sleep. Let's both Google ideapad acer-wmi and reconvene tomorrow.

---

### Post by thustam on 2011-06-14
Sorry :( ... Thanks for sticking with me thru this.

---

### Post by thustam on 2011-06-15
So I tried toggle that wireless switch 2-3 times....  and I think I broke it or something like that. Now Window7 cannot go on internet anymore. I'll see what I can do with this laptop. I just made the problem worse.

---

### Post by chili555 on 2011-06-15
> **thustam said:**
> So I tried toggle that wireless switch 2-3 times....  and I think I broke it or something like that. Now Window7 cannot go on internet anymore. I'll see what I can do with this laptop. I just made the problem worse.Post back if I can help you further. I'm subscribed so I'll get an email if you post. Sorry about what sounds like a mechanical problem.

---

