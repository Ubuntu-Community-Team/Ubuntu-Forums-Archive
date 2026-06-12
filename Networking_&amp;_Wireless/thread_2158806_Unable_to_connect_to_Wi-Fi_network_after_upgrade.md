---
title: "Unable to connect to Wi-Fi network after upgrade"
date: 2013-06-30
forum: Networking &amp; Wireless
---

### Post by Stretchkev1 on 2013-06-30
Hi,

I recently did a clean install, after rebooting I can't connect to my Wi-Fi network. My network pops up no problem, but after entering my password Mint thinks for a minute or two, but it fails to connect every time. t this point I don't know how to diagnosis the issue without being able to connect to the network. Any help would be appreciated.

Machine: ASUS U56E

Some More info:

```
**lsmod**
Module Size Used by
nls_iso8859_1 12713 0 
usb_storage 57204 0 
parport_pc 28152 0 
ppdev 17073 0 
bnep 18036 2 
rfcomm 42641 0 
bluetooth 228619 10 bnep,rfcomm
binfmt_misc 17500 1 
uvcvideo 80847 0 
i2400m_usb 36375 0 
i2400m 107578 1 i2400m_usb
videobuf2_vmalloc 13056 1 uvcvideo
videobuf2_memops 13202 1 videobuf2_vmalloc
videobuf2_core 40513 1 uvcvideo
wimax 34760 1 i2400m
videodev 129260 2 uvcvideo,videobuf2_core
joydev 17377 0 
snd_hda_codec_hdmi 36913 1 
snd_hda_codec_realtek 78399 1 
arc4 12615 2 
snd_hda_intel 39619 3 
snd_hda_codec 136453 3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
iwldvm 241834 0 
snd_hwdep 13602 1 snd_hda_codec
snd_pcm 97451 3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc 18710 2 snd_pcm,snd_hda_intel
coretemp 13355 0 
mac80211 606457 1 iwldvm
kvm_intel 132891 0 
snd_seq_midi 13324 0 
kvm 443165 1 kvm_intel
snd_seq_midi_event 14899 1 snd_seq_midi
ghash_clmulni_intel 13259 0 
aesni_intel 55399 0 
snd_rawmidi 30180 1 snd_seq_midi
aes_x86_64 17255 1 aesni_intel
xts 12885 1 aesni_intel
lrw 13257 1 aesni_intel
gf128mul 14951 2 lrw,xts
ablk_helper 13597 1 aesni_intel
cryptd 20373 3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq 61554 2 snd_seq_midi_event,snd_seq_midi
snd_seq_device 14497 3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer 29425 2 snd_pcm,snd_seq
snd 68876 16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
iwlwifi 173477 1 iwldvm
asus_nb_wmi 12854 0 
asus_wmi 24213 1 asus_nb_wmi
sparse_keymap 13890 1 asus_wmi
cfg80211 510937 3 iwlwifi,mac80211,iwldvm
mac_hid 13205 0 
mei 41158 0 
soundcore 12680 1 snd
psmouse 95870 0 
lpc_ich 17061 0 
microcode 22881 0 
lp 17759 0 
serio_raw 13215 0 
parport 46345 3 lp,ppdev,parport_pc
dm_multipath 22843 0 
scsi_dh 14843 1 dm_multipath
btrfs 785967 0 
zlib_deflate 26885 1 btrfs
libcrc32c 12615 1 btrfs
dm_raid45 76725 0 
xor 17116 1 dm_raid45
dm_mirror 21946 0 
dm_region_hash 20820 1 dm_mirror
dm_log 18529 3 dm_region_hash,dm_mirror,dm_raid45
hid_generic 12540 0 
usbhid 47074 0 
hid 101002 2 hid_generic,usbhid
atl1c 41071 0 
i915 600351 3 
ahci 25731 2 
libahci 31364 1 ahci
wmi 19070 1 asus_wmi
video 19390 2 i915,asus_wmi
i2c_algo_bit 13413 1 i915
drm_kms_helper 49394 1 i915
drm 286313 4 i915,drm_kms_helper
```

