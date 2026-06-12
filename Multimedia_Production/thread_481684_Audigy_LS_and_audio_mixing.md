---
title: "Audigy LS and audio mixing"
date: 2007-06-22
forum: Multimedia Production
---

### Post by Anonii on 2007-06-22
Greetings,

I could never understand ALSA. I could never understand sound mixing. I could never understand audio surround. I could never understand the ~/.asoundrc file.

In some Linux distros/installs ~/.asoundrc will work for me, providing both sound mixing (dmix style) and surround. In other Linux distros/installs it won't. 

For example, here is my Gentoo ~/.asoundrc which works greatly:

```

pcm.dsp0 {
    type plug
    slave.pcm "dmix"
}

ctl.mixer0 {
    type hw
    card 0
}

pcm.!default {
        type plug
        slave.pcm "dmix"
}
```

in Kubuntu it doesn't. I just don't get it. I don't know why. I also don't understand why and if the /etc/init.d/alsasound of Gentoo, is the same as the /etc/init.d/alsa-utils of Ubuntu. 

I'd like some suggestions, help and advices on the subject. I'm using an SB Audigy LS.

Also, what the hell is Dmix? And why it's required only by particular sound cards? Its required by mine?

---

### Post by sebast on 2007-07-09
I have the same problem.

Have been trying to make my aydigy ls surround work for too long now

---

