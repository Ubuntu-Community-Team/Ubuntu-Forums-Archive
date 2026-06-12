---
title: "AC3/DTS real time encoder for pulseaudio"
date: 2018-06-09
forum: Multimedia Software
---

### Post by hideman85 on 2018-06-09
Here is my problem my laptop (Debian 8) is connected to my TV via HDMI, itself connected to my 5.1 home theater via SPDIF optical cable.
And SPDIF only allow mono, stereo channels using PCM encoding or multi channels using Dolby format so DTS or AC-3 encoding.

My system correctly detects constraints:

    ```
cat /proc/asound/card0/eld#0.0
    monitor_present        1
    eld_valid        1
    monitor_name        LG TV
    connection_type        HDMI
    eld_version        [0x2] CEA-861D or below
    edid_version        [0x3] CEA-861-B, C or D
    manufacture_id        0x6d1e
    product_id        0x1
    port_id            0x0
    support_hdcp        0
    support_ai        1
    audio_sync_delay    0
    speakers        [0xffff] FL/FR LFE FC RL/RR RC FLC/FRC RLC/RRC FLW/FRW FLH/FRH TC FCH
    sad_count        4
    sad0_coding_type    [0x1] LPCM
    sad0_channels        2
    sad0_rates        [0x14e0] 32000 44100 48000 96000 192000
    sad0_bits        [0xe0000] 16 20 24
    sad1_coding_type    [0x2] AC-3
    sad1_channels        6
    sad1_rates        [0xe0] 32000 44100 48000
    sad1_max_bitrate    640000
    sad2_coding_type    [0xa] E-AC-3/DD+ (Dolby Digital Plus)
    sad2_channels        6
    sad2_rates        [0xe0] 32000 44100 48000
    sad3_coding_type    [0x7] DTS
    sad3_channels        6
    sad3_rates        [0xc0] 44100 48000
    sad3_max_bitrate    1536000 
```

I found a way to view my films using mpv it work because if I understand well it bypass pulseaudio.

    ```
mpv --fullscreen --speed=24000/25025 --hwdec=vaapi --deinterlace=yes --af scaletempo,lavcac3enc=tospdif=yes:bitrate=640:minch=2
```

But I really would like pulseaudio work itself in AC-3 or DTS to have 5.1 sound through SPDIF.

I found a first solution but I have some noise and cracking on audio : 
[https://github.com/darealshinji/dcaenc](https://github.com/darealshinji/dcaenc) 

I found another solution : 
[https://www.linuxquestions.org/questions/linux-hardware-18/alsa-sb-omni-surround-5-1-iec958-is-routed-to-the-analog-output-not-the-digital-output-4175609669/](https://www.linuxquestions.org/questions/linux-hardware-18/alsa-sb-omni-surround-5-1-iec958-is-routed-to-the-analog-output-not-the-digital-output-4175609669/)

But it seems that alsa not able to assign the correct device number :( (I just add that I change device 2 by device $DEV and I add it to input params)

Result : 

    ```
hdmi:CARD=HDMI,DEV=0        HDA Intel HDMI, HDMI 0 (HDMI Audio Output)
    hdmi:CARD=HDMI,DEV=1        HDA Intel HDMI, HDMI 1 (HDMI Audio Output)
    hdmi:CARD=HDMI,DEV=2        HDA Intel HDMI, HDMI 2 (HDMI Audio Output)
    hdmi:CARD=HDMI,DEV=3        HDA Intel HDMI, HDMI 3 (HDMI Audio Output)
    hdmi:CARD=HDMI,DEV=4        HDA Intel HDMI, HDMI 4 (HDMI Audio Output)
    ...
    a52:CARD=HDMI,DEV=3            HDA Intel HDMI, HDMI 0 (IEC958 (AC3) Digital Surround 5.1 with all software conversions)
    a52:CARD=HDMI,DEV=7            HDA Intel HDMI, HDMI 1 (IEC958 (AC3) Digital Surround 5.1 with all software conversions)
    a52:CARD=HDMI,DEV=8            HDA Intel HDMI, HDMI 2 (IEC958 (AC3) Digital Surround 5.1 with all software conversions)
    a52:CARD=HDMI,DEV=9            HDA Intel HDMI, HDMI 3 (IEC958 (AC3) Digital Surround 5.1 with all software conversions)
    a52:CARD=HDMI,DEV=10        HDA Intel HDMI, HDMI 4 (IEC958 (AC3) Digital Surround 5.1 with all software conversions)
    a52upmix:CARD=HDMI,DEV=3    HDA Intel HDMI, HDMI 0 (IEC958 (AC3) Digital Surround 2.0 -> 5.1 with all software conversions)
    a52upmix:CARD=HDMI,DEV=7    HDA Intel HDMI, HDMI 1 (IEC958 (AC3) Digital Surround 2.0 -> 5.1 with all software conversions)
    a52upmix:CARD=HDMI,DEV=8    HDA Intel HDMI, HDMI 2 (IEC958 (AC3) Digital Surround 2.0 -> 5.1 with all software conversions)
    a52upmix:CARD=HDMI,DEV=9    HDA Intel HDMI, HDMI 3 (IEC958 (AC3) Digital Surround 2.0 -> 5.1 with all software conversions)
    a52upmix:CARD=HDMI,DEV=10    HDA Intel HDMI, HDMI 4 (IEC958 (AC3) Digital Surround 2.0 -> 5.1 with all software conversions)
    dcahdmi:CARD=HDMI,DEV=0        HDA Intel HDMI, HDMI 0 (DTS Encoding through HDMI)
    dcahdmi:CARD=HDMI,DEV=1        HDA Intel HDMI, HDMI 1 (DTS Encoding through HDMI)
    dcahdmi:CARD=HDMI,DEV=2        HDA Intel HDMI, HDMI 2 (DTS Encoding through HDMI)
    dcahdmi:CARD=HDMI,DEV=3        HDA Intel HDMI, HDMI 3 (DTS Encoding through HDMI)
    dcahdmi:CARD=HDMI,DEV=4        HDA Intel HDMI, HDMI 4 (DTS Encoding through HDMI)
    ...
```

Full config :  [https://pastebin.com/ZtF9npBD](https://pastebin.com/ZtF9npBD)

I hope to hear from you soon ;)

---

