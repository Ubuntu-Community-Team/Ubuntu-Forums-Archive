---
title: "[SOLVED] SPDIF Got Dolby Digital passthrough but DTS is downmixing to stereo"
date: 2008-06-19
forum: Multimedia Software
---

### Post by harker on 2008-06-19
Hi,

recently something weird happened on my ubuntu box.

Somehow the onboard sound card enabled itself and completely cut out my sound blaster live.

Anyway, after much pottering around working out why the sound had disappeared on my mythbox, I worked out what the problem was.

So now I have things working again (sort of).

using the following settings

**.asoundrc**
```

pcm.!default {
   type plug
   slave {
        pcm "spdif"
        rate 48000
        format S16_LE
    }
}

```

~/.mplayer/config

```
ac=hwac3,
```

I've managed to get proper Dolby Digital passthrough to my home theatre system. Also standard PCM singals get passed through.

Unfortunately no luck with DTS. The last time passing through all AC3 happened just by specifying the output device. 

I have a number of Dolby Digital/DTS trailer videos that worked before I lost sound. My Home Theatre system registered it was receiving a DTS signal. Now it seems the DTS signal is being downmixed to PCM before being passed through.

Any suggestions??

Cheers

---

### Post by harker on 2008-06-22
Ok so basically a number of things I had already tried I forgot I had done before I had fully diagnosed why my sound card wasn't working.

So to make this work I added the afm=hwac3 so my player config.

```

ac=hwac3,
**afm=hwac3**

```

This now passes through DTS and DD. I noticed that my TV broadcast weren't coming through the sound card at all. Adding this line fixed that too.

Theonyl problem now is that my tv broadcasts aren't coming through as AC3. So will need to look into that.

---

