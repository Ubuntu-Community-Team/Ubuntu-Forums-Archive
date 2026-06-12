---
title: "Can't find wireless card after latest update."
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by ventrikolo on 2011-09-21
Had a lot of problems with my Realtek wireless card. Instable wificonnection was the problem, until recently when i followed a thread that explained how to install the latest realtek drivers. I got the whole thing working perfectly and today after the latest Ubuntu update the computer can't even find the the ******* card. I'm very ******* frustrated since you have to tweak everything all the time and when you finally get your **** working ubuntu is there to **** it all up with and update.

Now, any clues what so ever on how i could find my wificard again, make it work flawlessly like it did exactly before the update?
[FONT=Arial][/FONT]

---

### Post by praseodym on 2011-09-21
Hi,

please show the ******** ;-)  terminal outputs of

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
cat /var/lib/NetworkManager/NetworkManager.state
```

---

### Post by ventrikolo on 2011-09-22
Sorry for using a lot of star words last night. Sometimes ubuntu just knows how to make a bad day even worse. I'm greatful for the help. Here's everything you asked for: 

uname -a
```
Linux henrik-U31F 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```lspci -nnk | grep -iA2 net
```
Linux henrik-U31F 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```lsusb
```
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0b05:1788 ASUSTek Computer, Inc. 
Bus 001 Device 003: ID 04f2:b1b9 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```lsmod
```
Module                  Size  Used by
rfcomm                 47694  8 
binfmt_misc            17565  1 
sco                    18187  2 
bnep                   18308  2 
l2cap                  53570  16 rfcomm,bnep
joydev                 17606  0 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28167  1 
snd_hda_codec_realtek   336771  1 
snd_hda_intel          33176  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96391  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
i915                  515121  8 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         42136  1 i915
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               72195  0 
btusb                  18600  2 
videodev               82052  1 uvcvideo
drm                   227534  4 i915,drm_kms_helper
bluetooth              72320  9 rfcomm,sco,bnep,l2cap,btusb
intel_ips              18097  0 
v4l2_compat_ioctl32    17078  1 videodev
psmouse                73535  0 
serio_raw              13166  0 
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13400  1 i915
asus_laptop            24173  0 
sparse_keymap          13898  1 asus_laptop
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
ahci                   25951  2 
r8169                  48022  0 
libahci                26642  1 ahci
```iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.
```rfkill list
```
5: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```cat /var/lib/NetworkManager/NetworkManager.state
```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

---

### Post by Gordon D on 2011-09-22
I am having the same issue.

uname -a
```
Linux Latitude-D420 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686 i686 i386 GNU/Linux

```

lspci -nnk | grep -iA2 net
```
Linux Latitude-D420 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:18:14 UTC 2011 i686 i686 i386 GNU/Linux
~ $ lspci -nnk | grep -iA2 net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
	Subsystem: Dell Device [1028:01d6]
	Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
	Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
	Kernel modules: wl, ssb

