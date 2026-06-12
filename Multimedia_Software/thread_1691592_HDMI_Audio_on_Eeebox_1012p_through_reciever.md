---
title: "HDMI Audio on Eeebox 1012p through reciever"
date: 2011-02-20
forum: Multimedia Software
---

### Post by MaX on 2011-02-20
I've bought a EeeBox PC EB1012 and I've installed Ubuntu 10.10 fresh on it. It's got an Intel soundcard and Nvidia HDMI output. It's the ION2 platform.

So far I've gotten video to work through HDMI by specifying 1080p resolution in Xorg, since that seems to be what my home movie system will recognise (LG HB954PB). Due to strange EDID values from my 32LG3000 TV I can't seem to specify a 720p value.

If I connect my EeeBox directly to the TV I can get good Eld values and sound will pass through HDMI. But when I connect to my reciever I don't seem to get any sound at all.

I've tried most of the threads about getting audio through but nothing seem to work. 

Does anyone have a suggestion on how I can get specify ALSA or preferably Pulse to output 5.1 surround sound signal on my HDMI channel?

---

### Post by MaX on 2011-02-20
So now I actually got sound working through HDMI.

But for some reason it only sends 2.1 channel audio through the HDMI.

The recierver sais it supports 2 as well as 8 channels.
```
:~$ cat /proc/asound/card1/eld#1.0 
```
```
monitor_present		1
eld_valid		1
monitor_name		LG-BDHT
    
connection_type		HDMI
eld_version		[0x2] CEA-861D or below
edid_version		[0x3] CEA-861-B, C or D
manufacture_id		0xe530
product_id		0x0
port_id			0x10000
support_hdcp		0
support_ai		0
audio_sync_delay	0
speakers		[0x4f] FL/FR LFE FC RL/RR RLC/RRC
sad_count		7
sad0_coding_type	[0x1] LPCM
sad0_channels		2
sad0_rates		[0x1ee0] 44100 48000 88200 176400 192000 384000
sad0_bits		[0xe0000] 16 20 24
sad1_coding_type	[0x1] LPCM
sad1_channels		8
sad1_rates		[0x1ee0] 44100 48000 88200 176400 192000 384000
sad1_bits		[0xe0000] 16 20 24
sad2_coding_type	[0x2] AC-3
sad2_channels		8
sad2_rates		[0xe0] 44100 48000 88200
sad2_max_bitrate	640000
sad3_coding_type	[0x7] DTS
sad3_channels		8
sad3_rates		[0xc0] 48000 88200
sad3_max_bitrate	1536000
sad4_coding_type	[0xa] E-AC-3/DD+ (Dolby Digital Plus)
sad4_channels		8
sad4_rates		[0xc0] 48000 88200
sad5_coding_type	[0xb] DTS-HD
sad5_channels		8
sad5_rates		[0x1ee0] 44100 48000 88200 176400 192000 384000
sad6_coding_type	[0xc] MLP (Dolby TrueHD)
sad6_channels		8
sad6_rates		[0x16e0] 44100 48000 88200 176400 192000
```

Any suggestions on how to get 5.1 sound?

speaker-test -d hdmi:NVidia -c6 -twave also generates stereo output.

---

### Post by kapokasa on 2011-03-18
Hi!

I have exactly the same problem. I am running 10.10 64bits on the same eeebox model.

Can you tell me how did you get it to work?

Thanks in advance!

---

### Post by MaX on 2011-05-22
> **kapokasa said:**
> Hi!

I have exactly the same problem. I am running 10.10 64bits on the same eeebox model.

Can you tell me how did you get it to work?

Thanks in advance!


I didn't...

---

