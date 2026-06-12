---
title: "[SOLVED] A180 not locking on 99% signal channels"
date: 2008-10-09
forum: Mythbuntu
---

### Post by biggyfred on 2008-10-09
This thread is a continuation of the one I started this morning here: [http://ubuntuforums.org/showthread.php?t=942535](http://ubuntuforums.org/showthread.php?t=942535)

Last post:

> **newlinux said:**
> Mine show up as an air2pc v2 when I set mine up in 8.04 for the frontend ID, so that is okay. All of your outputs look in place. I assume you only blacklisted saa7134 not saa7134-dvb? You need saa7134-dvb, from your lsmod that is in place. I actually did not need to blacklist saa7134 either.

The additional information I need is all of your myth card setup and scan settings, what type of signal you are trying tune (OTA ATSC or QAM)? 

Aside from that, the next thing to do would be to test the card outside of myth using dvb-utils.
```

sudo apt-get install dvb-utils
scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.mplayer/channels.conf

```
(or use the QAM scan file if you are using QAM)

then you can look in your channels.conf file for channel names (what is before the first colon) and do:
```

mplayer dvb://channel

```
If nothing shows up in your channels.conf file it we'll troubleshoot that...

First off, I'm only looking for OTA ATSC connections. I have no cable and no intention of getting it. Also, I meant that I had put saa7134-dvb in /etc/modules. My bad on those. I should have caught those in the subsequent post edits.

So, I used the dvb-utils, scanned, and got some channels! Strangely, it passed over my strongest signals and seemed to catch random channels. The only correlation I saw was that they were typically weak, with none over 75% strength. 

Here's my channels.conf from the scan:

```

Smile of a Child:533028615:8VSB:113:116:7
Enlace:533028615:8VSB:97:100:6
JCTV:533028615:8VSB:81:84:5
The Church Channel:533028615:8VSB:65:68:4
TBN:533028615:8VSB:49:52:3
KETH Trinity Broadcasting Network:533028615:8VSB:0:0:65535
KRIVDT ·:551028615:8VSB:49:52:3
[0003]:575028615:8VSB:49:52:3
[0001]:575028615:8VSB:0:0:1
KTBU-DT:641028615:8VSB:49:53:3
KZJL-DT:653028615:8VSB:49:52:1
KTMD-DT:677028615:8VSB:49:52:3

```
Aside from a healthy dose of the Jesus channels and the local Fox affiliate (KRIV), I didn't even know the rest existed. I guess my question has become how do I grab those channels that aren't getting locked? The signal strength is there, the signal/noise ration is good, they just aren't getting grabbed by the tuner. I went looking for a channels.conf to crib from, but didn't find a Houston OTA one out there. 

I'd also like to thank newlinux. For the first time in my life, I actually messaged someone looking for help. He answered, and I'm eternally grateful for his time and the time of strangers. I put in a couple hours of support this morning in the hardware forums as penance :)

As for the myth card setup, I'm not sure I get your meaning. These are the setting I have in place in the mythtv backened relevant to the card (as far as I can tell):

Under General->Locale->TV Format = NTSC
Under General->Locale->VBI Format = None
Under General->Locale->Channel Frequency Table = us-bcast
Under Capture Cards->Capture Card Setup->Card Type = DVB
Under Capture Cards->Capture Card Setup->Signal Timeout->3000
Under Capture Cards->Capture Card Setup->Tuning Timeout->5500
Under Video Sources->Listings Grabber-> Schedules Direct
Under Video Sources->Data Direct Lineup->My zip code
Under Video Sources->Channel Frequency Table->default (I chanted this to us-bcast and rescanned with no changes)

---

### Post by newlinux on 2008-10-09
Your scan settings under input connections will be useful. Are you still unable to get any locks in mythtv?

Looks like your card is at least working though, so that's a good step. OTA can be a little tricky. Are you using an indoor antenna or is it connected to an outdoor system?

---

### Post by SiHa on 2008-10-10
One thought - perhaps your signal is too strong? I guess you're using an amplifier, it might be that the signal is being over-amplified, and the strongest signals are getting so distorted that your card can't get a lock.

On my setup, all signals are clean with good reception and low BER @ ~60%

If you are using an amplifier, the signal is just too weak without it and you can't adjust the gain, try putting a passive splitter in the line (if you have one) **before** the amp. That will knock a few dB off and reduce the amplified signal to distortion-free levels (if indeed that is the problem).

---

### Post by biggyfred on 2008-10-12
I'm out of town until tomorrow. 

