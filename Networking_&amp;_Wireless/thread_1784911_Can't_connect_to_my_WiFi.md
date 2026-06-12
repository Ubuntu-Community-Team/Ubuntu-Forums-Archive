---
title: "Can't connect to my WiFi"
date: 2011-06-17
forum: Networking &amp; Wireless
---

### Post by Chanpa on 2011-06-17
Hi,
I installed Ubuntu 11.04 yesterday and my wireless didn't work so I searched a little and found a way to make it work;
Uninstalled bcmwl-kernel-source and installed firmware-b43-lpphy-installer and b43-fwcutter.
And it worked. But today I accidentally pressed the "turn off wireless" button on my laptop. I obviously pressed it again and thought it would work but it doesn't. Now I find networks and stuff but I can't connect to them. It tries for awhile and then asks me to enter the password which I do (it is correct) and then it tries to connect for a few minutes again and then it asks me for the password again.
Any help would be appreciated.
Some info:
```
lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

``````
sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"alpne"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

``````
rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````
cat /etc/modprobe.d/* | egrep '8180|acx|at76|ath|b43|bcm|CX|eth|ipw|irmware|isl|lbtf|orinoco|ndiswrapper|NPE|p54|prism|rtl|rt2|rt3|rt6|rt7|witch|wl'
# which ath5k cannot recover. To prevent this condition, stop
blacklist ath_pci
blacklist eth1394
# replaced by p54pci
blacklist prism54
# replaced by b43 and ssb.
# blacklist bcm43xx
blacklist uart6850
blacklist twl4030_wdt

``````
sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: a4:ba:db:d3:82:c5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.187 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 70:f1:a1:c2:52:b5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=478.104 link=no multicast=yes wireless=IEEE 802.11bg

```

---

### Post by Chanpa on 2011-06-17
bump

---

### Post by superduperlinuxperson on 2011-06-17
alright, now the quetioning :)
so, you are saying that your firmware is installed and everything is set? if so, try going to additional drivers, and check and see whats activated. sometimes ubuntu screws with things it shouldn't. like, if i go to additional drivers and activate the sta driver, wlan0 dissapears. yeah i know its hilarious, i do it for fun all the time :)
thanks

---

### Post by Chanpa on 2011-06-17
Well I don't know what firmware I should be using, I've seen some people saying I should uninstall bcmwl-kernel-source and some people saying I should have that and uninstall the b43-fwcutter.

---

