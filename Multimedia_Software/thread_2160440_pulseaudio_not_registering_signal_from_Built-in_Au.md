---
title: "pulseaudio not registering signal from Built-in Audio Analog Stereo (no projectM)"
date: 2013-07-07
forum: Multimedia Software
---

### Post by anoe on 2013-07-07
Hi all, I've got an Acer Aspire TimelineX 3830TG with LUbuntu 12.10. Sound is working ok with all programs, the problem is that pulse audio doesn't register any output from the analog card, so I can't use any program based on this, like ProjectM Visualizations. My audio card models are the following:

```
Codec: Conexant CX20588
Codec: Intel CougarPoint HDMI

```

The interesting thing is that when I select the digital card in the PulseAudio Volume Control the signals are detected properly, but, of course, I don't have any sound because for that I should plug the corresponding hardware in the hdmi output, i guess.

So, as I said, sound with the analog card is working good, but pulse audio doesn't detect any signal coming from it.

any idea about how to solve this issue?

tx

---

### Post by anoe on 2013-09-09
[COLOR=#333333][FONT=UbuntuRegular]Solved.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]My pulseaudio's configuration files became corrupt, so i opened a terminal and wrote[/FONT][/COLOR]
```
rm -r ~/.pulse*; pulseaudio -k
```
[COLOR=#333333][FONT=UbuntuRegular]it worked like a charm[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]cheers[/FONT][/COLOR]

---

