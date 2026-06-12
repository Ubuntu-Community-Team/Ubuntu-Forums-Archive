---
title: "Ubuntu 10.04 RTL8101E/RTL8102E"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by rainie2k1 on 2011-12-27
Hey all. First experience with Linux at all. Trying to solve a problem with my wireless card after installing 10.04. Here's the breakdown:

HP Pavilion g6, Ubuntu 10.04 64 bit, Realtek RTL8101E/RTL8102E wireless card

So far, I've figured out that I have the age old issue for this card of the wrong driver within Ubuntu. Running the command sudo lshw, the driver I have is r8169. I've read elsewhere with people who have similar problems that this is the incorrect driver, and r8168 should be used. I made my way to the Realtek site, downloaded the driver package (for kernel 2.6.x and up) and extracted it on the HP/Ubuntu computer. I also followed the instructions of this person: [http://ubuntuforums.org/showthread.php?t=1328011](http://ubuntuforums.org/showthread.php?t=1328011)

HOWEVER, all of that said and done, when I type in the initial commands...

sudo apt-get install build-essential linux-headers-`uname -r`
sudo -E make clean modules
sudo make install
sudo depmod -a

the terminal reads, "package build-essential is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source. E: Package build-essential has no installation candidate"

I'm clearly missing an important step. Can anyone please help?

---

### Post by wildmanne39 on 2011-12-27
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.

Also this driver> r8169
is for your ehternet connection not your wireless.
Thank you

---

### Post by rainie2k1 on 2011-12-27
Hey. Thank you very much for the response. I should've said that both the ethernet and wireless were not working. In order to figure out that something was up with the driver, I had plugged my computer directly into the router, but no dice. At any rate, thanks for the info. Here are the results so far:

cat /etc/lsb-release; uname -a

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux ryan-laptop 2.6.32-33-generic #70-Ubuntu SMP Thu Jul 7 21:13:52 UTC 2011 x86_64 GNU/Linux

```

lspci -nnk | grep -iA2 net

```
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Kernel driver in use: r8169
	Kernel modules: r8101, r8169
07:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
08:00.0 Class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)

```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

```

rfkill list all

(no feedback)

lsmod

```
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_idt      61546  1 
snd_hda_codec_atihdmi     3023  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  3 snd_hda_codec_idt,snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
video                  20623  0 
output                  2503  1 video
psmouse                65040  0 
serio_raw               4918  0 
snd                    71283  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vga16fb                12757  1 
vgastate                9857  1 vga16fb
i2c_piix4               9639  0 
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
lp                      9336  0 
parport                37160  2 ppdev,lp
ahci                   38030  2 
r8169                  39714  0 
mii                     5237  1 r8169

```

---

### Post by wildmanne39 on 2011-12-27
Hi, the problem with compiling the driver is the build essentials can not be installed because you do not have an internet connection.

Put your livecd in your cdrom drive then open synaptic package manager click on settings, repositories and put a check by cdrom then reload the repositories, then type build essentials into the search window and you should be able to install it and you will also need kernel header and they must match the kernel you have installed.
Thanks

---

### Post by rainie2k1 on 2011-12-28
The build essentials installed, and the kernel header was already installed. I selected to reinstall it, but the report after installation said that the kernel header couldn't be reinstalled. I'd copy and paste, but it wasn't letting me. 

So I loaded Ubuntu back up without the Live CD, and still no network connections, not seeing any networks, etc. It's practically on top of a router right now.

---

### Post by wildmanne39 on 2011-12-28
Hi, let's try this please:
```
sudo rmmod -f r8169
```
```
sudo modprobe r8101

```

Make sure to unplug your wired connection first.
Thanks

---

### Post by rainie2k1 on 2011-12-28
Ok, did that. No wireless networks detected.

---

### Post by wildmanne39 on 2011-12-28
Hi, that is to try to get your wired connection working so it will be easier to get your wireless working, and that is just to try it if it works we need to make it permanent so if you have restarted your computer you will need to run the commands again and you need to have your computer plugged into your router.

Also when you tried to install build essentials from the livecd, you were booted into ubuntu and you just put the livecd into the drive and followed my directions right? you were not booted from the livecd correct?
Thanks

---

