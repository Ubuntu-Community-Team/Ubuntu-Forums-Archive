---
title: "another no sound thread..."
date: 2010-01-22
forum: Multimedia Software
---

### Post by Nightstalker2 on 2010-01-22
I have no sound in Ubuntu 6.10. I just installed it fresh, and so there is basically nothing I could have done to break it.

Here is my aplay -l:

```
@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Here is my alsamixer:

```
[AlsaMixer v1.0.20 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: Intel ICH6                                                             &#9474;
&#9474; Chip: Analog Devices AD1980                                                  &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00, 0.00]                                            &#9474;
&#9474;                                                                              &#9474;
&#9474;    &#9484;&#9472;&#9472;&#9488;     &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;              &#9484;&#9472;&#9472;&#9488;      &#9484;&#9472;&#9472;&#9488;              &#9484;&#9472;&#9472;&#9488;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;  &#9474;      &#9474;  &#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;     >
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9474;&#9618;&#9618;&#9474;     &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;              &#9474;&#9618;&#9618;&#9474;      &#9474;&#9618;&#9618;&#9474;    Shared    &#9474;&#9618;&#9618;&#9474;     &#9474;
&#9474;    &#9500;&#9472;&#9472;&#9508;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;     &#9484;&#9472;&#9472;&#9488;     &#9500;&#9472;&#9472;&#9508;      &#9500;&#9472;&#9472;&#9508;              &#9500;&#9472;&#9472;&#9508;     &#9474;
&#9474;    &#9474;OO&#9474;     &#9474;MM&#9474;      &#9474;OO&#9474;     &#9474;MM&#9474;     &#9474;OO&#9474;      &#9474;OO&#9474;              &#9474;OO&#9474;     &#9474;
&#9474;    &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;     &#9492;&#9472;&#9472;&#9496;      &#9492;&#9472;&#9472;&#9496;              &#9492;&#9472;&#9472;&#9496;     &#9474;
&#9474;  100<>100    74      81<>81           100<>100  100<>100             100     &#9474;
&#9474; < Master >Master M  Master S Headphon   PCM     Surround Surround  Center 
```

So it doesn't look like anything is muted. But I don't know what else I should do. Any suggestions?

---

### Post by Nightstalker2 on 2010-01-23
bump....

---

### Post by Yellow Pasque on 2010-01-23
It looks like you have 2 sound cards; an onboard chip and a discrete one. Which one are you trying to use?

---

### Post by Nightstalker2 on 2010-01-25
Whichever one is the Sound Blaster 24-bit (I don't know if you can tell from the above which one it is). I think it is the non-Intel one

---

### Post by Yellow Pasque on 2010-01-25
Disable your onboard audio in the BIOS if you don't need it. That's the easiest way.

---

### Post by Nightstalker2 on 2010-01-26
How do I do that?

---

### Post by VertexPusher on 2010-01-27
Copy these lines into a text editor and save the file as ".asoundrc" in your user home directory:
```
defaults.pcm.!card CA0106
defaults.ctl.!card CA0106
```
This will make the Sound Blaster card your default sound card.

---

### Post by Yellow Pasque on 2010-01-27
> **VertexPusher said:**
> Copy these lines into a text editor and save the file as ".asoundrc" in your user home directory:
```
defaults.pcm.!card CA0106
defaults.ctl.!card CA0106
```
This will make the Sound Blaster card your default sound card.

Thanks for posting the asoundrc config, but I think the user would be better off disabling the onboard audio in the BIOS. Why load a driver for a device you're not using? It only wastes memory and increases the chances of things going wrong.

Nightstalker2: the setting for the onboard audio should be somewhere in your BIOS/System Setup. Try pressing 'Del' or 'F1' when you boot your system.

---

