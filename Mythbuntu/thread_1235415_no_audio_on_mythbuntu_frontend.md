---
title: "no audio on mythbuntu frontend"
date: 2009-08-09
forum: Mythbuntu
---

### Post by derrickadean on 2009-08-09
it is know 2:00 in the morning and have just know got audio i needed to install the right driver for alsa. buttttttt!!! i dont have any audio on the myth frontend audio on mplayer works fine. ive played with the audio settings in the frontend for an hour or so and got nothing. Please help

---

### Post by pederj on 2009-08-09
Whats the name of your soundcard?

In the mythtv settings try following the syntax:

```
ALSA:hw:"soundcard"
```

Where you insert the name of your soundcard without quotes.
If you dont know what the name of your soundcard is, try typing in a terminal:

```
cat /prog/asound/cards
```
This should output info about all your detected cards. Use the name given in brackets

---

### Post by derrickadean on 2009-08-09
i discovered this im getting audio on the frontend just not from dvd playback  im getting audio from everything else can anyone help

---