### Post by rainie2k1 on 2011-12-28
I definitely booted from the LiveCD. So I went back a couple of steps and tried to open Synaptics Manager with the LiveCD in. I selected "build essentials" and looked for the applicable kernel. I have the computer plugged directly into the router. It's not getting the files from the server, though. I'm getting the same errors as when I booted with the Live CD. So, in short, I still haven't downloaded the build essentials.

---

### Post by wildmanne39 on 2011-12-28
Hi, ok let's try to get your wireless working instead, you will not need to install build essentials for that but you will need to put your livecd in your cdrom and install dkms, patch, fakeroot, and bcmwl-kernel-source that can be done by finding the folder > ~/pool/main/ the folders are in alphabetical order. 

The named packages are in the folders with their first letter. Just double click them one by one (this installs them) and activate the Broadcom-STA driver in "System-Settings-Hardware drivers.

Then take your livecd out and reboot.

Or you can insert the CD, add it to synaptic package manager like in the previous post and install these packages with synaptic. 
Thanks

---

### Post by rainie2k1 on 2011-12-28
Completed all of that. Right clicked my wifi icon in the taskbar. No wireless networks detected.

---

### Post by wildmanne39 on 2011-12-28
Hi, did you reboot? and please post:
```
lsmod
```
Thanks

---

### Post by rainie2k1 on 2011-12-28
I did. After removing the LiveCD. 

lsmod

```
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_idt      61546  1 
snd_hda_codec_atihdmi     3023  1 
lib80211_crypt_tkip     8676  0 
snd_pcm_oss            41394  0 
snd_hda_intel          25805  2 
snd_hda_codec          85759  3 snd_hda_codec_idt,snd_hda_codec_atihdmi,snd_hda_intel
snd_mixer_oss          16299  1 snd_pcm_oss
snd_hwdep               6924  1 snd_hda_codec
snd_pcm                87946  3 snd_pcm_oss,snd_hda_intel,snd_hda_codec
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
wl                   1964968  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
psmouse                65040  0 
video                  20623  0 
serio_raw               4918  0 
output                  2503  1 video
lib80211                6151  2 lib80211_crypt_tkip,wl
snd                    71283  16 snd_hda_codec_idt,snd_pcm_oss,snd_hda_intel,snd_hda_codec,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               62851  0 
videodev               40518  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
vga16fb                12757  1 
vgastate                9857  1 vga16fb
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
i2c_piix4               9639  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
r8169                  39714  0 
mii                     5237  1 r8169
ahci                   38030  2 



```

---

### Post by wildmanne39 on 2011-12-28
Hi, it looks like the driver is there, but it may need one more, this would be a lot easier if this was ubuntu 11.10, your wired connection should work right away for starters.

Please post the output of:
```
nm-tool
```
```
iwconfig
rfkill list all
```
```
lsmod | grep iwl
```
```
sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eht1 -eth0 -e etork | tail -n55
```
Thanks

---

