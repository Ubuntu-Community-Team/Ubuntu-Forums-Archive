---
title: "SPDIF sound problem"
date: 2009-04-26
forum: Multimedia Software
---

### Post by Bommel87 on 2009-04-26
Hello!

Using Ubuntu the first time. Was a hard step getting WLAN working, now its the turn for sound.

I thougt i could get my optical SPDIF working with an upgrade. So i used the script here in the forum.
> 
Board: Asus M3A78-T with ALC1200 sound chip

1. Ubuntu revision: 9.04
2. Kernel revision: 2.6.28-11-generic
3. Alsa revision: 1.0.19

I think all necessary details can be obtained in the log files... in Desktop.zip

Hope you can help me getting SPDIF to work, tried out several mixer, updated ALSA, tried using realtek driver, but didn't help... :/

Don't know why, but IEC958 regulater in mixer is missing, only IEC958 switch is present. Does PCM replace that regulator?!

also check:
[http://www.alsa-project.org/db/?f=3eeff7a986f4092c720513029e2fc6bfb5d7161c](http://www.alsa-project.org/db/?f=3eeff7a986f4092c720513029e2fc6bfb5d7161c)

Already startet to post an answer to the ALSA script thread, because update had some issues. Nevertheless analog sound is working.

Hopefully you are able to help me. :sad:

---

### Post by inobe on 2009-04-26
enable IEC958 then click switches tab and check IEC958.

---

### Post by Bommel87 on 2009-04-26
well, usually it is that easy..., already knew that...

got it working now, the problem was a wrong entry, had to add:
model=6stack-dig

last thing that would be great now:
my audio-receiver isn't fast enough in detecting the approaching signal... So if only a short sound is played there is no output.

problem for this is mainly: sometimes ubuntu switches between 41000 and 48000, so my receiver has to react on that.

Is it possible to force ubuntu to 48000 Hz?

greetings,
Tommy

---

### Post by inobe on 2009-04-26
i have an older receiver and i feel your pain in that category, no matter what i tried always had that second or so delay.

i will keep an eye on this thread but seriously thinking about purchasing a new receiver.

---

### Post by Bommel87 on 2009-04-26
Ok, the problem cannot be solved completely, but it can be done a thing.

[http://wiki.ubuntuusers.de/.asoundrc](http://wiki.ubuntuusers.de/.asoundrc)

Use the given information to set 48000 default.

---

### Post by inobe on 2009-04-26
anyway to translate to English ?

---

### Post by Bommel87 on 2009-04-27
[FONT=Arial][SIZE=2]Well, i am from germany^^

What you have to do:

start terminal
sudo gedit .asoundrc
paste in the lines from that webpage (Beispiele -> Softwaremixing: Stereo)
edit the device-lines in .asoundrc file

device edit like the following:
check first what number your SPDIF devices has: aplay -l
change settings in the file according to your configuration
for example my config is:

card 0
device 1

gl&hf

oh, i forgot: change the sample rate in every entry you can find, 48000 for example
[/SIZE][/FONT]

---

### Post by fastie81 on 2009-04-27
> **Bommel87 said:**
> well, usually it is that easy..., already knew that...

got it working now, the problem was a wrong entry, had to add:
model=6stack-dig

last thing that would be great now:
my audio-receiver isn't fast enough in detecting the approaching signal... So if only a short sound is played there is no output.

problem for this is mainly: sometimes ubuntu switches between 41000 and 48000, so my receiver has to react on that.

Is it possible to force ubuntu to 48000 Hz?

greetings,
Tommy

Hi Tommy
Can you please let me know where you added the model option.
I have the same problem..
Thanks chris

---

