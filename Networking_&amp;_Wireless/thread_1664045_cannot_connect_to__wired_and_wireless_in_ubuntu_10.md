---
title: "cannot connect to  wired and wireless in ubuntu 10.10 it tries to connect but fails"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by puneetgoyal on 2011-01-10
i am a newbie in linux world and have recently downloaded and installed ubuntu desktop 10.10
i cannot connect to both wired and wireless ethernet on my laptop
it tries to connect but fails in 30 seconds , it says"disconnected" while i am able to connect to the same in windows 

i have broadcom 4315 and i have tried both fwcutter and ndiswrapper but the problem persists .
the device id is 14e4:4315

kindly help me as i have been trying this for 2 days now but have not succeeded.](*,)

---

### Post by PatchesTheCaveman on 2011-01-11
Have you tried the STA driver?  Go to System > Administration > Additional Drivers (or Hardware Drivers on versions earlier than 10.10 Maverick Meerkat).  Select the *Broadcom STA wireless driver* and click Install.

---

### Post by puneetgoyal on 2011-01-12
i have also tried that option but an indexing error appears and nothing shows up in the drivers window ...

---

### Post by PatchesTheCaveman on 2011-01-12
Go to Applications > Accessories > Terminal and type the following and press Enter:
```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by puneetgoyal on 2011-01-12
this package was installed by default.
nevertheless i tried reinstalling it but it didnt help

---

### Post by PatchesTheCaveman on 2011-01-12
Okay, you might have conflicting drivers.

Copy/paste the output of:
```
lsmod
```

---

### Post by puneetgoyal on 2011-01-13
my apologies for late reply but i deleted the ubuntu partition and it (quite misteriously) swept two more drives with it.
now i am back after recovering all my data and i tried to install via ubuntu wubi...
but it too failed just when the bar reached 97% completion 
think i should create a new thread for this

---

### Post by PatchesTheCaveman on 2011-01-13
Yes.  The Installation help board is here:
[http://ubuntuforums.org/forumdisplay.php?f=333](http://ubuntuforums.org/forumdisplay.php?f=333)

---

### Post by puneetgoyal on 2011-01-27
i installed via wubi now and also installed sta drivers but the problem persists
stuck here

---

### Post by puneetgoyal on 2011-01-27
output of lsmod is 

 [FONT=&quot]Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_si3054     3440  1 
snd_hda_codec_realtek   217980  1 
joydev                  8735  0 
snd_hda_intel          22107  2 
lib80211_crypt_tkip     7736  0 
snd_hda_codec          87552  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
i915                  290938  2 
snd_pcm                71475  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  1 i915
snd_timer              19067  2 snd_pcm,snd_seq
drm                   168054  3 i915,drm_kms_helper
wl                   1959533  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                    9536  0 
sm_common               3285  1 r852
intel_agp              26360  2 i915
nand                   34905  2 r852,sm_common
nand_ids                2903  1 nand
nand_ecc                3938  1 nand
snd                    49006  14 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5168  1 i915
mtd                    18877  2 sm_common,nand
lib80211                5058  2 lib80211_crypt_tkip,wl
video                  18712  1 i915
output                  1883  1 video
soundcore                880  1 snd
psmouse                59033  0 
serio_raw               4022  0 
lp                      7342  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 drm,intel_agp
parport                31492  3 parport_pc,ppdev,lp
firewire_ohci          21106  0 
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci
firewire_core          46643  1 firewire_ohci
led_class               2633  1 sdhci
crc_itu_t               1383  1 firewire_core
tg3                   123310  0 
[/FONT]

---

### Post by puneetgoyal on 2011-02-03
i'm kinda stuck here plz help

---

### Post by Kegusa on 2011-02-03
Sounds awfully similar to my own problem. I have a BCM4306 card myself and it too can not connect to any AP. (It can detect them and iwlist gives a good info about all the neighbours AP's too..)

my dmesg is getting spammed with these messages while trying to connect. 

> [ 6610.362143] wlan0: direct probe to 00:1c:f0:54:d1:f7 (try 1)
[ 6610.560032] wlan0: direct probe to 00:1c:f0:54:d1:f7 (try 2)
[ 6610.760044] wlan0: direct probe to 00:1c:f0:54:d1:f7 (try 3)
[ 6610.960153] wlan0: direct probe to 00:1c:f0:54:d1:f7 timed out

I have tried both fwcutter and ndiswrapper, but havent tried the STA driver since it says it's not compatible with the 4306.

Can you show the output of dmesg here? 

> dmesg | grep YOUR_IFDEVICE | tail

*(in my case: dmesg | grep wlan0 | tail)*

---

### Post by Sternbergopolis on 2011-02-06
I'm having this same problem. I have a HP Compaq nx9010 laptop and installed Ubuntu 10.10 via Wubi. It installed perfectly. However, it sometimes fails to boot, and my main problem is the fact that it won't connect to my wireless internet because of missing firmware. I downloaded the driver off of the HP website and put it on a USB, and then tried to open it in Ubuntu. This failed. I have tried using ndiswrapper to open the driver, but I am not keen on code and I couldn't figure it out. I know that this is a common issue, so I hope there is a simple fix without a lot involved. I am not sure exactly what the name of my firmware is, but its Broadcom and works great in Windows XP and Vista. Please help!

---

### Post by brangkas on 2011-06-06
> **PatchesTheCaveman said:**
> Go to Applications > Accessories > Terminal and type the following and press Enter:
```
sudo apt-get install bcmwl-kernel-source
```

I got the same problem, and i tried your way and this is the result..

vanhombing@brangkas:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for vanhombing: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here (PCI id 14e4:1693)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

