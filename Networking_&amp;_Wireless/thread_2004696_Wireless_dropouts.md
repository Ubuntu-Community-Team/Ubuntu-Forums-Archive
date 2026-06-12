---
title: "Wireless dropouts"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by branchi on 2012-06-16
I have lubuntu 12.04 with wireless card D-Link PCI DWL-G510 (chipset RT3060).
Running iwconfig shows something like this: Ralink STA Nickname:"RT3562STA"
Installation went fine and I got it working, but now I'm experiencing occasional dropouts.
I googled and tried few tweaks with no success (setting MTU to 1500
and disabling IPv6).
I also tried making changes to /usr/lib/pm-utils/power.d/wireless like this post suggests: [http://askubuntu.com/questions/84959/ralink-rt3060-driver-not-working](http://askubuntu.com/questions/84959/ralink-rt3060-driver-not-working)
It didn't work.
I see that some people had success using wicd instead gnome-network-manager.
Before I do that, I thought I might find something here.
Attached you can find output of dmesg, right after one dropout.

---

### Post by praseodym on 2012-06-16
Please show the outputs of:

```
lspci -nnk | grep -iA2 net
iwconfig
lsmod
rfkill list
sudo iwlist scan
```
Try pure WPA2-AES encryption.

---

### Post by branchi on 2012-06-16
Praseodym, thank you for your reply.
Here are the outputs you requested.
Link was up and stable at the time of issuing commands.

lspci -nnk | grep -iA2 net

```
01:07.0 Network controller [0280]: Ralink corp. RT3060 Wireless 802.11n 1T/1R [1814:3060]
	Subsystem: D-Link System Inc Device [1186:3c44]
	Kernel driver in use: rt2860
--
01:0c.0 Ethernet controller [0200]: Intel Corporation 82540EM Gigabit Ethernet Controller [8086:100e] (rev 02)
	Subsystem: Dell Optiplex GX270 [1028:0151]
	Kernel driver in use: e1000
```

iwconfig

```
lo        no wireless extensions.

ra0       Ralink STA  ESSID:"Thom_D006714"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:24:D1:88:A3:14   
          Bit Rate=24 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=56/100  Signal level:-80 dBm  Noise level:-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.
```

lsmod

```
Module                  Size  Used by
snd_hrtimer            12648  1 
dm_crypt               22528  0 
snd_intel8x0           33455  3 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80845  3 snd_intel8x0,snd_ac97_codec
dcdbas                 14098  0 
snd_seq_midi           13132  0 
rfcomm                 38139  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
ppdev                  12849  0 
snd_seq                51567  3 snd_seq_midi,snd_seq_midi_event
rt3562sta             878243  1 
snd_timer              28931  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  13 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
shpchp                 32325  0 
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
parport_pc             32114  1 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
i915                  414637  2 
e1000                 101693  0 
drm_kms_helper         45466  1 i915
drm                   197692  3 i915,drm_kms_helper
usbhid                 41906  0 
hid                    77367  1 usbhid
floppy                 60310  0 
i2c_algo_bit           13199  1 i915
video                  19068  1 i915

```

rfkill list - nothing comes out

sudo iwlist scan

```
lo        Interface doesn't support scanning.

ra0       Scan completed :
          Cell 01 - Address: 00:24:D1:88:A3:14
                    Protocol:802.11b/g
                    ESSID:"Thom_D006714"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:52/100  Signal level:-69 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:24:D1:7E:46:ED
                    Protocol:802.11b/g
                    ESSID:"ssvuk"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-82 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 03 - Address: 00:26:24:B8:05:FC
                    Protocol:802.11b/g
                    ESSID:"Kisjelica"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:18/100  Signal level:-83 dBm  Noise level:-78 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:0B:6B:0A:9B:E2
                    Protocol:802.11b/g
                    ESSID:"WiFiHR.Ferka1"
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:13/100  Signal level:-85 dBm  Noise level:-80 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
          Cell 05 - Address: 00:1D:68:B7:25:A1
                    Protocol:802.11b/g
                    ESSID:"Leo ferka"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:18/100  Signal level:-83 dBm  Noise level:-78 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

eth0      Interface doesn't support scanning.

```

---

### Post by praseodym on 2012-06-16
Change from mixed WPA/WPA2 to pure WPA2 encryption

---

### Post by branchi on 2012-06-16
I've seen that as possible solution, but I don't know how to do that.
I cannot seem to find it as an option.
I have only following options:
- WEP 40/128-bit Key (Hex or ASCII)
- WEP 128-bit Passphrase
- LEAP
- Dynamic WEP 802.1x
- WPA & WPA2 Personal
- WPA & WPA2 Enterprise

---

### Post by praseodym on 2012-06-16
These are the settings in the NM ("WPA&WPA2 Personal" should be used).

You need to change the settings in your router. Connect via cable and type the router IP in your browser.

---

### Post by branchi on 2012-06-17
My router has out of the box configuration like this:
- WPA disabled
- WPA-PSK enabled
- WPA2 disabled
- WPA2-PSK enabled

What is the exact combination of those settings you would suggest?

---

### Post by praseodym on 2012-06-17
I suggest "WPA2-PSK" only.

---

### Post by branchi on 2012-06-17
Also, I see TKIP+AES is set for encryption.
Should I use AES only instead?

---

### Post by branchi on 2012-06-17
Router configured for WPA2-PSK only, AES only.
I will see behavior in next couple of days...

---

### Post by branchi on 2012-06-20
After the change computer was running for about 32 hours during which there was constant download in progress.
No dropouts occurred.
After downloading, there was about 14 hours of very little browsing here and there, almost no wireless activity.
Some dropouts did occur, much like it was before changing router settings.
Any insights on this?

---

### Post by branchi on 2012-07-07
About 10 days ago I removed gnome network manager and installed wicd. After that I had only one dropout. Few times computer would boot without network connection, but that was resolved by a reboot.
I consider this matter solved - thank you for your effort!

---

### Post by linuxgeoff on 2013-03-08
> **branchi said:**
> About 10 days ago I removed gnome network manager and installed wicd. After that I had only one dropout. Few times computer would boot without network connection, but that was resolved by a reboot.
I consider this matter solved - thank you for your effort!

for the record - and for others who come searching after this problem.....my eee 900 used to drop out the wifi periodically (like every 2 minutes, for about 15sec each time - pretty much unusable, since i use that machine as a music player) - I was running eeebuntu and then xbuntu, and fixed the issue by setting the connection speed at a fixed value to stop it always jumping up to the highest rate and then having to reset when the signal dropped a tad.  

Somewhere in a recent upgrade to xubuntu. I started suffering the same problem again.  After tearing my hair out for months trying to find a new solution, I finally installed wicd and removed the gnome network manager.  It's not 100%, but it's waaaaay better (one drop out in about an hour, and then only for about 5 secs)  - and again useable.

Hope this helps others.

so - if Gnome network manager is so c**p, and there are others that work, why isi t included as a default in the all the distros?

---

