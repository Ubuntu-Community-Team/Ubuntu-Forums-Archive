---
title: "soundoutput with hvr16-1600"
date: 2009-02-14
forum: Mythbuntu
---

### Post by dano1 on 2009-02-14
have just installed a happauge hvr1600 and cant get any sound. any tips for configuring sound output? Sorry am new to linux and capture cards.

---

### Post by klc5555 on 2009-02-14
> **dano1 said:**
> have just installed a happauge hvr1600 and cant get any sound. any tips for configuring sound output? Sorry am new to linux and capture cards.

Generally, the sound on the 1600 shouldn't require configuring. The first analog capture after the cx18 module loads is corrupted, but captures after that are OK.

If there's no sound at all, analog or digital from the 1600, the first thing to check is whether you have sound from apps generally, like xine or mplayer (with a dvd or some video file) If not, then it's a more general ALSA problem of some sort. If the 1600 sound problem is just on analog, but there is no problem on digital, sometimes /dev/dsp is being designated for sound output in the analog card setup, when /dev/dsp1 might actually be needed. Or the reverse.

Sometimes, however, and on some hardware, the cx18 module refuses to load correctly the first time round on bootup. In these cases, the card may be unable to tune at all, or the sound may just be a scratchy mess when the card tunes. In these cases, the module may be unloaded and reloaded by hand, i.e.:

sudo rmmod cx18
sudo modprobe cx18

and then generally it's OK. If this latter is the problem and it's consistent, the unload and reload of the module can be put into a boot script so it can happen on every startup.

Cheers! :)

---

