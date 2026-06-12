---
title: "changing the output physical jack"
date: 2009-03-02
forum: Multimedia Software
---

### Post by falkaholic on 2009-03-02
Hi,

The output jack (green port) fried on my motherboard. 

With the drivers on Windows, I was able change with port the sound out was.


Is there a way to do this with PulseAudio? 

thanks

---

### Post by W_Z on 2009-03-06
Hello

Lets try to do it.
First You need to configure pulseaudio properly (there is how-to on the forum).

Type into terminal: pacmd
next: list-sinks
If You have only one sink, its yours card active output. Description will help recognize the output.

Open new terminal and type: aplay -L (big L i suppose).
Its a list of your devices.
For my audigy devices are called: front:, rear:, etc. and card simple Audigy, but there can be only card and device numbers like here: [http://ubuntuforums.org/showthread.php?p=6628921](http://ubuntuforums.org/showthread.php?p=6628921)
You have to chose device which is working output.

Add to default.pa (gedit ~/.pulse/default.pa):

load-module module-alsa-sink device=your*new*output*device sink_name=your*name
set-default-sink your*name

your*new*output*device can be devicename:cardname or hw: (devicenumber),(cardnumber) for example rear:Audigy or hw:0,3
your*name for example NewOutput

Restart system.

Use: 
aplay -D device file 
aplay -D hw:0,2 ~/Desktop/myfile.waw or something like this,
to check which device is workink output. 


It should work ;)
Dont forget backup default.pa.

---

