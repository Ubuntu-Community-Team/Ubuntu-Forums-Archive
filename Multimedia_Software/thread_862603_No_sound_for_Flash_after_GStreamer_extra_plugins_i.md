---
title: "No sound for Flash after GStreamer extra plugins install"
date: 2008-07-17
forum: Multimedia Software
---

### Post by indiworks on 2008-07-17
After installing the GStreamer extra plugins I don't have sound for Flash anymore. Deinstalling the GStreamer extra plugins did not help. I also need them for .mp3 playback as far as I understand.

What could be the problem? I have Ubuntu 8.04, 32-Bit version. Thanks!

---

### Post by Afkpuz on 2008-07-17
Try this.

```
asoundconf list
```

Note the name of your primary sound card

```
asoundconf set-default-card soundcardname
```

And it is case sensitive.  See if that works.

---

### Post by indiworks on 2008-07-18
> **Afkpuz said:**
> Try this.

```
asoundconf list
```

Note the name of your primary sound card

```
asoundconf set-default-card soundcardname
```

And it is case sensitive.  See if that works.

Many thanks - it's working again right now though I'm not quite sure what fixed it: I used the "asoundconf list" command and that gave me "Intel".

I only then checked the Flash playback (to double check that it does not work before I use the other command to fix it) but then it already worked again...?! I did not install anything since yesterday, only restarted once, but I had done that before without the issue being fixed...

I'll try the second command should the problem come back - thanks again!

---

### Post by Afkpuz on 2008-07-31
That's weird.  The first command only lists the soundcards on your computer and nothing more.  Well, glad to hear that it's working now!

---

