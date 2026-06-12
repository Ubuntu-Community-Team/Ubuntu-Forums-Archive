---
title: "Lenovo B570e Wireless Problem"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by RogerMoore on 2012-12-12
I have a Lenovo B570e with Ubuntu 12.10 installed alongside Windows 7. In Windows 7, wireless works without a hitch, however in Ubuntu there isn't even a wireless option in the network manager.

I have tried almost every suggestion I've seen in similar threads, but I haven't had any luck so far.

lspci -nnk | grep -iA2 net
```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:051b]
	Kernel modules: bcma
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Lenovo Device [17aa:3975]
	Kernel driver in use: r8169

```

lsusb
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID e0ff:0002  
Bus 001 Device 004: ID 0bda:58e4 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. Card reader

```

iwconfig
```
eth0      no wireless extensions.

lo        no wireless extensions.

```

rfkill list
```
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

lsmod
```
Module                  Size  Used by
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_realtek    77876  1 
rfcomm                 46619  0 
parport_pc             32688  0 
ppdev                  17073  0 
bnep                   18140  2 
bluetooth             209199  10 rfcomm,bnep
binfmt_misc            17500  1 
acer_wmi               32453  0 
coretemp               13400  0 
kvm                   414070  0 
ghash_clmulni_intel    13180  0 
cryptd                 20403  1 ghash_clmulni_intel
snd_hda_intel          33491  5 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
microcode              22803  0 
snd_pcm                96580  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
ideapad_laptop         18086  0 
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
joydev                 17457  0 
rts5139               356158  0 
snd_seq_midi_event     14899  1 snd_seq_midi
uvcvideo               76749  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12860  1 uvcvideo
videobuf2_memops       13368  1 videobuf2_vmalloc
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lpc_ich                17061  0 
wmi                    19070  1 acer_wmi
psmouse                95552  0 
serio_raw              13215  0 
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
i915                  520629  3 
mac_hid                13205  0 
drm_kms_helper         46784  1 i915
drm                   275528  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
mei                    40690  0 
video                  19335  2 acer_wmi,i915
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
hid_generic            12493  0 
r8169                  61650  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid

```

Thanks in advance for any help.

---

### Post by Stormlord on 2012-12-12
It seems no driver for your wireless device is installed.  Just to make sure, post here the results of this please:

sudo ifconfig -a

I think there will be no wlan0 in the list.

If the only two are eth0 and lo, you need to search for proprietary drivers for your wireless using "Additional drivers" or install ndiswrapper.  Ndiswrapper will give you the ability to use your Windows driver with your Ubuntu.  But let's make sure there is no driver installed first.

---

### Post by RogerMoore on 2012-12-12
Thanks for your reply, Stormlord. You were right about only eth0 and lo being in the list, however according to Software Sources -> Additional Drivers I do have a driver installed (bcmwl-kernel-source).

---

### Post by Stormlord on 2012-12-12
Well, since there is no wlan0 device on your system, you can't have wireless connections.  This is the device Network Manager needs to find.  If the driver is installed as you say and you can see it is activated in Additional Drivers, it's either not installed correctly or something else is missing that I don't know of.

Nevertheless, if you cannot solve the problem otherwise, try to uninstall the proprietary driver using Additional drivers, install DKMS using synaptic if it's not installed already and then install the following packages:
ndisgtk
ndiswrapper-dkms

ndisgtk is the graphic environment app package that will automatically install ndiswrapper-common and ndiswrapper-utils-1.9 for you.

After all those installations, you should be able to see a new entry called Windows Wireless Drivers.

I guess you do have the necessary Windows drivers for your wireless device available somewhere.  Among the files contained in the driver installation folder, there is an .inf file.  That is the file ndiswrapper will ask for when you run Windows Wireless Drivers and you should tell it where to find it.

If all goes well, you should see a confirmation that the driver is installed successfully and you should be able to see a wlan0 device now.  :)

---