```
**lspci -vnn**
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
Subsystem: ASUSTeK Computer Inc. Device [1043:1157]
Flags: bus master, fast devsel, latency 0
Capabilities: <access denied>

00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09) (prog-if 00 [VGA controller])
Subsystem: ASUSTeK Computer Inc. Device [1043:1582]
Flags: bus master, fast devsel, latency 0, IRQ 50
Memory at dd000000 (64-bit, non-prefetchable) [size=4M]
Memory at c0000000 (64-bit, prefetchable) [size=256M]
I/O ports at e000 [size=64]
Expansion ROM at <unassigned> [disabled]
Capabilities: <access denied>
Kernel driver in use: i915

00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
Subsystem: ASUSTeK Computer Inc. Device [1043:1157]
Flags: bus master, fast devsel, latency 0, IRQ 51
Memory at dfc0b000 (64-bit, non-prefetchable) [size=16]
Capabilities: <access denied>
Kernel driver in use: mei

00:1a.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 [8086:1c2d] (rev 05) (prog-if 20 [EHCI])
Subsystem: ASUSTeK Computer Inc. Device [1043:1157]
Flags: bus master, medium devsel, latency 0, IRQ 16
Memory at dfc08000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
Kernel driver in use: ehci-pci

00:1b.0 Audio device [0403]: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)
Subsystem: ASUSTeK Computer Inc. Device [1043:1bd3]
Flags: bus master, fast devsel, latency 0, IRQ 53
Memory at dfc00000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 [8086:1c10] (rev b5) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
I/O behind bridge: 0000d000-0000dfff
Memory behind bridge: df200000-dfbfffff
Prefetchable memory behind bridge: 00000000d2100000-00000000d2afffff
Capabilities: <access denied>
Kernel driver in use: pcieport

00:1c.1 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 [8086:1c12] (rev b5) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
I/O behind bridge: 0000c000-0000cfff
Memory behind bridge: de800000-df1fffff
Prefetchable memory behind bridge: 00000000d1600000-00000000d1ffffff
Capabilities: <access denied>
Kernel driver in use: pcieport

00:1c.3 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 [8086:1c16] (rev b5) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
I/O behind bridge: 0000b000-0000bfff
Memory behind bridge: dde00000-de7fffff
Prefetchable memory behind bridge: 00000000d0b00000-00000000d14fffff
Capabilities: <access denied>
Kernel driver in use: pcieport

00:1c.5 PCI bridge [0604]: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 [8086:1c1a] (rev b5) (prog-if 00 [Normal decode])
Flags: bus master, fast devsel, latency 0
Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
I/O behind bridge: 0000a000-0000afff
Memory behind bridge: dd400000-dddfffff
Prefetchable memory behind bridge: 00000000d0000000-00000000d09fffff
Capabilities: <access denied>
Kernel driver in use: pcieport

00:1d.0 USB controller [0c03]: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 [8086:1c26] (rev 05) (prog-if 20 [EHCI])
Subsystem: ASUSTeK Computer Inc. Device [1043:1157]
Flags: bus master, medium devsel, latency 0, IRQ 23
Memory at dfc07000 (32-bit, non-prefetchable) [size=1K]
Capabilities: <access denied>
Kernel driver in use: ehci-pci

00:1f.0 ISA bridge [0601]: Intel Corporation HM65 Express Chipset Family LPC Controller [8086:1c49] (rev 05)
Subsystem: ASUSTeK Computer Inc. Device [1043:1157]
Flags: bus master, medium devsel, latency 0
Capabilities: <access denied>
Kernel driver in use: lpc_ich

00:1f.2 SATA controller [0106]: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller [8086:1c03] (rev 05) (prog-if 01 [AHCI 1.0])
Subsystem: ASUSTeK Computer Inc. Device [1043:1157]
Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 49
I/O ports at e0b0 [size=8]
I/O ports at e0a0 [size=4]
I/O ports at e090 [size=8]
I/O ports at e080 [size=4]
I/O ports at e060 [size=32]
Memory at dfc06000 (32-bit, non-prefetchable) [size=2K]
Capabilities: <access denied>
Kernel driver in use: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller [8086:1c22] (rev 05)
Subsystem: ASUSTeK Computer Inc. Device [1043:1157]
Flags: medium devsel, IRQ 3
Memory at dfc05000 (64-bit, non-prefetchable) [size=256]
I/O ports at e040 [size=32]

02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1305]
Flags: bus master, fast devsel, latency 0, IRQ 52
Memory at de800000 (64-bit, non-prefetchable) [size=8K]
Capabilities: <access denied>
Kernel driver in use: iwlwifi

03:00.0 USB controller [0c03]: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller [1b21:1042] (prog-if 30 [XHCI])
Subsystem: ASUSTeK Computer Inc. Device [1043:1059]
Flags: bus master, fast devsel, latency 0, IRQ 19
Memory at dde00000 (64-bit, non-prefetchable) [size=32K]
Capabilities: <access denied>
Kernel driver in use: xhci_hcd

04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
Flags: bus master, fast devsel, latency 0, IRQ 54
Memory at dd400000 (64-bit, non-prefetchable) [size=256K]
I/O ports at a000 [size=128]
Capabilities: <access denied>
Kernel driver in use: atl1c
```

