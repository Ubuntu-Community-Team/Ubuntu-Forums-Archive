---
title: "Hauppauge Nova-T 500 &quot;deinitialized and disconnected&quot;"
date: 2009-04-09
forum: Mythbuntu
---

### Post by Raptor Ramjet on 2009-04-09
Hello,

I've just installed Mythbuntu 8.10 on a system with an EPIA EN15000G motherboard and a Hauppauge Nova-T 500 DVB PCI card (Model: WinTV-NOVA-TD-500, SL2-89-V3.0-UK) 

Sadly however the card isn't working and the output of "dmesg | grep dvb" gives me the following:


> 
Apr  9 10:04:28 mythic kernel: [   26.151477] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
Apr  9 10:04:28 mythic kernel: [   26.151498] firmware: requesting dvb-usb-dib0700-1.10.fw
Apr  9 10:04:28 mythic kernel: [   30.942928] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
Apr  9 10:04:28 mythic kernel: [   51.290112] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
Apr  9 10:04:28 mythic kernel: [   51.295404] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Apr  9 10:04:28 mythic kernel: [   56.306536] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
Apr  9 10:04:28 mythic kernel: [   78.283160] DVB: registering frontend 0 (DiBcom 7000PC)...
Apr  9 10:04:28 mythic kernel: [   94.835828] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Apr  9 10:04:28 mythic kernel: [   94.848068] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
Apr  9 10:04:28 mythic kernel: [   96.263879] DVB: registering frontend 1 (DiBcom 7000PC)...
Apr  9 10:04:28 mythic kernel: [  112.816547] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
Apr  9 10:04:28 mythic kernel: [  112.828643] usbcore: registered new interface driver dvb_usb_dib0700
Apr  9 10:24:09 mythic kernel: [ 1305.441012] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully deinitialized and disconnected.


So it looks like the card is being found, is being initialised successfully but is then being "dropped" for reasons unknown (to me) as the last line clearly states: 
> 
Nova-TD-500 (84xxx) successfully deinitialized and disconnected.


Additionally the card doesn't show up in the output from "lspci" as this is:

> 
00:00.0 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT890 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN700/VN800/P4M800CE/Pro Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0d.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:0e.0 Ethernet controller: VIA Technologies, Inc. VT6120/VT6121/VT6122 Gigabit Ethernet Adapter (rev 11)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:14.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:14.2 USB Controller: VIA Technologies, Inc. Device 3004 (rev 65)
01:00.0 VGA compatible controller: VIA Technologies, Inc. CN700/P4M800 Pro/P4M800 CE/VN800 [S3 UniChrome Pro] (rev 01)



However despite a full days "googling" I can't find an answer to my problem and would be most grateful for any idea as to what is happening ?

Thank you.

---

### Post by Raptor Ramjet on 2009-04-12
Following on from my earlier post I discovered that my PCI riser seems to be problematic so, whilst waiting for a new one to arrive, I've taken the mobo out of the case and have plugged the Nova-TD-500 card directly in to the PCI slot.

But having got absolutely nowhere with getting MythTV working I decided to start again.  However to test that the hardware does actually work (card & aerial mainly) I decided to start off by formatting my drive and installing Windows so I could use the supplied Hauppauge software.  A short while later and this unsuprisingly proved that the card works perfectly with my aerial.  One quick channel scan later and I had 83 channels available and I was able to watch TV, listen to the radio etc.  etc.

So having satisfied myself that it's definitely not a hardware problem I formatted my disk again and reinstalled MythTV.  A quick view of my systems DVB related messages shows that the card seems to be getting picked up o.k.:

> 
user@host#grep -i dvb /var/log/messages
Apr 12 12:16:59 mythic kernel: [   25.775965] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
Apr 12 12:16:59 mythic kernel: [   25.775987] firmware: requesting dvb-usb-dib0700-1.10.fw
Apr 12 12:16:59 mythic kernel: [   31.225659] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
Apr 12 12:16:59 mythic kernel: [   51.779944] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
Apr 12 12:16:59 mythic kernel: [   51.785400] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Apr 12 12:16:59 mythic kernel: [   56.796549] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
Apr 12 12:16:59 mythic kernel: [   78.773942] DVB: registering frontend 0 (DiBcom 7000PC)...
Apr 12 12:16:59 mythic kernel: [   95.327191] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Apr 12 12:16:59 mythic kernel: [   95.339468] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
Apr 12 12:16:59 mythic kernel: [   96.755296] DVB: registering frontend 1 (DiBcom 7000PC)...
Apr 12 12:16:59 mythic kernel: [  113.308554] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
Apr 12 12:16:59 mythic kernel: [  113.320639] usbcore: registered new interface driver dvb_usb_dib0700
user@host#


