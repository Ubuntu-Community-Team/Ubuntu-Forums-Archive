---
title: "MCP61 High Definition Audio"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by Dr Small on 2008-01-23
Hi have 6 audio jacks in the back of my system, (see pictures), but only the one orange one works. I also have 2 front panel jacks (headphones & microphone), and only the microphone works.

I would like to be able to play audio from the headphone jack in the front (and or get the other jacks in the back to play.) Is there any possibility of doing this?

Here is the multimedia specs from lshw:
```

     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: iomemory:dfef8000-dfefbfff irq:17

```

Dr Small

---

### Post by Big Dan on 2008-02-15
Hi Dr. Small, 

  I have the same sound card and found this on the Debian forums

[http://forums.debian.net/viewtopic.php?t=17326&highlight=](http://forums.debian.net/viewtopic.php?t=17326&highlight=)

It works for me. :)

---

### Post by Dr Small on 2008-02-16
Thanks for the link :)
I'll have to try that out next time I have a system faiure :D
```
drsmall@darkghost:~$ uptime
 14:44:39 up 23 days, 19:30,  3 users,  load average: 0.45, 0.32, 0.18
```

---

### Post by damib on 2008-03-31
Hi to all,

I have the same problem with an Asrock MB. The chipset is the same:

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
        Subsystem: ASRock Incorporation Unknown device 0888

There is no sound from the headphone pugged on the front jack, while the speakers still work after the headphone jack has bee inserted. The front microphone, instead, is working fine.
I tried the the following option for the snd-hda-intel module : model=6stack, model=3stack, model=3stack-dig , but it still doesn't work.

With the option model=stack3-dig i can see the "mic-boost" controls and the "IEC958 capture" switch (I never seen them before....)


Any Idea?


Thanks

---