Being from Houston, I was forced out of my apartment due to storm damage. I just moved WAAAAY closer to town, with my OTA signals now less than 10 miles away. I am using a pretty gnarly little amp that I was using when I was farther out on an indoor antenna. I'm really excited to see if that's the problem, since it was the strong signals that weren't being caught. KRIV, the one channel I did catch, is the farthest away from me. I'll test tomrrow and report back.

Thanks to both of you for the ideas and help. Can't say it enough.

---

### Post by agamotto on 2008-10-12
> **biggyfred said:**
> I'm out of town until tomorrow. 

Being from Houston, I was forced out of my apartment due to storm damage. I just moved WAAAAY closer to town, with my OTA signals now less than 10 miles away. I am using a pretty gnarly little amp that I was using when I was farther out on an indoor antenna. I'm really excited to see if that's the problem, since it was the strong signals that weren't being caught. KRIV, the one channel I did catch, is the farthest away from me. I'll test tomrrow and report back.

Thanks to both of you for the ideas and help. Can't say it enough.

It definitely sounds as if your signals are swamping the antenna.  Turn off the amp, and rescan.  You should be pleasantly surprised.

---

### Post by biggyfred on 2008-10-13
Well, my well intentioned brother in law thought he would tinker and hosed the machine. No biggie. A quick reinstallation of Mythbuntu, drivers, and all that jazz gets me back to square one. I yank off the amp and start scanning. No locks at all this time, not even the ones I got before.

Hmmm.

I start nosing back around in all the usual places and noticed a new entry on my dmesg:

```
[   32.122800] saa7133[0]: subsystem: 1461:1044, board: AVerMedia AVerTVHD MCE A180 [card=75,autodetected]
[   32.122807] saa7133[0]: board init: gpio is 110400
[   32.257677] saa7133[0]: i2c eeprom 00: 61 14 44 10 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   32.257684] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 00 00 00 00 00 00 00 00 00 00
[   32.257690] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 06 ff 01 11 00 00 00 00
[   32.257695] saa7133[0]: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   32.257700] saa7133[0]: i2c eeprom 40: ff 64 00 c2 14 16 ff ff 00 00 00 00 00 00 00 00
[   32.257706] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.257711] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.257716] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   32.259663] saa7133[0]: registered device video0 [v4l2]
[   32.259680] saa7133[0]: registered device vbi0
[   32.260243] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   32.260246] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 17
[   32.260265] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   32.292382] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   32.324891] saa7134 ALSA driver for DMA sound loaded
[   32.324914] saa7133[0]/alsa: saa7133[0] at 0xfddfe000 irq 22 registered as card -2
[   32.409531] nxt200x: NXT2004 Detected
[   32.432662] DVB: registering new adapter (saa7133[0])
[   32.432668] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   32.437500] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   33.216496] nxt2004: Waiting for firmware upload(2)...
**[   34.185030] lp: driver loaded but no devices found**
[   34.807103] nxt2004: Firmware upload complete[/quote]

```
I'm wondering if the line, second from the bottom, could be a fascinating new issue for me. A google search for it brings up mostly wifi and video card issues with the occasional sound problem, but I didn't see much in the way of resolving it. ls -l /dev/dvb/adapter0, lspci, and lsmod all come back as before. 

 Anyone run into that message before? Any tips on getting a device found?

Thanks again all.

---

### Post by biggyfred on 2008-10-13
Unloading lp makes the message go away. Doh. Nothing like a little unrelated madness to make half your day disappear in a puff of smoke.

---

### Post by newlinux on 2008-10-13
so are your scans working again? Are you using the scan command or mplayer to scan?

---

### Post by biggyfred on 2008-10-13
> **newlinux said:**
> so are your scans working again? Are you using the scan command or mplayer to scan?
Hey again. Read your thread from 2 years ago when you were fighting this sucker and the Kworld. I'm hoping I can similarly look back from a victory instead of my current predicament. Really, I can't imagine anything more satisfying than bashing the tuner to pieces Office Space style. 

