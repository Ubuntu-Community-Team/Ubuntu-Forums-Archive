---
title: "I have the wireless driver file on usb but need to know how to install it"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by aaron3uk on 2013-03-12
Hey !
I am a complete beginner!

I need help, I have installed the required wireless realtek driver from the website onto a USB.
I now have the file onto my laptop (which has no internet acces at all)

So i need to know how you install the wireless driver file while its on the desktop, is there a command or something that you have to write, please can you tell me as basic as possible because all i know so far is how to open the terminal box but i dont really understand all the little code words people have been writing on these forums. 

Please help me, :( i have a useless laptop now with no internet access at all and I cant even get it wired internet access because im currently travelling so have no access to it, only wifi, 

Hope to hear from you!

---

### Post by carl4926 on 2013-03-12
First of all, lets be sure about your hardware
On you machine please run the following and paste the result here

```
lspci -nnk | grep -iA2 net
```

---

### Post by varunendra on 2013-03-12
*Thread moved to **Networking & Wireless**.*
-------------------------------------

Welcome to the forums alfred33 !:)

Please post the complete name of the driver, as well as the link (if possible) where you downloaded it from.

So that we can make sure the driver is correct for your chip, please also post the output of :
```
lspci -nnk | grep -iA2 net
```
Enter the above command in a terminal (Ctrl+Alt+T) and post back the result here.


**Edit:** ninja'd by carl4926 :P

---

### Post by aaron3uk on 2013-03-12
ahh thanks for the reply guys!! this is a nightmare, i am at a internet cafe and my laptop has just run out of battery!!!
grhh so i will have to come back tomorrow! Please check this again soon and not foget meee!! Thank you and i will reply tmorrow!!

---

### Post by aaron3uk on 2013-03-13
hi guys this is the infomation you require

lspci -nnk | grep -iA2 net
```
abf13@abf13-Satellite-C805D:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8211] 
Kernel driver in use: rtl8192ce
--
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
 Subsystem: Toshiba America Info Systems Device [1179:fcd3] 
Kernel driver in use: atl1c
abf13@abf13-Satellite-C805D:~$
```
 
and this is where i got the driver from.
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

Hope to hear from you soon!

---

### Post by varunendra on 2013-03-13
> **aaron3uk said:**
> 
```
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. **RTL8188CE 802.11b/g/n** WiFi Adapter [**10ec:8176**] (rev 01)
Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8211] 
Kernel driver in use: **[COLOR="#B22222"]rtl8192ce[/COLOR]**
```

Hi,
Your card is already supported by a native driver and normally the one from realtek is not required if the native one is working fine.

What is the problem you are having? Difficulty in connection, frequent drops or no wireless at all ?

Please post outputs of -
```
iwconfig
rfkill list all
iwlist scan
```

---

### Post by aaron3uk on 2013-03-13
Hey Var, the problem is im getting no internet all , cant connect, no devices or anything being shown!

```
abf13@abf13-Satellite-C805D:~$ iwconfig
eth0 
no wireless extensions.
lo no wireless extensions.

abf13@abf13-Satellite-C805D:~$ rfkill list all
abf13@abf13-Satellite-C805D:~$ rfkill list all
abf13@abf13-Satellite-C805D:~$ iwlist scan
eth0 
Interface doesn't support scanning.
lo 
Interface doesn't support scanning.
abf13@abf13-Satellite-C805D:~$ 
```


(the rkill list all didnt do anything!)

