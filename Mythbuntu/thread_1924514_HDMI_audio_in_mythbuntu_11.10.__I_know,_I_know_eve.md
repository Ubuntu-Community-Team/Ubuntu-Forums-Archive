---
title: "HDMI audio in mythbuntu 11.10.  I know, I know everyone has this problem."
date: 2012-02-12
forum: Mythbuntu
---

### Post by drfreakynutz on 2012-02-12
my relevant hardware is:
MSI K9A2GM-FIH m-ATX motherboard socket AM2+ 780G chipset
Integrated ATI Radeon HD2300 Video with VGA and HDMI
AMD Sempron LE-1300 @ 2.3Ghz
HD5500 HDTV Tuner Card

mythbuntu 11.10 installed and updated it comes with mythtv 0.24.?. I have tried almost every possible combination for the mythtvfrontend > utilities/setup > setup > general > audio systems but my current settings are:

audio output device = ALSA:dmix:CARD=HDMI,DEV=3
digital audio capabilities
dolby digital = checked, DTS = checked
speaker configuration = 5.1
upconvert stereo to 5.1 surround = checked
upmix quality = good
advanced audio configuration = checked
separate digital output device = checked
digital output device = default

with these settings the volume control on the remote brings up the volume graphic but the volume won't go up from zero.  other setting allow the remote to change the volume but no sound comes out of course.

```
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
~$ aplay -L
null
   Discard all samples (playback) or generate zero samples (capture)
pulse
   Playback/recording through the PulseAudio sound server
front:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   Front speakers
surround40:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Digital
   IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   Direct sample mixing device
dmix:CARD=SB,DEV=1
   HDA ATI SB, ALC888 Digital
   Direct sample mixing device
dsnoop:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   Direct sample snooping device
dsnoop:CARD=SB,DEV=1
   HDA ATI SB, ALC888 Digital
   Direct sample snooping device
hw:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   Direct hardware device without any conversions
hw:CARD=SB,DEV=1
   HDA ATI SB, ALC888 Digital
   Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
   HDA ATI SB, ALC888 Analog
   Hardware device with all software conversions
plughw:CARD=SB,DEV=1
   HDA ATI SB, ALC888 Digital
   Hardware device with all software conversions
hdmi:CARD=HDMI,DEV=0
   HDA ATI HDMI, HDMI 0
   HDMI Audio Output
dmix:CARD=HDMI,DEV=3
   HDA ATI HDMI, HDMI 0
   Direct sample mixing device
dsnoop:CARD=HDMI,DEV=3
   HDA ATI HDMI, HDMI 0
   Direct sample snooping device
hw:CARD=HDMI,DEV=3
   HDA ATI HDMI, HDMI 0
   Direct hardware device without any conversions
plughw:CARD=HDMI,DEV=3
   HDA ATI HDMI, HDMI 0
   Hardware device with all software conversions
```

neither .asoundrc or /etc/asound.conf existed so I created them and tried a bunch of stuff with and without these files in existence and the last thing I have there is:

```
~$ more .asoundrc
defaults.pcm.card 2
defaults.pcm.device 3
```

```
/etc$ more asound.conf
pcm.!default {
       type plug
       slave.pcm {
       type hw
       card 2
       device 3
       }
       }
```

in alsamixer S/PDIF and S/PDIF D both have 00 values

installed pulse audio and pavucontrol

in the pulseAudio mixer I set HDA ATI HDMI (ALSA mixer) as the soundcard and set IEC958 as the switcher

in pavucontrol:
output devices tab
RS780 Azalea controller analog stereo
port = Analog Output (no other option)
configuration tab
RS780 Azalea controller
profile = Analog Stereo Output

One thing I have seen suggested that I haven't tried is to update the BIOS.  I guess I could do that next.

totally at a loss and at this point there are so many variables in the mix that I feel like getting the right combination is going to be utterly impossible.  I have been banging my head against this for a couple days and I'm sick of it.  I'm kind of a newb so any step by step processes to fix this would be helpful.

Is it possible my hardware is a limitation?

---

### Post by nickrout on 2012-02-13
> **drfreakynutz said:**
> my relevant hardware is:

Integrated ATI Radeon HD2300 Video with VGA and HDMI
Is it possible my hardware is a limitation?

Well we all know nvidia is the bees knees for mythtv (including audio over hdmi) so why do people keep buying ATi?

> mythtvfrontend > utilities/setup > setup > general > audio systems

Did you scan for audio devices? (yes that is a button at the top of the page)

---

### Post by drfreakynutz on 2012-02-13
the system I have was a prepackaged media center barebones pc that I got for next to nothing.  admittedly nowhere near top of the line gear. though this is what I can afford.

I did scan for devices and tried every one of them.  I also tried the speaker-test utility to no avail.

I'm pretty desperate as I have been staring at forums, wikis, videos and guides all weekend.  any suggestions are appreciated.

---

### Post by drfreakynutz on 2012-02-14
by way of update/bump, I felt things were overly complicated so I removed pulseaudio, pavucontrol, the .asoundrc and the /etc/asound.conf

I went to the mythfrontend > setup/utlities > setup > general > audio settings and rescanned and retried all of the possible hdmi listings there.  no joy.:confused: any help would be so very welcome.

---

### Post by nickrout on 2012-02-14
Just to check, have you been into alsamixer (runs in a terminal) and checked that the output is not muted?

---

### Post by drfreakynutz on 2012-02-14
I did run alsamixer.  not totally sure what I am looking for there, but as I said in the first post S/PDIF and S/PDIF D both have "00" values as opposed to "MM".  Is there something else I can do in alsamixer or info from there I can post here that would be informative?

---

### Post by drfreakynutz on 2012-02-14
not sure if this info helps.  I ran lsmod | grep snd

```
$ lsmod | grep snd
snd_hda_codec_hdmi     31426  1 
snd_seq_midi           13132  0 
snd_hda_codec_realtek   254125  1 
snd_rawmidi            25241  1 snd_seq_midi
snd_hda_intel          24262  2 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_pcm                80435  4 snd_hda_codec_hdmi,cx88_alsa,snd_hda_intel,snd_hda_codec
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28932  2 snd_seq,snd_pcm
snd                    55902  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,cx88_alsa,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_seq,snd_pcm,snd_seq_device,snd_timer
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
```

and I looked at /proc/asound/card2/codec#0 

```
/proc/asound/card2$ more codec#0
Codec: ATI RS690/780 HDMI
Address: 0
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x1002791a
Subsystem Id: 0x00791a00
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x40]: 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="HDMI 0", type="HDMI", device=3
  Converter: stream=1, channel=0
  Digital: Enabled
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
```

finally I tried this:

```
modprobe snd_hda_intel
```

and 

```
modprobe snd_hda_intel model=6stack-digout
```

