---
title: "Delay select channels in surround setup"
date: 2019-01-12
forum: Multimedia Software
---

### Post by lucian-iuga-gmail on 2019-01-12
[COLOR=#333333][FONT=&quot]&#8203;Hi there!

I have a bit of a weird setup for surround sound, which I'm too lazy to explain. But it runs on a Raspberry Pi 3, with a USB sound card with surround support. In principle, it works quite nicely on a 5.1 speaker set.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]
However, long stoy short, I kind of need to insert a delay in the sound of the front speakers, the center speaker and the subwoofer.

I've googled this but haven't found anything definitve. I've read some sources which say it is possible with ladspa, but don't detail how exactly.

Can anyone support with this?&#8203; Any help will be greatly appreciated.[/FONT][/COLOR]

---

### Post by CatKiller on 2019-01-12
Note: I've never done this, and I haven't played around at all with PulseAudio for nearly 10 years.

It *should* be possible to split the sink into two sets of channels, and then feed one set through the [module-loopback]("https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Modules/#module-loopback") module before it goes to the output. That should let you add a delay of up to 2 seconds.

---

