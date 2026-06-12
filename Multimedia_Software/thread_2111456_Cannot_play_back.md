---
title: "Cannot play back"
date: 2013-02-02
forum: Multimedia Software
---

### Post by Mick8882003 on 2013-02-02
I  downloaded Ubuntu Studio earlier today so I could record through my fender mustang II amp, it has usb built in, so its also a recording interface. I have managed to record the guitar (I can see the waveforms in ardour,) but I cannot manage to play it back, I am really confuzzled. The levels change but for the life of me I cannot get sound out.

Help!

---

### Post by zealibib slaughter on 2013-02-02
are you connecting through qjackctl or gladish?

---

### Post by Mick8882003 on 2013-02-02
I opened up qjackctl but didnt manage to get it working, I tried it but no success.

---

### Post by zealibib slaughter on 2013-02-02
ok well only way i know how to is using jack so Ill try to explain the process the best I can.
start qjackctl and then when the gui pops up click start and wait for started to be displayed.  next click connect and it will pop up a gui that allows you to route the audio path to the different ports (I look at it kinda like different parts of my gear like amp, pedals, mixers and such) you will have outputs and inputs.  on both you should see pulseaudio jack and system. you can expand these to see the individual ports.  by selecting one port on the output and one port on the input you can connect them.  like connect system - capture_1 to Pulseaudio jack source front left ect. now when you open ardour you will have a master track and you should of course create a sub track (like audio 1). connect master out to system playback. connect system capture to audio 1 input and connect audio 1 out to master in).

Gladish is a little easier since it kinda looks more like cabinets and wires but its not as flexible from what ive seen. later today ill try to make a screencast of all this lol.  BTW if you havent played around with guitarix yet then i highly recommend doing so.:guitar:

---

### Post by Mick8882003 on 2013-02-02
I have connected everything in many possible ways, do I have to set the inputs in the mixer as well?

---

### Post by zealibib slaughter on 2013-02-02
no jack to jack clients you dont pulseaudio to jack you do. did you hear the guitar through your system speakers as you played?

---