So here's my scan:
```

scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 57028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 57028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 63028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 63028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 69028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 69028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 79028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 79028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 85028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 85028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 177028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 177028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 183028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 183028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 189028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 189028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 195028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 195028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 201028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 201028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 207028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 207028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 213028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 213028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 473028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 473028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 479028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 479028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 485028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 485028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 491028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 491028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 497028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 497028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 503028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 509028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 509028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 515028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 515028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 521028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 521028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 527028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 527028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 533028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 539028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 539028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 545028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 545028615:8VSB (tuning failed)
etc.
etc.

```
And the usual suspects:
dmesg:
```
[   30.327851] saa7133[0]: found at 0000:03:0a.0, rev: 209, irq: 22, latency: 84, mmio: 0xfdbfe000
[   30.327856] saa7133[0]: subsystem: 1461:1044, board: AVerMedia AVerTVHD MCE A180 [card=75,autodetected]
[   30.327863] saa7133[0]: board init: gpio is 10400
[   30.460014] saa7133[0]: i2c eeprom 00: 61 14 44 10 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   30.460022] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 00 00 00 00 00 00 00 00 00 00
[   30.460027] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 06 ff 01 11 00 00 00 00
[   30.460032] saa7133[0]: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   30.460037] saa7133[0]: i2c eeprom 40: ff 64 00 c2 14 16 ff ff 00 00 00 00 00 00 00 00
[   30.460042] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.460047] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.460052] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.462325] saa7133[0]: registered device video0 [v4l2]
[   30.462342] saa7133[0]: registered device vbi0
[   30.462905] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 22
[   30.462908] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [AAZA] -> GSI 22 (level, low) -> IRQ 17
[   30.462927] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   30.498798] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   30.534502] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   30.534507] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC5] -> GSI 16 (level, low) -> IRQ 21
[   30.534514] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   30.534695] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   30.546858] saa7134 ALSA driver for DMA sound loaded
[   30.546882] saa7133[0]/alsa: saa7133[0] at 0xfdbfe000 irq 22 registered as card -2
[   30.631844] nxt200x: NXT2004 Detected
[   30.654714] DVB: registering new adapter (saa7133[0])
[   30.654719] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   30.661715] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   31.362698] nxt2004: Waiting for firmware upload(2)...
[   32.408355] lp: driver loaded but no devices found
[   32.937669] nxt2004: Firmware upload complete

```
lspci -vnn:
```
03:0a.0 Multimedia controller [0480]: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
	Subsystem: Avermedia Technologies Inc AVerTVHD MCE A180 [1461:1044]
	Flags: bus master, medium devsel, latency 84, IRQ 22
	Memory at fdbfe000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>

```
ls -l /dev/dvb/adapter0:
```
crw-rw----+ 1 root video 212, 4 2008-10-13 18:15 demux0
crw-rw----+ 1 root video 212, 5 2008-10-13 18:15 dvr0
crw-rw----+ 1 root video 212, 3 2008-10-13 18:15 frontend0
crw-rw----+ 1 root video 212, 7 2008-10-13 18:15 net0

```

lsmod |grep saa:
```

saa7134_dvb            16652  1 
videobuf_dvb            7812  1 saa7134_dvb
saa7134_alsa           15424  0 
tda1004x               16900  1 saa7134_dvb
snd_pcm                78596  3 saa7134_alsa,snd_hda_intel,snd_pcm_oss
saa7134               131920  2 saa7134_dvb,saa7134_alsa
compat_ioctl32          2304  1 saa7134
videobuf_dma_sg        14980  4 saa7134_dvb,videobuf_dvb,saa7134_alsa,saa7134
videobuf_core          18820  3 videobuf_dvb,saa7134,videobuf_dma_sg
ir_kbd_i2c             10768  1 saa7134
ir_common              36100  2 saa7134,ir_kbd_i2c
videodev               29440  1 saa7134
v4l2_common            18304  2 saa7134,videodev
v4l1_compat            15492  2 saa7134,videodev
snd                    56996  14 saa7134_alsa,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_core               24832  8 dvb_pll,nxt200x,saa7134_dvb,tda1004x,nvidia,saa7134,ir_kbd_i2c,i2c_nforce2

```

Just. Don't. Get. What's. Going. On. Here.

---

### Post by biggyfred on 2008-10-27
The bug I've experienced is apparently a known bug, though the only documentation I've found is a single line at the bottom of the mythtv A180 page. I must have read that page 40 times and never saw it. I cold restarted the computer and my channels popped in immediately. After a week or so they went back out, I cold started again a couple of times again and they popped back in, so I'm not left with much but believing that this is that bug.

> If you can't tune any stations, try shutting down the computer, waiting a few seconds, and starting it up again. The AVerTV HD A180 in at least one wiki contributor's system can get into a state in which it doesn't work (or at least in which MythTV can't use it). Even a warm reset won't help in this case; only a cold start will return the card to useability.

I hope this helps someone else. Other than this bummer of a bug, it's a great card... if it can still qualify as such. 

Thanks to everyone that posted in this thread. I really appreciate the time you guys put in to going over this with me.

edit: just to tie up any loose ends for future readers:

The card is identified as an Air2PC card in the Capture Card setup under DVB. This works fine for me. 
No blacklisting was necessary to get the card working. Getting the firmware working and doing a modprobe saa7134-dvb was enough to kick the card into gear. 
I still had trouble with Myth scanning channels, so I used the dvb-tools as mentioned earlier then used the channels.conf in mythtv and they came right in. 

If anyone else has problems with this card, feel free to message me or post in this thread, though messaging will probably catch my attention faster. I've been the world and back with this card, so I can probably help out if you need it.

---

### Post by climbd on 2008-11-12
I'm having similar problems getting this card to tune in channels even though signal is 99%.  I had it working under Gutsy and it broke when I upgraded to Hardy Heron. After struggling to get it up and running on Hardy, i just upgraded to Ibex out of frustration but that didn't change anything either... 

My scan:
```
scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 57028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 57028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 63028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 63028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 69028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 69028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 79028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 79028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 85028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 85028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 177028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 177028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 183028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 183028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 189028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 189028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 195028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 195028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 201028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 201028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 207028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 207028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 213028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 213028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 473028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 473028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 479028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 479028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 485028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 485028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 491028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 491028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 497028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 497028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 503028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 503028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 509028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 509028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 515028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 521028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 527028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 527028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 533028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 533028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 539028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 539028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 545028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 551028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 551028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 557028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 557028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 563028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 563028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 569028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 569028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 575028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 575028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 581028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 581028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 587028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 587028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 593028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 599028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 599028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 605028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 605028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 611028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 611028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 617028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 617028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 623028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 623028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 629028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 629028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 635028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 635028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 641028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 641028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 647028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 647028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 653028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 653028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 659028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 659028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 665028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 665028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 671028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 671028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 677028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 677028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 683028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 683028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 689028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 695028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 695028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 701028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 701028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 707028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 707028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 713028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 713028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 719028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 719028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 725028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 725028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 731028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 731028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 737028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 737028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 743028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 743028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 749028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 749028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 755028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 755028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 761028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 761028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 767028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 767028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 773028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 773028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 779028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 779028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 785028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 785028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 791028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 791028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 797028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 797028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 803028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 803028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
dumping lists (0 services)
Done.
```

dmesg
```
[   19.708657] saa7130/34: v4l2 driver version 0.2.14 loaded
[   19.708752] saa7134 0000:02:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.708766] saa7133[0]: found at 0000:02:01.0, rev: 209, irq: 22, latency: 64, mmio: 0xfbfcb000
[   19.708780] saa7133[0]: subsystem: 1461:1044, board: AVerMedia AVerTVHD MCE A180 [card=75,autodetected]
[   19.708797] saa7133[0]: board init: gpio is 10400
[   19.871582] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   19.897351] saa7133[0]: i2c eeprom 00: 61 14 44 10 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   19.897386] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 00 00 00 00 00 00 00 00 00 00
[   19.897418] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 ff 01 03 06 ff 01 11 00 00 00 00
[   19.897450] saa7133[0]: i2c eeprom 30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   19.897481] saa7133[0]: i2c eeprom 40: ff 64 00 c2 14 16 ff ff 00 00 00 00 00 00 00 00
[   19.897512] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.897544] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.897575] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.897607] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.897638] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.897670] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.897701] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.897733] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.897764] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.897795] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.897826] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   19.899629] saa7133[0]: registered device video0 [v4l2]
[   19.899757] saa7133[0]: registered device vbi0
[   20.544060] nxt200x: NXT2004 Detected
[   20.568379] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   20.667384] DVB: registering new adapter (saa7133[0])
[   20.667394] DVB: registering frontend 0 (Nextwave NXT200X VSB/QAM frontend)...
[   20.676054] nxt2004: Waiting for firmware upload (dvb-fe-nxt2004.fw)...
[   20.676065] firmware: requesting dvb-fe-nxt2004.fw
[   20.778191] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   20.778224] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   21.204588] intel8x0_measure_ac97_clock: measured 56188 usecs
[   21.204598] intel8x0: clocking to 48000
[   21.846865] end_request: I/O error, dev sr0, sector 13531024
[   21.846877] Buffer I/O error on device sr0, logical block 1691378
[   21.929704] end_request: I/O error, dev sr0, sector 13531024
[   21.929715] Buffer I/O error on device sr0, logical block 1691378
[   22.472971] nxt2004: Waiting for firmware upload(2)...
[   23.698610] lp0: using parport0 (interrupt-driven).
[   24.080034] nxt2004: Firmware upload complete
```

