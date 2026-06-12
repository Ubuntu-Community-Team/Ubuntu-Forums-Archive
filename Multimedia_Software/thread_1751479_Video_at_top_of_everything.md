---
title: "Video at top of everything"
date: 2011-05-06
forum: Multimedia Software
---

### Post by 10robinho on 2011-05-06
I have strange problem that I couldn't even find on google.

When I play any video in VLC or any other player my video is on top of everything.

For example, if I open a video and play it - everything looks ok. But, if I open another window "above" VLC, video suddenly appears at top and I can't see window opened in front of VLC.

This print-screen will make it more clear.

---

### Post by 10robinho on 2011-05-06
I've figured this out, so for others, here is what happened.

This was caused by VLC -> Tools -> Preferences -> Video -> [COLOR=Red]enabled[/COLOR] "Accelerated video output (Overlay)".

So, when I [COLOR=Red]disabled[/COLOR] this, everything worked well.

I think that this was because I've installed VLC from **catalysthacks** ppa, which has va-api support for ATI drivers and that option messed up this configuration.

Just to notice, in Properties -> Input and Codecs -> [COLOR=Red]enable[/COLOR] "Use GPU acceleration (experimental)"

I also forgot to say that I use VLC 1.1.9.

I will be happy if this can hep to anyone.

SOLVED. \\:D/

---

### Post by mike55 on 2011-05-07
Thank you, I upgraded to 11.04 today and ran into the same issue. Setting 'Accelerated video output (Overlay)' to off and ticking 'Use GPU acceleration (experimental)' solved it for me as well.

---

### Post by EmeraldGreen on 2011-05-30
Thank you! This fixed the problem for me - and apparently also fixed another long-standing issue, where my entire screen would flash black for a moment when VLC began to play a DVD.

Totem is still suffering from this issue, but I can live with that.

Thanks again!

---

