---
title: "ALSA, 5.1 surround, etc."
date: 2006-01-27
forum: Multimedia &amp; Video
---

### Post by Maniace on 2006-01-27
I'm totally newbie what comes to Linux. I've got problems with 5.1 surround sound.

I want 2 channel sound(for example MP3 in XMMS) to be played from all channels, now it comes only from front speakers. I have tried many things found from all over net without results.

I think the drivers are not the problem 'cause

```

speaker-test -Dplug:surround51 -c6

```

works fine. But

```

speaker-test -c6

```

doesn't work. So i'll think that I must somehow get ALSA to use that -Dplug -thing as default? If I'm right, how can I do that?

Like I said I have tried allmost anything that newbie can do, I don't know have i done something wrong or what, that's why it would be best if someone could gimme simple step-by-step intructions to configure ALSA to play 2-channel sound from all channels.

Thanks for your help and sorry for bad english :)

---

