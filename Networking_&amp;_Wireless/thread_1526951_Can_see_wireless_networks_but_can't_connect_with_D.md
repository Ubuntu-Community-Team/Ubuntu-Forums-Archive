---
title: "Can see wireless networks but can't connect with Dell C400"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by ChzPlz on 2010-07-08
Hi - Ubuntu and linux rookie here, so please bear with me.

I've got a vintage Dell C400 with a fresh install of Ubuntu 10.04 (Lucid Lynx).  It has been fully patched with all available updates.  No other changes to the system.

Short version - I can see wireless networks, but I can't connect to anything.  My router is an Apple Airport Extreme, if that matters.  I've tried dropping all encryption and that didn't help.

I walked through the wifi troubleshooting guide here: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
...but that didn't resolve anything.

The Dell system information site says that my system was originally shipped with the following:  8U082	Card Wireless,Mini PCI, Internal,Agere Systems,2.4GHz   I have no reason to believe this has changed, but I haven't confirmed.

I see multiple wireless networks in the panel applet.  My network showed no security when I had it configured that way. I can't connect to it with WPA or with no encryption.  I can connect to it with other computers.  And I was able to connect to it with this D400 with Ubuntu - before I upgraded to Lucid.  I did a full wipe and reinstall rather than an upgrade.  I can't remember what I did to get wireless working previously, but I remember it was a frustrating process.  Not sure what step ultimately worked.

Here's some of the results from the wifi troubleshooting guide:
> nm-tool
- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             disconnected
  Default:           no
  HW Address:        00:02:2D:B8:37:07

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes

  Wireless Access Points 
<multiple access points listed, including mine>


> lshw -C network
8000000-2801ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:b8:37:07
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 multicast=yes wireless=IEEE 802.11b


> lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
michael_mic             1732  4 
ppdev                   5259  0 
orinoco_cs              8782  1 
orinoco                62841  1 orinoco_cs
cfg80211              126517  1 orinoco
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
pcmcia                 33024  1 orinoco_cs
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
joydev                  8708  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           20408  4 
i915                  285076  1 
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  4 orinoco_cs,pcmcia,yenta_socket,rsrc_nonstatic
drm_kms_helper         29297  1 i915
dell_wmi                1793  0 
soundcore               6620  1 snd
psmouse                63245  0 
intel_agp              24119  2 i915
dcdbas                  5422  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
serio_raw               3978  0 
drm                   162377  3 i915,drm_kms_helper
shpchp                 28820  0 
agpgart                31724  3 intel_agp,drm
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
3c59x                  31839  0 
mii                     4381  1 3c59x
floppy                 53016  0 


> sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"<my SSID was here>"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:12
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Any help would be greatly appreciated.

---

### Post by ChzPlz on 2010-07-11
Hmm... digging some more, I'm not seeing a wireless listing in the lspci results.  But the card is there, and the machine seems to know it exists, as NetworkManager is using it to see wireless networks.  Still can't connect to any of them though.

---

### Post by ChzPlz on 2010-07-17
bump/help!

---

### Post by ixpl on 2010-07-17
Hello,  Could you post the output of lspci?  Is it possible to connect the D400 up with a patch cable to see if there are restricted drivers available?

---

### Post by ChzPlz on 2010-07-17
> **ixpl said:**
> Hello,  Could you post the output of lspci?  Is it possible to connect the D400 up with a patch cable to see if there are restricted drivers available?

Thanks for responding!

> lspci
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:01.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
02:03.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)


I have it connected via ethernet, have checked the "proprietary drivers for devices (restricted)" option, and installed all available updates.  If I launch System->Admin->Hardware Drivers it says "no proprietary drivers are in use on this system".

---

### Post by ixpl on 2010-07-17
is that card plugged in via pcmcia or usb? your'e right it doesn't show up in lspci unless it's the tornado one but I think that is eth0. also check for any wifi toggles on the outside of the laptop. you could also try ```
#iwlist eth1 scan
```

---

### Post by laithbsoul on 2010-07-17
just thought I'd chime in here to say try wicd instead of the default ubuntu network manager in my opinion it works better I've had many various problems with ubuntu's default network manager

---

### Post by ixpl on 2010-07-17
wicd is a great tool and definately worth taking a look. Make sure to check in the "other networks" part in the nm applet drop down. I think it tends to put unencrypted ap's in there.

---

### Post by ChzPlz on 2010-07-17
> **ixpl said:**
> is that card plugged in via pcmcia or usb? your'e right it doesn't show up in lspci unless it's the tornado one but I think that is eth0. also check for any wifi toggles on the outside of the laptop. you could also try ```
#iwlist eth1 scan
```

The wireless card is internal, so def not USB.  No hardware toggles or softkeys to enable/disable wifi on this machine.

> iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:1B:63:2C:92:21
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-37 dBm  
                    Encryption key:on
                    ESSID:"<<my ssid was here>>"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000002f91f19474
                    Extra: Last beacon: 10956ms ago
                    IE: Unknown: 000A736A70416972506F7274
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 0706434120010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201010F0003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301680120

...other networks were listed after mine.



Note that I turned security back on my router, but I wasn't able to connect even when it was disabled.  I can disable all the security and run this again if that'd help.

---

### Post by ChzPlz on 2010-07-17
> **ixpl said:**
> wicd is a great tool and definately worth taking a look. Make sure to check in the "other networks" part in the nm applet drop down. I think it tends to put unencrypted ap's in there.

Will give this a try and respond - thx!

---

### Post by sleezy2 on 2011-04-18
Hi all, i have just got a C400 in a job lot, (cost me the massive sum of £5) it was setup on win95 and had no wireless card in it.
I installed a card from a packard bell "R" series and tried it on netbook ubuntu, it didnt see the wireless, so i installed Mint 8 which is built on ubuntu, and it found it and now works a treat.
So i decided to try a few other cards in it and it picked up on the Intel 2200 and the Broadcom BCM94306 too without any adjustments.
There was no need to install any driver or use Ndiswrapper or whatever its called, and by the way i am a bit of a newbie to linux and didnt really know what i was doing, and i dont really understand anything to do with command lines or programming either.
I hope this helps someone.

---

### Post by josephmills on 2011-04-18
hi there could we see a ```
rfkill list all 
``` thanks

---

### Post by roschell on 2011-04-30
Hi, I have here the same machine and can not connect to the net either. However, with other c400 have no problems to get onto the net through wired connection. 

What do you think seems to be the issue? Is there hardware problem or other?

Thanks

---