---

### Post by wildmanne39 on 2013-06-30
Hi, please try:
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
I am on my way out the door, be back later.
Thanks

---

### Post by Stretchkev1 on 2013-06-30
It gives me a fatal when I try the 1st modprobe:

```
stretch@stretch ~ $ echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
[sudo]password for stretch: 
options iwlwifi 11n_disable=1
stretch@stretch ~ $ sudo modprobe -rfv iwlwifi
FATAL: Module iwlwifi is in use.
stretch@stretch ~ $ sudo modprobe -v iwlwifi

```

Thanks!

---

### Post by wildmanne39 on 2013-06-30
Hi, please try it like this:
```
sudo ifconfig wlan0 down
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Thanks

---

### Post by Stretchkev1 on 2013-07-01
Still getting the Fatal\

```
stretch@stretch ~ $ sudo ifconfig wlan0 down[sudo] password for stretch: 
stretch@stretch ~ $ echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
options iwlwifi 11n_disable=1
stretch@stretch ~ $ sudo modprobe -rfv iwlwifi
FATAL: Module iwlwifi is in use.
stretch@stretch ~ $ sudo modprobe -v iwlwifi
```

---

### Post by ajgreeny on 2013-07-01
Have you disabled wifi before attempting all this?  I also wonder if it might be easier to simply use gedit or other text editor to create the **/etc/modprobe.d/iwlwifi.conf** and maybe also try something different to disabling the 11n wifi speed.

I accept it is a different adapter card but nevertheless I have had to disable hardware encryption in my card to get it to work properly, with a similar, but in my case, /etc/modprobe.d/**ath9k**.conf file containing ```
options ath9k nohwcrypt=1
``` then restarting networking.

If it does not help you can easily remove the new file to get back to where you started from.

---

### Post by wildmanne39 on 2013-07-01
Hi, you must be using 13.04 in this version this was also added iwldvm that needs to be removed. 
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -r iwldvm
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

Your driver does not have the parameter mentioned in the previous post so doing that will not help you.
Thanks

---

### Post by Stretchkev1 on 2013-07-01
After that last set, it won't detect any wireless network.

Sorry I forgot to state in the orginal post it is 13.04.02

---

### Post by wildmanne39 on 2013-07-01
Pleasde try:
```
sudo modprobe -r iwldvm
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwldvm
sudo modprobe -v iwlwifi
```
Thanks

---

### Post by Stretchkev1 on 2013-07-01
There back but it keeps asking for authentication now and not connecting.  Thanks for all the help Wild Man by the way.

---

### Post by wildmanne39 on 2013-07-01
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named wireless-info.tar.gz in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by wildmanne39 on 2013-07-01
Also please post the contents of:
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
Thanks

---

### Post by Stretchkev1 on 2013-07-01
Contents of gksudo gedit /etc/modprobe.d/iwlwifi.c't allow me toonf:

```
options iwlwifi 11n_disable=1
```

---

### Post by wildmanne39 on 2013-07-02
Hi, please do:
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
add
```
swcrypto=1
```
like this
```
options iwlwifi 11n_disable=1 swcrypto=1
```
Then save and close gedit.

Also if you can ubuntu wireless will work best with wpa2 AES only encryption.

Set the channel to 1 or 11.
Reboot
Thanks

---

### Post by Stretchkev1 on 2013-07-02
That hasn't worked either.

---

### Post by wildmanne39 on 2013-07-02
Hi, did you also do:
> Also if you can ubuntu wireless will work best with wpa2 AES only encryption.

Set the channel to 1 or 11.
Thanks

---

### Post by wildmanne39 on 2013-07-02
Hi, you have some error messages and my research shows to add wd_disable=1
to 
```
options iwlwifi 11n_disable=1 swcrypto=1
```
like this:
```
options iwlwifi 11n_disable=1 swcrypto=1 wd_disable=1
```
by running this command to open the file then add wd_disable=1:
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
then save and close gedit and reboot.
Thanks

---

### Post by Stretchkev1 on 2013-07-02
Even after the modification to that file still won't connect to either channel 1 or 11.

---

### Post by wildmanne39 on 2013-07-03
Okay before we go further please set your wireless settings in network manager to match the screenshots.
Thanks

---

### Post by Stretchkev1 on 2013-07-03
Okay.

IPv6 is set to ignore

and IPv4 DNS Servers is set yo 8.8.8.8, 8.8.4.4

With WPA2 AES security and on channel 11

---

### Post by wildmanne39 on 2013-07-03
Still will not connect?

---

### Post by Stretchkev1 on 2013-07-03
nope.

---

### Post by wildmanne39 on 2013-07-03
I am installing 13.04 so I can check some things, I will get back to you after I have it installed.
Thanks

---

### Post by wildmanne39 on 2013-07-04
We are going to remove the last parameter we added and add another one.

Please do:
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```
remove wd_disable=1 and add bt_coex_active=N
save and close gedit and reboot.