### Post by superduperlinuxperson on 2011-06-17
very sorry for postinfg that, links are outdated.
  [http://www.omattos.com/sites/default...all-fw.tar_.gz]("http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz")
take the two folders in it and extract them into lib/firmware/

---

### Post by nm_geo on 2011-06-17
> **Chanpa said:**
> Well I don't know what firmware I should be using, I've seen some people saying I should uninstall bcmwl-kernel-source and some people saying I should have that and uninstall the b43-fwcutter.

You have a working wireless driver and firmware installed. The wireless switch looks to be on not off.  I would not change wireless drivers just yet.. 

A test would be to toggle the wireless switch;
do ```
rfkill list
```Toggle switch again
```
rfkill list
``````
cat /var/lib/NetworkManager/NetworkManager.state
```Try to reboot without the ethernet cable connected, and we might consider re-installing the network-manager.  Go to synaptic and just mark it for re-install.. apply

---

### Post by Chanpa on 2011-06-18
Toggle switch
```
rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```Toggle again
```
rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````
cat /var/lib/NetworkManager/NetworkManager.state

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
```Rebooting now.
Edit: It worked. Did we even change anything? I've rebooted without the ethernetcable plugged in before :S
Thanks though :D

---

### Post by Chanpa on 2011-06-18
Seems like I spoke too soon. My wireless just disconnected and now it can't connect again.

---

### Post by Chanpa on 2011-06-18
I did the same thing as I did before and it didn't work now so maybe it was just a fluke :(
Anyone able to help?

---

### Post by Black Angel Aster on 2011-06-18
Have you tried:

```
sudo service network-manager stop

sudo service network-manager start
```

In the terminal? Might work...

---

### Post by Chanpa on 2011-06-18
Tried it and wireless still doens't want to connect, it tries for awhile then it says Wireless disconnected

---

### Post by Black Angel Aster on 2011-06-18
Hm... Then I have the exact same problem. (almost) If I get an Answer before you, I will let you know.

---

### Post by Chanpa on 2011-06-18
Bump. Anyone?

---

### Post by nm_geo on 2011-06-18
> **Chanpa said:**
> Bump. Anyone?

Try an 
```

lsmod
```and 

```
dmesg | egrep 'ound|irmware|eth|ath|wl|ipw|b43|witch|ndiswrapper'
```

---

### Post by Chanpa on 2011-06-18
```
lsmod
Module                  Size  Used by
parport_pc             36959  0 
ppdev                  17113  0 
binfmt_misc            17565  1 
snd_hda_codec_idt      71137  1 
arc4                   12529  2 
joydev                 17606  0 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
i915                  514985  3 
dell_wmi               12681  0 
b43                   318638  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13898  1 dell_wmi
dell_laptop            13827  0 
dcdbas                 14438  1 dell_laptop
mac80211              294370  1 b43
snd_timer              29602  2 snd_pcm,snd_seq
uvcvideo               72195  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
videodev               82052  1 uvcvideo
v4l2_compat_ioctl32    17078  1 videodev
drm_kms_helper         42136  1 i915
cfg80211              178528  2 b43,mac80211
psmouse                73535  0 
snd                    67382  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13166  0 
drm                   227495  4 i915,drm_kms_helper
soundcore              12680  1 snd
i2c_algo_bit           13400  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
video                  19438  1 i915
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
usb_storage            53538  0 
hid                    91020  1 usbhid
uas                    17996  0 
ssb                    51945  1 b43
sky2                   58509  0 
ahci                   25951  3 
libahci                26642  1 ahci

```
```
dmesg | egrep 'ound|irmware|eth|ath|wl|ipw|b43|witch|ndiswrapper'
[    0.000000] No AGP bridge found
[    0.000000] No NUMA configuration found
[    0.000000] No AGP bridge found
[    0.380148] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.520189] ACPI: No dock devices found.
[    0.520195] HEST: Table not found.
[    0.620109] Switching to clocksource hpet
[    0.629928] Switched to NOHz mode on CPU #0
[    0.629930] Switched to NOHz mode on CPU #1
[    0.662730] pnp: PnP ACPI: found 13 devices
[    0.694760] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.770017] ACPI: Lid Switch [LID]
[    0.840854] ERST: Table is not found!
[    1.043151] i2c-core: driver [adp5520] using legacy suspend method
[    1.043153] i2c-core: driver [adp5520] using legacy resume method
[    1.070151] hub 1-0:1.0: USB hub found
[    1.090139] hub 2-0:1.0: USB hub found
[    1.090531] hub 3-0:1.0: USB hub found
[    1.090838] hub 4-0:1.0: USB hub found
[    1.100188] hub 5-0:1.0: USB hub found
[    1.100484] hub 6-0:1.0: USB hub found
[    1.100776] hub 7-0:1.0: USB hub found
[    1.101077] hub 8-0:1.0: USB hub found
[    1.132552] device-mapper: multipath: version 1.2.0 loaded
[    1.132555] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.135904] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.342444] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.342464] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    1.350340] sky2 0000:09:00.0: eth0: addr a4:ba:db:d3:82:c5
[    1.380327] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x16, vendor 0x4243)
[    1.380345] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0F, vendor 0x4243)
[    1.380362] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x0A, vendor 0x4243)
[    1.380379] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x09, vendor 0x4243)
[    1.460333] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[    3.197670] input: Razer DeathAdder as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input4
[    3.197809] generic-usb 0003:1532:0007.0001: input,hidraw0: USB HID v1.11 Mouse [Razer DeathAdder] on usb-0000:00:1d.0-1/input0
[   11.319353] lp: driver loaded but no devices found
[   11.694665] uvcvideo: Found UVC 1.00 device Integrated Webcam (05ca:180a)
[   11.946793] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   12.107115] Registered led device: b43-phy0::tx
[   12.107136] Registered led device: b43-phy0::rx
[   12.107160] Registered led device: b43-phy0::radio
[   12.107181] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[   12.487507] Console: switching to colour frame buffer device 170x48
[   12.501720] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   12.620957] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   12.621138] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   13.250415] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   27.280369] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   27.280373] b43-phy0 ERROR: This device does not support DMA on your system. It will now be switched to PIO.
[   27.280376] b43-phy0: Controller RESET (DMA error) ...
[   27.620251] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   41.571553] b43-phy0: Controller restarted
[   41.572658] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.577666] sky2 0000:09:00.0: eth0: enabling interface
[   41.578667] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.747814] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   44.631355] wlan0: authenticate with 00:18:e7:f5:0c:b8 (try 1)
[   44.633116] wlan0: authenticated
[   44.633461] wlan0: associate with 00:18:e7:f5:0c:b8 (try 1)
[   44.636475] wlan0: RX AssocResp from 00:18:e7:f5:0c:b8 (capab=0x431 status=0 aid=1)
[   44.636479] wlan0: associated
[   44.638182] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   48.540037] ieee80211 phy0: wlan0: No probe response from AP 00:18:e7:f5:0c:b8 after 500ms, disconnecting.
[   50.181082] wlan0: authenticate with 00:18:e7:f5:0c:b8 (try 1)
[   50.380042] wlan0: authenticate with 00:18:e7:f5:0c:b8 (try 2)
[   50.580047] wlan0: authenticate with 00:18:e7:f5:0c:b8 (try 3)
[   50.780051] wlan0: authentication with 00:18:e7:f5:0c:b8 timed out
[   55.240070] wlan0: no IPv6 routers present
[   58.346074] sky2 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex, flow control both
[   58.346658] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   68.720020] eth0: no IPv6 routers present

```

---

### Post by nm_geo on 2011-06-18
I have not forgotten you, but I need to go do something else for a while.

---

### Post by francisv@comcast.net on 2011-06-18
I'm having a similar issue on 10.1.  Works fine for hours then I start getting prompted for my WPA password and it won't reconnect even after I retype the password.

Since your hardware is apparently being seen you may have similar issue.

I just power down, wait a few minutes and restart. Seems to clear the problem.
I think the password encryption is behind it but don't know enough to be sure yet.
My next try will be to remove the WPA requirement from my Belkin router
and see if I stay connected.

Sometimes Ubuntu acts like Winders. But it's more fun and a lot cheaper to fix.



wlan0     IEEE 802.11bg  ESSID:"alpne"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

---

### Post by nbound on 2011-06-18
You likely have a different issue unless you have the same card or similar, post the output of **lshw -C network** and **lsmod** if its different in a new thread :)

