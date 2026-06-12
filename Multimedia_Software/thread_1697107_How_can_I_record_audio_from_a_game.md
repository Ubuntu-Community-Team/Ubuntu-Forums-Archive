---
title: "How can I record audio from a game?"
date: 2011-02-28
forum: Multimedia Software
---

### Post by barisurum on 2011-02-28
I want to record audio from a sdl game which uses alsa as output (pulseaudio is purged). I tried gtk-recordmydesktop to no avail. Can I make the game output to jack? If not how can I record the alsa output of the game? Thank you.

---

### Post by lykeion on 2011-02-28
Have you tried setting the audio device in recordMyDesktop?
Click Advanced > Sound tab > Device
You set a device in this format:  hw:X,Y (where X is card number and Y is device number, default is hw:0,0)

To find your audio device enter this command in a terminal:
```
aplay -L
```

If you'll get something like this:
```
card 0: NVidia [HDA NVidia], device 1: AD198x Analog [AD198x Analog]
```
The device should be set to: hw:0,1

---

### Post by barisurum on 2011-02-28
@lykeion thanks for the info but it fails with exit status 768 could not open sound card. I've tried both hw:0,0 ( card 0: Juli [ESI Juli@], device 0: ICE1724 [ICE1724] )
and hw:0,1 ( card 0: Juli [ESI Juli@], device 1: ICE1724 IEC958 [ICE1724 IEC958] ).

Is there a way to make alsa output flow to jack? This would solve the problem.

---

### Post by cchhrriiss121212 on 2011-02-28
Like this:
[http://www.alsa-project.org/main/index.php/Asoundrc#JACK_plugin](http://www.alsa-project.org/main/index.php/Asoundrc#JACK_plugin)

---

### Post by lykeion on 2011-02-28
I'm no expert in using Jack server, but there are a lot of very knowledgeable people here on the forum (like chris^^) that might come to your rescue. I found some links that might help you a bit though:
[http://jackaudio.org/routing_alsa](http://jackaudio.org/routing_alsa)
[https://help.ubuntu.com/community/What%20is%20JACK](https://help.ubuntu.com/community/What%20is%20JACK)

---

### Post by barisurum on 2011-02-28
@cchhrriiss121212

.asoundrc is not present in my system. Do I have to create it?

---

### Post by cchhrriiss121212 on 2011-02-28
Yes you can just make one with gedit, and save it in your home directory. May need a reboot or ALSA restart to take effect.

---

