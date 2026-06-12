---
title: "Flash and other sounds can't play together (OSS?)"
date: 2008-05-04
forum: Multimedia Software
---

### Post by Luke has no name on 2008-05-04
If I'm listening to anything (Skype, Amarok) I can't watch Youtube, and if I have youtube open I can't play Skype calls. I assume this is OSS? i'm a sound noob in Linux. Can I adjust my Flash sound settings?

---

### Post by ropotamski on 2008-05-04
I have the same problem. When I'm listening to Amarok (or anything else) I have no sound on YouTube and oder sites.
I'm with Realtek sound card and 5.1 audio

---

### Post by ropotamski on 2008-05-04
[http://ubuntuforums.org/showpost.php?p=1085341&postcount=8](http://ubuntuforums.org/showpost.php?p=1085341&postcount=8)
System -> Preferences -> Sound -> Soundtab -> Disable software sound mixing (ESD)
:)

---

### Post by Luke has no name on 2008-05-04
> **ropotamski said:**
> [http://ubuntuforums.org/showpost.php?p=1085341&postcount=8](http://ubuntuforums.org/showpost.php?p=1085341&postcount=8)
System -> Preferences -> Sound -> Soundtab -> Disable software sound mixing (ESD)
:)

Nice. Once again, what seems to be a common problem with a common solution isn't fixed? The question begs asking: What benefit is there to leaving ESD enabled by default? And would more people get a benefit from it being disabled by default?

These are things that need discussed.

---

### Post by Bingulim on 2008-05-04
To fix the problem with flash you can also do this:
```
sudo apt-get install libflashsupport
```

---

### Post by alecz20 on 2008-08-09
> **Bingulim said:**
> To fix the problem with flash you can also do this:
```
sudo apt-get install libflashsupport
```

Awsome! Worked like a charm!:guitar:

Wanted to give thanks, but its past 60 days...:(

THANKS, tho!

---

