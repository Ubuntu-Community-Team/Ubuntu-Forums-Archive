---
title: "weird bug with flash 10"
date: 2008-12-03
forum: Multimedia Software
---

### Post by afaw on 2008-12-03
So I'm not 100% if this is a bug or just some setting I missed but for some reason my flash audio is playing through my motherboard audio output, while all of my other audio (rhythmbox etc) plays through my sound card.

Has anyone else experienced this or is this computer just crazy?

sound card shows up as "Ensoniq AudioPCI ENS1371" and the motherboard audio is "Intel ICH5"

computer is running a fairly fresh install of ubuntu 8.10 with flash 10 (non-free) installed for firefox.

I'm not sure if that is enough information but thats all that i can think of as relevant that I know (not my computer).

---

### Post by kostkon on 2008-12-03
> **afaw said:**
> So I'm not 100% if this is a bug or just some setting I missed but for some reason my flash audio is playing through my motherboard audio output, while all of my other audio (rhythmbox etc) plays through my sound card.

Has anyone else experienced this or is this computer just crazy?

sound card shows up as "Ensoniq AudioPCI ENS1371" and the motherboard audio is "Intel ICH5"

computer is running a fairly fresh install of ubuntu 8.10 with flash 10 (non-free) installed for firefox.

I'm not sure if that is enough information but thats all that i can think of as relevant that I know (not my computer).
You'll have to install the *PulseAudio Device Chooser* and either set one of your cards as the default in *PulseAudio* (do this anyway) and if that does not work for *Flash*, just load a *Flash* video in *Firefox* and then go to *PulseAudio*'s volume control and move its stream from the mobo Intel card to the Ensoniq one. *PulseAudio* will remember your choice.

Check my post [here]("http://ubuntuforums.org/showpost.php?p=6229132&postcount=5") for more details on how to install the *PulseAudio Device Chooser* and access its volume control.

---

### Post by afaw on 2008-12-03
neat, all fixed.

thanks a lot :)

---

