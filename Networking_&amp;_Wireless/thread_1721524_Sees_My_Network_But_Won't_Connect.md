---
title: "Sees My Network But Won't Connect?"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by Funklink on 2011-04-04
Hello, I often post on this site and don't get answers to more complicated questions hut this one sounded simple enough for me to get responses. I have a computer running Ubuntu, I downloaded the Broadcom STA driver and enabled it. After that I had Internet all morning at the office. I came home and opened up my computer (it's a laptop, I simply close it to transport. Let me know if that's an issue) and sat down. I have a WEP network with a passwOrd at home as well, and I left clicked and went to Network Connects as I did last time and added my network and password ( should I be doing something else instead, am I doing it wrong?) I clicked on the Wireless Notification Icon and clicked my Network name after it says "Available" and the icon flashes a bit and says <Network Name> Disconnected. I do not understand, I had it running earlier....Anyway, any help is GREATLY appreciated. 

PS. I setup a wireless network without a password to test it and it didn't connect on my Ubuntu computer either...

---

### Post by fela on 2011-04-04
You don't need to go to network connections and add the network. You simply need to click the network in the dropdown menu.

It sounds like you entered the wrong password. Also, as a word of advice, use WPA2-PSK (or any WPA) instead of WEP - WEP can be hacked in 5 minutes :O

---

### Post by Funklink on 2011-04-04
I am using a open network right now just to see if I entered the password wrong and, as I had feared, I did not. Here's what I am doing :
----------------------------------------
Wireless Networks
   disconnected
          Available 
<Network Name Here>(STR)
<Other Network Here>(STR)

----------------------------------------

I click on <Network Name Here> and the icon at the top blinks a few times and then I get a notification message that says "Wireless Disconnected." 

Thanks anyway.

---

### Post by fela on 2011-04-04
This link might be of some use to you:

