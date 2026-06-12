---
title: "ThinkPad x120e won't Auto Connect"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by RMOP on 2011-09-21
ThinkPad x120e
Ubuntu 64-bit 11.04 Desktop
RealTek Wireless
Netgear Router w Hidden SSID & WPA

This install won't connect to my wireless automatically, though it is set to do so. I have to manually choose "Connect to Hidden Wireless Network" and then chose my (already defined) network from the drop-down menu. When I do, I'm prompted to enter my administrator PW. Afterwards, I have to manually select "Connect." Once connected, it's rock stable. But this manual intervention is required each and every time I boot. FWIW: I did an earlier install w v10.10 and had the exact same problem w WiFi. I've deleted and recreated the connection, but no success.

Ideas, please? Is this a driver problem, or what?

---

### Post by wildmanne39 on 2011-09-21
Hi, let's see if we can figure this out.

First a hidden network really is not much more secure then one not hidden, not sure that is the problem most of the time people can not connect to a hidden network at all when there is a problem.

I am thinking that the driver is not loading automatically, so we will try that first please post the results of these commands here:
```
lspci -nn | grep -e 0280 -e 0200
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by RMOP on 2011-09-21
> **wildmanne39 said:**
> Hi, let's see if we can figure this out.

First a hidden network really is not much more secure then one not hidden, not sure that is the problem most of the time people can not connect to a hidden network at all when there is a problem.

I am thinking that the driver is not loading automatically, so we will try that first please post the results of these commands here:

```
lspci -nn | grep -e 0280 -e 0200
```

$ lspci -nn | grep -e 0280 -e 0200
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

```
iwconfig
```

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"My-Hidden-SSID-Here"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:CA:63:11   
          Bit Rate=57.8 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:115   Missed beacon:0


```
rfkill list all
```~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

~$ rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
lsmod
```

~$ lsmod
Module                  Size  Used by
btrfs                 550402  0 
zlib_deflate           27074  1 btrfs
libcrc32c              12644  1 btrfs
ufs                    75815  0 
qnx4                   17685  0 
hfsplus                84797  0 
hfs                    54731  0 
minix                  36367  0 
ntfs                  101769  0 
vfat                   21708  0 
msdos                  17333  0 
fat                    61374  2 vfat,msdos
jfs                   182186  0 
xfs                   823190  0 
exportfs               12998  1 xfs
reiserfs              248223  0 
cryptd                 20510  0 
aes_x86_64             17208  1 
aes_generic            38279  1 aes_x86_64
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_conexant    57511  1 
snd_hda_codec_hdmi     28103  1 
binfmt_misc            17565  1 
snd_hda_intel          33211  2 
arc4                   12529  2 
snd_hda_codec         103804  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rtl8192ce             123008  0 
joydev                 17606  0 
radeon                982197  3 
rtlwifi                85089  1 rtl8192ce
rfcomm                 47694  8 
mac80211              294370  2 rtl8192ce,rtlwifi
sco                    18131  2 
bnep                   18308  2 
snd_seq_midi           13324  0 
l2cap                  53570  16 rfcomm,bnep
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ttm                    76664  1 radeon
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72195  0 
btusb                  18600  2 
videodev               82052  1 uvcvideo
drm_kms_helper         42136  1 radeon
thinkpad_acpi          81587  0 
snd_timer              29602  2 snd_pcm,snd_seq
k10temp                13119  0 
bluetooth              72448  9 rfcomm,sco,bnep,l2cap,btusb
cfg80211              178528  2 rtlwifi,mac80211
psmouse                73535  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    17078  1 videodev
drm                   227495  5 radeon,ttm,drm_kms_helper
nvram                  14419  1 thinkpad_acpi
serio_raw              13166  0 
snd                    67382  15 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,thinkpad_acpi
video                  19438  0 
sp5100_tco             13744  0 
i2c_piix4              13303  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13400  1 radeon
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  3 
libahci                26642  1 ahci
r8169                  48022  0 



Thanks for the reply. FWIW: The Wireless driver DOES appear to load, and sees neighboring networks. It just doesn't connect to mine unless I do the "Connect to Hidden" bit.

---

### Post by wildmanne39 on 2011-09-21
Hi, when you ran the ```
lsmod
```command was that before you clicked to connect to your hidden network or after? If after please restart your computer then run the command again before you click connect to your hidden network.
Thank you

---

### Post by RMOP on 2011-09-22
> **wildmanne39 said:**
> Hi, when you ran the ```
lsmod
```

~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
rfcomm                 47694  8 
sco                    18187  2 
snd_hda_codec_conexant    57511  1 
snd_hda_codec_hdmi     28167  1 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
radeon                982152  3 
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
thinkpad_acpi          81587  0 
snd_seq_midi           13324  0 
ttm                    76664  1 radeon
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
joydev                 17606  0 
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12529  2 
snd                    67382  15 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         42136  1 radeon
drm                   227534  5 radeon,ttm,drm_kms_helper
uvcvideo               72195  0 
rtl8192ce             122961  0 
videodev               82052  1 uvcvideo
rtlwifi                85089  1 rtl8192ce
v4l2_compat_ioctl32    17078  1 videodev
sp5100_tco             13744  0 
btusb                  18600  2 
i2c_algo_bit           13400  1 radeon
soundcore              12680  1 snd
mac80211              294370  2 rtl8192ce,rtlwifi
psmouse                73535  0 
serio_raw              13166  0 
nvram                  14419  1 thinkpad_acpi
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
k10temp                13119  0 
lp                     17825  0 
video                  19438  0 
cfg80211              178528  2 rtlwifi,mac80211
i2c_piix4              13303  0 
parport                46458  3 parport_pc,ppdev,lp
usb_storage            53538  0 
uas                    17996  0 
ahci                   25951  2 
libahci                26642  1 ahci
r8169                  48022  0