---

### Post by TheCuomo on 2011-06-18
Dudes,

Your symptoms sound similar to mine (detects the network, asks for the password, but continually tried to connect with no success).

What worked for me was setting a static IP:

[http://ubuntuforums.org/showthread.php?p=10955477#post10955477](http://ubuntuforums.org/showthread.php?p=10955477#post10955477)

Dunno if it'll work for you but it's worth a shot...

---

### Post by Chanpa on 2011-06-18
Tried what you wrote, nothing worked. Going to bed now again :(

---

### Post by maphew on 2011-06-19
> **TheCuomo said:**
> Dudes,

Your symptoms sound similar to mine (detects the network, asks for the password, but continually tried to connect with no success).

What worked for me was setting a static IP:

[http://ubuntuforums.org/showthread.php?p=10955477#post10955477](http://ubuntuforums.org/showthread.php?p=10955477#post10955477)

Dunno if it'll work for you but it's worth a shot...
yup, similar symptoms here too, only with an Atheros card instead of Broadcom. Setting a static ip worked for a little while but doesn't anymore. Boot from a sysrescue cd and wifi works without a hitch.

---

### Post by nbound on 2011-06-19
> **maphew said:**
> yup, similar symptoms here too, only with an Atheros card instead of Broadcom. Setting a static ip worked for a little while but doesn't anymore. Boot from a sysrescue cd and wifi works without a hitch.

What kind of Atheros?

---

### Post by Chanpa on 2011-06-19
Anyone got any idea how to fix this? It's getting really annoying with a laptop that needs an ethernet connection ;(

---

### Post by nm_geo on 2011-06-19
> **Chanpa said:**
> Anyone got any idea how to fix this? It's getting really annoying with a laptop that needs an ethernet connection ;(

I have seen where the dell-laptop module is messing with the network..

Try this ... we can always get it back.

```
sudo modprobe -r dell-laptop

```We are basically temporarily turning that module off.  I just did it on my laptop here and it has no adverse effect. 

Then run the 

```
rfkill list all
```We need to make sure no rfkill say yes.

---

### Post by Chanpa on 2011-06-19
```
rfkill list all
1: phy0: Wireless LAN 
Soft blocked: no 
Hard blocked: no 
``` I have installed Wicd network manager and that is telling me that the connection is trying to authenticate but it is a "bad password" which it isn't.

---

### Post by Chanpa on 2011-06-19
When I try to connect to my wireless it says:
Disconnecting active connections...
alpne: Resetting IP address...
alpne: Putting up interface...
alpne: Validating authentication...
alpne: Connection Failed: Bad password

And then it fails.

I did this if it is of any help... It sure looks bad;
```
dmesg | grep b43
[    3.064404] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.064420] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[   12.020998] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   12.699491] Registered led device: b43-phy0::tx
[   12.699511] Registered led device: b43-phy0::rx
[   12.699531] Registered led device: b43-phy0::radio
[   13.880280] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   27.770406] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   27.770410] b43-phy0 ERROR: This device does not support DMA on your system. It will now be switched to PIO.
[   27.770412] b43-phy0: Controller RESET (DMA error) ...
[   28.140278] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   42.171427] b43-phy0: Controller restarted
[  225.500299] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  240.140294] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  254.360316] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  280.530101] b43-phy0 ERROR: MAC suspend failed
[  281.330097] b43-phy0 ERROR: MAC suspend failed
[  289.880063] b43-phy0 ERROR: MAC suspend failed
[  290.680103] b43-phy0 ERROR: MAC suspend failed
[  291.610100] b43-phy0 ERROR: MAC suspend failed
[  292.490051] b43-phy0 ERROR: MAC suspend failed
[  293.380068] b43-phy0 ERROR: MAC suspend failed
[  294.260082] b43-phy0 ERROR: MAC suspend failed
[  295.150102] b43-phy0 ERROR: MAC suspend failed
[  296.030070] b43-phy0 ERROR: MAC suspend failed
[  296.910073] b43-phy0 ERROR: MAC suspend failed
[  297.790092] b43-phy0 ERROR: MAC suspend failed
[  305.080090] b43-phy0 ERROR: MAC suspend failed
[  305.960087] b43-phy0 ERROR: MAC suspend failed
[  307.200084] b43-phy0 ERROR: MAC suspend failed
[  308.090077] b43-phy0 ERROR: MAC suspend failed
[  308.980086] b43-phy0 ERROR: MAC suspend failed
[  309.880072] b43-phy0 ERROR: MAC suspend failed
[  310.770084] b43-phy0 ERROR: MAC suspend failed
[  317.720098] b43-phy0 ERROR: MAC suspend failed
[  318.610097] b43-phy0 ERROR: MAC suspend failed
[  319.490070] b43-phy0 ERROR: MAC suspend failed
[  320.910071] b43-phy0 ERROR: MAC suspend failed
[  321.800064] b43-phy0 ERROR: MAC suspend failed
[  322.770087] b43-phy0 ERROR: MAC suspend failed
[  323.710097] b43-phy0 ERROR: MAC suspend failed
[  329.860066] b43-phy0 ERROR: MAC suspend failed
[  330.740099] b43-phy0 ERROR: MAC suspend failed
[  331.660092] b43-phy0 ERROR: MAC suspend failed
[  332.720083] b43-phy0 ERROR: MAC suspend failed
[  333.600085] b43-phy0 ERROR: MAC suspend failed
[  334.490053] b43-phy0 ERROR: MAC suspend failed
[  342.080055] b43-phy0 ERROR: MAC suspend failed
[  342.970108] b43-phy0 ERROR: MAC suspend failed
[  343.880080] b43-phy0 ERROR: MAC suspend failed
[  344.770067] b43-phy0 ERROR: MAC suspend failed
[  345.650101] b43-phy0 ERROR: MAC suspend failed
[  346.530229] b43-phy0 ERROR: MAC suspend failed
[  347.730069] b43-phy0 ERROR: MAC suspend failed
[  348.630059] b43-phy0 ERROR: MAC suspend failed
[  349.590085] b43-phy0 ERROR: MAC suspend failed
[  350.540105] b43-phy0 ERROR: MAC suspend failed
[  351.480102] b43-phy0 ERROR: MAC suspend failed
[  357.660081] b43-phy0 ERROR: MAC suspend failed
[  358.560073] b43-phy0 ERROR: MAC suspend failed
[  359.440084] b43-phy0 ERROR: MAC suspend failed
[  360.330099] b43-phy0 ERROR: MAC suspend failed
[  361.210099] b43-phy0 ERROR: MAC suspend failed
[  362.090117] b43-phy0 ERROR: MAC suspend failed
[  362.970096] b43-phy0 ERROR: MAC suspend failed
[  363.850050] b43-phy0 ERROR: MAC suspend failed
[  364.730084] b43-phy0 ERROR: MAC suspend failed
[  371.440097] b43-phy0 ERROR: MAC suspend failed
[  372.320097] b43-phy0 ERROR: MAC suspend failed
[  373.210098] b43-phy0 ERROR: MAC suspend failed
[  374.850086] b43-phy0 ERROR: MAC suspend failed
[  375.670074] b43-phy0 ERROR: MAC suspend failed
[  376.490056] b43-phy0 ERROR: MAC suspend failed
[  377.290084] b43-phy0 ERROR: MAC suspend failed
[  378.140061] b43-phy0 ERROR: MAC suspend failed
[  378.380253] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  429.280258] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  443.430249] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  458.020306] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  478.690077] b43-phy0 ERROR: MAC suspend failed
[  479.570068] b43-phy0 ERROR: MAC suspend failed
[  480.470069] b43-phy0 ERROR: MAC suspend failed
[  494.460073] b43-phy0 ERROR: MAC suspend failed
[  495.340072] b43-phy0 ERROR: MAC suspend failed
[  496.220085] b43-phy0 ERROR: MAC suspend failed
[  497.110069] b43-phy0 ERROR: MAC suspend failed
[  498.810056] b43-phy0 ERROR: MAC suspend failed
[  505.600092] b43-phy0 ERROR: MAC suspend failed
[  506.510078] b43-phy0 ERROR: MAC suspend failed
[  507.400051] b43-phy0 ERROR: MAC suspend failed
[  508.480069] b43-phy0 ERROR: MAC suspend failed
[  509.890293] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  530.370278] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  544.560276] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  568.840303] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  583.320296] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  604.710088] b43-phy0 ERROR: MAC suspend failed
[  605.590078] b43-phy0 ERROR: MAC suspend failed
[  606.470074] b43-phy0 ERROR: MAC suspend failed
[  619.660068] b43-phy0 ERROR: MAC suspend failed
[  620.480068] b43-phy0 ERROR: MAC suspend failed
[  622.250290] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  636.450272] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  720.370288] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  734.870289] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  755.760093] b43-phy0 ERROR: MAC suspend failed
[  756.650075] b43-phy0 ERROR: MAC suspend failed
[  757.550068] b43-phy0 ERROR: MAC suspend failed
[  760.760251] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  774.920277] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  789.420309] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  810.770102] b43-phy0 ERROR: MAC suspend failed
[  811.650066] b43-phy0 ERROR: MAC suspend failed
[  812.540092] b43-phy0 ERROR: MAC suspend failed
[  825.920089] b43-phy0 ERROR: MAC suspend failed
[  826.800070] b43-phy0 ERROR: MAC suspend failed
[  827.680062] b43-phy0 ERROR: MAC suspend failed
[  828.570085] b43-phy0 ERROR: MAC suspend failed
[  830.150091] b43-phy0 ERROR: MAC suspend failed
[  838.840067] b43-phy0 ERROR: MAC suspend failed
[  839.750093] b43-phy0 ERROR: MAC suspend failed
[  840.630068] b43-phy0 ERROR: MAC suspend failed
[  841.240268] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  880.450285] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[  894.570278] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
```
I don't know what the MAC suspend failed means but the error at 27 seconds seems to be the problem to my novice eyes.

---

### Post by nm_geo on 2011-06-19
Yeah I would agree those MAC failures are not good, but .... We can try some others things too. Did you stop the dell-laptop module?  

We might need to remove and re-install the driver and firmware it will certainly not hurt anything.  I see you are trying WICD and unless Network Manager is remove they conflict sometimes.

---

### Post by Chanpa on 2011-06-19
Yeah I stopped the dell-laptop and I removed network manager
Edit: Well, I ran the sudo modprobe -r dell-laptop

---

### Post by nm_geo on 2011-06-19
> **Chanpa said:**
> Yeah I stopped the dell-laptop and I removed network manager

You are making me experiment here.. I had never installed wicd in Natty until just now mine works okay by the way but not in upper right panel, but that is another issue.

Try the re-install of b43-fwcutter and the firmare.. As I remember you have the low power chip set correct?

---

### Post by Chanpa on 2011-06-19
Yes, how would I do those things? Through synaptic? Which packet is the firmware
And yeah, I uninstalled network manager and not just removed from panel :D

---

### Post by nm_geo on 2011-06-19
Just a thought since you have got this up a couple of times .. Have you reset your wireless access point?

Sorry we crossed messages there a little .. Synaptic is fine..

---

### Post by Chanpa on 2011-06-19
How do I reset the access point? And what packets should i reinstall

---

### Post by nm_geo on 2011-06-19
I would remove the b43-fwcutter and the firmware that has b43 listed too.
Then we re-install the same packages.. 

You reset your wireless router/wlan just power it off and turn it back on.

---

### Post by nm_geo on 2011-06-19
Run this code also .. I should have had you do that long ago.

```
lspci -nn
```

---

### Post by Chanpa on 2011-06-19
Ok, reset the router (got confused when you called it Access point :D) and reinstalled b43-fwcutter and that is the only package that shows up when I type b43 in synaptic

---

### Post by Chanpa on 2011-06-19
```
lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)

```

---

### Post by nm_geo on 2011-06-19
> **Chanpa said:**
> Ok, reset the router (got confused when you called it Access point :D) and reinstalled b43-fwcutter and that is the only package that shows up when I type b43 in synaptic

Check for firmware-b43-lpphy-installer ... I thought you had it installed if any other firmware that has b43 listed in it remove it also.

We just want b43-fwcutter 
and the firmware-b43-lpphy-installer

---

### Post by Chanpa on 2011-06-19
I though I had it installed aswell... I used to have it :S But now it doesn't show up in synaptic. Is there a way to download it?

---

### Post by nm_geo on 2011-06-19
> **Chanpa said:**
> I though I had it installed aswell... I used to have it :S But now it doesn't show up in synaptic. Is there a way to download it?

Yeah but try search on bcm instead of b43.. we need that firmware

in terminal try this if you can't find it in synaptic.

```
sudo apt-get install firmware-b43-lpphy-installer
```

---

### Post by Chanpa on 2011-06-19
```
sudo apt-get install firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43-lpphy-installer

```
sigh

---

### Post by nm_geo on 2011-06-19
> **Chanpa said:**
> ```
sudo apt-get install firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43-lpphy-installer

```sigh
  okay you are running Natty 11.04 right?  And it is updated? 
```

sudo apt-get update
```

```
sudo apt-get upgrade
```

---

### Post by Chanpa on 2011-06-19
running the update/upgrade now and it will take ahwile it looks like

---

### Post by nm_geo on 2011-06-19
> **Chanpa said:**
> running the update/upgrade now and it will take ahwile it looks like

Try getting the firmware after the upgrade.. I should have asked that earlier too.. np

---

### Post by Chanpa on 2011-06-19
ok i've installed the firmware aswell

---

### Post by nm_geo on 2011-06-19
> **Chanpa said:**
> ok i've installed the firmware aswell

Okay reboot.. and lets check a few things,,

---

### Post by Chanpa on 2011-06-19
Ok I've rebooted

---

### Post by nm_geo on 2011-06-19
> **Chanpa said:**
> Ok I've rebooted

Ok let's see 
```

sudo lshw -C network
```

```
rfkill list all
```

```
dmesg | grep b43
```

---

### Post by Chanpa on 2011-06-19
```
sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: a4:ba:db:d3:82:c5
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.184 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 70:f1:a1:c2:52:b5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38 firmware=478.104 link=yes multicast=yes wireless=IEEE 802.11bg
``````
rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
``````
dmesg | grep b43
[    2.891035] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.895954] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[   11.543990] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   11.780824] Registered led device: b43-phy0::tx
[   11.780847] Registered led device: b43-phy0::rx
[   11.780865] Registered led device: b43-phy0::radio
[   13.480278] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   27.630401] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[   27.630405] b43-phy0 ERROR: This device does not support DMA on your system. It will now be switched to PIO.
[   27.630408] b43-phy0: Controller RESET (DMA error) ...
[   27.970294] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[   42.151433] b43-phy0: Controller restarted
[   96.910265] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  111.570280] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  163.990285] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  197.050284] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  211.240288] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  225.810260] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  277.640315] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  295.190292] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  309.370273] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
```

---

### Post by nm_geo on 2011-06-19
[   13.480278] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23) [   27.630401] b43-phy0 ERROR: Fatal DMA error: 0x00000400, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000 [   27.630405] b43-phy0 ERROR: This device does not support DMA on your system. It will now be switched to PIO.

not good here.. dang it

---

### Post by Chanpa on 2011-06-19
Yeeah.. Found this somewhere
>  
**Known issues**

 LP-PHY devices: DMA  errors on some machines with kernel 2.6. Problem was fixed in 3.0. Using  PIO (module param) can be used as workaround for 2.6. 

---

### Post by nm_geo on 2011-06-19
> **Chanpa said:**
> Yeeah.. Found this somewhere

I read that as well ... Looks like the newest kernel works for some..

[http://ubuntuforums.org/showthread.php?t=1266620&page=84](http://ubuntuforums.org/showthread.php?t=1266620&page=84)

Sorry I gotta go for now .. But let me know how it goes..

---

### Post by maphew on 2011-06-20
> **nbound said:**
> What kind of Atheros?
AR2413 802.11bg NIC (rev 01), should probably follow up at [http://ubuntuforums.org/showthread.php?t=1785286](http://ubuntuforums.org/showthread.php?t=1785286) so as not to sidetrack this thread which seems to have gained some traction.

---

### Post by nm_geo on 2011-06-20
Just upgraded my Natty 11.04 with the new kernel linux 3.0.0-300rc2-generic.  Had no adverse effect on my test version fully upgraded from alpha testing.  In fact I had some blinking going on at boot up that are now gone with the new kernel.  Chanpa it might be something to try..

---

