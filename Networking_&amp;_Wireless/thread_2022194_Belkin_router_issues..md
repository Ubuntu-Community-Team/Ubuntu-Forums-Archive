---
title: "Belkin router issues."
date: 2012-07-10
forum: Networking &amp; Wireless
---

### Post by AnOddRadish on 2012-07-10
I recently installed Ubuntu 12.04 along side OS X Snow Leopard on my Macbook Pro. (Haven't updated to Lion, sue me :P) and am really liking it so far, other than the fact that I can't connect to the internet without connecting directly to my modem via ethernet cable. It says that firmware is missing. What can be done to remedy this? 

Using Belkin N600 DB N+ router, a Motorola modem (I can check the model if need be), and I can connect fine when I boot to Snow Leopard or connect with any other computer in the house. (no other linux OS)

Any help would be super appreciated!

-AnOddRadish

---

### Post by computer13137 on 2012-07-10
> **AnOddRadish said:**
> It says that firmware is missing. What can be done to remedy this?
What says that firmware is missing?  Could you furnish us with a screenshot or a paste of the error message?

> **AnOddRadish said:**
> Using Belkin N600 DB N+ router, a Motorola modem (I can check the model if need be), and I can connect fine when I boot to Snow Leopard or connect with any other computer in the house. (no other linux OS)
I'm going out on a limb and saying the router likely has nothing to do with this issue.  Can you connect to any other wireless networks on this laptop while you're booted into Ubuntu?  Perhaps the drivers for your WiFi card are outdated and you need to install some later ones.

It would be useful if you could paste the output of these commands, either in a code or quote box here or on [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

```
lspci
```

```
lsmod
```

```
iwconfig
```

```
ifconfig
```

This information should get us started nicely.

computer13137

---

### Post by AnOddRadish on 2012-07-10
lspci gives me

```
 [COLOR=#000000][SIZE=3][FONT=Liberation Serif, serif][FONT=Lucida Sans Unicode]anoddradish@anoddradish-MacBookPro:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:01.1 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #5 (rev 05)
00:1a.7 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Universal Host Controller #1 (rev 05)
00:1d.7 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Whistler [AMD Radeon HD 6600M Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Turks HDMI Audio [Radeon HD 6000 Series]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM57765 Gigabit Ethernet PCIe (rev 10)
02:00.1 SD Host controller: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader (rev 10)
03:00.0 Network controller: Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)
04:00.0 FireWire (IEEE 1394): LSI Corporation FW643 PCI Express 1394b Controller (PHY/Link) (rev 08)[/FONT]
[/FONT][/SIZE][/COLOR]
```lsmod gives me

```
anoddradish@anoddradish-MacBookPro:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
hfsplus                83507  1 
vesafb                 13516  1 
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17830  2 
rfcomm                 38139  0 
snd_hda_codec_hdmi     31775  1 
arc4                   12473  2 
b43                   342643  0 
mac80211              436455  1 b43
cfg80211              178679  2 b43,mac80211
ssb                    50691  1 b43
apple_gmux             12655  0 
snd_hda_codec_cirrus    23322  1 
applesmc               18978  0 
input_polldev          13648  1 applesmc
fglrx                2909855  162 
bcma                   25651  1 b43
snd_hda_intel          32765  5 
joydev                 17393  0 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_seq_midi           13132  0 
snd_hwdep              13276  1 snd_hda_codec
snd_rawmidi            25424  1 snd_seq_midi
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
btusb                  17912  1 
bluetooth             158438  13 bnep,rfcomm,btusb
uvcvideo               67203  0 
bcm5974                17199  0 
snd_seq_midi_event     14475  1 snd_seq_midi
videodev               86588  1 uvcvideo
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  20 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
mei                    36570  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
video                  19068  1 apple_gmux
apple_bl               13425  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
hid_apple              13166  0 
sdhci_pci              18324  0 
firewire_ohci          40172  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56906  1 firewire_ohci
tg3                   141369  0 
crc_itu_t              12627  1 firewire_core
usbhid                 41906  0 
hid                    77367  2 hid_apple,usbhid

```iwconfig gives me

```
lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

```and finally, ifconfig gives me

```
anoddradish@anoddradish-MacBookPro:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr c8:2a:14:0a:6b:44  
          inet addr:24.101.91.56  Bcast:24.101.91.255  Mask:255.255.255.0
          inet6 addr: fe80::ca2a:14ff:fe0a:6b44/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31533 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15472 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41382281 (41.3 MB)  TX bytes:1508544 (1.5 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69518 (69.5 KB)  TX bytes:69518 (69.5 KB)

```

I'll post a screenshot in just a minute, assuming that photobucket has stopped acting up.

[IMG]http://i1117.photobucket.com/albums/k589/AnOddRadish/2012-07-10153103HDR.jpg[/IMG]

---

### Post by Kirk Schnable on 2012-07-10
Your wireless card is:
**Broadcom Corporation BCM4331 802.11a/b/g/n (rev 02)**

Now, we should begin looking for any known issues with drivers for this network card...

Let's determine what drivers you have loaded up right now.  I believe your loaded module for this chipset is **bcm5974**.

To determine the version of the drivers you have installed, please run this and get the output to us.

```
modinfo bcm5974
```

Kirk

---

### Post by AnOddRadish on 2012-07-10
Are you sure that's the right driver to be search for? It's saying that it's the apple multitouch driver.

```
anoddradish@anoddradish-MacBookPro:~$ modinfo bcm5974
filename:       /lib/modules/3.2.0-26-generic-pae/kernel/drivers/input/mouse/bcm5974.ko
license:        GPL
description:    Apple USB BCM5974 multitouch driver
author:         Henrik Rydberg
srcversion:     C6FEBEF33D93EDBF248AEDB
alias:          usb:v05ACp0254d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0253d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0252d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp024Ed*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp024Dd*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp024Cd*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp024Bd*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp024Ad*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0249d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0247d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0246d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0245d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0244d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0243d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0242d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0241d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0240d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp023Fd*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0238d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0237d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0236d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0232d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0231d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0230d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0225d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0224d*dc*dsc*dp*ic03isc*ip02*
alias:          usb:v05ACp0223d*dc*dsc*dp*ic03isc*ip02*
depends:        
intree:         Y
vermagic:       3.2.0-26-generic-pae SMP mod_unload modversions 686 
parm:           debug:Activate debugging output (int)

```

Anyway, sorry for the horrible image quality, I couldn't get linux to take an image of the dropdown menu so I took it with my phone.

---

### Post by Kirk Schnable on 2012-07-10
Wow, sorry, that was a shot in the dark.  Usually Broadcom Wireless drivers are "bcmwl" something.  I took one look at the "bcm" driver and assumed it was Broadcom Wireless.  Hmm, I will have to look over your modules more closely and perhaps cross reference with a Google search on your hardware.  I would be happy to do that later or you can try it yourself.

At any rate, I **am** sure that the card I posted above is your wireless card.  I have not had an opportunity to do any Googling for you yet on this topic.

---

### Post by steeldriver on 2012-07-10
Have a read here:

[http://ubuntuforums.org/showthread.php?t=2011756&highlight=4331](http://ubuntuforums.org/showthread.php?t=2011756&highlight=4331)

Please be sure to confirm the PCI IDs are the same for your device using

```
lspci -nn | grep 0280
```before going ahead with chili555's fix. Post back if you get stuck.

BTW does the **wired** connection work through the Belkin router?

---

### Post by AnOddRadish on 2012-07-10
Thank you for posting that forum thread, it provided everything I needed and am posting this from wifi instead of ethernet :)

will mark thread solved

---