### Post by zuerston on 2011-12-28
Hey Wildmanne39
When you get done here can you (please) take a look at [http://ubuntuforums.org/showthread.php?p=11571236#post11571236](http://ubuntuforums.org/showthread.php?p=11571236#post11571236)

---

### Post by rainie2k1 on 2011-12-28
I tried 11.10. That's a whole other story. When the install screen came up, and I selected for full install, the screen would go black. Black as in the screen was turned off. Looked it up, and on HP g6's, 11.10 resets the screen brightness during install, so I just have to adjust it with the screen brightness button. Easy. Except my incorrigible computer won't change the screen brightness during that install screen for some reason. I tried every combination of buttons. I gave up thinking that correcting the wireless in 10.04 would be easier. If you can fix that screen brightness issue easier, I'd be more than happy to bump up to 11.10. 


nm-tool

```
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        78:E3:B5:62:DE:89

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        60:D8:19:1E:9A:1E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    TallWillow-guest:Infra, C0:C1:C0:C3:94:5D, Freq 2462 MHz, Rate 0 Mb/s, Strength 40
    HOME-A1C8:       Infra, 00:26:F3:D1:A1:C8, Freq 2427 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    TallWillow:      Infra, C0:C1:C0:C3:94:5B, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2

```


iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```


no feedback on rfkill list all


no feedback on lsmod  | grep iwl


sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eht1 -eth0 -e etork | tail -n55

```
Dec 28 19:25:55 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/eth0, iface: eth0)
Dec 28 19:25:55 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec 28 19:25:55 ryan-laptop NetworkManager: <info>  (eth0): carrier is OFF
Dec 28 19:25:55 ryan-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Dec 28 19:25:55 ryan-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 28 19:51:30 ryan-laptop kernel: [    1.381904] eth0: RTL8101e at 0xffffc9000579c000, 78:e3:b5:62:de:89, XID 00a00000 IRQ 28
Dec 28 19:51:30 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/eth0, iface: eth0)
Dec 28 19:51:30 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec 28 19:51:30 ryan-laptop NetworkManager: <info>  (eth0): carrier is OFF
Dec 28 19:51:30 ryan-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Dec 28 19:51:30 ryan-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 28 20:03:45 ryan-laptop kernel: [    1.380765] eth0: RTL8101e at 0xffffc900057a2000, 78:e3:b5:62:de:89, XID 00a00000 IRQ 29
Dec 28 20:03:45 ryan-laptop kernel: [    9.185777] wl: module license 'MIXED/Proprietary' taints kernel.
Dec 28 20:03:45 ryan-laptop kernel: [    9.190974] wl 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 28 20:03:45 ryan-laptop kernel: [    9.190983] wl 0000:07:00.0: setting latency timer to 64
Dec 28 20:03:45 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/eth0, iface: eth0)
Dec 28 20:03:45 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec 28 20:03:45 ryan-laptop NetworkManager: <info>  (eth0): carrier is OFF
Dec 28 20:03:45 ryan-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Dec 28 20:03:45 ryan-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 28 20:03:45 ryan-laptop NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl')
Dec 28 20:04:20 ryan-laptop NetworkManager: <info>  (eth0): now managed
Dec 28 20:04:20 ryan-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Dec 28 20:04:20 ryan-laptop NetworkManager: <info>  (eth0): bringing up device.
Dec 28 20:04:20 ryan-laptop kernel: [   44.099395] r8169: eth0: link down
Dec 28 20:04:20 ryan-laptop NetworkManager: <info>  (eth0): preparing device.
Dec 28 20:04:20 ryan-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Dec 28 20:04:20 ryan-laptop kernel: [   44.100275] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 28 20:04:25 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:04:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:05:16 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:05:56 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:06:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:07:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:08:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:09:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:10:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:11:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:12:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:13:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:15:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:16:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:17:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:18:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:19:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:20:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:21:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:22:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:23:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:24:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:25:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:26:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:27:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:28:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:29:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 

```

---

### Post by zuerston on 2011-12-28
> **rainie2k1 said:**
> I tried 11.10. That's a whole other story. When the install screen came up, and I selected for full install, the screen would go black. Black as in the screen was turned off. Looked it up, and on HP g6's, 11.10 resets the screen brightness during install, so I just have to adjust it with the screen brightness button. Easy. Except my incorrigible computer won't change the screen brightness during that install screen for some reason. I tried every combination of buttons. I gave up thinking that correcting the wireless in 10.04 would be easier. If you can fix that screen brightness issue easier, I'd be more than happy to bump up to 11.10. 


nm-tool

```
NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        78:E3:B5:62:DE:89

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             disconnected
  Default:           no
  HW Address:        60:D8:19:1E:9A:1E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    TallWillow-guest:Infra, C0:C1:C0:C3:94:5D, Freq 2462 MHz, Rate 0 Mb/s, Strength 40
    HOME-A1C8:       Infra, 00:26:F3:D1:A1:C8, Freq 2427 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    TallWillow:      Infra, C0:C1:C0:C3:94:5B, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2

```
iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```
no feedback on rfkill list all


no feedback on lsmod  | grep iwl


sudo cat /var/log/syslog | grep -e wl -e firmware -e wpa -e eht1 -eth0 -e etork | tail -n55

