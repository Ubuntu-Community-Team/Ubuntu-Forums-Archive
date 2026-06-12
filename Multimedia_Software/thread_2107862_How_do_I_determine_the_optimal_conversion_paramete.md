---
title: "How do I determine the optimal conversion parameters for VLC?"
date: 2013-01-22
forum: Multimedia Software
---

### Post by MakOwner on 2013-01-22
This is the input stream - I'm currently capturng it wav format then converting it to mp3 with lame, as I can't get vlc to convert it directly to mp3.  So, which codec will result in a direct capture of the stream so that lame can convert to mp3?


```

[0x7f36900009e8] main generic debug: using decoder module "faad"
[0x7f36900009e8] main generic debug: TIMER module_need() : 6.054 ms - Total 6.054 ms / 1 intvls (Avg 6.054 ms)
[0x7f3690000e28] main encoder debug: looking for encoder module: 12 candidates
[0x7f3690000e28] araw encoder debug: samplerate:44100Hz channels:2 bits/sample:16
[0x7f3690000e28] main encoder debug: using encoder module "araw"
[0x7f3690000e28] main encoder debug: TIMER module_need() : 0.847 ms - Total 0.847 ms / 1 intvls (Avg 0.847 ms)
[0x7f3694001538] stream_out_transcode stream out debug: Looking for filter (f32l->s16l, channels 2->2, rate 44100->44100)
[0x7f3690002e48] main filter debug: looking for audio filter module: 13 candidates
[0x7f3690002e48] audio_format filter debug: f32l->s16l, bits per sample: 32->16
[0x7f3690002e48] main filter debug: using audio filter module "audio_format"
[0x7f3690002e48] main filter debug: TIMER module_need() : 2.639 ms - Total 2.639 ms / 1 intvls (Avg 2.639 ms)
[0x7f3694001538] main stream out debug: Filter 'audio_format' (0x7f3690002e48) appended to chain
[0x7f3694001538] stream_out_transcode stream out debug: Got complete audio filter chain
[0x7f36940019a8] main mux debug: adding a new input
[0x7f36940019a8] mux_wav mux debug: adding 2 input channels, 44100Hz
[0x7f369c000b28] main input debug: Decoder buffering done in 7 ms
[0x7f36900009e8] faad generic warning: decoded zero sample


```

---

