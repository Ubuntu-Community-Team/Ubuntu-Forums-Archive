---
title: "Network manager / Broadcom 4306"
date: 2013-08-26
forum: Networking &amp; Wireless
---

### Post by soulofthegods88 on 2013-08-26
Please help me im a complete linux noob and have spent the last 5 days working on getting wifi to work. I know a few commands but im not entirely sure what to do. My network Manager sees my home router but when I click to connect the wifi symbol in system tray pulses repeatedly and will switch back over to ethernet symbol.

---

### Post by Niall_Dawson on 2013-08-26
What encryption is your WiFi pass? Are you using the desktop version or the server version with the desktop GUI installed? I'm still abit new to this too but I know some things that have helped me work with Ubuntu on other PCs/laptops

---

### Post by soulofthegods88 on 2013-08-26
Ok what I know, I am using Ubuntu 12.04lts Desktop I have a Broadcom 4306 rev.2 device, (I believe) correctly installed b43legacy firmware installer, I can see my wifi network but it just keeps acting like its going to connect then disconnects. The router is unsecured for the time being while i try to fix it connecting to begin with then move onto encrypted network.

---

### Post by jlh68 on 2013-08-26
I have an AcerAspireOne 725 netbook with an Atheros 9485 chip and I have the same problem.  I tried a WiFi dongle (Realteck chip) and it did not work either. I have searched the internet and as of yet found a solution.  The WiFi will come on but it NEVER connects to my wireless router.  My Laptop does fine and my wife's Kindle Fire does fine, just the netbook has the problem.

---

### Post by soulofthegods88 on 2013-08-26
I apologize I left out that i have the 32-bit os system.

---

### Post by Hadaka on 2013-08-26
Hi,please disconnect your wired ethernet cable
and then try to connect to a wireless access point.
*IF that doesnt work, then reconnect the ethernet cable.
open a terminal ctrl/alt/t....Copy and paste the following
one line at a time,post the results..
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list all
cat /etc/network/interfaces
```
thanks.

---

### Post by soulofthegods88 on 2013-08-26
```
01:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11bg Wireless Network Controller [14e4:4325] (rev 02)
    Subsystem: Microsoft Corporation Wireless PCI Adapter MN-730 [1414:0004]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
--
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:2a6f]
    Kernel driver in use: r8169
    Kernel modules: r8169
```

```
Module                  Size  Used by
b43                   364596  0 
bcma                   39810  1 b43
nls_utf8               12493  1 
udf                    84660  1 
bnep                   17852  2 
rfcomm                 38400  12 
parport_pc             27612  0 
ppdev                  12849  0 
nvidia               8503151  29 
binfmt_misc            17292  1 
snd_hda_codec_realtek    65004  1 
snd_hda_intel          38819  3 
snd_hda_codec         118613  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                85934  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25157  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51593  2 snd_seq_midi,snd_seq_midi_event
coretemp               13324  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
kvm_intel             127786  0 
joydev                 17329  0 
kvm                   384557  1 kvm_intel
btusb                  17951  0 
snd                    57014  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bluetooth             211435  24 bnep,rfcomm,btusb
psmouse                82769  0 
gpio_ich               13278  0 
drm                   233935  2 nvidia
soundcore              12600  1 snd
snd_page_alloc         18398  2 snd_hda_intel,snd_pcm
serio_raw              13031  0 
mac_hid                13077  0 
microcode              18433  0 
lpc_ich                17048  0 
arc4                   12509  2 
b43legacy             117994  0 
ssb                    51554  2 b43,b43legacy
mac80211              541819  2 b43,b43legacy
cfg80211              453853  3 b43,b43legacy,mac80211
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_generic            12484  0 
usbhid                 46125  0 
hid                    83037  2 hid_generic,usbhid
usb_storage            48053  0 
firewire_ohci          35914  0 
firewire_core          62086  1 firewire_ohci
crc_itu_t              12627  2 udf,firewire_core
ahci                   25631  3 
libahci                26336  1 ahci
r8169                  62532  0
```

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```

```
auto lo
iface lo inet loopback

```