Here it is before making the connection manually. The first time was AFTER connecting. Before doing anything, I did get a popup advising that wireless networks were available.

---

### Post by wildmanne39 on 2011-09-22
Hi, we are going to troubleshoot this further, it still may end up being a hidden network issue.
```
dmesg | egrep 'rtl|firm|radio|switch|wlan0'
```
```
lsmod | grep rtl
```
Run these commands also when it will not connect so we can see the error messages.
Thank you

---

### Post by RMOP on 2011-09-23
> **wildmanne39 said:**
> Hi, we are going to troubleshoot this further, it still may end up being a hidden network issue.

```
dmesg | egrep 'rtl|firm|radio|switch|wlan0'
```

:~$ dmesg | egrep 'rtl|firm|radio|switch|wlan0'
[   15.141019] thinkpad_acpi: radio switch found; radios are enabled
[   15.141055] thinkpad_acpi: possible tablet mode switch found; ThinkPad in laptop mode
[   15.244528] rtl8192ce 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.244544] rtl8192ce 0000:04:00.0: setting latency timer to 64
[   15.281274] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   15.379257] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   15.847666] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.424961] Console: switching to colour frame buffer device 170x48
[   21.211424] IBM TrackPoint firmware: 0x0e, buttons: 3/3

```
lsmod | grep rtl
```

~$ lsmod | grep rtl
rtl8192ce             122961  0 
rtlwifi                85089  1 rtl8192ce
mac80211              294370  2 rtl8192ce,rtlwifi
cfg80211              178528  2 rtlwifi,mac80211


Run these commands also when it will not connect so we can see the error messages.
Thank you

I'm suspecting some sort of permissions issue, as I'm prompted to enter my PW the first time I select "Connect to Hidden Wireless Network." The requirement for manual input at that level strikes me as linked to the failure of the auto-connect. On the other hand, if I toggle my wireless adapter off/on AFTER having first made the connection manually, it does NOT automatically reconnect. But, when I later force a manual reconnect, it doesn't ask for a PW the second time.

---

### Post by wildmanne39 on 2011-09-23
Hi, I have found with google a lot of reports with thankpads with auto connect issues with hidden network's some has success by unhiding there network.

Some said it was an issue with using wpa enterprise encryption, most never found a solution, one said it just went away on its own, most were not helpful.

When you ran 
```
rfkill list all
```
was that when you were not connected?
Thank you

---

### Post by RMOP on 2011-09-24
Well...yes, the output from the command was when off-line. And, you were correct in thinking this might be a hidden SSID issue, but in a rather unexpected way.

I've solved the problem, and perhaps my stumbled-upon solution, if that's what it is, might be useful to someone else.

I created a NEW wireless connection. This time, instead of using the LOCATION (e.g., "Home") as the connection name, I used the SSID itself. With that simple change, all is working fine with the hidden SSID. It connects immediately and is solid.

Now, in case you're curious as to how I cam across this solution, here's the play-by-play account:

1) I edited my original "Home" connection by adding the router's MAC address to the field for that in the "Device MAC Address" field. I was hoping that might help Ubuntu to "see" the connection. It didn't.

2) My connection was rendered unavailable when I tried the "Connect to Hidden Wireless Network" option. I was offered on the option of entering the name of a NEW connection. I declined at first.

3) Instead, I edited the existing connection further and added the same router MAC to the "Cloned MAC Address" field, thinking, "why not?" as it wasn't working at all by now.

4) I still could not connect, either automatically or via the "Connect to Hidden Wireless" option.

5) In frustration, I went ahead and defined a new AP in the "Connect to Hidden Wireless" option drop-down for a new connection. This time, the router's SSID was used as the AP's name, as this particular menu doesn't allow you to use a location name in lieu of the SSID.

6) The newly-defined connection attached even before I clicked the "connect" button, and has automatically connected ever since. If I toggle WiFi off/on, the connection drops and reconnects smoothly. As it should.

7) I had earlier created a new wireless connection from the Edit Connections menu, but used another location-specific name instead of the SSID. It did NOT automatically connect, but required me to jump through the "Connect to Hidden Wireless Network" hoops.

Why adding the routers MAC address to my original connection rendered it totally incapable of connecting is opaque to me. But, had that not happened, I'm not at all sure when or if I'd have used the actual SSID as the name of the AP. I just tend not to do that, as my SSID's tend to be longer and less aesthetically pleasing than a location name. But, all's well that ends better...

Thanks again for your interest in my problem, which helped maintain my own long enough to fix it rather than give up. 

BTW: temporarily setting my SSID to broadcast DID cause the Automatic connection to work, but I wanted to make my system connect to a hidden SSID, if only for the sake of principle.

---

### Post by wildmanne39 on 2011-09-24
Hi, that is great I am glad you have it working thank you for sharing the solution.

---

