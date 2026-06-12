---
title: "Bluetooth Not Working"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by mahawksid on 2012-02-20
Hello friends,
  I have Ubuntu 11.10, Windows 7 and Kubuntu 11.10; all on separate partitions; installed on a HP-g6-1219tu laptop. Mine has Broadcom BCM4313 wireless adapter on it. I have installed Broadcom STA wireless driver installed on it. I had to blacklist bcma and bcmsmac modules in order to get my WiFi working.
  But i have no clue on how to get my Bluetooth adapter running. Please guide me someone.
  Here are the outputs of some of the commands you might find useful:
lspci:
```
lspci:

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)

```
lsmod:
```
lsmod:

Module                  Size  Used by
nls_iso8859_1          12713  0 
nls_cp437              16991  0 
vfat                   17585  0 
fat                    61475  1 vfat
michael_mic            12612  0 
arc4                   12529  0 
ppp_deflate            13038  0 
zlib_deflate           27139  1 ppp_deflate
bsd_comp               12994  0 
ppp_async              17539  1 
crc_ccitt              12667  1 ppp_async
option                 25849  1 
usb_wwan               20491  1 option
usbserial              47107  5 option,usb_wwan
cdc_ether              13536  0 
usbnet                 26212  1 cdc_ether
usb_storage            57901  0 
uas                    18027  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
lib80211_crypt_tkip    17390  0 
wl                   2573568  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
joydev                 17693  0 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_intel          33390  4 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
psmouse                73882  0 
serio_raw              13166  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  17 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rts_pstor             445246  0 
lib80211               14991  2 lib80211_crypt_tkip,wl
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i915                  571221  3 
drm_kms_helper         42558  1 i915
wmi                    19256  1 hp_wmi
mei                    41480  0 
drm                   236290  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  5 
libahci                26861  1 ahci
r8169                  52788  0 

```

rfkill list:
```

rfkill list:
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
sudo /etc/init.d/bluetooth status:
```

sudo /etc/init.d/bluetooth status:

 * bluetooth is running

```
Please friends help me here. I have many Bluetooth devices that are totally wasted to me now cause my Linux is not detecting them. Any help is sincerely welcomed.
If you guys want more information pleas tell, i will reply with the asked asap.
Thanks You

---

### Post by Aseel on 2012-03-03
Did you find a solution this problem, because i have the same exact thing ?

---

