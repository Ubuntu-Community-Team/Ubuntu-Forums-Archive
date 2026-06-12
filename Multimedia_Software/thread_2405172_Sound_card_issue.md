---
title: "Sound card issue"
date: 2018-11-02
forum: Multimedia Software
---

### Post by pmbergin on 2018-11-02
Not sure what I did, but now I  get audio feed from the browser etc, but not from my audio software, Audacity, VLC media player etc. I use Ubuntu Studio, so there are a bunch of sound card GUIs, but I can't figure out which setting is screwing this up. I obviously did something wrong when I went in and tried to incease the output volume on the card

---

### Post by yancek on 2018-11-02
How did you try to increase the output volume on the card, do you remember which software you used?

What output do you get from the following commands.

```
aplay -l
```

```
sudo  lspci -v | grep -A7 -i "audio"
```

You might try reading through the suggestions at the site below, take care to understand what a command does before running it.

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