---

### Post by Hadaka on 2013-08-26
Hi, bit of an oddball you have there..BCM4306 [14e4:4325]
give this a try..
```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
improvment??

---

### Post by soulofthegods88 on 2013-08-27
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
firmware-b43-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
When I tried to run sudo modprobe b43 it started a new line seemingly no response.

---

### Post by soulofthegods88 on 2013-08-27
Is there any update on this?

---

### Post by Hadaka on 2013-08-27
Hi, sorry im late getting back to you. The no response
on ..sudo modprobe b43..means it took the command. Please
be a little more detailed in your responses, as in...still doesnt connect.
not seeing access points.  Did you unplug the wired connection ??
When you are entering commands you will need to be internet connected
via hardwire....but when you test the wireless, please disconnect the wired connection.
please do..
```
sudo modprobe ssb
```
any response?
does it try to connect?

---

### Post by Hadaka on 2013-08-27
Let's verify that your settings are correct..
Click the wireless icon
Click Edit Connections
Click Wireless tab
Click YOUR_Connection name
Click Edit... then configure eaxctly like the attached..


[ATTACH=CONFIG]245779[/ATTACH][ATTACH=CONFIG]245780[/ATTACH][ATTACH=CONFIG]245781[/ATTACH]

---

### Post by soulofthegods88 on 2013-08-28
I set everything per your pictures, still no connection it tries for a few moments then reports disconnected, I tried accessing different internet sites while it was to see if the connection was tricking me but no luck. On a side note when checking the dmesg | Grep b43 command I recieved this error. 
```
[   14.277223] b43legacy-phy0: Broadcom 4306 WLAN found (core revision 4)
[   14.324086] b43legacy-phy0: Loading firmware b43legacy/ucode4.fw
[   14.435180] b43legacy-phy0: Loading firmware b43legacy/pcm4.fw
[   14.452412] b43legacy-phy0: Loading firmware b43legacy/b0g0initvals2.fw
[   24.860045] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  325.059998] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  325.063799] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  385.987910] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  505.689525] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  625.701415] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  865.103889] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  865.815195] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  925.851225] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)

```

---

### Post by Hadaka on 2013-08-28
try setting your router to no encryption, also the network mgr settings under security.
just to see if it will connect, also choose channel 1 or 11
and be sure o be disconnected from the wired.

---

### Post by soulofthegods88 on 2013-08-28
Same result as before no connection, I do see the network and another one. It tried to connect but gave the disconnect error again.

---

### Post by Hadaka on 2013-08-28
lets try the linux nonfree driver and see what happens
please do..
```
sudo apt get install linux-firmware-nonfree
sudo modprobe b43
```

---

### Post by soulofthegods88 on 2013-08-28
I had the same result as before double checked the open wifi, other devices are currently connected so I know there is a good connection. Was I supposed to install or uninstall anything to do your last command? It did installed without error.

---

### Post by Hadaka on 2013-08-28
probably just needs a little more thought..and at 2 am here
im blurry.
please do..
```
sudo modprobe -r b43
sudo modprobe -v b43
dmesg | grep b43
```
post the dmesg results please..
I will look at them tomorrow...night.

---

### Post by soulofthegods88 on 2013-08-28
Thank you very much for your assistance I look forward to hearing from you tommorrow night. I performed all three commands the second command produced this result, ```
insmod /lib/modules/3.8.0-29-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.8.0-29-generic/kernel/drivers/net/wireless/b43/b43.ko
``` the dmesg | grep b43 produced this message, 

```
[   14.277223] b43legacy-phy0: Broadcom 4306 WLAN found (core revision 4)
[   14.324086] b43legacy-phy0: Loading firmware b43legacy/ucode4.fw
[   14.435180] b43legacy-phy0: Loading firmware b43legacy/pcm4.fw
[   14.452412] b43legacy-phy0: Loading firmware b43legacy/b0g0initvals2.fw
[   24.860045] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  325.059998] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  325.063799] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  385.987910] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  505.689525] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  625.701415] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  865.103889] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  865.815195] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[  925.851225] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[ 1135.977210] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[ 1195.332585] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[ 1285.250202] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[ 1465.457917] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[ 1525.624486] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[ 1675.676738] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[ 2185.752930] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[ 3145.210656] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[ 4135.331282] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[ 4135.361152] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[ 4465.393943] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
[ 4465.415555] b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)
```

---

### Post by Hadaka on 2013-08-28
Let's rummage around and look at some stuff.
disconnect the wired connection
boot
then do..
```
dmesg | grep b43
lsmod | grep b43
ls /lib/firmware/b43legacy
ls /etc/modprobe.d
```
please post the output of this..
thanks.

---

### Post by soulofthegods88 on 2013-08-28
The dmesg | grep b43 came back with

```
[   13.910488] b43legacy-phy0: Broadcom 4306 WLAN found (core revision 4)
[   13.956072] b43legacy-phy0: Loading firmware b43legacy/ucode4.fw
[   14.143415] b43legacy-phy0: Loading firmware b43legacy/pcm4.fw
[   14.160646] b43legacy-phy0: Loading firmware b43legacy/b0g0initvals2.fw
[   25.552038] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)