lspci -vnn
```
02:01.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
Subsystem: Avermedia Technologies Inc Device [1461:1044]
Flags: bus master, medium devsel, latency 64, IRQ 22
Memory at fbfcb000 (32-bit, non-prefetchable) [size=2K]
Capabilities: <access denied>
Kernel driver in use: saa7134
Kernel modules: saa7134
```

ls -l /dev/dvb/adapter0
```
total 0
crw-rw----+ 1 root video 212, 4 2008-11-12 12:09 demux0
crw-rw----+ 1 root video 212, 5 2008-11-12 12:09 dvr0
crw-rw----+ 1 root video 212, 3 2008-11-12 12:09 frontend0
crw-rw----+ 1 root video 212, 7 2008-11-12 12:09 net0
```


lsmod |grep saa
```
saa7134_dvb            27532  0 
videobuf_dvb           12932  1 saa7134_dvb
dvb_core               86272  2 saa7134_dvb,videobuf_dvb
saa7134               147284  1 saa7134_dvb
ir_common              48132  1 saa7134
videodev               41344  1 saa7134
compat_ioctl32          9344  1 saa7134
v4l2_common            19840  1 saa7134
videobuf_dma_sg        20612  2 saa7134_dvb,saa7134
videobuf_core          26628  3 videobuf_dvb,saa7134,videobuf_dma_sg
tveeprom               20228  1 saa7134
i2c_core               31892  7 dvb_pll,nxt200x,saa7134_dvb,saa7134,v4l2_common,tveeprom,nvidia
```

Any assistance would be greatly appreciated.

---

### Post by climbd on 2008-11-14
I've tried several cold restarts with varying amounts of down time but without luck. Doh!  What am I missing?!?

---

### Post by climbd on 2008-11-16
I just remembered that at the same time I initialy made the upgrade to Hardy which I attributed to killing my reception via the A180, I also hooked up a new antenna that worked a lot better than the previous one (through the TV's tuner), so I'm curious if the signal is too strong as SiHa suggested.  I'm going to pick up an attenuator today and see if weakening the signal will fix it.  At times I can get it to register a few channels, but I'm guessing those are the ones with weaker signals...

---

### Post by climbd on 2008-11-17
I couldn't find a attenuator, but also don't think that would help... It's probably something obvious, but I'm obviously not seeing it.

---

### Post by biggyfred on 2008-11-19
Perhaps expanding on my situation will help push you in the right direction.

I had a TV with built in tuner and rabbit ears next to it (in another room) as my test base. I made the following assumptions:

[LIST]
[*]Signal was good (but not great) in the other room, so it was reasonable to assume it would be relatively similar in my living room
[*]Using the same antenna, it would reasonably catch the same signal (give or take)
[*]My drivers and firmware were loading correctly
[*]The cable from the card to the antenna was good (I used two separate ones tested on the test base setup in the other room)
[*]Being so close to the broadcasters (10 miles or so) meant that any signal issues would be a factor other than signal strength
[/LIST]

Here's where it got sticky for me. Before realizing that the "no lock" bug was out there, I figured it was either a bad card (that had worked previously and died, it happens but not particularly likely) or it might just be my house. Having literally nothing left to test but antenna position, I used a preinstalled coax in the house that went to a dish on the roof. I crawled my butt up on the roof, disconnected the dish, and stuck my indoor/outdoor HDTV rabbit ears out there (same one from the test bed). Came back in, retested, and it didn't work. I shut down the machine and began working under the assumption that the card and/or drivers were bad, even though newlinux has said it was good (based on my dmesg, etc. that you've also posted and look good to my noobish eyes). I just didn't have anything left to test and so had to assume that my assumptions were wrong.

I had had a scan when a couple of channels did come through though. I wondered why I had caught an HD channel, but just once. I went back to the machine, turned it on, and scanned again. Everything popped in perfectly and I dumped 31 channels using the same dvb-scan tools that you used. A few days later, I turned on MythTV to find the channels refusing to lock. A cold restart and they popped right in. 

My problem was two issues. One, the no lock bug reared its ugly head and I have no way of deciphering which times that came into play. At the same time, it's obvious that my assumption that my signal was good based on my test bed was wrong. It was showing 99% 91% on scans, but not locking. I believe that over half the time the problem was signal, with a sprinkle of no lock bug to really make life tough.

Just as an aside, most of my channels came in during the second half of the scan. More than once I cut it off about half way through believing that was an indicator that nothing would come in. I was wrong. And I never caught anything scanning in MythTV until I brought in the channels.conf from dvb-scan. After import, they worked just fine. 

My apologies if that was really wordy, but I always feel like you can't write enough about this kind of stuff when trying to help other people. I hope this helps in some way. And sorry about taking so long to reply.

---

