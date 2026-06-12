---
title: "Neither Wired Nor Wireless Working Dell Inspiron 1545"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by chaozuper on 2011-07-27
Hi.

I just installed Ubuntu 10.04.1 on my Dell Inspiron 1545 laptop, but I can't connected to the Internet with a wired or wireless connection. I have a BT Home Hub 2 wireless router. I can connect to the Internet when running Windows Vista, but not with Ubuntu.

I tried installing the Broadcom STA driver off of the live disk, which initially seemed to work. However, I still couldn't connect to the Internet and when I clicked on System > Administration > Hardware Drivers, there weren't any proprietary drivers to install or that had been installed. Also, when I reboot, Ubuntu tries to connect to my network automatically but always fails. That's what makes me think that a driver has been installed, but just isn't the right one or isn't working.

Thanks in advance.

chaozuper.

---

### Post by chaozuper on 2011-07-28
hate to have to do this but ... bump.

---

### Post by Megaptera on 2011-07-28
I know this says Dell Mini and an older version of Ubuntu, but it's worked with several versions of Ubuntu on my Dell 1545.
Hope it works?

Don't forget the re-boot step.

---

### Post by nm_geo on 2011-07-28
You may have what I call the "perfect storm"
 
Did you have ethernet connection when you installed the STA (wl) driver?
 
In terminal copy and paste the following
 
```
 
lspci -nn | grep -e 0280 -e 0200

```
 
Then copy the results here.. 
 
That will return the pci numbers for your wireless and ethernet cards..
I am not on my linux box but others can help ... chili555, wildmanne or others
I would remove unistall the STA (wl) driver for now anyway... 
You may have blacklist issues as well that need to be resolved.
 
If you get ethernet working do the following..gets you up-to-date..
 
```
 
sudo apt-get update && sudo apt-get upgrade

```

---

### Post by chaozuper on 2011-07-28
@Megaptera
Not quite sure what you're trying to say. I think maybe you forgot to put in a link? thanks for trying to help though.

@nm_geo
I have never had an ethernet connection at all, unfortunately.
here are the results of lspci:

```

09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```

also ran *sudo apt-get remove bcmwl-kernel-source* as per your instruction to uninstall the Broadcom STA driver.

---

### Post by wildmanne39 on 2011-07-28
Hi, run these commands please
```
lsmod
```
```
iwconfig
```
```
sudo lshw -C network
```
```
rfkill list all
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Megaptera on 2011-07-29
> **chaozuper said:**
> @Megaptera
Not quite sure what you're trying to say. I think maybe you forgot to put in a link? thanks for trying to help though.
I will now go and write out 100 times "Don't forget the link!"

[http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html](http://www.ubuntumini.com/2010/04/broadcom-wireless-driver-fix-in-lucid.html)

Aplogies :redface:

---

### Post by chaozuper on 2011-07-29
@Megaptera
No need to apologise! Thanks for the link, but unfortunately I couldn't follow the steps as I can't even connect using a wired connection, with or without the Broadcom STA driver.

@wildmanne39
ok, here's the results

lsmod
```

Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_idt      51978  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
arc4                    1153  2 
snd_hda_intel          21941  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
b43                   163523  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205146  1 b43
dell_wmi                1793  0 
i915                  285076  3 
uvcvideo               56990  0 
cfg80211              126517  2 b43,mac80211
dell_laptop             6856  0 
dcdbas                  5422  1 dell_laptop
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54148  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29297  1 i915
led_class               2864  1 b43
psmouse                63245  0 
serio_raw               3978  0 
drm                   162377  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
output                  1871  1 video
intel_agp              24119  2 i915
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39425  1 
sky2                   40775  0 
ahci                   32200  3 
ssb                    38671  1 b43

```

iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
sudo lshw -C network
```

  *-network
       description: Network controller
       product: BCM4312 802.11b/g
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
       serial: 00:25:64:4c:ac:32
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A latency=0 link=no multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:26:5e:33:98:0d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```rfkill list all
```

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```One thing I did notice from these results that seemed odd is that eth01 cares about wireless extensions, but I've got nothing to base that opinion on - it probably is perfectly normal. But, then again, I am new to this whole business and I try and stay out of networking as much as possible.

Thanks for the help so far everyone.

---

### Post by wildmanne39 on 2011-07-29
Deleted

---

### Post by wildmanne39 on 2011-07-29
Hi, run these commands please and post the results here.
```
nm-tool
```
```
dmesg | grep b43
```
```
dmesg | grep firmware
```
```
dmesg | grep wlan0
```
Thank you

---

### Post by chaozuper on 2011-07-30
Ok, here we go:

nm-tool
```

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        00:26:5E:33:98:0D

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:25:64:4C:AC:32

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

dmesg | grep b43
```

[    1.107134] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.107151] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[   10.874671] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   11.051087] Registered led device: b43-phy0::tx
[   11.051105] Registered led device: b43-phy0::rx
[   11.051121] Registered led device: b43-phy0::radio
[   12.264280] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   12.297618] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   12.301188] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   12.301252] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   12.301306] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   12.340839] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   12.343228] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   12.346571] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   12.346633] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   12.346686] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

dmesg | grep firmware
```

[   12.264280] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   12.297618] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   12.301306] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   12.340839] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   12.343228] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   12.346686] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```

*dmesg | grep wlan0* didn't return any results

Thanks for this continued help!

---

### Post by wildmanne39 on 2011-07-30
Hi, it look like you need to install firmware-b43-lpphy-installer after you remove firmware-b43-installer.

You can remove firmware-b43-installer by opening synaptic and type broadcom into the search window then remove it.

If you still do not have wired connection you can go to the link I am giving you and scroll down the page to where it says how to install without an internet connection and follow the directions, you already have the driver you just need the firmware-b43-lpphy-installer.
Thank you

---

### Post by chaozuper on 2011-07-31
I don't think I have *firmware-b43-installer* installed because I can't find it in synaptic or using the terminal. Also, I think you might have forgotten to put in the link. Thanks for helping this much so far!

---

### Post by wildmanne39 on 2011-07-31
Hi, your right the link is not included, I am sorry about that.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)
Do you have a wired connection now? if so you do not need the link.
Thank you

---

### Post by chaozuper on 2011-07-31
Hi again. I followed the instructions in your link (seeing as my wired connection still isn't working) but still no luck. Also, after following the instructions, I couldn't find* firmware-b43-ipphy-installer *in synaptic. Thank you for the continued support.

---

### Post by wildmanne39 on 2011-07-31
Hi, when you open synaptic do you see b43fwcutter?

If so while you are in synaptic click on settings,repositories,where it says installable from cdrom put a check by cdrom then put the ubuntu cd in your drive after if loads close that window and reload synaptic and you should then be able to install firmware-b43-ipphy-installer in synaptic from the cd.
Thank you

---

### Post by nm_geo on 2011-07-31
Guys I think we can use the instructions and b43.zip chili555 gave last week. I am pretty sure chaozuper needs the firmware-b43-installer not the low power firmware.

Try this link and follow message #21 by chili it should work read closely and follow each line.
[http://ubuntuforums.org/showthread.php?p=11075482](http://ubuntuforums.org/showthread.php?p=11075482)

---

