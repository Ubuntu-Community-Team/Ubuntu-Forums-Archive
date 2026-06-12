---
title: "Wireless is too slow."
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by vitalka on 2009-08-26
Hello.

My wireless card is not working at full speed as it should. For some reason my speed can go up to around 100kb/s, which is not even a single Mb. It's not even up to speed with my Internet connection which is up to 10Mbps. I do get full speed over ethernet though.

I'm running Windows 7 RC1 and Ubuntu 9.04 on my Inspiron 1520 laptop. Wireless works just fine under windows, but not in Ubuntu.

my wireless card:
Intel(R) PRO/Wireless 3945ABG

iwconfig output:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"SKYNET"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:10:34:27:DF   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=57/100  Signal level:-74 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Any thoughts?

---

### Post by .kkursor on 2009-08-26
Which driver do you use for your card? Maybe there is an update...
Show your lspci | grep Ethernet and lsmod

I have Atheros-based card, with ath5k (and ZTE access point) it allows to transmit/receive data to/from my FreeBSD-based home server with speeds up to 1 MB/s (depends on distance). I use IEEE802.11g and WPA2 encryption.

---

### Post by Luca_turicci on 2009-08-26
Did it work well before? have you done any kernel updates?

---

### Post by vitalka on 2009-08-26
Wireless worked great when I was running Open Suse 10.3, but that was a year ago. I was running Windows XP up until a week ago and it worked just fine too.

I did run Ubuntu updates after installation and a new kernel was installed.
old kernel : 2.6.28-11-generic
new kernel: 2.6.28-15-generic

Wireless is slow under both kernels.

I checked for a driver on Intel's website and kernel 2.6.24 and higher have my driver included.

Here are some command line outputs:
```

lspci | grep Ethernet
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

lspci | grep Wireless
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

lsmode
Module                  Size  Used by
aes_i586               15744  1 
aes_generic            35880  1 aes_i586
binfmt_misc            16776  1 
ppdev                  15620  0 
input_polldev          11912  0 
joydev                 18368  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
arc4                    9856  2 
snd_hda_intel         435636  3 
ecb                    10752  2 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
iwl3945                97912  0 
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              217208  1 iwl3945
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class              12036  1 iwl3945
psmouse                61972  0 
sdhci_pci              15232  0 
intel_agp              34108  0 
dcdbas                 15264  0 
video                  25360  6 
nvidia               7233756  30 
pcspkr                 10496  0 
serio_raw              13316  0 
sdhci                  23940  1 sdhci_pci
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
cfg80211               38032  2 iwl3945,mac80211
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                 11008  1 video
agpgart                42696  2 intel_agp,nvidia
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usbhid                 42336  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
b44                    35984  0 
ssb                    41220  1 b44
mii                    13312  1 b44
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```
My wireless at home uses WPA2 encryption, disabling it does not change anything.

---

### Post by vitalka on 2009-08-26
I ran some testing using Open Suse 10.3 Live CD and Ubuntu 8.04 LTS Live CD:

Open Suse 10.3 - 7.5Mbps to 9Mbps (this I can live with - kernel 2.6.22.5-default)
Ubuntu 8.04 - 2Mbps and less (kernel 2.6.24-24-generic)
Ubuntu 9.04 - 1Mbps and less (kernel 2.6.28-11-generic & after update 2.6.28-15-generic)

Test involved moving a 200MB folder, with files in it, across wireless. I monitored speed using System Monitor that comes with Gnome and Wireless monitor that comes with dd-wrt firmware on my router.

I'm going to try Open Suse 11.1 Live CD, so I'll update my findings.

---

### Post by vitalka on 2009-08-26
Here is a list of all live cd distros I have tried (except Ubuntu 9.04 which is installed):

Open Suse 10.3 - 7.5Mbps to 9Mbps (this I can live with - kernel 2.6.22.5-default)
Ubuntu 8.04 - 2Mbps and less (kernel 2.6.24-24-generic)
Ubuntu 9.04 - 1Mbps and less (kernel 2.6.28-11-generic & after update 2.6.28-15-generic)
Open Suse 11.1 - 1Mbps and less (kernel 2.6.27.7-9-default)
Linux Mint 7 - 1Mbps and less (kernel 2.6.28-11-generic)
Mandirva 2009.1 - 1 Mbps and less (kernel 2.6.29.1-desktop586)

Open Suse 10.3 is the only one that worked. According to Intel, driver for my wireless card is included with the kernel since 2.6.24 and higher. I'm confused here. Did they include wrong driver?

Here is a link to Intel's page about the driver: [http://www.intellinuxwireless.org/](http://www.intellinuxwireless.org/)

---

### Post by vitalka on 2009-08-28
Well i looked around the web and it seems that its and issue with iwl3945 driver (suse10.3 uses ipw3945 I think, which is depreciated). Maybe there is some one out there who knows how to go around this driver's limitations?

I feel like I'm having a conversation with my self. I just need some some alcohol and a mirror now.

---

### Post by gronbaek on 2009-09-10
Hey vitalka. Sorry that I can't help you, just wanted to let you know I have exactly the same problem. Every thing looks fine, but min ping time to my wireless router is around 900 ms. Using Windows XP everything works fine.

---

### Post by Anthorn on 2010-11-09
The problem is that the default wireless manager only allows a wireless card / adapter to router speed of 1mbps. What fixed it for me was the instructions in the forum thread located at [http://peppermintos.net/viewtopic.php?f=39&t=311](http://peppermintos.net/viewtopic.php?f=39&t=311)

I now get 54mbps on wlan0

Also if you're in the U.K. on BT Total Broadband using the BT Home Hub 2, press and hold the "Wireless Association" button until all the lights go out, then release the button. It will take up to a couple of minutes for all the lights to be back on and then reconnect the wireless connection. Doing this tripled my speed according to different online tests to just under 8mbps

---

