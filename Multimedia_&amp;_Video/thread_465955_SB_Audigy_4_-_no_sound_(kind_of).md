---
title: "SB Audigy 4 - no sound (kind of)"
date: 2007-06-06
forum: Multimedia &amp; Video
---

### Post by august on 2007-06-06
[SIZE="4"]I fixed this by disabling the onboard sound card from the BIOS. Worked instantly, no further configuration was needed![/SIZE]

[COLOR="Gray"]Been googling around for a while now, reading a couple of posts about this. Tried what they suggested, but I'm still in silent, lonely, scary mute mode

My *cat /proc/asound/cards* outputs this:

```

 0 [CK804          ]: NFORCE - NVidia CK804
                      NVidia CK804 with ALC850 at 0xfe02d000, irq 17
 1 [Audigy2        ]: Audigy2 - Audigy 4 [SB0610]
                      Audigy 4 [SB0610] (rev.0, serial:0x10211102) at 0xac00, irq 21


```

It's listed in the "Volume Control" app - the one you get when you double click the volume icon in the top panel thingie on the desktop. I also added all the available channels for my Audigy and made sure noone was muted and on 0 volume.

I also checked the infamous "Audigy Analog/Digital Output Jack". Still no sound. But as weird as it might sound, I hear a small "popping" sound, 100hz'ish - as if something gets turned on in the sound card - when I check that box. When it goes from checked to unchecked. No popping sound from unchecked to checked though.

Also, if I go system -> preferences -> sound in the top panel, select "Multichannel playback" and press the test button, I get a square testing tone. This is only if "IEC958" is switched off.

As if that weren't enough, I can also hear the input from my microphone through my earplugs/speakers (which I can in windows too, so this is a good sign I guess). This is when the "digy Analog/Digital Output Jack" option is checked. Unchecked, I don't hear the mic.

But, playing a CD, .ogg, YouTube video or anything else that creates sound, does not yield anything at all.

Any suggestions welcome, I'm very much in "aaaaaargh work ffs" mode.[/COLOR]

---

### Post by august on 2007-06-09
Fixed this by disabling the onboard sound card in the bios. No further configuration needed, that was all.

---

