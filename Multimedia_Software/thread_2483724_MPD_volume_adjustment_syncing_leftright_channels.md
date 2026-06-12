---
title: "MPD volume adjustment syncing left/right channels"
date: 2023-02-07
forum: Multimedia Software
---

### Post by pqwoerituytrueiwoq on 2023-02-07
For this card
```
[FONT=monospace][COLOR=#000000]audio_output { [/COLOR]
[COLOR=#000000]type[/COLOR][COLOR=#000000]"alsa" [/COLOR]
[COLOR=#000000]name[/COLOR][COLOR=#000000]"Bedrooms: ASUS DGX Analog Output" [/COLOR]
[COLOR=#000000]device[/COLOR][COLOR=#000000]"hw:CARD=DGX,DEV=0"[/COLOR][COLOR=#000000]# optional [/COLOR]
[COLOR=#18b2b2]##[/COLOR][COLOR=#18b2b2]mixer_type      "hardware"[/COLOR][COLOR=#18b2b2]# optional[/COLOR]
[COLOR=#18b2b2]##[/COLOR][COLOR=#18b2b2]mixer_device[/COLOR][COLOR=#18b2b2]"default"[/COLOR][COLOR=#18b2b2]# optional[/COLOR]
        mixer_device    "hw:DGX" 
[COLOR=#000000]mixer_control[/COLOR][COLOR=#000000]   "Headphone"[/COLOR][COLOR=#000000]# optional [/COLOR]
[COLOR=#18b2b2]#[/COLOR][COLOR=#18b2b2]mixer_index[/COLOR][COLOR=#18b2b2]"0"[/COLOR][COLOR=#18b2b2]# optional[/COLOR]
[COLOR=#18b2b2]##        buffer_time     "5000000"       # optional[/COLOR]
} 
audio_output { 
        type            "alsa" 
        name            "Kitchen: ASUS DGX Digital Output" 
        device          "iec958:CARD=DGX,DEV=0"     # optional 
        mixer_type      "none"      # optional 
[COLOR=#18b2b2]##      mixer_device    "default"       # optional[/COLOR]
[COLOR=#18b2b2]#        mixer_device    "hw:3"[/COLOR]
[COLOR=#18b2b2]#        mixer_control   "Headphone"     # optional[/COLOR]
[COLOR=#18b2b2]#        mixer_index     "0"             # optional[/COLOR]
[COLOR=#18b2b2]##        buffer_time     "5000000"       # optional[/COLOR]
}
[/FONT]
```
```

[FONT=monospace][COLOR=#000000]$ amixer -c 0 scontents[/COLOR][/FONT]
[FONT=monospace][COLOR=#000000]Simple mixer control 'Headphone',0 [/COLOR]
  Capabilities: pvolume pswitch pswitch-joined 
  Playback channels: Front Left - Front Right 
  Limits: Playback 0 - 255 
  Mono: 
  Front Left: Playback 222 [87%] [-16.25dB] [on] 
  Front Right: Playback 222 [87%] [-16.25dB] [on][/FONT]

```

sometime if i use mpc volume 30 it sets left to 0 and right to 30


Also noticed MPD has my left/right channels reversed

note that [FONT=courier new]$ speaker-test -c 2 shows i have left/right correct
[/FONT]
```

[FONT=monospace][COLOR=#000000]amixer -c 0 scontents [/COLOR]
Simple mixer control 'Headphone',0 
  Capabilities: pvolume pswitch pswitch-joined 
  Playback channels: Front Left - Front Right 
  Limits: Playback 0 - 255 
  Mono: 
  Front Left: Playback 0 [0%] [-125.50dB] [on] 
  Front Right: Playback 193 [76%] [-30.52dB] [on]
[/FONT]
```

this only provide sound via the left speaker

---

