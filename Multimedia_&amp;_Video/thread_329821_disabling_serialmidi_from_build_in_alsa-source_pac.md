---
title: "disabling serialmidi from build in alsa-source package"
date: 2007-01-02
forum: Multimedia &amp; Video
---

### Post by afoozle on 2007-01-02
Hi, I am having issues with concurrent sound on my crappy onboard snd-hda-intel chip which can probably be fixed by enabling dmix.

Because dmix is supposedly enabled by default with newer versions of alsa I thought I would build the alsa-source package in Edgy via module-assist and hit this bug:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2039](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2039)

Since 
a) I don't care about serialmidi and 
b) it's disabled upstream 
what is the best way to disable it locally, am I looking at a kernel recompile or can I get away with just modifying the alsa-source package to not build serialmidi ?

On the other hand is it easier to just pull down a kernel and alsa-source from feisty? will that solve this problem?

Many thanks

---

