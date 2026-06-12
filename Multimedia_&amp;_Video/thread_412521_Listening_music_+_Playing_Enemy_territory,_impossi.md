---
title: "Listening music + Playing Enemy territory, impossible?"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by Davigetto on 2007-04-18
Hello, I have a little problem.

I have solved the tipical problem that Wolfestein sound doesn't work. Now I can play at perfection, with sound, but if I am listening music, Wolfenstein sound doesn't work, and if I am playing Wolfenstein with sound, and I decide to listen music, I can hear the music.

What can I do to solve that problem?

Greetings

---

### Post by bananabob on 2007-04-18
It sounds like you are using ALSA - Go to System>Preferences>Sound and check it out there

---

### Post by joft on 2007-04-19
What sound card/chip do you have? I think you have got a chip which does not do hardware mixing. What does
```
cat /proc/asound/cards
```
say?
**If** you indeed have such a sound chip, you'll need a software mixing solution. The problem is, that ET AFAIK is still a OSS application (OSS = OpenSoundSystem, old sound architecture of Linux). I have written a HOWTO on such a software mixing solution, _but it's for dapper_:

[http://ubuntuforums.org/showthread.php?t=208488]("http://ubuntuforums.org/showthread.php?t=208488")

_Currently I am working on it, to support feisty._

Someone posted instructions to make it work on edgy:
[http://ubuntuforums.org/showpost.php?p=1612627&postcount=18]("http://ubuntuforums.org/showpost.php?p=1612627&postcount=18")
(I never tried them, I didn't/don't use/support edgy).

---