as suggested here: [http://alsa.opensrc.org/Hda](http://alsa.opensrc.org/Hda)

jeezem crow it's a full time job.

---

### Post by nickrout on 2012-02-14
Looking at your first post:

> audio output device = ALSA:dmix:CARD=HDMI,DEV=3

I assume this wil lbe different now you have scanned

> digital audio capabilities
dolby digital = checked, DTS = checked
speaker configuration = 5.1

Really? What are you playing into? Most TVs are only stereo.
> upconvert stereo to 5.1 surround = checked

Turn this off for testing anyway.
> upmix quality = good
advanced audio configuration = checked
separate digital output device = checked
digital output device = default

Why? turn all that off.

---

### Post by drfreakynutz on 2012-02-15
I have been scanning from the beginning and ALSA:dmix:CARD=HDMI,DEV=3 is one of the choices along with hw or plughw in place of dmix.  none of them work and they all make the video jumpy when I turn them on and no sound comes out.

the whole point of this exercise is the hope that I can pass 5.1 through my tv via hdmi to my receiver.  perhaps that doesn't work, but I think it does when I use hdmi from my blu-ray through the tv.

I believe I have tried the settings with all of those configurations off, (5.1, upmix and advanced audio) but I will confirm tonight when I get back home.

I have also been trying just to get any sound out using aplay and mplayer in a terminal with various settings playing a .wav file, but there is nothing coming out there either.

I really appreciate all of the help you are offering.

---

### Post by drfreakynutz on 2012-02-15
yep, after trying again at home, turned off all that crap in the general audio settings (DTS, Dolby, upmix, 5.1 etc.) and the results were the same, jumpy video with no sound.  the relevant audio devices from the scan are:

ALSA:dmix:CARD=HDMI,DEV=3
ALSA:hw:CARD=HDMI,DEV=3
ALSA:plughw:CARD=HDMI,DEV=3

weird the third option for some reason becomes an emoticon.  it should be ALSA : plughw

---

### Post by nickrout on 2012-02-16
> **drfreakynutz said:**
> yep, after trying again at home, turned off all that crap in the general audio settings (DTS, Dolby, upmix, 5.1 etc.) and the results were the same, jumpy video with no sound.  the relevant audio devices from the scan are:

ALSA:dmix:CARD=HDMI,DEV=3
ALSA:hw:CARD=HDMI,DEV=3
ALSA:plughw:CARD=HDMI,DEV=3

weird the third option for some reason becomes an emoticon.  it should be ALSA : plughw

Frankly I am not sure why you have dmix or plughw devices if you have no asound.conf or .asoundrc.

---

### Post by drfreakynutz on 2012-02-16
the hw option doesn't work either.  I had created .asoundrc and asound-conf files at one point but have since removed them.  I'm willing to try just about anything.  any suggestions?

---

### Post by nickrout on 2012-02-17
My hdmi audio device is ALSA:hdmi:CARD=NVidia,DEV=0 but that (as may be obvious) is an nvidia card.

Dunno if this has been covered - I subscribe to lots of threads, but what versions of mythfrontend and alsa-libs are you running?

---

### Post by jlp_engineer on 2012-02-17
I am certainly a lot less qualified than Nick to be offering suggestions, but I would try and tackle one issue at at time.  Separate the video and audio issues by focusing on one or the other.  Play some MP3's with the tools available to you outside of MythTV.  Once you get that working, then move on to the video issue.

Nick is very knowledgeable, and this community owes him a debt of gratitude.  We are lucky to have him here.

---

### Post by nickrout on 2012-02-17
Looking at this post [http://www.gossamer-threads.com/lists/mythtv/dev/380600](http://www.gossamer-threads.com/lists/mythtv/dev/380600) it seems that (at least in 2009) the radeonhd video driver was needed for hdmi audio support.

So what video driver are you using? These commands might help you find out:```
lsmod|grep radeon
grep -i radeon /var/log/Xorg.0.log
```

---

### Post by drfreakynutz on 2012-02-18
> **jlp_engineer said:**
> I am certainly a lot less qualified than Nick to be offering suggestions, but I would try and tackle one issue at at time.  Separate the video and audio issues by focusing on one or the other.  Play some MP3's with the tools available to you outside of MythTV.  Once you get that working, then move on to the video issue.

Nick is very knowledgeable, and this community owes him a debt of gratitude.  We are lucky to have him here.

thanks.  I kind of came to that same conclusion and am trying to get sound working by playing wav files with mplayer and aplay.  I appreciate all of the help here.

---

### Post by drfreakynutz on 2012-02-18
> **nickrout said:**
> Looking at this post [http://www.gossamer-threads.com/lists/mythtv/dev/380600](http://www.gossamer-threads.com/lists/mythtv/dev/380600) it seems that (at least in 2009) the radeonhd video driver was needed for hdmi audio support.

So what video driver are you using? These commands might help you find out:```
lsmod|grep radeon
grep -i radeon /var/log/Xorg.0.log
```

I will try to figure out which driver I have when I get home tonight.  thanks for the idea.  I was starting to despair that I might be running out of options.

---

### Post by nickrout on 2012-02-18
> **jlp_engineer said:**
> I am certainly a lot less qualified than Nick to be offering suggestions, but I would try and tackle one issue at at time.  Separate the video and audio issues by focusing on one or the other.  Play some MP3's with the tools available to you outside of MythTV.  Once you get that working, then move on to the video issue.

Nick is very knowledgeable, and this community owes him a debt of gratitude.  We are lucky to have him here.

you are far too kind!

---

### Post by drfreakynutz on 2012-02-18
OK looking at the link you sent, we are getting outside my pay grade here.  I'm willing to try anything though.  here is the out put to the first command:

```
~$ lsmod|grep radeon
radeon                929507  2 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192194  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  3 cx88_vp3054_i2c,cx88xx,radeon

```

the second command has tons of output. hope I'm not committing a massive faux pas by code bombing this thread:

```
~$ grep -i radeon /var/log/Xorg.0.log
[    14.311] (II) LoadModule: "radeon"
[    14.312] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    14.312] (II) Module radeon: vendor="X.Org Foundation"
[    14.313] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
	ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
	ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
	ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
	ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
	ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
	ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
	ATI Mobility Radeon HD 4670, ATI FirePro M5750,
	ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
	ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
	ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
	ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
	ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
	ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
	ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
	ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
	ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
	ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
	ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
	ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
	ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
	ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
	ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
	ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
	ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
	SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200, ATI Radeon 4100,
	ATI Mobility Radeon HD 4200, ATI Mobility Radeon 4100,
	ATI Radeon HD 4290, ATI Radeon HD 4250, AMD Radeon HD 6310 Graphics,
	AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
	AMD Radeon HD 6250 Graphics, AMD Radeon HD 6300 Series Graphics,
	AMD Radeon HD 6200 Series Graphics, CYPRESS,
	AMD Firestream 9350, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
	ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
	ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series,
	ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
	ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
	ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
	ATI Mobility Radeon HD 5000 Series,
	ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
	ATI Mobility Radeon Graphics, CEDAR,
	ATI Radeon HD 5450, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
	CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, AMD Radeon HD 6900 Series,
	AMD Radeon HD 6900 Series, CAYMAN, CAYMAN, CAYMAN,
	AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
	BARTS, Mobility Radeon HD 6000 Series,
	Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
	AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
	AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
[    14.317] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    14.318] (II) RADEON(0): Creating default Display subsection in Screen section
[    14.318] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    14.318] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    14.318] (==) RADEON(0): Default visual is TrueColor
[    14.318] (==) RADEON(0): RGB weight 888
[    14.318] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    14.318] (--) RADEON(0): Chipset: "ATI Radeon HD 3200 Graphics" (ChipID = 0x9610)
[    14.318] (II) RADEON(0): PCI card detected
[    14.319] (II) RADEON(0): KMS Color Tiling: enabled
[    14.319] (II) RADEON(0): KMS Pageflipping: enabled
[    14.319] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    14.344] (II) RADEON(0): Output VGA-0 has no monitor section
[    14.563] (II) RADEON(0): Output HDMI-0 has no monitor section
[    14.588] (II) RADEON(0): EDID for output VGA-0
[    14.816] (II) RADEON(0): EDID for output HDMI-0
[    14.816] (II) RADEON(0): Manufacturer: SYN  Model: f  Serial#: 138
[    14.816] (II) RADEON(0): Year: 2006  Week: 29
[    14.816] (II) RADEON(0): EDID Version: 1.3
[    14.816] (II) RADEON(0): Digital Display Input
[    14.816] (II) RADEON(0): Max Image Size [cm]: horiz.: 93  vert.: 52
[    14.816] (II) RADEON(0): Gamma: 2.20
[    14.816] (II) RADEON(0): No DPMS capabilities specified
[    14.816] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    14.816] (II) RADEON(0): First detailed timing is preferred mode
[    14.816] (II) RADEON(0): GTF timings supported
[    14.816] (II) RADEON(0): redX: 0.652 redY: 0.331   greenX: 0.276 greenY: 0.597
[    14.816] (II) RADEON(0): blueX: 0.145 blueY: 0.066   whiteX: 0.285 whiteY: 0.293
[    14.816] (II) RADEON(0): Supported established timings:
[    14.816] (II) RADEON(0): 640x480@60Hz
[    14.816] (II) RADEON(0): 640x480@75Hz
[    14.816] (II) RADEON(0): 800x600@60Hz
[    14.816] (II) RADEON(0): 800x600@75Hz
[    14.816] (II) RADEON(0): 1024x768@60Hz
[    14.816] (II) RADEON(0): 1024x768@75Hz
[    14.816] (II) RADEON(0): Manufacturer's mask: 0
[    14.816] (II) RADEON(0): Supported standard timings:
[    14.816] (II) RADEON(0): #0: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    14.816] (II) RADEON(0): Supported detailed timing:
[    14.816] (II) RADEON(0): clock: 72.0 MHz   Image Size:  930 x 520 mm
[    14.816] (II) RADEON(0): h_active: 1360  h_sync: 1408  h_sync_end 1440 h_blank_end 1520 h_border: 0
[    14.816] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 790 v_border: 0
[    14.816] (II) RADEON(0): Supported detailed timing:
[    14.816] (II) RADEON(0): clock: 79.5 MHz   Image Size:  930 x 520 mm
[    14.816] (II) RADEON(0): h_active: 1280  h_sync: 1344  h_sync_end 1472 h_blank_end 1664 h_border: 0
[    14.816] (II) RADEON(0): v_active: 768  v_sync: 771  v_sync_end 778 v_blanking: 798 v_border: 0
[    14.816] (II) RADEON(0): Ranges: V min: 49 V max: 76 Hz, H min: 15 H max: 80 kHz, PixClock max 145 MHz
[    14.816] (II) RADEON(0): Monitor name: 542-B11
[    14.816] (II) RADEON(0): Supported detailed timing:
[    14.816] (II) RADEON(0): clock: 74.2 MHz   Image Size:  930 x 520 mm
[    14.816] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    14.816] (II) RADEON(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 563 v_border: 0
[    14.816] (II) RADEON(0): Supported detailed timing:
[    14.816] (II) RADEON(0): clock: 74.2 MHz   Image Size:  930 x 520 mm
[    14.817] (II) RADEON(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    14.817] (II) RADEON(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    14.817] (II) RADEON(0): Supported detailed timing:
[    14.817] (II) RADEON(0): clock: 27.0 MHz   Image Size:  930 x 520 mm
[    14.817] (II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    14.817] (II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    14.817] (II) RADEON(0): Supported detailed timing:
[    14.817] (II) RADEON(0): clock: 27.0 MHz   Image Size:  690 x 520 mm
[    14.817] (II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    14.817] (II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    14.817] (II) RADEON(0): Supported detailed timing:
[    14.817] (II) RADEON(0): clock: 27.0 MHz   Image Size:  930 x 520 mm
[    14.817] (II) RADEON(0): h_active: 1440  h_sync: 1478  h_sync_end 1602 h_blank_end 1716 h_border: 0
[    14.817] (II) RADEON(0): v_active: 240  v_sync: 244  v_sync_end 247 v_blanking: 262 v_border: 0
[    14.817] (II) RADEON(0): Number of EDID sections to follow: 1
[    14.817] (II) RADEON(0): EDID (in hex):
[    14.817] (II) RADEON(0): 	00ffffffffffff004f2e0f008a000000
[    14.817] (II) RADEON(0): 	1d100103805d34780b3f00a754469825
[    14.817] (II) RADEON(0): 	11494b254a0081c0014001400140014f
[    14.817] (II) RADEON(0): 	01590159010a201c50a0500016303020
[    14.817] (II) RADEON(0): 	3500a2083200001c0e1f008051001e30
[    14.817] (II) RADEON(0): 	40803700a2083200001a000000fd0031
[    14.817] (II) RADEON(0): 	4c0f500e000a202020202020000000fc
[    14.817] (II) RADEON(0): 	003534322d4231310a2020202020018b
[    14.817] (II) RADEON(0): 	02031971468502030406072309170783
[    14.817] (II) RADEON(0): 	01000065030c001000011d8018711c17
[    14.817] (II) RADEON(0): 	20582c2500a2083200009e011d007251
[    14.817] (II) RADEON(0): 	d01e206e285500a2083200001e8c0ad0
[    14.817] (II) RADEON(0): 	8a20e02d10103e9600a208320000188c
[    14.817] (II) RADEON(0): 	0ad08a20e02d10103e9600b208220000
[    14.817] (II) RADEON(0): 	188c0aa01451f01600267c4300a20832
[    14.817] (II) RADEON(0): 	000098000000000000000000000000c9
[    14.817] (II) RADEON(0): Printing probed modes for output HDMI-0
[    14.817] (II) RADEON(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 776 790 -hsync +vsync (47.4 kHz)
[    14.817] (II) RADEON(0): Modeline "1920x1080i"x59.9   74.25  1920 2008 2052 2200  1080 1084 1094 1127 interlace +hsync +vsync (33.8 kHz)
[    14.817] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    14.817] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    14.817] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    14.817] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    14.817] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    14.817] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    14.817] (II) RADEON(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
[    14.817] (II) RADEON(0): Modeline "1280x800"x74.9  106.50  1280 1360 1488 1696  800 803 809 838 -hsync +vsync (62.8 kHz)
[    14.817] (II) RADEON(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 +hsync -vsync (49.7 kHz)
[    14.817] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    14.817] (II) RADEON(0): Modeline "1280x768"x74.9  102.25  1280 1360 1488 1696  768 771 778 805 +hsync -vsync (60.3 kHz)
[    14.817] (II) RADEON(0): Modeline "1280x768"x59.9   79.50  1280 1344 1472 1664  768 771 778 798 -hsync +vsync (47.8 kHz)
[    14.817] (II) RADEON(0): Modeline "1280x768"x59.9   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    14.817] (II) RADEON(0): Modeline "1280x720"x60.0   74.44  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.7 kHz)
[    14.817] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    14.817] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    14.817] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    14.817] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    14.817] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    14.817] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    14.817] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    14.817] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    14.817] (II) RADEON(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    14.817] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    14.817] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    14.817] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    14.817] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    14.818] (II) RADEON(0): Modeline "256x192"x85.2    4.96  256 248 272 288  192 193 196 202 -hsync +vsync (17.2 kHz)
[    14.818] (II) RADEON(0): Modeline "256x192"x75.1    4.35  256 248 272 288  192 193 196 201 -hsync +vsync (15.1 kHz)
[    14.818] (II) RADEON(0): Modeline "256x192"x59.9    3.26  256 240 264 272  192 193 196 200 -hsync +vsync (12.0 kHz)
[    14.818] (II) RADEON(0): Modeline "256x160"x70.2    3.19  256 240 264 272  160 161 164 167 -hsync +vsync (11.7 kHz)
[    14.818] (II) RADEON(0): Output VGA-0 disconnected
[    14.818] (II) RADEON(0): Output HDMI-0 connected
[    14.818] (II) RADEON(0): Using exact sizes for initial modes
[    14.818] (II) RADEON(0): Output HDMI-0 using initial mode 1360x768
[    14.818] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    14.818] (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:10000000 visible:fba0000
[    14.818] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    14.818] (==) RADEON(0): DPI set to (96, 96)
[    14.818] (II) RADEON(0): [DRI2] Setup complete
[    14.818] (II) RADEON(0): [DRI2]   DRI driver: r600
[    14.819] (II) RADEON(0): Front buffer size: 4224K
[    14.819] (II) RADEON(0): VRAM usage limit set to 228096K
[    14.819] (==) RADEON(0): Backing store disabled
[    14.819] (II) RADEON(0): Direct rendering enabled
[    14.819] (II) RADEON(0): Setting EXA maxPitchBytes
[    14.819] (II) RADEON(0): Acceleration enabled
[    14.819] (==) RADEON(0): DPMS enabled
[    14.819] (==) RADEON(0): Silken mouse enabled
[    14.819] (II) RADEON(0): Set up textured video
[    14.819] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    14.819] (II) RADEON(0): [XvMC] Extension initialized.
[    14.819] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    14.894] (II) RADEON(0): Setting screen physical size to 359 x 203
[    17.845] (II) RADEON(0): EDID vendor "SYN", prod id 15
[    17.845] (II) RADEON(0): Using EDID range info for horizontal sync
[    17.845] (II) RADEON(0): Using EDID range info for vertical refresh
[    17.845] (II) RADEON(0): Printing DDC gathered Modelines:
[    17.845] (II) RADEON(0): Modeline "1360x768"x0.0   72.00  1360 1408 1440 1520  768 771 776 790 -hsync +vsync (47.4 kHz)
[    17.845] (II) RADEON(0): Modeline "1280x768"x0.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    17.845] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1127 interlace +hsync +vsync (33.8 kHz)
[    17.845] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    17.845] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    17.845] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    17.845] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    17.845] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    17.845] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    17.845] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    17.845] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    17.845] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    17.845] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    17.845] (II) RADEON(0): Modeline "256x192"x60.0    3.26  256 240 264 272  192 193 196 200 -hsync +vsync (12.0 kHz)
[    17.845] (II) RADEON(0): Modeline "256x192"x75.0    4.34  256 248 272 288  192 193 196 201 -hsync +vsync (15.1 kHz)
[    17.845] (II) RADEON(0): Modeline "256x192"x85.0    4.94  256 248 272 288  192 193 196 202 -hsync +vsync (17.2 kHz)
[    17.845] (II) RADEON(0): Modeline "256x160"x70.0    3.18  256 240 264 272  160 161 164 167 -hsync +vsync (11.7 kHz)
[    17.845] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    17.845] (II) RADEON(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    18.174] (II) RADEON(0): EDID vendor "SYN", prod id 15
[    18.174] (II) RADEON(0): Using hsync ranges from config file
[    18.174] (II) RADEON(0): Using vrefresh ranges from config file
[    18.174] (II) RADEON(0): Printing DDC gathered Modelines:
[    18.174] (II) RADEON(0): Modeline "1360x768"x0.0   72.00  1360 1408 1440 1520  768 771 776 790 -hsync +vsync (47.4 kHz)
[    18.174] (II) RADEON(0): Modeline "1280x768"x0.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    18.174] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1127 interlace +hsync +vsync (33.8 kHz)
[    18.174] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    18.174] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    18.175] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    18.175] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.175] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.175] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.175] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.175] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.175] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.175] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    18.175] (II) RADEON(0): Modeline "256x192"x60.0    3.26  256 240 264 272  192 193 196 200 -hsync +vsync (12.0 kHz)
[    18.175] (II) RADEON(0): Modeline "256x192"x75.0    4.34  256 248 272 288  192 193 196 201 -hsync +vsync (15.1 kHz)
[    18.175] (II) RADEON(0): Modeline "256x192"x85.0    4.94  256 248 272 288  192 193 196 202 -hsync +vsync (17.2 kHz)
[    18.175] (II) RADEON(0): Modeline "256x160"x70.0    3.18  256 240 264 272  160 161 164 167 -hsync +vsync (11.7 kHz)
[    18.175] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    18.175] (II) RADEON(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    18.951] (II) RADEON(0): EDID vendor "SYN", prod id 15
[    18.951] (II) RADEON(0): Using hsync ranges from config file
[    18.951] (II) RADEON(0): Using vrefresh ranges from config file
[    18.951] (II) RADEON(0): Printing DDC gathered Modelines:
[    18.951] (II) RADEON(0): Modeline "1360x768"x0.0   72.00  1360 1408 1440 1520  768 771 776 790 -hsync +vsync (47.4 kHz)
[    18.951] (II) RADEON(0): Modeline "1280x768"x0.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    18.951] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1127 interlace +hsync +vsync (33.8 kHz)
[    18.951] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    18.951] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    18.951] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    18.951] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    18.951] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    18.951] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    18.951] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    18.951] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    18.951] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    18.951] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    18.951] (II) RADEON(0): Modeline "256x192"x60.0    3.26  256 240 264 272  192 193 196 200 -hsync +vsync (12.0 kHz)
[    18.951] (II) RADEON(0): Modeline "256x192"x75.0    4.34  256 248 272 288  192 193 196 201 -hsync +vsync (15.1 kHz)
[    18.951] (II) RADEON(0): Modeline "256x192"x85.0    4.94  256 248 272 288  192 193 196 202 -hsync +vsync (17.2 kHz)
[    18.951] (II) RADEON(0): Modeline "256x160"x70.0    3.18  256 240 264 272  160 161 164 167 -hsync +vsync (11.7 kHz)
[    18.951] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    18.951] (II) RADEON(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    21.013] (II) RADEON(0): EDID vendor "SYN", prod id 15
[    21.013] (II) RADEON(0): Using hsync ranges from config file
[    21.013] (II) RADEON(0): Using vrefresh ranges from config file
[    21.013] (II) RADEON(0): Printing DDC gathered Modelines:
[    21.013] (II) RADEON(0): Modeline "1360x768"x0.0   72.00  1360 1408 1440 1520  768 771 776 790 -hsync +vsync (47.4 kHz)
[    21.013] (II) RADEON(0): Modeline "1280x768"x0.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    21.013] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1127 interlace +hsync +vsync (33.8 kHz)
[    21.013] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    21.013] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    21.013] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    21.013] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.013] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    21.013] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.013] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    21.013] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.013] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    21.013] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    21.013] (II) RADEON(0): Modeline "256x192"x60.0    3.26  256 240 264 272  192 193 196 200 -hsync +vsync (12.0 kHz)
[    21.013] (II) RADEON(0): Modeline "256x192"x75.0    4.34  256 248 272 288  192 193 196 201 -hsync +vsync (15.1 kHz)
[    21.013] (II) RADEON(0): Modeline "256x192"x85.0    4.94  256 248 272 288  192 193 196 202 -hsync +vsync (17.2 kHz)
[    21.013] (II) RADEON(0): Modeline "256x160"x70.0    3.18  256 240 264 272  160 161 164 167 -hsync +vsync (11.7 kHz)
[    21.013] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    21.013] (II) RADEON(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
[    21.257] (II) RADEON(0): EDID vendor "SYN", prod id 15
[    21.257] (II) RADEON(0): Using hsync ranges from config file
[    21.257] (II) RADEON(0): Using vrefresh ranges from config file
[    21.257] (II) RADEON(0): Printing DDC gathered Modelines:
[    21.257] (II) RADEON(0): Modeline "1360x768"x0.0   72.00  1360 1408 1440 1520  768 771 776 790 -hsync +vsync (47.4 kHz)
[    21.257] (II) RADEON(0): Modeline "1280x768"x0.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync -vsync (47.8 kHz)
[    21.257] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1127 interlace +hsync +vsync (33.8 kHz)
[    21.257] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz)
[    21.258] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz)
[    21.258] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz)
[    21.258] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    21.258] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    21.258] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    21.258] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    21.258] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    21.258] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    21.258] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[    21.258] (II) RADEON(0): Modeline "256x192"x60.0    3.26  256 240 264 272  192 193 196 200 -hsync +vsync (12.0 kHz)
[    21.258] (II) RADEON(0): Modeline "256x192"x75.0    4.34  256 248 272 288  192 193 196 201 -hsync +vsync (15.1 kHz)
[    21.258] (II) RADEON(0): Modeline "256x192"x85.0    4.94  256 248 272 288  192 193 196 202 -hsync +vsync (17.2 kHz)
[    21.258] (II) RADEON(0): Modeline "256x160"x70.0    3.18  256 240 264 272  160 161 164 167 -hsync +vsync (11.7 kHz)
[    21.258] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz)
[    21.258] (II) RADEON(0): Modeline "1440x240"x0.0   27.00  1440 1478 1602 1716  240 244 247 262 -hsync -vsync (15.7 kHz)
```

I'm not getting much meaningful info from this output.  I won't try to parse it and let you guys tell me what the deal is.

---

### Post by nickrout on 2012-02-18
Further reading reveals radeonhd is defunct, so that is a false lead.

I have however discovered that in kernels >3.0 the audio part of the radeon driver is disabled.

I suggest:

1. kill X - ```
sudo /etc/init.d/lightdm stop
```

2. you will be left at a command prompt. Log in and then try```
modprobe -r radeon
modprobe radeon audio=1
```

3. Start X ```
sudo /etc/init.d/lightdm start
```


4. Try to get audio out of hdmi

PS I got this tip from [https://wiki.archlinux.org/index.php/ATI#HDMI_Audio](https://wiki.archlinux.org/index.php/ATI#HDMI_Audio) which is obviously a different distro, but worth a shot anyways.

---

### Post by drfreakynutz on 2012-02-20
the modprobe -r radeon results in:

FATAL: module radeon is in use

basically I logged out, ctl-alt-F1, then stopped X which seemed to work fine then the modprobe command failed.  

I have seen the fact that the audio is disabled for the radeon driver implicated as the problem elsewhere.  mostly people have installed the radeon driver in the past, but as you say it is deprecated.

---

### Post by drfreakynutz on 2012-02-21
any ideas on how to get the modprobe command to work?  Or any other ideas for that matter.

---

### Post by nickrout on 2012-02-21
> **drfreakynutz said:**
> any ideas on how to get the modprobe command to work?  Or any other ideas for that matter.

lsmod should tell you what the module is in use by, and you can modprobe -r the modules that are using radeon before you remove the radeon module.

Or you could follow the advice i liknked to and try forcing the module to load audio support on boot, then reboot.

You need to add radeon.audio=1 to the kernel line in grub.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by drfreakynutz on 2012-02-22
> **nickrout said:**
> lsmod should tell you what the module is in use by, and you can modprobe -r the modules that are using radeon before you remove the radeon module.

Or you could follow the advice i liknked to and try forcing the module to load audio support on boot, then reboot.

You need to add radeon.audio=1 to the kernel line in grub.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

just to clarify (sorry, I'm learning as I go).  For ubuntu 11.10 I should do something to the effect of:

go to:
/etc/default/grub

and change

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

to

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"
```

then:

```
sudo update-grub
```

then reboot.

?

---

### Post by drfreakynutz on 2012-02-22
HOLY MOTHA FUNKIN' SHIP that did it!

I was starting to lose faith.  THANKS SO MUCH nickrout!!!!!

full surround sound passed through my tv to the stereo and out all 5.1 speakers.  WOOHOOOO!


THANKS AGAIN!  thanks for sticking with me and tolerating my incessant bumping.

---

### Post by nickrout on 2012-02-22
Pleased to be of service :)

---

### Post by drfreakynutz on 2012-03-05
I hate to bring this back, but hdmi sound suddenly stopped working.  Nothing should have changed.  I have been looking around for answers but I am as baffled as I was in the beginning of this whole process.  the only thing I found was this:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

but none of the suggestions I've tried seem to make a difference.

again, any help is greatly appreciated.

---

### Post by nickrout on 2012-03-05
> **drfreakynutz said:**
> I hate to bring this back, but hdmi sound suddenly stopped working.  Nothing should have changed.  I have been looking around for answers but I am as baffled as I was in the beginning of this whole process.  the only thing I found was this:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

but none of the suggestions I've tried seem to make a difference.

again, any help is greatly appreciated.

Did you do an update and get a new kernel? if so grub will probably have changed back to the default?

---

### Post by drfreakynutz on 2012-03-06
> **nickrout said:**
> Did you do an update and get a new kernel? if so grub will probably have changed back to the default?

No, no update.  anyway, I tried the same grub-update process after checking that the audio option was still in the kernel line when the sound stopped working.  no luck.

---

### Post by drfreakynutz on 2012-03-07
Um... the HDMI audio started working again.  I was messing with the channel editor and running mythfilldatabase several times.  I then decided just to test the hdmi audio output again for the hell of it, switched it to the hdmi sound and it worked.  maybe there is some hardware thing going on, because I can't think what else would have changed.

---

### Post by mathog on 2012-03-09
> **drfreakynutz said:**
> Um... the HDMI audio started working again.  I was messing with the channel editor and running mythfilldatabase several times.  I then decided just to test the hdmi audio output again for the hell of it, switched it to the hdmi sound and it worked.  maybe there is some hardware thing going on, because I can't think what else would have changed.


EDID issue?  Here is a thread about an EDID problem with an Nvidia card:

[http://www.nvnews.net/vbulletin/showthread.php?t=141707](http://www.nvnews.net/vbulletin/showthread.php?t=141707)

---

### Post by drfreakynutz on 2012-03-10
> **mathog said:**
> EDID issue?  Here is a thread about an EDID problem with an Nvidia card:

[http://www.nvnews.net/vbulletin/showthread.php?t=141707](http://www.nvnews.net/vbulletin/showthread.php?t=141707)

I will look into it.  see if I can get the EDID number from the tv and maybe put that in the xorg.conf.  would the edid that the system is getting change in the middle of a frontend session though? 

what happened last night was that I was watching tv and the sound was working fine.  Then I went to set up MythNetVision, which I just started using, and watched a short part of a video from hulu or something.  the sound did not work for hulu, then I went back to watch OTA tv and the hdmi sound stopped working there as well. 
 I'm not sure these are related, may just be coincidence.

---

### Post by nickrout on 2012-03-10
> **drfreakynutz said:**
> I will look into it.  see if I can get the EDID number from the tv and maybe put that in the xorg.conf.  would the edid that the system is getting change in the middle of a frontend session though? 

what happened last night was that I was watching tv and the sound was working fine.  Then I went to set up MythNetVision, which I just started using, and watched a short part of a video from hulu or something.  the sound did not work for hulu, then I went back to watch OTA tv and the hdmi sound stopped working there as well. 
 I'm not sure these are related, may just be coincidence.

perhaps the sound device used by whatever you used to play hulu was being held open and was blocking?

what do your frontend logs say?

---

### Post by drfreakynutz on 2012-03-10
> **nickrout said:**
> perhaps the sound device used by whatever you used to play hulu was being held open and was blocking?

what do your frontend logs say?

I will check the frontend log when I get in front of the tv, but I did restart the machine when the problem occurred and went straight to "watch tv" and still have the same problem.  no HDMI sound.

nickrout, do you think the suggested EDID thing could be part of the problem?

---

### Post by nickrout on 2012-03-10
> **drfreakynutz said:**
> I will check the frontend log when I get in front of the tv, but I did restart the machine when the problem occurred and went straight to "watch tv" and still have the same problem.  no HDMI sound.

nickrout, do you think the suggested EDID thing could be part of the problem?

EDID is read from the TV/Monitor when X starts, so if the TV is off when you start the frontend iw will not be able to read the edid, so yes if that is happening, it may be the problem.

Had all sorts of problems watching a video from a laptop at my brother-in-law's house yesterday, turned out to be a faulty hdmi cable. However that would stop both video and sound as they all travel the same path.

Some TVs are simply flaky too. Once they think there is no audio signal coming through the hdmi cable, some switch to th analogue audio inputs. In that case you may need to turn the frontend off, turn the TV off (or perhaps to another input altogether) then turn the tv back on and then the computer on.

Or something like that.

---

### Post by drfreakynutz on 2012-03-10
here is the output from 

```
sudo apt-get install read-edid
```

```
Section "Monitor"
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
	Identifier "542-B11"
	VendorName "SYN"
	ModelName "542-B11"
	# Block type: 2:0 3:fd
	HorizSync 15-80
	VertRefresh 49-76
	# Max dot clock (video bandwidth) 140 MHz
	# Block type: 2:0 3:fc
	# DPMS capabilities: Active off:no  Suspend:no  Standby:no

	Mode 	"1360x768"	# vfreq 59.960Hz, hfreq 47.368kHz
		DotClock	72.000000
		HTimings	1360 1408 1440 1520
		VTimings	768 771 776 790
		Flags	"+HSync" "-VSync"
	EndMode
	Mode 	"1280x768"	# vfreq 59.870Hz, hfreq 47.776kHz
		DotClock	79.500000
		HTimings	1280 1344 1472 1664
		VTimings	768 771 778 798
		Flags	"-HSync" "+VSync"
	EndMode
	# Block type: 2:0 3:fd
	# Block type: 2:0 3:fc
EndSection

```

not sure what I can do with this.  I would be flailing in the dark were I to try to edit the xorg.conf with this info.

The output from the mythfrontend.log even for a couple hours of watching is pretty extensive and I'm not really sure what I'm looking for.  anyway here is around that time when things went badly

```
2012-03-09 21:28:56.250 TV: Changing from None to WatchingLiveTV
2012-03-09 21:28:56.250 TV: State is LiveTV & mctx == ctx
2012-03-09 21:28:56.251 TV: UpdateOSDInput done
2012-03-09 21:28:56.251 TV: UpdateLCD done
2012-03-09 21:28:56.251 TV: ITVRestart done
2012-03-09 21:28:56.322 VideoOutput: Created YV12 OSD.
2012-03-09 21:28:58.105 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2012-03-09 21:28:58.353 OSD: Base theme size: 1280x720
2012-03-09 21:28:58.353 OSD: Scaling factors: 1.5x1.5
2012-03-09 21:28:58.381 AFD: Opened codec 0x967b0f0, id(MPEG2VIDEO) type(Video)
2012-03-09 21:28:58.381 AFD: codec AC3 has 2 channels
2012-03-09 21:28:58.381 AFD: Opened codec 0x94b23d0, id(AC3) type(Audio)
2012-03-09 21:28:58.382 AFD: codec AC3 has 1 channels
2012-03-09 21:28:58.382 AFD: Opened codec 0x90b4a30, id(AC3) type(Audio)
2012-03-09 21:28:58.564 Pulse: PulseAudio resume OK
2012-03-09 21:28:58.769 Pulse: PulseAudio suspend OK
2012-03-09 21:28:58.807 AO: Opening audio device 'plughw:CARD=HDMI,DEV=3' ch 2(2) sr 48000 sf signed 16 bit reenc 1
2012-03-09 21:28:58.809 AudioPlayer: Enabling Audio
2012-03-09 21:28:58.891 AFD: Resetting byte context eof (livetv 1 was eof 0)
2012-03-09 21:28:59.684 VideoOutput: Created YV12 OSD.
2012-03-09 21:29:08.251 OSD: Base theme size: 1280x720
2012-03-09 21:29:08.251 OSD: Scaling factors: 1.5x1.5
2012-03-09 21:29:08.289 MythUIHelper, Error: LoadScaleImage(uparrow_alt.png)Unable to find image file
2012-03-09 21:29:08.290 MythUIHelper, Error: LoadScaleImage(downarrow_alt.png)Unable to find image file
2012-03-09 21:29:16.730 TV: OSDDialogEvent: result 3 text Schedule action DIALOG_MENU_SCHEDULE_0
2012-03-09 21:29:18.582 TV: OSDDialogEvent: result 0 text Program Guide action GUIDE
2012-03-09 21:29:18.622 pause_active: 0
2012-03-09 21:29:59.815 OSD: Base theme size: 1280x720
2012-03-09 21:29:59.815 OSD: Scaling factors: 1.5x1.5
2012-03-09 21:29:59.827 MythUIHelper, Error: LoadScaleImage(uparrow_alt.png)Unable to find image file
2012-03-09 21:29:59.828 MythUIHelper, Error: LoadScaleImage(downarrow_alt.png)Unable to find image file
2012-03-09 21:30:06.374 TV: OSDDialogEvent: result 3 text Schedule action DIALOG_MENU_SCHEDULE_0
2012-03-09 21:30:08.176 TV: OSDDialogEvent: result 0 text Program Guide action GUIDE
2012-03-09 21:30:08.209 pause_active: 0
2012-03-09 21:30:16.425 RingBuf(/var/lib/mythtv/livetv/1072_20120309213015.mpg) Warning: Not starting read ahead thread, already running
2012-03-09 21:30:17.366 OSD: Base theme size: 1280x720
2012-03-09 21:30:17.366 OSD: Scaling factors: 0.4125x0.666667
2012-03-09 21:30:17.424 AFD: Opened codec 0x9692090, id(MPEG2VIDEO) type(Video)
2012-03-09 21:30:17.424 AFD: codec AC3 has 2 channels
2012-03-09 21:30:17.424 AFD: Opened codec 0x96f82d0, id(AC3) type(Audio)
2012-03-09 21:30:17.626 AFD: Resetting byte context eof (livetv 1 was eof 0)
2012-03-09 21:30:17.821 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAAAuL
2012-03-09 21:30:17.838 Player(1): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAAAuL
2012-03-09 21:30:17.955 Player(1): Waited 100ms for video buffers UUuUULuAAAAAAAAAAAAAAAAAAAAAAUU
2012-03-09 21:30:17.972 Player(1): Waited 100ms for video buffers UUUUUuUULAAAAAAAAAAAAAAAAAAAAUU
2012-03-09 21:30:18.000 VideoOutput: Created YV12 OSD.
2012-03-09 21:30:32.491 TV: Attempting to change from WatchingLiveTV to None
2012-03-09 21:30:32.534 MythPainter: 3 images not yet de-allocated.
2012-03-09 21:30:32.815 Pulse: PulseAudio resume OK
2012-03-09 21:30:33.350 TV: Changing from WatchingLiveTV to None
2012-03-09 21:31:12.341 Opened DVD device at /dev/dvd
2012-03-09 21:31:12.342 There are 15 titles on the disk
2012-03-09 21:31:12.342 DVDRB: Title 1 has 51 parts.
2012-03-09 21:31:12.342 DVDRB: Title 2 has 2 parts.
2012-03-09 21:31:12.342 DVDRB: Title 3 has 2 parts.
2012-03-09 21:31:12.342 DVDRB: Title 4 has 1 parts.
2012-03-09 21:31:12.342 DVDRB: Title 5 has 1 parts.
2012-03-09 21:31:12.342 DVDRB: Title 6 has 1 parts.
2012-03-09 21:31:12.342 DVDRB: Title 7 has 1 parts.
2012-03-09 21:31:12.342 DVDRB: Title 8 has 1 parts.
2012-03-09 21:31:12.342 DVDRB: Title 9 has 1 parts.
2012-03-09 21:31:12.342 DVDRB: Title 10 has 10 parts.
2012-03-09 21:31:12.342 DVDRB: Title 11 has 19 parts.
2012-03-09 21:31:12.342 DVDRB: Title 12 has 3 parts.
2012-03-09 21:31:12.342 DVDRB: Title 13 has 3 parts.
2012-03-09 21:31:12.342 DVDRB: Title 14 has 1 parts.
2012-03-09 21:31:12.342 DVDRB: Title 15 has 1 parts.
2012-03-09 21:31:12.611 TV: Attempting to change from None to WatchingDVD
2012-03-09 21:31:12.710 Opened DVD device at /dev/dvd
2012-03-09 21:31:12.710 There are 15 titles on the disk
2012-03-09 21:31:12.710 DVDRB: Title 1 has 51 parts.
2012-03-09 21:31:12.710 DVDRB: Title 2 has 2 parts.
2012-03-09 21:31:12.710 DVDRB: Title 3 has 2 parts.
2012-03-09 21:31:12.710 DVDRB: Title 4 has 1 parts.
2012-03-09 21:31:12.710 DVDRB: Title 5 has 1 parts.
2012-03-09 21:31:12.710 DVDRB: Title 6 has 1 parts.
2012-03-09 21:31:12.710 DVDRB: Title 7 has 1 parts.
2012-03-09 21:31:12.710 DVDRB: Title 8 has 1 parts.
2012-03-09 21:31:12.710 DVDRB: Title 9 has 1 parts.
2012-03-09 21:31:12.710 DVDRB: Title 10 has 10 parts.
2012-03-09 21:31:12.710 DVDRB: Title 11 has 19 parts.
2012-03-09 21:31:12.711 DVDRB: Title 12 has 3 parts.
2012-03-09 21:31:12.711 DVDRB: Title 13 has 3 parts.
2012-03-09 21:31:12.711 DVDRB: Title 14 has 1 parts.
2012-03-09 21:31:12.711 DVDRB: Title 15 has 1 parts.
2012-03-09 21:31:12.849 Pulse: PulseAudio suspend OK
2012-03-09 21:31:14.315 DVDRB: Resetting DVD device.
2012-03-09 21:31:14.317 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2012-03-09 21:31:14.318 AFD: Opened codec 0x9693cf0, id(MPEG2VIDEO) type(Video)
2012-03-09 21:31:14.318 AFD: codec AC3 has 6 channels
2012-03-09 21:31:14.318 AFD: Opened codec 0x9fc0770, id(AC3) type(Audio)
2012-03-09 21:31:14.318 AFD: codec AC3 has 2 channels
2012-03-09 21:31:14.318 AFD: Opened codec 0x94979e0, id(AC3) type(Audio)
2012-03-09 21:31:14.319 AFD: codec AC3 has 2 channels
2012-03-09 21:31:14.319 AFD: Opened codec 0x9693340, id(AC3) type(Audio)
2012-03-09 21:31:14.319 AFD: codec AC3 has 2 channels
2012-03-09 21:31:14.319 AFD: Opened codec 0x9f07280, id(AC3) type(Audio)
2012-03-09 21:31:14.320 AFD: codec AC3 has 2 channels
2012-03-09 21:31:14.320 AFD: Opened codec 0xa3ebd80, id(AC3) type(Audio)
2012-03-09 21:31:14.451 Pulse: PulseAudio resume OK
2012-03-09 21:31:14.650 Pulse: PulseAudio suspend OK
2012-03-09 21:31:14.683 AO: Opening audio device 'plughw:CARD=HDMI,DEV=3' ch 2(6) sr 48000 sf signed 16 bit reenc 0
2012-03-09 21:31:14.684 AudioPlayer: Enabling Audio
2012-03-09 21:31:14.703 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2012-03-09 21:31:14.744 OSD: Base theme size: 1280x720
2012-03-09 21:31:14.744 OSD: Scaling factors: 0.5625x0.666667
2012-03-09 21:31:14.787 OSD: Base theme size: 1280x720
2012-03-09 21:31:14.788 OSD: Scaling factors: 0.5625x0.666667
2012-03-09 21:31:14.822 Player(2): Video timing method: DRM
2012-03-09 21:31:14.837 TV: Changing from None to WatchingDVD
2012-03-09 21:31:14.861 VideoOutput: Created YV12 OSD.
2012-03-09 21:31:14.892 AudioPlayer: Disabling Audio, params(0,-1,-1)
2012-03-09 21:31:15.155 Pulse: PulseAudio resume OK
2012-03-09 21:31:15.353 Pulse: PulseAudio suspend OK
2012-03-09 21:31:15.388 AudioPlayer: Disabling Audio, reason is: Aborting Audio Reconfigure. Invalid audio parameters ch -1 fmt 0 @ -1Hz
2012-03-09 21:31:17.253 AFD: Opened codec 0x9fc0770, id(DVD_SUBTITLE) type(Subtitle)
2012-03-09 21:31:17.263 AFD: Opened codec 0x9674640, id(DVD_SUBTITLE) type(Subtitle)
2012-03-09 21:31:25.535 TV: Attempting to change from WatchingDVD to None
2012-03-09 21:31:25.665 Pulse: PulseAudio resume OK
2012-03-09 21:31:25.665 TV: Changing from WatchingDVD to None
2012-03-09 21:31:36.244 Locking input devices
2012-03-09 21:31:37.836 Unlocking input devices
2012-03-09 21:31:40.518 Opened DVD device at /dev/dvd
2012-03-09 21:31:40.519 There are 15 titles on the disk
2012-03-09 21:31:40.519 DVDRB: Title 1 has 51 parts.
2012-03-09 21:31:40.519 DVDRB: Title 2 has 2 parts.
2012-03-09 21:31:40.519 DVDRB: Title 3 has 2 parts.
2012-03-09 21:31:40.519 DVDRB: Title 4 has 1 parts.
2012-03-09 21:31:40.519 DVDRB: Title 5 has 1 parts.
2012-03-09 21:31:40.519 DVDRB: Title 6 has 1 parts.
2012-03-09 21:31:40.519 DVDRB: Title 7 has 1 parts.
2012-03-09 21:31:40.519 DVDRB: Title 8 has 1 parts.
2012-03-09 21:31:40.519 DVDRB: Title 9 has 1 parts.
2012-03-09 21:31:40.519 DVDRB: Title 10 has 10 parts.
2012-03-09 21:31:40.519 DVDRB: Title 11 has 19 parts.
2012-03-09 21:31:40.519 DVDRB: Title 12 has 3 parts.
2012-03-09 21:31:40.519 DVDRB: Title 13 has 3 parts.
2012-03-09 21:31:40.519 DVDRB: Title 14 has 1 parts.
2012-03-09 21:31:40.519 DVDRB: Title 15 has 1 parts.
2012-03-09 21:31:40.586 TV: Attempting to change from None to WatchingDVD
2012-03-09 21:31:40.686 Opened DVD device at /dev/dvd
2012-03-09 21:31:40.686 There are 15 titles on the disk
2012-03-09 21:31:40.686 DVDRB: Title 1 has 51 parts.
2012-03-09 21:31:40.686 DVDRB: Title 2 has 2 parts.
2012-03-09 21:31:40.686 DVDRB: Title 3 has 2 parts.
2012-03-09 21:31:40.686 DVDRB: Title 4 has 1 parts.
2012-03-09 21:31:40.686 DVDRB: Title 5 has 1 parts.
2012-03-09 21:31:40.686 DVDRB: Title 6 has 1 parts.
2012-03-09 21:31:40.686 DVDRB: Title 7 has 1 parts.
2012-03-09 21:31:40.686 DVDRB: Title 8 has 1 parts.
2012-03-09 21:31:40.686 DVDRB: Title 9 has 1 parts.
2012-03-09 21:31:40.686 DVDRB: Title 10 has 10 parts.
2012-03-09 21:31:40.686 DVDRB: Title 11 has 19 parts.
2012-03-09 21:31:40.686 DVDRB: Title 12 has 3 parts.
2012-03-09 21:31:40.686 DVDRB: Title 13 has 3 parts.
2012-03-09 21:31:40.686 DVDRB: Title 14 has 1 parts.
2012-03-09 21:31:40.686 DVDRB: Title 15 has 1 parts.
2012-03-09 21:31:40.876 Pulse: PulseAudio suspend OK
2012-03-09 21:31:40.932 DVDRB: Resetting DVD device.
2012-03-09 21:31:40.935 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2012-03-09 21:31:40.935 AFD: Opened codec 0x9fbd390, id(MPEG2VIDEO) type(Video)
2012-03-09 21:31:40.935 AFD: codec AC3 has 6 channels
2012-03-09 21:31:40.936 AFD: Opened codec 0x9675600, id(AC3) type(Audio)
2012-03-09 21:31:40.936 AFD: codec AC3 has 2 channels
2012-03-09 21:31:40.936 AFD: Opened codec 0x95ec780, id(AC3) type(Audio)
2012-03-09 21:31:40.936 AFD: codec AC3 has 2 channels
2012-03-09 21:31:40.937 AFD: Opened codec 0x97399e0, id(AC3) type(Audio)
2012-03-09 21:31:40.937 AFD: codec AC3 has 2 channels
2012-03-09 21:31:40.937 AFD: Opened codec 0x97902b0, id(AC3) type(Audio)
2012-03-09 21:31:40.937 AFD: codec AC3 has 2 channels
2012-03-09 21:31:40.938 AFD: Opened codec 0x9fe21d0, id(AC3) type(Audio)
2012-03-09 21:31:41.077 Pulse: PulseAudio resume OK
2012-03-09 21:31:41.281 Pulse: PulseAudio suspend OK
2012-03-09 21:31:41.315 AO: Opening audio device 'plughw:CARD=HDMI,DEV=3' ch 2(6) sr 48000 sf signed 16 bit reenc 0
2012-03-09 21:31:41.316 AudioPlayer: Enabling Audio
2012-03-09 21:31:41.330 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2012-03-09 21:31:41.373 OSD: Base theme size: 1280x720
2012-03-09 21:31:41.373 OSD: Scaling factors: 0.5625x0.666667
2012-03-09 21:31:41.399 OSD: Base theme size: 1280x720
2012-03-09 21:31:41.399 OSD: Scaling factors: 0.5625x0.666667
2012-03-09 21:31:41.421 Player(2): Video timing method: DRM
2012-03-09 21:31:41.437 TV: Changing from None to WatchingDVD
2012-03-09 21:31:41.460 VideoOutput: Created YV12 OSD.
2012-03-09 21:31:41.505 AudioPlayer: Disabling Audio, params(0,-1,-1)
2012-03-09 21:31:41.778 Pulse: PulseAudio resume OK
2012-03-09 21:31:41.977 Pulse: PulseAudio suspend OK
2012-03-09 21:31:42.014 AudioPlayer: Disabling Audio, reason is: Aborting Audio Reconfigure. Invalid audio parameters ch -1 fmt 0 @ -1Hz
2012-03-09 21:31:43.561 AFD: Opened codec 0x9f57650, id(DVD_SUBTITLE) type(Subtitle)
2012-03-09 21:31:43.562 AFD: Opened codec 0x9f5a280, id(DVD_SUBTITLE) type(Subtitle)
2012-03-09 21:31:57.408 TV: Attempting to change from WatchingDVD to None
2012-03-09 21:31:57.592 Pulse: PulseAudio resume OK
2012-03-09 21:31:57.592 TV: Changing from WatchingDVD to None
2012-03-09 21:32:33.450 TV: Attempting to change from None to WatchingPreRecorded
2012-03-09 21:32:33.623 Pulse: PulseAudio suspend OK
2012-03-09 21:32:33.731 AFD: Opened codec 0x95e1200, id(MPEG2VIDEO) type(Video)
2012-03-09 21:32:33.732 AFD: codec AC3 has 6 channels
2012-03-09 21:32:33.732 AFD: Opened codec 0x95e15e0, id(AC3) type(Audio)
2012-03-09 21:32:33.732 AFD: codec AC3 has 2 channels
2012-03-09 21:32:33.732 AFD: Opened codec 0x95e1d20, id(AC3) type(Audio)
2012-03-09 21:32:33.927 Pulse: PulseAudio resume OK
2012-03-09 21:32:34.124 Pulse: PulseAudio suspend OK
2012-03-09 21:32:34.163 AO: Opening audio device 'plughw:CARD=HDMI,DEV=3' ch 2(6) sr 48000 sf signed 16 bit reenc 0
2012-03-09 21:32:34.164 AudioPlayer: Enabling Audio
2012-03-09 21:32:34.512 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2012-03-09 21:32:34.601 OSD: Base theme size: 1280x720
2012-03-09 21:32:34.601 OSD: Scaling factors: 1x1
2012-03-09 21:32:34.646 OSD: Base theme size: 1280x720
2012-03-09 21:32:34.646 OSD: Scaling factors: 1x1
2012-03-09 21:32:34.687 Player(3): Video timing method: DRM
2012-03-09 21:32:34.703 TV: Changing from None to WatchingPreRecorded
2012-03-09 21:32:34.785 VideoOutput: Created YV12 OSD.
2012-03-09 21:32:43.102 TV: Attempting to change from WatchingPreRecorded to None
2012-03-09 21:32:43.344 Pulse: PulseAudio resume OK
2012-03-09 21:32:43.395 TV: Changing from WatchingPreRecorded to None
2012-03-09 21:33:00.116 TV: Attempting to change from None to WatchingVideo
2012-03-09 21:33:00.559 Pulse: PulseAudio suspend OK
2012-03-09 21:33:00.721 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2012-03-09 21:33:00.721 AFD: Opened codec 0x97690c0, id(H264) type(Video)
2012-03-09 21:33:00.721 AFD: codec AAC has 2 channels
2012-03-09 21:33:00.723 AFD: Opened codec 0x9769490, id(AAC) type(Audio)
2012-03-09 21:33:00.867 Pulse: PulseAudio resume OK
2012-03-09 21:33:01.064 Pulse: PulseAudio suspend OK
2012-03-09 21:33:01.103 AO: Opening audio device 'plughw:CARD=HDMI,DEV=3' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2012-03-09 21:33:01.105 AudioPlayer: Enabling Audio
2012-03-09 21:33:01.117 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2012-03-09 21:33:01.154 OSD: Base theme size: 1280x720
2012-03-09 21:33:01.154 OSD: Scaling factors: 0.5625x0.561111
2012-03-09 21:33:01.196 OSD: Base theme size: 1280x720
2012-03-09 21:33:01.196 OSD: Scaling factors: 0.5625x0.561111
2012-03-09 21:33:01.236 Player(4): Video timing method: DRM
2012-03-09 21:33:01.252 TV: Changing from None to WatchingVideo
2012-03-09 21:33:01.301 VideoOutput: Created YV12 OSD.
2012-03-09 21:33:09.764 TV: Attempting to change from WatchingVideo to None
2012-03-09 21:33:09.973 Pulse: PulseAudio resume OK
2012-03-09 21:33:10.024 TV: Changing from WatchingVideo to None
2012-03-09 21:33:43.158 NetContent: Internet Content Source BBC iPlayer Updating...
2012-03-09 21:33:56.113 NetContent: Internet Content Source BBC iPlayer completed download, beginning processing...
2012-03-09 21:34:19.190 NetContent: Internet Content Source BBC iPlayer completed processing, marking as updated.
2012-03-09 21:34:19.218 NetContent: Internet Content Source Comedy Central Updating...
2012-03-09 21:34:22.197 NetContent: Internet Content Source Comedy Central completed download, beginning processing...
2012-03-09 21:34:22.267 NetContent: Internet Content Source Comedy Central completed processing, marking as updated.
2012-03-09 21:34:22.269 NetContent: Internet Content Source Hulu Updating...
2012-03-09 21:34:24.814 NetContent: Internet Content Source Hulu completed download, beginning processing...
2012-03-09 21:34:28.206 NetContent: Internet Content Source Hulu completed processing, marking as updated.
2012-03-09 21:34:28.213 NetContent: Internet Content Source The WB Updating...
2012-03-09 21:34:46.797 NetContent: Internet Content Source The WB completed download, beginning processing...
2012-03-09 21:38:47.791 NetContent: Internet Content Source The WB completed processing, marking as updated.
2012-03-09 21:38:47.877 NetContent: Internet Content Source YouTube Updating...
2012-03-09 21:39:28.002 NetContent: Internet Content Source YouTube completed download, beginning processing...
2012-03-09 21:40:13.655 NetContent: Internet Content Source YouTube completed processing, marking as updated.
2012-03-09 21:58:37.543 MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
2012-03-09 21:58:37.571 MythUIWebBrowser: enabling plugins
2012-03-09 22:00:29.694 MythUIWebBrowser: Loading css from - file:///usr/share/mythtv/themes/default/htmls/mythbrowser.css
2012-03-09 22:00:29.696 MythUIWebBrowser: enabling plugins
2012-03-09 22:01:44.573 Found Browseable Source BBC iPlayer...
2012-03-09 22:01:44.573 Found Browseable Source blip.tv...
2012-03-09 22:01:44.573 Found Browseable Source Comedy Central...
2012-03-09 22:01:44.573 Found Browseable Source Dailymotion...
2012-03-09 22:01:44.573 Found Browseable Source Hulu...
2012-03-09 22:01:44.573 Found Browseable Source MTV...
2012-03-09 22:01:44.573 Found Browseable Source Revision3...
2012-03-09 22:01:44.574 Found Browseable Source TedTalks...
2012-03-09 22:01:44.574 Found Browseable Source The WB...
2012-03-09 22:01:44.574 Found Browseable Source Movie Trailers...
2012-03-09 22:01:44.574 Found Browseable Source YouTube...
2012-03-09 22:02:21.252 MythFontProperties, Error: Unknown tag in font 'largetitle'
2012-03-09 22:02:21.284 Couldn't find any game handlers!
2012-03-09 22:02:21.361 Error preparing query: select distinct ,system,year,genre,gamename from gamemetadata where 1=0 and favorite=1 and  display = 1  order by ;
2012-03-09 22:02:21.362 Driver error was [2/1064]:
2012-03-09 22:02:23.950 Error preparing query: select distinct ,system,year,genre,gamename from gamemetadata where 1=0 and  display = 1  order by ;
2012-03-09 22:02:23.950 Driver error was [2/1064]:
2012-03-09 22:02:29.870 Error preparing query: select distinct ,system,year,genre,gamename from gamemetadata where 1=0 and  display = 1  order by ;
2012-03-09 22:02:29.870 Driver error was [2/1064]:
2012-03-09 22:02:34.179 Error preparing query: select distinct ,system,year,genre,gamename from gamemetadata where 1=0 and  display = 1  order by ;
2012-03-09 22:02:34.179 Driver error was [2/1064]:
2012-03-09 22:02:42.372 TV: Attempting to change from None to WatchingLiveTV
2012-03-09 22:02:42.372 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2012-03-09 22:02:42.375 Using protocol version 63
2012-03-09 22:02:42.461 Spawning LiveTV Recorder -- begin
2012-03-09 22:02:43.033 Spawning LiveTV Recorder -- end
2012-03-09 22:02:43.038 We have a playbackURL(/var/lib/mythtv/livetv/1623_20120309220243.mpg) & cardtype(DUMMY)
2012-03-09 22:02:43.038 We have a RingBuffer
2012-03-09 22:02:43.246 Pulse: PulseAudio suspend OK
2012-03-09 22:02:43.297 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2012-03-09 22:02:43.343 OSD: Base theme size: 1280x720
2012-03-09 22:02:43.343 OSD: Scaling factors: 0.5625x0.8
2012-03-09 22:02:43.381 OSD: Base theme size: 1280x720
2012-03-09 22:02:43.381 OSD: Scaling factors: 0.5625x0.8
2012-03-09 22:02:43.417 Player(5): Video timing method: DRM
2012-03-09 22:02:43.433 TV: Changing from None to WatchingLiveTV
2012-03-09 22:02:43.433 TV: State is LiveTV & mctx == ctx
2012-03-09 22:02:43.435 TV: UpdateOSDInput done
2012-03-09 22:02:43.435 TV: UpdateLCD done
2012-03-09 22:02:43.435 TV: ITVRestart done
2012-03-09 22:02:44.983 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2012-03-09 22:02:45.199 OSD: Base theme size: 1280x720
2012-03-09 22:02:45.199 OSD: Scaling factors: 1.5x1.5
2012-03-09 22:02:45.289 AFD: Opened codec 0x9dc53f0, id(MPEG2VIDEO) type(Video)
2012-03-09 22:02:45.289 AFD: codec AC3 has 2 channels
2012-03-09 22:02:45.289 AFD: Opened codec 0x9effe30, id(AC3) type(Audio)
2012-03-09 22:02:45.289 AFD: codec AC3 has 1 channels
2012-03-09 22:02:45.295 AFD: Opened codec 0xb28bb60, id(AC3) type(Audio)
2012-03-09 22:02:45.554 Pulse: PulseAudio resume OK
2012-03-09 22:02:45.757 Pulse: PulseAudio suspend OK
2012-03-09 22:02:45.803 AO: Opening audio device 'plughw:CARD=HDMI,DEV=3' ch 2(2) sr 48000 sf signed 16 bit reenc 1
2012-03-09 22:02:45.805 AudioPlayer: Enabling Audio
2012-03-09 22:02:45.888 AFD: Resetting byte context eof (livetv 1 was eof 0)
2012-03-09 22:02:46.627 VideoOutput: Created YV12 OSD.
2012-03-09 22:02:56.737 BrowseDispInfo()
2012-03-09 22:02:56.737 BrowseStart()
2012-03-09 22:02:56.744 browsechanid: 1623 -> 1624
2012-03-09 22:02:57.620 BrowseDispInfo()
2012-03-09 22:02:57.621 BrowseStart()
2012-03-09 22:02:57.626 browsechanid: 1624 -> 1626
2012-03-09 22:02:58.963 BrowseEnd()
2012-03-09 22:03:01.753 RingBuf(/var/lib/mythtv/livetv/1626_20120309220301.mpg) Warning: Not starting read ahead thread, already running
2012-03-09 22:03:02.668 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:02.669 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:02.669 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:02.669 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:02.670 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:02.670 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:02.670 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:02.671 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:02.671 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:02.671 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:02.672 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:02.672 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:02.672 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:02.673 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:04.411 RingBuf(/var/lib/mythtv/livetv/1626_20120309220301.mpg): Waited 0.2 seconds for data 
2012-03-09 22:03:05.756 AFD: Opened codec 0x9effe30, id(MPEG2VIDEO) type(Video)
2012-03-09 22:03:05.756 AFD: codec AC3 has 6 channels
2012-03-09 22:03:05.756 AFD: Opened codec 0xa924b60, id(AC3) type(Audio)
2012-03-09 22:03:05.756 AFD: codec AC3 has 2 channels
2012-03-09 22:03:05.757 AFD: Opened codec 0x96f0d50, id(AC3) type(Audio)
2012-03-09 22:03:06.069 AO: Opening audio device 'plughw:CARD=HDMI,DEV=3' ch 2(6) sr 48000 sf signed 16 bit reenc 0
2012-03-09 22:03:06.134 AFD: Resetting byte context eof (livetv 1 was eof 0)
2012-03-09 22:03:06.449 Player(5): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAAAAAAAAAuULL
2012-03-09 22:03:10.274 TV: Attempting to change from WatchingLiveTV to None
2012-03-09 22:03:10.600 Pulse: PulseAudio resume OK
2012-03-09 22:03:11.128 TV: Changing from WatchingLiveTV to None
2012-03-09 22:03:20.525 TV: Attempting to change from None to WatchingLiveTV
2012-03-09 22:03:20.525 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2012-03-09 22:03:20.527 Using protocol version 63
2012-03-09 22:03:20.708 Spawning LiveTV Recorder -- begin
2012-03-09 22:03:20.899 Spawning LiveTV Recorder -- end
2012-03-09 22:03:20.904 We have a playbackURL(/var/lib/mythtv/livetv/1626_20120309220320.mpg) & cardtype(DUMMY)
2012-03-09 22:03:20.904 We have a RingBuffer
2012-03-09 22:03:21.105 Pulse: PulseAudio suspend OK
2012-03-09 22:03:21.156 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2012-03-09 22:03:21.207 OSD: Base theme size: 1280x720
2012-03-09 22:03:21.207 OSD: Scaling factors: 0.5625x0.8
2012-03-09 22:03:21.239 OSD: Base theme size: 1280x720
2012-03-09 22:03:21.239 OSD: Scaling factors: 0.5625x0.8
2012-03-09 22:03:21.264 Player(5): Video timing method: DRM
2012-03-09 22:03:21.280 TV: Changing from None to WatchingLiveTV
2012-03-09 22:03:21.280 TV: State is LiveTV & mctx == ctx
2012-03-09 22:03:21.281 TV: UpdateOSDInput done
2012-03-09 22:03:21.282 TV: UpdateLCD done
2012-03-09 22:03:21.282 TV: ITVRestart done
2012-03-09 22:03:21.367 VideoOutput: Created YV12 OSD.
2012-03-09 22:03:22.370 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:22.431 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:22.496 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:22.497 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:22.562 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:22.562 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:22.562 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:22.627 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:22.693 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:22.694 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:22.758 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:22.759 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:22.824 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:22.889 [mpeg2video @ 0x179db40]mpeg_decode_postinit() failure
2012-03-09 22:03:24.994 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2012-03-09 22:03:25.202 OSD: Base theme size: 1280x720
2012-03-09 22:03:25.202 OSD: Scaling factors: 1.5x1.5
2012-03-09 22:03:25.235 AFD: Opened codec 0xb28bb60, id(MPEG2VIDEO) type(Video)
2012-03-09 22:03:25.235 AFD: codec AC3 has 6 channels
2012-03-09 22:03:25.236 AFD: Opened codec 0x9dc53f0, id(AC3) type(Audio)
2012-03-09 22:03:25.236 AFD: codec AC3 has 2 channels
2012-03-09 22:03:25.236 AFD: Opened codec 0xa222ec0, id(AC3) type(Audio)
2012-03-09 22:03:25.410 Pulse: PulseAudio resume OK
2012-03-09 22:03:25.608 Pulse: PulseAudio suspend OK
2012-03-09 22:03:25.653 AO: Opening audio device 'plughw:CARD=HDMI,DEV=3' ch 2(6) sr 48000 sf signed 16 bit reenc 0
2012-03-09 22:03:25.655 AudioPlayer: Enabling Audio
2012-03-09 22:03:25.769 AFD: Resetting byte context eof (livetv 1 was eof 0)
2012-03-09 22:03:26.197 VideoOutput: Created YV12 OSD.
2012-03-09 22:03:30.662 BrowseDispInfo()
2012-03-09 22:03:30.662 BrowseStart()
2012-03-09 22:03:30.669 browsechanid: 1626 -> 1625
2012-03-09 22:03:31.529 BrowseDispInfo()
2012-03-09 22:03:31.529 BrowseStart()
2012-03-09 22:03:31.534 browsechanid: 1625 -> 1071
2012-03-09 22:03:32.597 BrowseDispInfo()
2012-03-09 22:03:32.597 BrowseStart()
2012-03-09 22:03:32.603 browsechanid: 1071 -> 1625
2012-03-09 22:03:33.431 BrowseDispInfo()
2012-03-09 22:03:33.431 BrowseStart()
2012-03-09 22:03:33.438 browsechanid: 1625 -> 1071
2012-03-09 22:03:35.234 BrowseEnd()
2012-03-09 22:03:39.507 TV: Attempting to change from WatchingLiveTV to None
2012-03-09 22:03:39.728 Pulse: PulseAudio resume OK
2012-03-09 22:03:40.142 TV: Changing from WatchingLiveTV to None
2012-03-09 22:03:43.084 Pulse: Cleaning up PulseHandler
2012-03-09 22:03:43.086 Deleting UPnP client...
2012-03-09 22:04:59.155 mythfrontend version: fixes/0.24 [v0.24.1-80-g1de0431] www.mythtv.org
2012-03-09 22:04:59.155 Using runtime prefix = /usr
2012-03-09 22:04:59.155 Using configuration directory = /home/guido/.mythtv
2012-03-09 22:04:59.174 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2012-03-09 22:05:00.024 DBPassword is not set in mysql.txt
2012-03-09 22:05:00.024 Empty LocalHostName.
2012-03-09 22:05:00.024 Using localhost value of guido-desktop
2012-03-09 22:05:00.043 New DB connection, total: 1
2012-03-09 22:05:00.047 Connected to database 'mythconverg' at host: localhost
2012-03-09 22:05:00.050 Closing DB connection named 'DBManager0'
2012-03-09 22:05:00.051 Connected to database 'mythconverg' at host: localhost
2012-03-09 22:05:00.053 Current locale en_US
2012-03-09 22:05:00.053 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2012-03-09 22:05:00.267 ScreenSaverX11Private: XScreenSaver support enabled
2012-03-09 22:05:00.267 ScreenSaverX11Private: Gnome screen saver support enabled
2012-03-09 22:05:00.268 DPMS is disabled.
2012-03-09 22:05:00.282 Desktop video mode: 1360x768 59.960 Hz
2012-03-09 22:05:00.570 Enabled verbose msgs:  important general
2012-03-09 22:05:00.574 Loading en_us translation for module mythfrontend
2012-03-09 22:05:00.584 LIRC: Successfully initialized '/dev/lircd' using '/home/guido/.mythtv/lircrc' config
2012-03-09 22:05:00.584 JoystickMenuThread: Joystick disabled - Failed to read /home/guido/.mythtv/joystickmenurc
2012-03-09 22:05:00.615 Using Frameless Window
2012-03-09 22:05:00.615 Using Full Screen Window
2012-03-09 22:05:00.772 Using the Qt painter
2012-03-09 22:05:01.197 Current MythTV Schema Version (DBSchemaVer): 1264
2012-03-09 22:05:01.199 New DB connection, total: 2
2012-03-09 22:05:01.199 Connected to database 'mythconverg' at host: localhost
2012-03-09 22:05:01.679 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/BlackCurves-OSD/themeinfo.xml
2012-03-09 22:05:01.679 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/BlackCurves-OSD) is missing a themeinfo.xml file.
2012-03-09 22:05:01.681 ThemeInfo, Warning: Unable to open themeinfo.xml for /usr/share/mythtv/themes/Gray-OSD/themeinfo.xml
2012-03-09 22:05:01.681 ThemeInfo, Error: The theme (/usr/share/mythtv/themes/Gray-OSD) is missing a themeinfo.xml file.
2012-03-09 22:05:02.045 Pulse: PulseAudio suspend OK
2012-03-09 22:05:02.240 Pulse: PulseAudio resume OK
2012-03-09 22:05:02.353 Registering Internal as a media playback plugin.
2012-03-09 22:05:02.410 Loading en_us translation for module mytharchive
2012-03-09 22:05:02.415 Registering WebBrowser as a media playback plugin.
2012-03-09 22:05:02.415 Loading en_us translation for module mythbrowser
2012-03-09 22:05:02.466 MediaMonitorUnix::AddDevice() - empty device path.
2012-03-09 22:05:02.467 MediaMonitorUnix::AddDevice() - empty device path.
2012-03-09 22:05:02.467 MediaMonitorUnix::AddDevice() - empty device path.
2012-03-09 22:05:02.467 MonitorRegisterExtensions(0x100, gif,jpg,png)
2012-03-09 22:05:02.484 Loading en_us translation for module mythgallery
2012-03-09 22:05:02.516 Loading en_us translation for module mythgame
2012-03-09 22:05:02.624 Current MythMusic Schema Version (MusicDBSchemaVer): 1017
2012-03-09 22:05:02.666 MonitorRegisterExtensions(0x40, mp3,mp2,ogg,oga,flac,wma,wav,ac3,oma,omg,atp,ra,dts,aac,m4a,aa3,tta,mka,aiff,swa,wv)
2012-03-09 22:05:02.672 Loading en_us translation for module mythmusic
2012-03-09 22:05:02.675 Loading en_us translation for module mythnetvision
2012-03-09 22:05:02.700 Loading en_us translation for module mythnews
2012-03-09 22:05:02.724 Current MythVideo Schema Version (mythvideo.DBSchemaVer): 1038
2012-03-09 22:05:02.743 Loading en_us translation for module mythvideo
2012-03-09 22:05:02.750 Loading en_us translation for module mythweather
2012-03-09 22:05:02.919 Found mainmenu.xml for theme 'Mythbuntu'
2012-03-09 22:05:03.179 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2012-03-09 22:05:03.180 Using protocol version 63
2012-03-09 22:05:06.327 TV: Attempting to change from None to WatchingLiveTV
2012-03-09 22:05:06.327 MythCoreContext: Connecting to backend server: 127.0.0.1:6543 (try 1 of 1)
2012-03-09 22:05:06.328 Using protocol version 63
2012-03-09 22:05:06.437 Spawning LiveTV Recorder -- begin
2012-03-09 22:05:06.960 Spawning LiveTV Recorder -- end
2012-03-09 22:05:06.966 We have a playbackURL(/var/lib/mythtv/livetv/1626_20120309220506.mpg) & cardtype(DUMMY)
2012-03-09 22:05:06.966 We have a RingBuffer
2012-03-09 22:05:07.145 Pulse: PulseAudio suspend OK
2012-03-09 22:05:07.217 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2012-03-09 22:05:07.266 OSD: Base theme size: 1280x720
2012-03-09 22:05:07.267 OSD: Scaling factors: 0.5625x0.8
2012-03-09 22:05:07.296 OSD: Base theme size: 1280x720
2012-03-09 22:05:07.296 OSD: Scaling factors: 0.5625x0.8
2012-03-09 22:05:07.328 Player(0): Video timing method: DRM
2012-03-09 22:05:07.344 TV: Changing from None to WatchingLiveTV
2012-03-09 22:05:07.344 TV: State is LiveTV & mctx == ctx
2012-03-09 22:05:07.347 TV: UpdateOSDInput done
2012-03-09 22:05:07.347 TV: UpdateLCD done
2012-03-09 22:05:07.347 TV: ITVRestart done
2012-03-09 22:05:07.433 VideoOutput: Created YV12 OSD.
2012-03-09 22:05:08.500 [mpeg2video @ 0x1b5ab40]mpeg_decode_postinit() failure
2012-03-09 22:05:08.559 [mpeg2video @ 0x1b5ab40]mpeg_decode_postinit() failure
2012-03-09 22:05:08.560 [mpeg2video @ 0x1b5ab40]mpeg_decode_postinit() failure
2012-03-09 22:05:08.564 [mpeg2video @ 0x1b5ab40]mpeg_decode_postinit() failure
2012-03-09 22:05:08.630 [mpeg2video @ 0x1b5ab40]mpeg_decode_postinit() failure
2012-03-09 22:05:08.631 [mpeg2video @ 0x1b5ab40]mpeg_decode_postinit() failure
2012-03-09 22:05:08.631 [mpeg2video @ 0x1b5ab40]mpeg_decode_postinit() failure
2012-03-09 22:05:08.695 [mpeg2video @ 0x1b5ab40]mpeg_decode_postinit() failure
2012-03-09 22:05:08.761 [mpeg2video @ 0x1b5ab40]mpeg_decode_postinit() failure
2012-03-09 22:05:08.761 [mpeg2video @ 0x1b5ab40]mpeg_decode_postinit() failure
2012-03-09 22:05:08.826 [mpeg2video @ 0x1b5ab40]mpeg_decode_postinit() failure
2012-03-09 22:05:08.827 [mpeg2video @ 0x1b5ab40]mpeg_decode_postinit() failure
2012-03-09 22:05:08.892 [mpeg2video @ 0x1b5ab40]mpeg_decode_postinit() failure
2012-03-09 22:05:08.958 [mpeg2video @ 0x1b5ab40]mpeg_decode_postinit() failure
2012-03-09 22:05:10.944 VideoOutputXv: XVideo Adaptor Name: 'Radeon Textured Video'
2012-03-09 22:05:11.271 OSD: Base theme size: 1280x720
2012-03-09 22:05:11.271 OSD: Scaling factors: 1.5x1.5
2012-03-09 22:05:11.301 AFD: Opened codec 0x8e36bb0, id(MPEG2VIDEO) type(Video)
2012-03-09 22:05:11.301 AFD: codec AC3 has 6 channels
2012-03-09 22:05:11.303 AFD: Opened codec 0x95889b0, id(AC3) type(Audio)
2012-03-09 22:05:11.303 AFD: codec AC3 has 2 channels
2012-03-09 22:05:11.303 AFD: Opened codec 0x959d260, id(AC3) type(Audio)
2012-03-09 22:05:11.452 Pulse: PulseAudio resume OK
2012-03-09 22:05:11.652 Pulse: PulseAudio suspend OK
2012-03-09 22:05:11.690 AO: Opening audio device 'plughw:CARD=HDMI,DEV=3' ch 2(6) sr 48000 sf signed 16 bit reenc 0
2012-03-09 22:05:11.692 AudioPlayer: Enabling Audio
2012-03-09 22:05:11.775 AFD: Resetting byte context eof (livetv 1 was eof 0)
2012-03-09 22:05:12.274 VideoOutput: Created YV12 OSD.
2012-03-09 22:05:28.676 TV: Attempting to change from WatchingLiveTV to None
2012-03-09 22:05:28.725 MythPainter: 2 images not yet de-allocated.
2012-03-09 22:05:28.879 Pulse: PulseAudio resume OK
2012-03-09 22:05:29.377 TV: Changing from WatchingLiveTV to None
2012-03-09 22:05:31.600 Pulse: Cleaning up PulseHandler
2012-03-09 22:05:31.601 Deleting UPnP client...

```

any help is greatly appreciated.  all the help I've received so far is also greatly appreciated.

---

### Post by drfreakynutz on 2012-03-10
also there seems to be two resolutions that the log file indicates both 1280x720 and 1360x768

I'm not sure if one of those resolutions might cause the tv to switch to analog audio or something.

---

### Post by nickrout on 2012-03-10
I think you need to compare the logs when audio is working with when it isn't working.

---

### Post by donb21 on 2012-03-10
[FONT=Verdana][SIZE=2]I do[/SIZE][/FONT][FONT=Verdana][SIZE=2]n't want to m[/SIZE][/FONT][FONT=Verdana][SIZE=2]ess-up you train of troubleshooting, but was wondering if you checked to see if the driver was loading in /etc/modprobe.d/alsa-base.conf?  This is the instruction for the Nvidia hardware:
[/SIZE][/FONT]    [FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
  
[FONT=Verdana][SIZE=2][FONT=Calibri]Add the driver to /etc/modprobe.d/alsa-base.conf (in MythDora, it was dist-alsa.conf)[/FONT][/SIZE][/FONT]
  [FONT=Verdana][SIZE=2][FONT=Calibri]- open alsa-base.conf with an editor[/FONT][/SIZE][/FONT]
  [FONT=Verdana][SIZE=2][FONT=Calibri]- add this line to the end of the file[/FONT][/SIZE][/FONT]
  
  [FONT=Verdana][SIZE=2][FONT=Calibri]options snd-hda-intel enable_msi=0[/FONT][/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]
Don't know what the line is for ATI hardware, but it might be similar.
[/SIZE][/FONT]

---

### Post by nickrout on 2012-03-10
> **donb21 said:**
> [FONT=Verdana][SIZE=2]I do[/SIZE][/FONT][FONT=Verdana][SIZE=2]n't want to m[/SIZE][/FONT][FONT=Verdana][SIZE=2]ess-up you train of troubleshooting, but was wondering if you checked to see if the driver was loading in /etc/modprobe.d/alsa-base.conf?  This is the instruction for the Nvidia hardware:
[/SIZE][/FONT]    [FONT=Verdana][SIZE=2]
[/SIZE][/FONT]
  
[FONT=Verdana][SIZE=2][FONT=Calibri]Add the driver to /etc/modprobe.d/alsa-base.conf (in MythDora, it was dist-alsa.conf)[/FONT][/SIZE][/FONT]
  [FONT=Verdana][SIZE=2][FONT=Calibri]- open alsa-base.conf with an editor[/FONT][/SIZE][/FONT]
  [FONT=Verdana][SIZE=2][FONT=Calibri]- add this line to the end of the file[/FONT][/SIZE][/FONT]
  
  [FONT=Verdana][SIZE=2][FONT=Calibri]options snd-hda-intel enable_msi=0[/FONT][/SIZE][/FONT]
  [FONT=Verdana][SIZE=2]
Don't know what the line is for ATI hardware, but it might be similar.
[/SIZE][/FONT]

yeah we have set the correct kernel options I believe.

---

### Post by drfreakynutz on 2012-03-12
> **nickrout said:**
> I think you need to compare the logs when audio is working with when it isn't working.

Any hint on what I might be looking for in the log files. 

it seems that the audio craps out in the middle of watching tv when the signal goes from HD to standard def channels and the system has to adjust to different aspect ratio or resolution.  any way to keep this stuff fro changing so that it doesn't have to adjust?

---

### Post by nickrout on 2012-03-12
> **drfreakynutz said:**
> Any hint on what I might be looking for in the log files. 

it seems that the audio craps out in the middle of watching tv when the signal goes from HD to standard def channels and the system has to adjust to different aspect ratio or resolution.  any way to keep this stuff fro changing so that it doesn't have to adjust?

No, your system gets what your broadcaster sends you.

What are your settings now in audio setup in mythtv frontend settings?

---

### Post by drfreakynutz on 2012-03-12
audio output device = ALSA:plughw:CARD=HDMI,DEV=3
digital audio capabilities
dolby digital = checked, DTS = checked
speaker configuration = 5.1
upconvert stereo to 5.1 surround = checked
upmix quality = best
advanced audio configuration = unchecked

freaking emoticon (it should be a ":" then "p".  no way to type that without getting a smilie)

---

### Post by nickrout on 2012-03-12
Click on the "disable smilies in text" below the box where you type your message (yes it is a PITA!)

The error may be in the upmixing. Try turning it off to see if that is the case.

The other thing is this: is your TV really 5.1 and capable of DD and DTS? (or are you playing into an amplifier?) Sorry you may have given that info before but I haven't the time to trawl through 5 pages of posts :)

---

### Post by misterspider on 2012-03-12
Hi,
I've recently gone through a lot of this kind of thing myself, although I have an NVidia GPU with HDMI out, and have now got the sound and video working through it. I made a quick blog of MythTV screenshots of all my settings and steps of how to do it, [see the link here]("http://archlinux-pcguide.blogspot.com.au/2012/03/sound-using-hdmi-from-gpu.html").

In short, you used
```
$ aplay -l
```
to discover your hardware playback devices. Have you then tried all of the combinations using (for example)
```
$ aplay -D plughw:0,1 /usr/share/sounds/alsa/Front_Center.wav
```
where "0" is the card number and "1" is the device number. If you find a combination that works, you can then create (or edit) your /etc/asound.conf for your whole system, or ~/.asoundrc for individual users.

Actually, I think from your out put in your original post you could use 
```
$ aplay -D plughw:HDMI,3 /usr/share/sounds/alsa/Front_Center.wav
```
which would guard against your card number changing after reboot.

---

### Post by drfreakynutz on 2012-03-13
> **nickrout said:**
> 
The other thing is this: is your TV really 5.1 and capable of DD and DTS? (or are you playing into an amplifier?) Sorry you may have given that info before but I haven't the time to trawl through 5 pages of posts :)

I will try turning off the upmix I thought of that but haven't tried it.

I am passing the signal through the tv to an amplifier that is 5.1 capable and is confirmed receiving a 5.1 signal from the mythtv through the tv when the sound is actually working.

---

### Post by BicyclerBoy on 2012-03-13
So the HT amp is connected by S/PDIF cable to the TV output pass-thru'?

Your TV likely accepts audio modes/rates that the TV will not/can not output over S/PDIF.

The TV most likely does not play DTS. (don't tick)
The TV can not transcode/re-encode..
The TV reports its audio capability over HDMI ELD. This does not match the TV output (spdif).

If you select "upmix best" you could cause:
- all rate to be upsampled to multi-channel LPCM 96KHz or higher
- S/PDIF does not support multi-channel LPCM or >96KHz stereo
- your TV can not resample/tramscode so you get silence.

The best solution is to connect PC-amp directly via HDMI then amp-TV HDMI.
Use the TV-amp S/PDIF for TV only mode..

---

### Post by nickrout on 2012-03-14
> **BicyclerBoy said:**
> So the HT amp is connected by S/PDIF cable to the TV output pass-thru'?

Your TV likely accepts audio modes/rates that the TV will not/can not output over S/PDIF.

The TV most likely does not play DTS. (don't tick)
The TV can not transcode/re-encode..
The TV reports its audio capability over HDMI ELD. This does not match the TV output (spdif).

If you select "upmix best" you could cause:
- all rate to be upsampled to multi-channel LPCM 96KHz or higher
- S/PDIF does not support multi-channel LPCM or >96KHz stereo
- your TV can not resample/tramscode so you get silence.

The best solution is to connect PC-amp directly via HDMI then amp-TV HDMI.
Use the TV-amp S/PDIF for TV only mode..

what he said.

---

### Post by drfreakynutz on 2012-03-17
> **BicyclerBoy said:**
> So the HT amp is connected by S/PDIF cable to the TV output pass-thru'?

Your TV likely accepts audio modes/rates that the TV will not/can not output over S/PDIF.

The TV most likely does not play DTS. (don't tick)
The TV can not transcode/re-encode..
The TV reports its audio capability over HDMI ELD. This does not match the TV output (spdif).

If you select "upmix best" you could cause:
- all rate to be upsampled to multi-channel LPCM 96KHz or higher
- S/PDIF does not support multi-channel LPCM or >96KHz stereo
- your TV can not resample/tramscode so you get silence.

The best solution is to connect PC-amp directly via HDMI then amp-TV HDMI.
Use the TV-amp S/PDIF for TV only mode..

the signal goes from the pc into the tv via hdmi.  the sound goes out from the tv to the amp via optical not hdmi.  this being an older amp there is no hdmi input.  I can still try to uncheck the DTS and see if that solves the problem.  

Having unchecked upmix, I'm still having the sound problem.  It goes out in the middle of watching something and then doesn't come back unless I restart everything.

---

### Post by nickrout on 2012-03-17
I had a problem last night which restarting the frontend computer did not solve, but unplugging and replugging the hdmi cable itself worked. Must have been some handshaking error.

In your scenario, does sound work on the TV but not on the AMP, or not on the TV either?

---