hey ver, i dont no too much technical info at all, but is it using the **[COLOR=#b22222]rtl8192ce[/COLOR]** instead of the **RTL8188CE 802.11b/g/n****RTL8188CE 802.11b/g/n** ???

---

### Post by varunendra on 2013-03-13
> (the rkill list all didnt do anything!)
That's very odd !

Reboot, go into BIOS and make sure wireless is enabled there. Also, if there is a physical switch for it, make sure it is turned On.

If all these are okay and still rfkill list doesn't return any outputs, please follow the Wireless Script link in my signature, do as the linked post asks to do and post back the diagnostics report here.

---

### Post by varunendra on 2013-03-13
> **aaron3uk said:**
> hey ver, i dont no too much technical info at all, but is it using the **[COLOR=#b22222]rtl8192ce[/COLOR]** instead of the **RTL8188CE 802.11b/g/n****RTL8188CE 802.11b/g/n** ???

That's a common confusion and I just explained it in a post yesterday : [http://ubuntuforums.org/showthread.php?t=2124731&p=12554130#post12554130](http://ubuntuforums.org/showthread.php?t=2124731&p=12554130#post12554130)

---

### Post by aaron3uk on 2013-03-13
Hey Var, thanks for your help but can you please explain as basic what you mean go to BIOS ?? and how do i check its enabled?

---

### Post by carl4926 on 2013-03-13
> **aaron3uk said:**
> Hey Var, thanks for your help but can you please explain as basic what you mean go to BIOS ?? and how do i check its enabled?

BIOS is **Basic Input/Output System**

And is the [COLOR=#000000][FONT=sans-serif]first software run by a PC when powered on. You usually see some sort of splash screen with options as to accessing it[/FONT][/COLOR]

---

### Post by varunendra on 2013-03-13
BIOS is the basic firmware program of your laptop which you can access by pressing some dedicated key for it while the laptop starts booting. Unfortunately, this dedicated key is not common for all. Usually it is any of the Esc, Tab, Del or one of the Function keys (mostly F1, F2, F8, F9, F10 or F12).

Usually it is stated in the initial boot screen of the pc/laptop (which key does what). If not, try starting with Esc key. (the option to enter BIOS may be listed as "Enter Setup" or something similar).

Once in the BIOS, there can be several settings under several categories depending upon laptop model and BIOS version.

Usually the settings like wireless, USB etc. are placed under "Advanced" settings, but it can also be called something different. You'll have to find it yourself.

While you search for it, post back your laptop's full and exact model no., and I'll try to search over the net, although BIOS references are hard to find.

Also, if your laptop is an old model (2 years or more), you can easily reset the BIOS to "Optimal defaults" setting. That is relatively easier to find. With newer UEFI supporting models, it can create problems.

---

### Post by varunendra on 2013-03-14
Hi,

Regarding script download problem you mentioned in your pm, here **I've attached it** for you. Just download and extract it to your desktop, then in a terminal do-
```
cd ~/Desktop
chmod +x wireless_script
./wireless_script
```

Type your password when asked. Post back the contents of the "netinfo.txt" file it creates on the desktop.

PS:
Please also post output of -
```
sudo ufw status
```

---

### Post by aaron3uk on 2013-03-14
Hey thanks for that , here is the info from the netinfo.txt

```

*************** info trace ****************
 
**** uname -a ****

Linux abf13-Satellite-C805D 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

**** lsb-release ****

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"

**** lspci ****

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
 Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8211]
 Kernel driver in use: rtl8192ce
--
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
 Subsystem: Toshiba America Info Systems Device [1179:fcd3]
 Kernel driver in use: atl1c

**** lsusb ****

Bus 002 Device 002: ID 04f2:b303 Chicony Electronics Co., Ltd 
Bus 006 Device 003: ID 0204:6025 Chipsbank Microelectronics Co., Ltd CBM2080 Flash drive controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

**** iwconfig ****
 

**** rfkill ****
 

**** lsmod ****

Module                  Size  Used by
nls_iso8859_1          12714  1 
usb_storage            49288  1 
uas                    18073  0 
snd_hda_codec_hdmi     32476  1 
joydev                 17694  0 
kvm                   422160  0 
snd_hda_codec_conexant    58308  1 
microcode              23030  0 
snd_seq_midi           13325  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_hda_intel          34117  5 
snd_hda_codec         135141  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              17765  1 snd_hda_codec
snd_seq_midi_event     14900  1 snd_seq_midi
rtl8192ce              58779  0 
rtl8192c_common        49512  1 rtl8192ce
rtlwifi                76086  1 rtl8192ce
uvcvideo               78117  0 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                97523  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videobuf2_memops       13405  1 videobuf2_vmalloc
mac80211              555198  3 rtl8192ce,rtl8192c_common,rtlwifi
psmouse               102075  0 
serio_raw              13216  0 
k10temp                13174  0 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4              13302  0 
radeon                912794  3 
cfg80211              208382  2 rtlwifi,mac80211
snd_timer              29990  2 snd_seq,snd_pcm
snd                    83674  20 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
ttm                    88495  1 radeon
drm_kms_helper         49259  1 radeon
soundcore              15092  1 snd
drm                   290344  5 radeon,ttm,drm_kms_helper
toshiba_acpi           18735  0 
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13565  1 radeon
sparse_keymap          13891  1 toshiba_acpi
wmi                    19257  1 toshiba_acpi
bnep                   18240  2 
parport_pc             32867  0 
rfcomm                 47562  0 
ppdev                  17114  0 
bluetooth             211812  10 bnep,rfcomm
video                  19598  0 
mac_hid                13254  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
atl1c                  42092  0 

**** nm-tool ****
 
NetworkManager Tool
State: disconnected
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>
  Capabilities:
    Carrier Detect:  yes
  Wired Properties
    Carrier:         off
 

**** NetworkManager.state ****
 
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

**** NetworkManager.conf ****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq
[ifupdown]
managed=false

**** NetworkManager.conf-10.04 ****
 

**** interfaces ****

auto lo
iface lo inet loopback
 
**** iwlist ****
 

**** resolv ****

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

**** blacklist.conf ****

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.
# evbug is a debug tool that should be loaded explicitly
blacklist evbug
# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd
# replaced by e100
blacklist eepro100
# replaced by tulip
blacklist de4x5
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m
# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2
# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
blacklist bcm43xx
# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps
# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

**** dmesg ****

[    8.854019] wmi: Mapper loaded
[    9.084266] rtl8192ce: ****** This B_CUT device may not work with kernels 3.6 and earlier
[    9.084269] rtl8192ce: Using firmware rtlwifi/rtl8192cfwU_B.bin
[    9.600109] type=1400 audit(1363285405.153:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=746 comm="apparmor_parser"
[    9.758499] rtlwifi: Firmware rtlwifi/rtl8192cfwU_B.bin not available
[   96.094250] type=1400 audit(1363285491.709:24): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=1691 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[  539.723263] Modules linked in: snd_hda_codec_hdmi joydev kvm snd_hda_codec_conexant microcode snd_seq_midi snd_rawmidi snd_hda_intel snd_hda_codec snd_hwdep snd_seq_midi_event rtl8192ce rtl8192c_common rtlwifi uvcvideo videobuf2_core videodev videobuf2_vmalloc snd_seq snd_pcm videobuf2_memops mac80211 psmouse serio_raw k10temp snd_seq_device i2c_piix4 radeon cfg80211 snd_timer snd ttm drm_kms_helper soundcore drm toshiba_acpi snd_page_alloc i2c_algo_bit sparse_keymap wmi bnep parport_pc rfcomm ppdev bluetooth video mac_hid lp parport atl1c
[  539.723314]  [<ffffffff81052c9f>] warn_slowpath_common+0x7f/0xc0
[  539.723324]  [<ffffffff81052cfa>] warn_slowpath_null+0x1a/0x20

**************** done ********************

  
```

And the Sudo ufw status said 'Inactive'

Hope this helps!

---

### Post by varunendra on 2013-03-14
> **aaron3uk said:**
> 
```
[    9.084266] rtl8192ce: ****** This B_CUT device **may not work with kernels 3.6 and earlier**
[    9.084269] rtl8192ce: Using firmware rtlwifi/**rtl8192cfwU_B.bin**
..
[    9.758499] rtlwifi: Firmware rtlwifi/**[COLOR="#FF0000"]rtl8192cfwU_B.bin not available[/COLOR]**
```

Please download the attached file, extract the zipped **rtl8192cfwU_B.bin** file to your desktop, then in a terminal, do -
```
sudo cp ~/Desktop/rtl8192cfwU_B.bin /lib/firmware/rtlwifi
```
This will copy the file to your /lib/firmware/rtlwifi directory. Now unload/reload the driver -
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce
```

Then check if the wireless comes up. Moreover, if you can connect and if the connection is stable.
Post back how it behaves.

---

### Post by aaron3uk on 2013-03-14
hey ver, ok so i have extracted the file onto my desktop, open up the terminal and put 
"sudo cp ~/Desktop/rtl8192cfwU_B.bin /lib/firmware/rtlwifi"

then i type my password, then this comes up straight away
"abf13-Satellite-C805D :~$"

is something suppose to happen??

actually ignore this, i just read its only copying a file, anyways i will continue now, however i did do it like 4 times so hope thats not a problem.

---

### Post by aaron3uk on 2013-03-14
VERR you are a the best!!!!!!!!!!!!!!! I now have WIFI finally after 2 weeks and lots of money spent at this internet cafe i finally have wifi!! _**THank you**_ veryyy muchh! I now have wireless connections avalible!! Ver you are my hero haha! Again i cant thank you enough!!

With all these files on my desktop now, can i delete them or do they need to stay??

as for the connections , i havent tried it yet, but tomorrow i will go to a wifi place and try it and let you know :D but hopefully should be ok!

---

### Post by varunendra on 2013-03-14
> **aaron3uk said:**
> I now have WIFI finally after 2 weeks
So sweet to hear that :P

> With all these files on my desktop now, can i delete them or do they need to stay??
You may delete them, but I would recommend you keep them somewhere in case you need them again.

When you try connecting to other networks, let me know how well it works. To be honest, the native driver we are using sometimes doesn't work so well for some people. So if it gives you any problems, we can try the proprietary driver.

Hope and wish it'll be a good boy for you.

And thanks for the kind words... :)

---

