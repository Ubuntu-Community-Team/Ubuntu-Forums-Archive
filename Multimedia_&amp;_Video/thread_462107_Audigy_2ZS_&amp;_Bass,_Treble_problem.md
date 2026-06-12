---
title: "Audigy 2ZS &amp; Bass, Treble problem"
date: 2007-06-02
forum: Multimedia &amp; Video
---

### Post by Dark Dominion on 2007-06-02
Ok i'm using Ubuntu Feisty Fawn and i have an Audigy 2ZS sound card. My problem is that although i'm hearing sound normally and can lower volume from the mixer, i can't change the bass and treble settings. Any suggestions?

---

### Post by Eplenektar on 2007-07-28
I have the same problem, although I am using the standard Audigy 2 sound card. I can adjust the volume, but not change just the bass or the treble. Any suggestions?

---

### Post by MrHippocampus on 2007-07-28
Im not on my desktop at the moment, so im just going to have to try and remember the correct way to do it.

Open a terminal and run "alsamixer", you should see bass/treble sliders and then a switch on one side of them, toggle the switch using "m" and the switch should go green. You should then be able to modify the treble and bass.

Hopefully that should work.

---

### Post by acidrain42 on 2007-07-31
I also had this problem and your solution works just fine.
Thanks a lot!

---

### Post by MemoryDump on 2007-10-22
I'm having the same prob under gutsy.. I see the options/sliders for the bass&treble.. however moving the sliders produces no changes to the sound.. :(

```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: Audigy 2 ZS [SB0350]                                                   &#9474;
&#9474; Chip: SigmaTel STAC9750,51                                                   &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=-6.00]                                                 &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;               &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;              &#9474;
&#9474;    &#9474;  &#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;              &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;  &#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;              &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;              >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;              &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;              &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;               &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;  &#9474;     &#9474;  &#9474;              &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9500;&#9472;&#9472;&#9508;      &#9484;&#9472;&#9472;&#9488;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;             &#9474;MM&#9474;      &#9474;MM&#9474;                                          &#9474;MM&#9474;     &#9474;
&#9474;             &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;                                          &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;     85     42<>42             75<>75   95<>95       0        0               &#9474;
&#9474; < Master >Headphon    Tone     Bass    Treble   3D Contr 3D Contr 3D Contr
```

---

### Post by MrHippocampus on 2007-10-23
move to the Tone switch and press the m key on your keyboard so the letters above change from MM to 00, then the treble/bass sliders should work

---

### Post by MemoryDump on 2007-10-23
> **MrHippocampus said:**
> move to the Tone switch and press the m key on your keyboard so the letters above change from MM to 00, then the treble/bass sliders should work
I had tried that and still no go. (nothing happened)

I actually figured it out not too long ago and was going to post the solution :D
If you open your Volume controls and go to the SWITCHES tab there's a CHECKBOX for TONE. Simply enable this and your BASS&TREBLE will work :P
If you don't see the option for TONE simply go to your properties and make sure TONE is checked ON there too.

---

