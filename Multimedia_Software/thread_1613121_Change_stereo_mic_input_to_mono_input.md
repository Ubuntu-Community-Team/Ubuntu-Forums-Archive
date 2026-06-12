---
title: "Change stereo mic input to mono input"
date: 2010-11-04
forum: Multimedia Software
---

### Post by ThatBum on 2010-11-04
Heya. I recently got a real fancy [unidirectional microphone]("http://www.radioshack.com/product/index.jsp?productId=2123173"), but when I go and use it, something strange happens. The mic is a mono mic, but when I record something, it appears to think it's stereo. Instead of having the same thing on both channels, it puts it all in the left channel, and silence on the right channel.

I tried fiddling with alsamixer. In capture (F4),  adjusting the "Capture" device has an effect. However, it doesn't do anything useful. Lowering the right channel to zero does nothing, lowering the left channel to zero creates silence, and disabling the right channel creates silence.

In my System>Preferences>Sound (or pavucontrol, or what-have-you), there are "Analog Stereo Input" and "Analog Stereo Duplex" options there, but no "Analog Mono Input" or "Analog Stereo Output + Analog Mono Input" options (the latter being ideal).

Something interesting, though, if I do this: ```
arecord -r 96000 -D pulse **-c 1** -vv -V mono /dev/null
```it works correctly and outputs on both channels. But if I do ```
arecord -r 96000 -D pulse **-c 2** -vv -V stereo /dev/null
```then it's back to the same behavior. The VU meter on the second command shows the left channel going up and down as I make noise, but the right one always at zero.

The machine does have a crap internal mic built in to the screen bezel. If I do either of the above commands, they both work correctly. The stereo VU shows the same activity for both channels.

The machine is a Eee 1015PED, which has Intel integrated sound. Something probably insignificant is that the mic has a 1/4 inch mono plug, and to get it to plug into the Eee, I needed to get a 1/4 female to 1/8 male adapter. The mic's 1/4 plug is mono (duh) and therefore two-conductor, but the adapter I got is stereo, or three conductor (L, R, GND). I don't know if this is tripping something in hardware to tell it it's stereo or something.

I tried the mic on my desktop, which has a SB Audigy 4 (the non-pro flavor) and that has the "Analog Mono Input" function, so that works fine.

Is there some way to turn this stereo input into mono input?

THANKS!

---

### Post by ThatBum on 2010-11-04
Bump. I realized if I use the mic on the desktop, it doesn't matter if I set it to Mono or Stereo input, the signal comes out both channels either way. Also, I scrounged up a clip mic that came with an old webcam. It's also a mono mic, but it comes out both channels on the netbook. The mic has a stereo 1/8 inch connector on it. I'm starting to think I got the wrong adapter...

E: Here's a screenie from audacity, if it's not clear what I'm talking about.

E2: I got a 1/4 inch mono to 1/8 inch mono adapter, it didn't do anything.

---

