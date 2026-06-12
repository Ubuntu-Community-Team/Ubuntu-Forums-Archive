---
title: "Monitor changed and livetv crashes"
date: 2011-02-04
forum: Mythbuntu
---

### Post by anaximandro22 on 2011-02-04
I've been configuring Mythtv in a monitor, and when I had more o less OK, I changed to the TV (LCD) in the living room.
The resolution is different and I had to change it in the NVIDIA X server settings in Ubuntu. I've changed also the resolution in MythTV frontend configuration, in Setup->Appearance->Video Mode Settings.
But I can't watch livetv, the screen says Please wait..., and then returns to de menu.

In the log of mythwelcome I've found:
TV Error: HandleStateChange(): LiveTV not successfully started
and
TV Error: LiveTV not successfully started

I don't know if this information is enough, but I can put log info or anything you say to me.

Any suggestion?

---

### Post by thatguruguy on 2011-02-04
> **anaximandro22 said:**
> I've changed also the resolution in MythTV frontend configuration, in Setup->Appearance->Video Mode Settings.

Why?

Also, you state that your Mythtv setup was "more o less OK". Does that mean you were able to watch live TV on it?

---

### Post by anaximandro22 on 2011-02-04
> **thatguruguy said:**
> Why?

Also, you state that your Mythtv setup was "more o less OK". Does that mean you were able to watch live TV on it?

Of course. Everything worked OK. I watched live TV, record, schedule records... I said "more o less OK", because I didn't see deeply all the options in the configuration screens of the frontend and the backend (mainly the frontend).

One question: is it possible that this happend because a corruption of the database?

---

### Post by anaximandro22 on 2011-02-07
I answer the question. The problem was that the database was corrupted. I restored it and livetv worked again.

---

