---
title: "Clementine plays back 24bit files in 16bit mode"
date: 2015-02-13
forum: Multimedia Software
---

### Post by kmm2 on 2015-02-13
How can i configure Clementine to play back all files without resampling?


Output of "pacmd list-sink-inputs":
```

    driver: <protocol-native.c>
    flags: START_CORKED 
    state: RUNNING
    sink: 1 <ladspa_output.mbeq_1197.mbeq>
    volume: 0: 100% 1: 100%
            0: 0,00 dB 1: 0,00 dB
            balance 0,00
    muted: no
    current latency: 71,64 ms
    requested latency: 85,33 ms
    sample spec: s16le 2ch 96000Hz
    channel map: front-left,front-right
                 Stereo
    resample method: copy
    module: 11
    client: 57 <Clementine>

```

Same file played back in mplayer:
```

    driver: <protocol-native.c>
    flags: 
    state: RUNNING
    sink: 1 <ladspa_output.mbeq_1197.mbeq>
    volume: 0:  46% 1:  46%
            0: -20,24 dB 1: -20,24 dB
            balance 0,00
    muted: no
    current latency: 198,33 ms
    requested latency: 85,33 ms
    sample spec: s32le 2ch 96000Hz
    channel map: front-left,front-right
                 Stereo
    resample method: copy
    module: 11
    client: 60 <MPlayer>

```

---

### Post by shantiq on 2015-02-14
hi kmm2   i do not think it is necessarily Clementine doing that as

```
    driver: <protocol-native.c>
    flags: START_CORKED 
    state: RUNNING
[B]    sink: 0 <alsa_output.usb-Lexicon_Lexicon_Alpha-00-Alpha.iec958-stereo>
[/B]     volume: 0: 101% 1: 101%
            0: 0.20 dB 1: 0.20 dB
            balance 0.00
    muted: no
    current latency: 56.01 ms
    requested latency: 90.00 ms
[B]    sample spec: float32le 2ch 44100Hz
[/B]     channel map: front-left,front-right
                 Stereo
    resample method: copy
    module: 12
    client: 62 <**Clementine**>
    properties:
        media.name = "'Violin Concerto in D Major, Op. 8, No. 11, RV. 210 - I. Allegro' by 'The Avison Ensemble'"
        application.name = "Clementine"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "28"
        application.process.id = "13041"
        application.process.user = "shantiq"
        application.process.host = "shantiq-00000000000000000000000"
        application.process.binary = "clementine"
        application.language = "en_GB.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "452ba5f8f8ec6c770235436554955327"
        application.process.session_id = "c2"
        application.icon_name = "application-x-clementine"
        module-stream-restore.id = "sink-input-by-application-name:Clementine"
        media.title = "Violin Concerto in D Major, Op. 8, No. 11, RV. 210 - I. Allegro"
        media.artist = "The Avison Ensemble"
```




reading around you probably need the gstreamer from[ here]("http://ubuntuforums.org/showthread.php?t=2250693&highlight=clementine+gstreamer")   more up to date

---