```
Dec 28 19:25:55 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/eth0, iface: eth0)
Dec 28 19:25:55 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec 28 19:25:55 ryan-laptop NetworkManager: <info>  (eth0): carrier is OFF
Dec 28 19:25:55 ryan-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Dec 28 19:25:55 ryan-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 28 19:51:30 ryan-laptop kernel: [    1.381904] eth0: RTL8101e at 0xffffc9000579c000, 78:e3:b5:62:de:89, XID 00a00000 IRQ 28
Dec 28 19:51:30 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/eth0, iface: eth0)
Dec 28 19:51:30 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec 28 19:51:30 ryan-laptop NetworkManager: <info>  (eth0): carrier is OFF
Dec 28 19:51:30 ryan-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Dec 28 19:51:30 ryan-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 28 20:03:45 ryan-laptop kernel: [    1.380765] eth0: RTL8101e at 0xffffc900057a2000, 78:e3:b5:62:de:89, XID 00a00000 IRQ 29
Dec 28 20:03:45 ryan-laptop kernel: [    9.185777] wl: module license 'MIXED/Proprietary' taints kernel.
Dec 28 20:03:45 ryan-laptop kernel: [    9.190974] wl 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 28 20:03:45 ryan-laptop kernel: [    9.190983] wl 0000:07:00.0: setting latency timer to 64
Dec 28 20:03:45 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/eth0, iface: eth0)
Dec 28 20:03:45 ryan-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.0/0000:01:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
Dec 28 20:03:45 ryan-laptop NetworkManager: <info>  (eth0): carrier is OFF
Dec 28 20:03:45 ryan-laptop NetworkManager: <info>  (eth0): new Ethernet device (driver: 'r8169')
Dec 28 20:03:45 ryan-laptop NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Dec 28 20:03:45 ryan-laptop NetworkManager: <info>  (eth1): new 802.11 WiFi device (driver: 'wl')
Dec 28 20:04:20 ryan-laptop NetworkManager: <info>  (eth0): now managed
Dec 28 20:04:20 ryan-laptop NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Dec 28 20:04:20 ryan-laptop NetworkManager: <info>  (eth0): bringing up device.
Dec 28 20:04:20 ryan-laptop kernel: [   44.099395] r8169: eth0: link down
Dec 28 20:04:20 ryan-laptop NetworkManager: <info>  (eth0): preparing device.
Dec 28 20:04:20 ryan-laptop NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Dec 28 20:04:20 ryan-laptop kernel: [   44.100275] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 28 20:04:25 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:04:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:05:16 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:05:56 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:06:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:07:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:08:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:09:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:10:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:11:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:12:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:13:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:15:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:16:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:17:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:18:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:19:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:20:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:21:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:22:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:23:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:24:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:25:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:26:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:27:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:28:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 
Dec 28 20:29:46 ryan-laptop wpa_supplicant[935]: WPS-AP-AVAILABLE 

```