```

lsusb
```
Bus 005 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 002 Device 004: ID 413c:8103 Dell Computer Corp. Wireless 350 Bluetooth
Bus 002 Device 003: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 002 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 12d1:140c Huawei Technologies Co., Ltd. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsmod
```
Module                  Size  Used by
nfs                   282952  0 
lockd                  74292  1 nfs
fscache                50364  1 nfs
nfs_acl                12771  1 nfs
auth_rpcgss            39173  1 nfs
sunrpc                199096  4 nfs,lockd,nfs_acl,auth_rpcgss
ppp_deflate            12838  0 
zlib_deflate           26594  1 ppp_deflate
bsd_comp               12777  0 
ppp_async              17308  1 
crc_ccitt              12595  1 ppp_async
option                 21045  2 
usb_wwan               19711  1 option
usbserial              37116  7 option,usb_wwan
usb_storage            43946  0 
uas                    17676  0 
usbhid                 41704  0 
hid                    77084  1 usbhid
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  2 snd_hda_intel,snd_hda_codec
rfcomm                 38125  8 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
sco                    17827  2 
i915                  451033  3 
snd_seq_midi_event     14475  1 snd_seq_midi
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
joydev                 17322  0 
dell_wmi               12601  0 
drm_kms_helper         40745  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
sparse_keymap          13666  1 dell_wmi
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   184164  4 i915,drm_kms_helper
dell_laptop            13515  0 
pcmcia                 39671  0 
btusb                  18160  2 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                 14054  1 dell_laptop
psmouse                73312  0 
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
wl                   2642531  0 
yenta_socket           27230  0 
serio_raw              12990  0 
pcmcia_rsrc            18292  1 yenta_socket
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
soundcore              12600  1 snd
lib80211               14570  1 wl
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
firewire_ohci          31504  0 
firewire_core          56138  1 firewire_ohci
sdhci_pci              13623  0 
tg3                   131476  0 
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core

```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

```

rfkill list
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

cat /var/lib/NetworkManager/NetworkManager.state
```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```

---

### Post by Brian shep on 2011-09-22
hey guys! kinda the same problem with me actually it seems to be a little more profound on my rig  with realtek 8185 based pci card when installind from the dvd everything worked great switching nicely from wireless to wired BUT when you update all heck breaks loose.............why..  is the network manager changed or what. is there a command for straighten your but out and fly right....real frustrating and i wrote about this problem 4 days and 2 fresh installs ago.... and wow not one reply....uh VALID reply .... i would really appreciate any advice on this problem . as of now i snatched the wireless card out and things are running smoothly. well maybe still a little scared to check if i can use either of my optical drives to actually record a cd or dvd! that would be terrific ............hmm i never remember having so many problems with  any distribution.. but for the benefit of all the great hard working people who make all this possible ...i will gladly chalk up my problems by presuming that with the rapid advances in computer technology your software needs to be on the forefront of technology ...drivers and such ...and by gearing youre product for the new equipment sometimes relics like my optiplex 160 get left behind...that being said .. overall great job on natty thanks for the hard work...........Brian

---

### Post by ventrikolo on 2011-09-24
so thats it? we just got ****** in the *** by ubuntu? no solution? without working wifi i'm gonna have to go back to awesome win7! :shock: damn this really makes me sad

---

### Post by ventrikolo on 2011-09-24
just got a tip from another forum. It didn't solve the problem anyone was expecting it to do it but it seems it all worked out in the end. You still need a working ethernet connected though.

Got a recommendation to try wicd network-manager instead. So I tried installing it and then uninstalling gnome network-manager.

sudo apt-get install wicd && sudo apt-get purge network-manager

i only got a ethernetconnection with that as well and it looked pretty dull so i just thought i get rid of wicd after installing gnome network-manager.

sudo apt-get install
reboot

 So I installed gnome network-manager again rebooted and then uninstalled wicd. To my surprise wifi was back in action in gnome! In other words: get rid of gnomes nwm, but not until you have a working replacement nwm for ethernetconnection. Then install gnomes nwm again and reboot and then get rid of the extra nwm. Theres probably a better and more effective way of doing this with awesome code in the terminal but i'm a noob and this is how it worked for me.

Hope this works for you too guys! GL!):P

Please get back to me if this works so I can set this thread to solved. If this only works for me I think you guys deserve a better answer!

---

### Post by praseodym on 2011-09-24
Ok, guys, this is gonna go confusing. Three users with three different hardware devices ;-)

To ventrikolo: Glad its working

To Gordon G: Uninstall the Broadcom-STA-driver (just deactivate it in "additional drivers") and install the missing firmware for the b43 driver via cable connection:

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Reboot.

To Brian shep:

Please show the same terminal outputs like Gordon G did, plus

```
dmesg | egrep 'rtl8|r8'
```
Would be the best to open a new thread.

---

