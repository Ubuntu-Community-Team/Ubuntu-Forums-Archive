---
title: "Audacity records but at very low sound"
date: 2007-11-03
forum: Multimedia Production
---

### Post by Footer on 2007-11-03
Subject says it all.  Is there a special way to start Audacity so that it records normally or am I missing something?  I'm using ALSA and an onboard nVidia sound card:

```
footer@kubuntu64:~$ lspci | grep Audio
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

```

Audacity is right from the Gutsy repositories (ver. 1.3.3).  Any suggestions GREATLY appreciated!

Thanks!

---

### Post by bingoUV on 2007-11-03
Have you tried playing with mixer settings?

If you are running Gnome, right click on sound mixer applet. Open volume control. Increase volume of mic / line in, whatever you are recording from.

---

### Post by Footer on 2007-11-03
Thanks for the reply bingoUV.  I use Kubuntu and I have messed with the Kmix settings.  The two that change the volume of my source are Line and Analog Mix (see attached screenshot).

However, even with those both as high as they'll go, Audacity recordings are still barely audible.

Thanks!

---

