---
title: "streamtuner + audacious + shoutcast = crash"
date: 2009-03-29
forum: Multimedia Software
---

### Post by akoblentz on 2009-03-29
Hi,
When I try to "tune in" to a stream with streamtuner, most of the channels will load audacious and then audacious will crash.
Some channels work great.

I did a bunch of searching on google without finding much,
so I tried running the command streamtuner is supposedly
running in hopes of getting some meaningful crash message.

Here's what I've got:
```
% audacious http://scfire-dtc-aa05.stream.aol.com:80/stream/1007, http://scfire-mtc-aa04.stream.aol.com:80/stream/1007, http://scfire-ntc-aa05.stream.aol.com:80/stream/1007, http://scfire-ntc-aa08.stream.aol.com:80/stream/1007, http://scfire-dtc-aa01.stream.aol.com:80/stream/1007, http://scfire-dtc-aa02.stream.aol.com:80/stream/1007, http://scfire-mtc-aa02.stream.aol.com:80/stream/1007, http://scfire-mtc-aa03.stream.aol.com:80/stream/1007, http://scfire-ntc-aa02.stream.aol.com:80/stream/1007, http://scfire-ntc-aa06.stream.aol.com:80/stream/1007, http://scfire-ntc-aa07.stream.aol.com:80/stream/1007, http://scfire-mtc-aa06.stream.aol.com:80/stream/1007, http://scfire-ntc-aa09.stream.aol.com:80/stream/1007, http://scfire-ntc-aa04.stream.aol.com:80/stream/1007, http://scfire-dtc-aa04.stream.aol.com:80/stream/1007, http://scfire-dtc-aa03.stream.aol.com:80/stream/1007, http://scfire-mtc-aa05.stream.aol.com:80/stream/1007, http://scfire-ntc-aa01.stream.aol.com:80/stream/1007, http://scfire-mtc-aa01.stream.aol.com:80/stream/1007, http://scfire-ntc-aa03.stream.aol.com:80/stream/1007, http://205.188.215.226:8002
amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded
zsh: abort      audacious http://scfire-dtc-aa05.stream.aol.com:80/stream/1007, 
```

I figure it has to do with the several urls comma separated.  I tried using BMPx (my favorite music player) and that works when I do: 
```
bmpx http://scfire-dtc-aa05.stream.aol.com:80/stream/1007, http://scfire-mtc-aa04.stream.aol.com:80/stream/1007, http://scfire-ntc-aa05.stream.aol.com:80/stream/1007, http://scfire-ntc-aa08.stream.aol.com:80/stream/1007, http://scfire-dtc-aa01.stream.aol.com:80/stream/1007, http://scfire-dtc-aa02.stream.aol.com:80/stream/1007, http://scfire-mtc-aa02.stream.aol.com:80/stream/1007, http://scfire-mtc-aa03.stream.aol.com:80/stream/1007, http://scfire-ntc-aa02.stream.aol.com:80/stream/1007, http://scfire-ntc-aa06.stream.aol.com:80/stream/1007, http://scfire-ntc-aa07.stream.aol.com:80/stream/1007, http://scfire-mtc-aa06.stream.aol.com:80/stream/1007, http://scfire-ntc-aa09.stream.aol.com:80/stream/1007, http://scfire-ntc-aa04.stream.aol.com:80/stream/1007, http://scfire-dtc-aa04.stream.aol.com:80/stream/1007, http://scfire-dtc-aa03.stream.aol.com:80/stream/1007, http://scfire-mtc-aa05.stream.aol.com:80/stream/1007, http://scfire-ntc-aa01.stream.aol.com:80/stream/1007, http://scfire-mtc-aa01.stream.aol.com:80/stream/1007, http://scfire-ntc-aa03.stream.aol.com:80/stream/1007, http://205.188.215.226:8002

```

I thought maybe I'd be able to get BMPx to also work through
streamtuner's Applications panel in the preferences, however that just
loads BMPx and doesn't actually play.  I tried using %u and %q, for unquoted and quoted respectively.
It's a no-go.  With %u, BMPx stalls while loading the gui,
with %q the gui loads, but nothing happens.

Any ideas?  Thanks.

---

### Post by akoblentz on 2009-03-30
I really hate to bump my thread, but I'm having real issues with this
and the speed at which this forum moves, I should avoid starting topics in the middle
of the night from now on...

---