YOU are running a HP G6 ? !!! mine is a HP a**6**333w  desktop and I too have screen black out when it boots up! and my monitor (24" Spectre LCD) says "UN SUPPORTED" but it (Video) is ok after boot-up, but NO WIFI surfing even after connecting to an open WIFI router!  wired works fine. damn I sure would like to know the answer!
:confused:

---

### Post by wildmanne39 on 2011-12-28
Hi, it sees the router which network are you trying to connect too? and the signal strength is very weak are you still close to the router? 

Weak signal is one reason I do not like this driver, in 11.10 we could use a different driver that is better but I am not sure how to fix your brightness issue.

If you can turn your encryption off a few minutes and see if we can get it to connect that would help then we can change it to encrypted.
Thanks

---

### Post by wildmanne39 on 2011-12-28
Hi, I can not really get into the black screen problem on this thread we have to stick to the topic but I would think this link would help with that issue.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by rainie2k1 on 2011-12-28
TallWillow (not guest). I'm about 5 feet from my router.

Unfortunately, I'm unsure how to turn off the encryption...if you can tell me how...I do have the password readily available if you want to just skip that de-encryption step.

...Maybe in the meantime I'll see if anyone has another answer about my 11.10 issue other than, "press the brightness button."

---

### Post by wildmanne39 on 2011-12-28
Hi, I made a typo in one of the commands please run:
```
lsmod | grep wl
```

To turn off encryption open your web browser and type 192.168.0.1 into your browser, you have to be wired to your router, this usually gets you into the setting of the router so you can change them.
Thanks

---

### Post by rainie2k1 on 2011-12-28
Looks like 11.10 and hp g6 do not get along. After fixing the install black screen, there are a handful of other caveats after boot up.

lsmod | grep wl

```
wl                   1964968  0 
lib80211                6151  2 lib80211_crypt_tkip,wl



```

---

### Post by rainie2k1 on 2011-12-28
And 192.168.1.1 pulled up the router setup page. I realized what you were talking about after I saw your response.

---

### Post by rainie2k1 on 2011-12-28
Router is ready to go.

---

### Post by wildmanne39 on 2011-12-28
Hi, okay it still does not connect? I am doing a little research give me a couple of minutes.
Thanks

---

### Post by rainie2k1 on 2011-12-28
Oh I didn't mean to rush you. Just getting ahead of myself and posting before I have all my info together. Ok, with my router encryption off, it sees my network...and someone else's that it didn't see before.

---

### Post by wildmanne39 on 2011-12-28
Hi, you have a button on your router for WPS right? can you make it where it is not used? in the error message that is a problem it looks like it just keeps repeating that message.

Is that where you put in your password? here is one link about it.
[http://linuxwireless.org/en/developers/Brainstorming/WPS-client](http://linuxwireless.org/en/developers/Brainstorming/WPS-client)
Thanks

---

### Post by rainie2k1 on 2011-12-28
Actually, it appears to be in manual already (rather than WPS). I brought the Linux computer to work earlier today to continue working on the problem when I had free time. It didn't connect or do anything there either. Also, by the way, in my previous post I said that it sees the networks in the area. I should directly state that it's connect to my home network currently since encryption was turned off.

---

### Post by wildmanne39 on 2011-12-28
Hi, that is a good sign, we finally got the driver working. Try setting your encryption to just wpa2 if you can it works better then wpa/wpa2 or wep usually but there are some drivers in ubuntu that have problems with wpa or wpa2 so just try one at a time until you find one that works.
Thanks

---

### Post by rainie2k1 on 2011-12-28
Fantastic! Thank you for getting the drivers running. WPA2 setup. As far as WPA2 drivers in Ubuntu, you're talking about the drivers within the Synaptics Manager, correct? Skimming through and doing a search, I only see the wpasupplicant package, and it says that's already installed. Are you speaking of drivers to download from the internet?

---

### Post by wildmanne39 on 2011-12-29
Hi, no I mean go back into your router settings and turn on encryption, hopefully  with one of them enabled you will be able to connect. Try wpa2 first.

When it is connecting using encryption would you please go to the top of the page and mark this thread solved by clicking on thread tools, unless you want to try to get your wired connection working also but I do not really have much experience with wired connections but it should be easier now that your wireless is working. 
Thanks

---

### Post by rainie2k1 on 2011-12-29
Oh I see. So WPA2 wont allow it to connect. It sees the network, and I can put in the address, but then it just sits and thinks. Nothing more. WPA would knock out the n on my b/g/n according to the warning that popped up when I tried to select it. While I don't need n, I appreciate the speed, so I didn't try there. Also, the WPA2 breaks into two separate options: enterprise and personal. I didn't bother with enterprise since it's just a home network.

---

### Post by wildmanne39 on 2011-12-29
Hi, will unless you have a real fast internet connection above 54mb n speed is not going to help you. 

You can also try wep but it is less secure then wpa or wpa2 but it is better then nothing.
Thanks

---

### Post by rainie2k1 on 2011-12-29
Well, yeah, that's a fair point on the 54mps. So before I left for work, I tried to give this one more good try. I logged into my router, opened up the HP, and before I could switch it out of WPA2, the HP connected. Much like an incorrigible small child, my computer apparently needed a nap to work. That's my only logical explanation. 

Thank you so much for all of your help! You're fantastic for even searching these forums for some poor fool who can't get their Ubuntu up correctly. And, I learned a lot more because of it--something I'm all for.

---

### Post by wildmanne39 on 2011-12-29
Hi, I am glad it is working now and you are very welcome!!!, it is hard for everyone when there is no internet at all to use to fix wireless or wired so it was a challenge for us both.
Enjoy

---