Please post everything that is in that file.
Thanks

---

### Post by SeijiSensei on 2013-07-04
Can you tell us  the kernel version you are using?  Run "uname -r" and report back the results.

My Intel adaptor refused to connect with [one recent kernel version]("http://ubuntuforums.org/showthread.php?t=2143218"), but came back to life in the next one.  I'm now on 3.8.0-23-generic, and the card connects with WPA2.

---

### Post by Stretchkev1 on 2013-07-04
The Kernel its running is 3.8.0-25-generic. I get nervous about go back to older versions of Kernels, forced clean installs in the past.

That last file change did it Wild Man, I'm now totally unwired. Thanks so much for the help! I'm glad that you where able to find a solution. Sorry for any trouble it may have caused, I'm somewhat computer illerate when comes to the hardware interfacing bits.

---

### Post by wildmanne39 on 2013-07-04
That is great I am glad it is working!!!
Enjoy.

---

### Post by wildmanne39 on 2013-07-04
Hi, would you mind posting the wireless script information and the complete contents of the file we have been working on, it will help with our learning experience and make it easier to help people in the future.
Thanks

---

### Post by SeijiSensei on 2013-07-04
Just as an added data point, I just upgraded from 3.8.0-23 to 3.8.0-25 tonight.  My wireless continues to work without incident using Kubuntu's network manager and no additional shell commands.

---

### Post by Stretchkev1 on 2013-07-09
Sorry was away for the weekend

Attached is the new/functioning wireless script and what the modifications to [COLOR=#000000][FONT=Ubuntu Mono]gksudo gedit /etc/modprobe.d/iwlwifi.conf look like:[/FONT][/COLOR]

```
options iwlwifi 11n_disable=1 swcrypto=1 bt_coex_active=N
```

---

### Post by wildmanne39 on 2013-07-09
Thank you!

---

