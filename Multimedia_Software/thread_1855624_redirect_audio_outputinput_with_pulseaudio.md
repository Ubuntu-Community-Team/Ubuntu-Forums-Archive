---
title: "redirect audio output/input with pulseaudio"
date: 2011-10-06
forum: Multimedia Software
---

### Post by metalfan_ on 2011-10-06
hi,

i would like to redirect the output from totem to line in and have teamspeak3 listen on line in.
currently theres no line in listed in ts3.


currently ive set ts3 to "monitor of internal audio analog stereo"
but when another user joins the channel anything he says gets echoed back by the "bot"


if i could set ts3 to listen on line in or something similar the echo would probably get away...any ideas howto do this?

---

### Post by metalfan_ on 2011-10-11
load the pulse module module-null-sink

then redirect output from totem to the null sind and set ts3 to listen on monitor of null sink.

---

