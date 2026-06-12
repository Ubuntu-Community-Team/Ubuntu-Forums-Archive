---
title: "Only 2 channels over SPDIF"
date: 2009-02-12
forum: Multimedia Software
---

### Post by nicoloks on 2009-02-12
I have a feeling I've read something about this before while looking for something else, but typically I can't seem to find it now.

I Have a Realtek ALC888 chip on my motherboard and am wanting to use the SPDIF header for digital audio pass through for decoding by my receiver. This works well, however only the front speakers seem to be working. If I run this;
```

speaker-test -Dplug:spdif -c6 -l1 -twav

```
I get sound out the front left and front right speakers, but nothing else. The only things I have done from the default ALSA install on Mythbuntu 8.10 is upgrade to ALSA 1.0.19 using the upgrade script on these forums, and add;
```

options snd-hda-intel model=6stack-dig

```

Any ideas?

---

### Post by nicoloks on 2009-02-14
Still having no luck with this. Any advice/suggestions?

---

### Post by deruberhanyok on 2009-02-15
Do you have AC3/DTS pass-through enabled in Myth?

Without the pass-through enabled, SPDIF digital output only has enough bandwidth to send PCM stereo audio. If you enable the pass-through you will have surround sound for any pre-encoded audio sources (such as a DVD movie), but other sources (games, for example) will still be limited to stereo output.

---