[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

Good luck

---

### Post by Funklink on 2011-04-04
I tried that and it didn't seem to help. I entered : lshw -C network. I scrolled down and got:

-*network

logical name: eth1 

and 

-*network

logical name: eth0.

Shouldn't it say wlan1 or something to that effect? I am truly lost.

---

### Post by IWantFroyo on 2011-04-04
```
ifconfig wlan0 up
```Then, for no key:
```
iwconfig wlan0 essid "YourNetworkName"
```For WEP HEX:
```
iwconfig wlan0 essid "YourNetworkName" key WEPKEY
```For WEP ASCII:
```
iwconfig wlan0 essid "YourNetworkName" key s:WPA/WPA2KEY
```

---

### Post by Funklink on 2011-04-04
I am going to try that in a second, thanks.

---

### Post by bkratz on 2011-04-04
> **Funklink said:**
> I tried that and it didn't seem to help. I entered : lshw -C network. I scrolled down and got:

-*network

logical name: eth1 

and 

-*network

logical name: eth0.

Shouldn't it say wlan1 or something to that effect? I am truly lost.



No your wireless network could be one of the eth names (usually the second one). You might post the output of 

```
sudo iwlist scan
```

and we can probably tell which it is.

PS maybe 

```
iwconfig
```

too

---

### Post by Funklink on 2011-04-04
I entered:

```
iwconfig wlan0 essid "MyNetworkName"
```

and got this:

----------------------------------------------------
iwconfig wlan0 essid "MyNetworkName"
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
----------------------------------------------------

---

### Post by Funklink on 2011-04-04
Upon entering:

```
sudo iwlist scan
```

I got this:

------------------------------------------------------------------------------------------
eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:11:D8:EB:29:D9
                    ESSID:"MyNetwork"
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:5/5  Signal level:-29 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:1C:F0:FD:C4:CE
                    ESSID:"MyNetwork2"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-66 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s

----------------------------------------------------------------------------------------

---

### Post by Funklink on 2011-04-04
Oops, those have got to come off....

---

### Post by Funklink on 2011-04-04
Upon typing in:

```
sudo iwlist scan
```I got:


eth0      Interface doesn't support scanning.

eth1      Scan completed :
     

     Cell 01 - Address: 00:11:D8:EB:29:D9
                    ESSID:"MyNetwork"
                    Mode:Managed
                    Frequency:2.432 GHz (Channel 5)
                    Quality:5/5  Signal level:-29 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 00:1C:F0:FD:C4:CE
                    ESSID:"MyNetwork2"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:4/5  Signal level:-66 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s

---

### Post by Funklink on 2011-04-04
When I enter:

```
iwconfig
```

I get:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

---

### Post by fela on 2011-04-04
Try ```
sudo iwconfig
```

EDIT: try this: ```
sudo iwconfig eth1 essid "MyNetworkName"
```

eth1, BTW, is your wireless card.

---

### Post by bkratz on 2011-04-04
> **Funklink said:**
> When I enter:

```
iwconfig
```

I get:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:199
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


well eth1 is your wireless, I think I would try (and post)


```
rfkill list
```

and if you get no output--

```
sudo apt-get install rfkill
```

then 
```
rfkill list
```

again

---

### Post by Funklink on 2011-04-04
```
rfkill list
```

: 

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by bkratz on 2011-04-04
> **Funklink said:**
> ```
rfkill list
```

: 

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no


Well that is good not blocked by either hardware or software. Looking at a few recent suspend/sleep/hibernate postings ( I just reread post 1).

---

### Post by Funklink on 2011-04-04
Okay...

---

### Post by bkratz on 2011-04-04
Been looking at this one

[http://ubuntuforums.org/showthread.php?t=1714938](http://ubuntuforums.org/showthread.php?t=1714938)

It is about wired rather than wireless, but it looks like we can follow a similar path

First thing would be to post the output of

lspci -nnk | grep -A3 Network

We will be looking at the module information (see posts 5 and 9)

---

### Post by Funklink on 2011-04-04
```
lspci - nnk | grep -A3 Network
```

lspci - nnk | grep -A3 Network
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file

---

### Post by Funklink on 2011-04-04
> **bkratz said:**
> Been looking at this one

[http://ubuntuforums.org/showthread.php?t=1714938](http://ubuntuforums.org/showthread.php?t=1714938)

It is about wired rather than wireless, but it looks like we can follow a similar path

First thing would be to post the output of

lspci -nnk | grep -A3 Network

We will be looking at the module information (see posts 5 and 9)

I did step 5

sudo /etc/init.d/networking restart and got:
 * Reconfiguring network interfaces...                                                                                                                       Ignoring unknown interface eth0=eth0.
                                                                                                                                                      [ OK ]

---

### Post by bkratz on 2011-04-04
Boy that sure doesn't look anything like what they got in the thread! It just looks like the manual listing for lspci. Is this device a usb one? Anyway, using the code tags, how about the output of 

lsmod

We will find those modules!

---

### Post by inkrypted on 2011-04-04
Have you rebooted since you got home? I used to have issues if I let the notebook sleep and then tried to connect that has not happened since I switched to WICD but I saw you refering to eth0 and eth1 as wireless network interfaces and i think that should be eth0 is wired and wlan0 is wireless. Another thing is does it connect and surf if connected via ethernet? This sounds alot like having the wrong wireless drivers installed. Is it a Broadcom adapter if so what chipset?

---

### Post by Funklink on 2011-04-04
After step 9:

```
 lspci -nnk | grep -A3 Network
```

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Kernel driver in use: wl
    Kernel modules: wl, ssb

```
 lspci -nnk | grep -A3 Ethernet 
```

09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
    Kernel driver in use: tg3
    Kernel modules: tg3
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

---

### Post by Funklink on 2011-04-04
That look better?

---

### Post by Funklink on 2011-04-04
@ Inkrypted. My laptop says it might be : "BCM94311MCG. Does that have anything to do with what you want?

---

### Post by bkratz on 2011-04-04
Boy I'll say back in a minute

---

### Post by Funklink on 2011-04-04
Is that a "L"smod or "I"smod?

Upon entering:

```
lsmod
```

I got:

Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
mmc_block               8258  2 
nls_utf8                1069  1 
isofs                  29250  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
dm_crypt               11331  0 
snd_hda_codec_idt      52010  1 
snd_hda_intel          22037  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
lib80211_crypt_tkip     7596  0 
snd_seq_oss            26722  0 
joydev                  8740  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
wl                   1959598  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_wmi                1793  0 
sdhci_pci               5470  0 
sdhci                  15462  1 sdhci_pci
lib80211                5046  2 lib80211_crypt_tkip,wl
ricoh_mmc               2923  0 
dell_laptop             6888  0 
lp                      7028  0 
led_class               2864  1 sdhci
snd                    54180  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dcdbas                  5422  1 dell_laptop
psmouse                63245  0 
serio_raw               3978  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
dm_raid45              81647  0 
xor                    15028  1 dm_raid45
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  287458  5 
ohci1394               26950  0 
drm_kms_helper         29329  1 i915
intel_agp              24375  2 i915
ieee1394               81181  1 ohci1394
drm                   162345  6 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
ahci                   32200  2 
tg3                   109324  0 
agpgart                31724  2 intel_agp,drm

---

### Post by bkratz on 2011-04-04
OK we are going to try to temporarily remove the module and reload it (nothing permanent though).

sudo rmmod wl
sudo modprobe wl

and then try to connect.

yes it was a lowercase L. But we got the same info from your second try.
See wl is listed there.

---

### Post by inkrypted on 2011-04-04
I know that the b43/bcm43xx drivers do not work for all chipsets so using an ndiswrapper for the drivers might be a better choice. Unless you already tried that.

---

### Post by Funklink on 2011-04-04
Thank you! How long will the connection last/will I have to do it again?

---

### Post by inkrypted on 2011-04-04
Written for 7.10 but I assume alot of the info would still be relavant.
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

---

### Post by bkratz on 2011-04-04
> **Funklink said:**
> Thank you! How long will the connection last/will I have to do it again?



Well it should reload when you reboot, but if not post back, if it does--congratulations! Please go to the thread tools above and mark as [solved] in case it helps someone else

---

### Post by Funklink on 2011-04-04
@ Inkrypted. Thanks anyway. I had already tried that. I love the help you can get from everyone here at the Ubuntu Forums. :D

---

### Post by Funklink on 2011-04-04
Okay, I am going to reboot now

---

### Post by inkrypted on 2011-04-04
Good luck I hope it sticks.

---

### Post by Funklink on 2011-04-04
Well, it stuck guys, so thanks a lot! I'm sure I'll be back here with another issue for some reason or another but I appreciate your help a ton. I am so happy now. :D

---

### Post by bkratz on 2011-04-04
> **Funklink said:**
> Well, it stuck guys, so thanks a lot! I'm sure I'll be back here with another issue for some reason or another but I appreciate your help a ton. I am so happy now. :D



Sure glad it worked out. If it happens again just the last two commands should help (the remove and modprobe). Anyway don't forget to mark as solved (see last post).

---

### Post by fela on 2011-04-04
Glad you managed to fix the problem :D

---

