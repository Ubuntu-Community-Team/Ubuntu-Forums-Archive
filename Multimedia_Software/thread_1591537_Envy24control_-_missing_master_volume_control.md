---
title: "Envy24control - missing master volume control"
date: 2010-10-09
forum: Multimedia Software
---

### Post by joanaomgod on 2010-10-09
I've just removed PulseAudio and installed Envy24Control in order to make sound working with my M-Audio Delta 1010LT, it's working fine now, but the only problem is that the master volume control disappeared, and the buttons on my keyboard (volume + and volume -) are not working (with PulseAudio they were fine).

Using Ubuntu 10.10 :)

---

### Post by cchhrriiss121212 on 2010-10-09
The master volume control disappeared as it is part of pulse. If you want an alternative GUI there is envy24control which is designed for your card, or try alsamixergui.

---

### Post by joanaomgod on 2010-10-10
> **cchhrriiss121212 said:**
> The master volume control disappeared as it is part of pulse. If you want an alternative GUI there is envy24control which is designed for your card, or try alsamixergui.

I know, I have envy24control, and actually when I was with PulseAudio, I was having problems with my sound card, so I installed envy24control and removed PulseAudio. After I removed PulseAudio, the master volume control disappeared, but the sound itself is ok now. I can change my sound levels from envy24control, but I want to have the icon with the master volume icon on my top panel :)

---

### Post by cchhrriiss121212 on 2010-10-10
Part of the reason pulse does not work well with this card is that it has no designated master volume. If I check envy24 with my delta card, all I have are ins and outs, no master, I don't have a 1010LT but I think it is the same.
If you want an icon on your panel, then try [volwheel]("http://oliwer.net/b/volwheel.html").

---

