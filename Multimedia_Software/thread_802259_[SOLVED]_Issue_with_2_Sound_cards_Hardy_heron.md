---
title: "[SOLVED] Issue with 2 Sound cards Hardy heron"
date: 2008-05-21
forum: Multimedia Software
---

### Post by g1rnz on 2008-05-21
Hi all, I have 2 soundcards on my PC one is onboard CH5 the other is a USB adaptor with CM106-F chipset. What I am trying to achieve is to have system sounds and playback from the onboard S/C and I run an amateur radio PSK31 software which I want to use only the USB adaptor. I can select DSP or DSP1 in the PSK s/w and that works fine but I get system sounds on the onboard s/c and Video sound playback on the USB adaptor. It does not appear to matter what settings I select in the sounds option it either does not work at all or we get the above problem any ideas would be good.

Graham

---

### Post by aeiah on 2008-05-21
try setting the default soundcard with asoundconf. does that do anything for system and multimedia sounds?

```

asoundconf list
asoundconf set-default-card <card>
```

---

### Post by g1rnz on 2008-05-21
> **aeiah said:**
> try setting the default soundcard with asoundconf. does that do anything for system and multimedia sounds?

```

asoundconf list
asoundconf set-default-card <card>
```

No this make no it does not but thanks for help

---

### Post by monraaf on 2008-05-21
You can use the **pavucontrol** program to move audio streams between sound cards.

---

### Post by g1rnz on 2008-05-22
> **monraaf said:**
> You can use the **pavucontrol** program to move audio streams between sound cards.

Thanks for help I have now tried pavucontrol and no audio streams are listed, I have looked at pulseaudio --dump-modules and none are listed implying that pulseaudio is not loaded??????

---

### Post by monraaf on 2008-05-23
Streams are dynamic, they only show up when applications are sending sound data to PulseAudio.

Also you have to make sure your applications are using PulseAudio:

**asoundconf set-pulseaudio**

And in the menu:

**system->preferences->sound** set everything to PulseAudio Sound Server. 

Additionally some applications have their own settings regarding sound output, and some application may need to be started with the **padsp** wrapper.

---