Now I go into mythtv-setup and after initial configuration the main parts of my setup are:

> 
1 General
TV-Format: PAL
Channel Frequency Table: europe-west (I've also tried "try-all")

2 Capture Card
Name: DVB-0
Card Type: DVB DTV Capture card (v3.x)
DVB Device Number: 0
Frontend ID: DiBcom 7000 PC Subtype: DVB-T

3 Video Source
Name: EIT
Listings Grabber: Transmitted Guide Only (EIT)
Channel Frequency Table: default (I've also also tried "try-all")

4 Input Connection
Capture Device: DVB-0
Input: DVBInput
Display Name: Freeview
Video Source: EIT



At this point I use the "scan for channels" function and after a long time the system finds nothing.  Nada.  Zilch.  Whilst performing the scan the display alternates between "scanning offset 1", which shows a signal strength of up to 62%, and "scanning offset 2" which always shows a signal strength of 0%.  Whilst this scan is progressing you can also see in the background a series of repeating messages of:

> 
Timeout Scanning -- No Signal
Timeout Scanning offset 1 -- No Signal
Timeout Scanning offset 2 -- No Signal
Timeout Scanning -- No Signal
Timeout Scanning offset 1 -- No Signal
Timeout Scanning offset 2 -- No Signal


So... following this I've been off to find some advice after which I shut down mythtv front end, shut down the backed (with "sudo /etc/init.d/mythtv-backend stop") then tried using the "scan" command from a terminal which gave me:

> 
user@host# scan /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill > /root/.tzap/channels.conf
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-WinterHill
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 754166670 0 3 9 1 0 0 0
>>> tune to: 754166670:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 754166670:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.


In case if it's relevant the output from lsmod shows plenty of "dib0700" modules have been loaded.

```

user@host#lsmod
Module                  Size  Used by
af_packet              25728  2 
via                    49280  3 
drm                    86056  4 via
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
rfcomm                 44560  0 
l2cap                  30464  6 bnep,rfcomm
bluetooth              61924  6 sco,bnep,rfcomm,l2cap
ppdev                  15748  0 
ipv6                  263972  27 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
xfs                   558632  1 
sbp2                   29324  0 
lp                     17156  0 
parport                42604  2 ppdev,lp
snd_via82xx            32536  1 
gameport               19468  1 snd_via82xx
snd_ac97_codec        111652  1 snd_via82xx
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  2 snd_via82xx,snd_pcm
snd_mpu401_uart        15360  1 snd_via82xx
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
evdev                  17696  4 
snd_seq_midi           14336  0 
dvb_usb_dib0700        37128  1 
dib7000p               25224  3 dvb_usb_dib0700
dib7000m               24068  1 dvb_usb_dib0700
dvb_usb                24460  1 dvb_usb_dib0700
snd_rawmidi            29824  2 snd_mpu401_uart,snd_seq_midi
dvb_core               86016  1 dvb_usb
dib3000mc              20616  1 dvb_usb_dib0700
dibx000_common         11652  3 dib7000p,dib7000m,dib3000mc
dib0070                15876  3 dvb_usb_dib0700
serio_raw              13444  0 
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
psmouse                45200  0 
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  13 snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcspkr                 10624  0 
i2c_viapro             15764  0 
soundcore              15328  1 snd
i2c_core               31892  8 dvb_usb_dib0700,dib7000p,dib7000m,dvb_usb,dib3000mc,dibx000_common,dib0070,i2c_viapro
via_agp                16256  1 
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
agpgart                42184  2 drm,via_agp
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  4 
crc_t10dif              9984  1 sd_mod
sg                     39732  0 
pata_acpi              12160  0 
pata_via               16132  0 
sata_via               15492  3 
ata_generic            12932  0 
libata                178208  4 pata_acpi,pata_via,sata_via,ata_generic
uhci_hcd               30864  0 
ehci_hcd               43788  0 
scsi_mod              155212  5 sbp2,sr_mod,sd_mod,sg,libata
dock                   16656  1 libata
via_velocity           37896  0 
crc_ccitt              10112  1 via_velocity
ohci1394               37936  0 
usbcore               149488  5 dvb_usb_dib0700,dvb_usb,uhci_hcd,ehci_hcd
ieee1394               96324  2 sbp2,ohci1394
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  1 
user@host

```

And, whilst I'm not sure what the device is (I'm using a PCI Nova-TD-500 card *NOT* the USB stick model), there's something from Hauppauge showing up under USB as the output from lsusb shows:

> 
user@host#lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 2040:8400 Hauppauge 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
user@host#


Sadly at this point I must say I'm completely stumped, thoroughly disillusioned, and am sadly coming to the conclusion that MythTV simply doesn't work with this version of the card.  Despite me buying the thing after reading that the card is supported "out of the box" by the latest kernels.  

Compared to setting the system up using Windows this is a total pain in the proverbial...

Or can anyone point me in the direction as to what's going wrong ?

Thank you.

---

### Post by utar on 2009-04-12
Have you enabled the low noise amplifier on the card?

---

### Post by Raptor Ramjet on 2009-04-12
Hello,

Yes I forgot to mention it (I've been doing an awful lot of googling this weekend) and I found and followed the instructions at [http://ubuntuforums.org/showthread.php?t=880830](http://ubuntuforums.org/showthread.php?t=880830) so I have the following two lines in my /etc/modprobe.d/options.

> 
#2009-04-11 - See [http://ubuntuforums.org/showthread.php?t=880830](http://ubuntuforums.org/showthread.php?t=880830)
# Enable LNA (Low Noise Amplifier)
options dvb-usb-dib0700 force_lna_activation=1
# Disable 2nd tuner suspend
options usbcore autosuspend=-1


---

### Post by utar on 2009-04-12
I assume you have both tuners set up in Myth?  Not sure if it makes any difference if you only have one set-up?

I'm not any sort of expert so not sure what else could be the problem as per [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500) the card with your usb id should work out of the box.

If you get desperate (after trying everything else first) you could try an install of the latest v4l drivers:

[http://linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers](http://linuxtv.org/wiki/index.php/How_to_Obtain%2C_Build_and_Install_V4L-DVB_Device_Drivers)



Utar

---

### Post by Raptor Ramjet on 2009-04-12
I have indeed tried setting up both tuners, then removed them and tried with only 1 etc.  

Cheers for the links too.  I had originally seen some advice to try compiling V4L drivers but I was leaving it as a total last resort as, with it being so close to the Ubuntu Jaunty release, I didn't want to break package compatibilty with Mythbuntu by starting to "roll my own" stuff.

However I might well give it a try if I get time tomorrow as nothing else seems to be working and I've got to give up for the day.

Cheers for the input though.

---

### Post by nickrout on 2009-04-13
I do not know the solution to your problem but I do know why the card does not show up in lspci. 

The pci card has a usb bridge on it and then the usb bridge connects to the TV hardware. so all lspci sees is the usb adaptor. Hope that helps in some small way.

---

### Post by Raptor Ramjet on 2009-04-13
Thanks to nickrout for the heads up on the USB/PCI point which is useful to know.

But sadly I've now tried compiling the V4L drivers etc. and the box *still* cannot tune any channels.  Despite "offset 1" showing a signal strength of 62% during the scan process it finds absolutely nothing.

So I'm afraid that I'm now totally disillusioned and entirely frustrated with the whole process.  The only solution is to give up with MythTV, put Windows back on the hard drive (good job I've got a spare licence), install [GBPVR]("http://www.gbpvr.com/") and get on with using the thing.  As I said in an earlier post having tried this already it *just works* (tm).  

My advice is therefore that the Nova-TD-500 marked as "WinTV-NOVA-TD-500, Model 289, SL-289-V3.0-UK" on the box and  "WinTV-NOVA-TD-500 DVB-T 84109 LF Rev D1F4" on the sticker on the card does *NOT* work with MythTV.  Or maybe it's down to the combination of using it with an EPIA EN15000G motherboard ? All I know is that this combination of  hardware works perfectly under Windows but cannot even tune in a signal with MythTV.

On which note should any MythTV developer ever read this thread I would like to ask why the setup procedure isn't mostly a matter of selecting a country and region (i.e. in my case UK and either county name or postcode) after which everything (hardware, video sources, channel setup etc.) is setup with sensible defaults for you ?

Obviously a user should have full access to the settings, so they can setup the box in as non standard a way as they wish, but initial setup should be trivially simple.  At the very least the hardware should be found and fully configured without user interaction being required.

Ho hum... another abject failure in my ongoing Linux experiments.

---

