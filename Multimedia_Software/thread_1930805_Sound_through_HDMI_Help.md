---
title: "Sound through HDMI??? Help"
date: 2012-02-24
forum: Multimedia Software
---

### Post by yusuo85 on 2012-02-24
So I have an external display and use a HDMI cable to do this, in Windows this isn't an issue but in Ubuntu it refuses to output the sound via the HDMI. Picture isn't an issue but the sound is coming out from my laptop speakers.

How do I rectify this as this is the only issue thats holding me back from making a full switch over to Linux

---

### Post by yusuo85 on 2012-02-25
Whoa please slow down with all the answers guys its all so over whelming,
but seriously im not asking how to code my laptop into half cybernetic monkey semen, this should be something really simple to answer.

Help me guys

---

### Post by Yellow Pasque on 2012-02-25
Please don't provide so much info, like what laptop and/or GPU you're using. It's so overwhelming! ;P

---

### Post by divague on 2012-02-25
Go to Sound Settings, in the Hardware tab in Settings for the selected device choose Digital Stereo HDMI (output)

---

### Post by yusuo85 on 2012-02-26
> **Temüjin said:**
> Please don't provide so much info, like what laptop and/or GPU you're using. It's so overwhelming! ;P

Touché smart ***, but you hold a valid point, Ok im using a Acer Aspire One 522 which holds a C-50 dual core 1ghz processor, intergrated HD graphics

---

### Post by yusuo85 on 2012-02-26
> **divague said:**
> Go to Sound Settings, in the Hardware tab in Settings for the selected device choose Digital Stereo HDMI (output)
 Thanks for an answer but that seems to kill the sound completly

---

### Post by Yellow Pasque on 2012-02-26
Okay, so it's a Radeon HD 6250. Do you know if you're using the propiretary fglrx/Catalyst driver? (The default open-source ati driver doesn't support HDMI audio on RadeonHD 6000-series cards at the moment). If you're unsure, look at output of:
```
lspci -vv
```

> Touché smart ***
:lol:

---

