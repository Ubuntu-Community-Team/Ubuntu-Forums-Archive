---
title: "Recording sound: where are the secret settings?"
date: 2006-08-17
forum: Multimedia &amp; Video
---

### Post by AskHL on 2006-08-17
I would like to record sound using an ordinary microphone. This worked in Breezy. But now, when I start the sound recorder (actually I'd like to use Skype, but one step at a time), I get:
> Your audio capture settings are invalid. Please correct them in the Multimedia settings.
But where are these "Multimedia settings"? I have no idea! I remember that in Breezy you could select some multimedia "channels" for input and output like Alsa, OSS, ESD and another one. But this golden application has disappeared fron Dapper for reasons unknown.

Any help would be greatly appreciated!

EDIT: The application which I suspect it is referring to is the "Multimedia Systems Selector", which is no longer available in dapper.

---

### Post by drycellbattery on 2006-08-17
alt-f2 to get the run dialog and type > gstreamer-properties
was that what you were talking about?

---

### Post by AskHL on 2006-08-18
That was *exactly* what I talked about. And what's more, it *worked*! Thank you!

---

