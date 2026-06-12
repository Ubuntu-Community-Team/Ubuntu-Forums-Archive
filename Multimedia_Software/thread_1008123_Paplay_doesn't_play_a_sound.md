---
title: "Paplay doesn't play a sound"
date: 2008-12-11
forum: Multimedia Software
---

### Post by Jæd on 2008-12-11
Hi,

I'm trying to use paplay to generate sounds from the command-line (to signify that scripts, etc have completed...). 

Problem is, it doesn't make a sound. However, all other sounds work fine through PulseAudio. (Ie, I can use the PulseAudio applet to verify Rythmnbox, etc, are going through PulseAudio.)

If I try:

```
paplay /usr/share/sounds/question.wav  --volume 65536
```

I get nothing, not even an error. If I watch the PulseAudio Manager I can see a process being attached and the sound playing...

Do I need to add more to the paplay command...?

Thanks...!

J

---

### Post by markbuntu on 2008-12-11
You can probably do this better in the PA volume control.
Is the stream using the proper output device (right click on it to find out or change the output device with move stream)?
Do you have the proper output device set as default in Output Devices section (again, right click to make default)? 

Once you have set the default output device, all new streams will use it.

---