```

lsmod | grep b43 was...

```
b43legacy             117994  0 
ssb                    51554  1 b43legacy
mac80211              541819  1 b43legacy
cfg80211              453853  2 b43legacy,mac80211

```

ls /lib/firmware/b43legacy....

```
a0g0bsinitvals2.fw  a0g1bsinitvals5.fw    b0g0initvals2.fw  ucode11.fw
a0g0bsinitvals5.fw  a0g1initvals5.fw    b0g0initvals5.fw  ucode2.fw
a0g0initvals2.fw    b0g0bsinitvals2.fw    pcm4.fw          ucode4.fw
a0g0initvals5.fw    b0g0bsinitvals5.fw    pcm5.fw          ucode5.fw

```

ls /etc/modprobe.d was...

```
alsa-base.conf            blacklist-oss.conf
blacklist-ath_pci.conf        blacklist-rare-network.conf
blacklist-b43.conf        blacklist-watchdog.conf
blacklist-bcm43.conf        dkms.conf
blacklist.conf            ndiswrapper.conf
blacklist.conf~            nvidia-319-updates_hybrid.conf
blacklist-firewire.conf     nvidia-graphics-drivers.conf
blacklist-framebuffer.conf  oss-compat.conf
blacklist-modem.conf        vmwgfx-fbdev.conf

```

---

### Post by soulofthegods88 on 2013-08-28
Also when it tried to auto connect to the wireless (failed again of course) this message was added to the 
dmesg | grep b43

 b43legacy-phy0 warning: Unexpected value for chanstat (0x7C00)

---

### Post by Hadaka on 2013-08-28
ok, from a wired conection please do..
```
sudo apt-get update
sudo apt-get upgrade
sudo modprobe -r ssb
sudo modprobe ssb
```
boot and see if it connects

---

### Post by soulofthegods88 on 2013-08-28
I ran each one one at a time when i did sudo modprobe -r ssb i received FATAL ERROR: Module ssb is in use. I tried with ethernet to start rebooted and tried again without ethernet and recieved the same error. The results were the same it tried to connect to wireless waited about 1-2 minutes and said it was disconnected without ever connecting to it.

---

### Post by soulofthegods88 on 2013-08-28
Ok an update to this post for some very strange reason my wireless just started working out of nowhere. After doing the last commands and it not working I connected back to the ethernet. I ran the program Ubuntu Tweaks and ran the janitor program deleting all in the list with the exception of old kernels. I settled into my GIMP software to do some work, in the meantime my fiancee needed to use her laptop so I disconnected the ethernet from my computer and the wifi connected immediatly and is so far working stable even after two reboots. Thank You so very much for your help and if there is any way I can find out exactly what happened so that I can post it and let others having my problem know of a possible solution I would appreciate it for now I will mark this as solved since its working at this moment.

---

### Post by Hadaka on 2013-08-28
Magic,smoke and mirrors, I'm glad it's working !

---

