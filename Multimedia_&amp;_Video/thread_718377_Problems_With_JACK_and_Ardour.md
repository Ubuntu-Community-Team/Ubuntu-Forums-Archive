---
title: "Problems With JACK and Ardour"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by seagullplayer77 on 2008-03-08
I'm a Linux noob, so I'm sorry if this is a stupid question, but it's been driving me up the wall and I've gotta ask it.

So here's my problem: I'd like to record some stuff using Ardour, but I can't seem to get anything to work. I've messed around with the settings in JACK numerous times and I've played around with the Ardour mixer, but I still can't manage to get something to record from my microphone port.

I have gotten Hydrogen and Ardour to link up, but I really want to be able to plug something into my mic port and record from there. 

I'm not exactly sure what kind of info you guys would need to help me, so feel free to ask me for something if you need it.

Thanks!

---

### Post by kapello on 2008-03-11
In Jack Control, check your input device. Try and select your mic from the drop-down menu.

Jack will not necessarily have your mic selected as input by default, and on my system at least, it sometimes seems to just mess all the inputs and outputs up and swap them all around. 

sometimes, if I can't see my mic, I have to reboot my whole system and then check the Jack settings.

If you can get your mic to be the input on Jack, it should be able to connect from there to Ardour.

PS I find Ardour really hard work - if you don't need all it's advanced features, you might want to use Audacity instead, you can configure inputs/outputs really easy in preferences, and you can run it without Jack if you like.

---

### Post by nlz on 2008-03-11
in Ardour you have to set the input and output for every track/bus, you can do this with SHIFT + M. It would be a good idea to first do the 20 minute Ardour tutorial so you have an idea what you are doing.

[http://www.out-of-order.ca/tutorials/ardour/](http://www.out-of-order.ca/tutorials/ardour/)

if you did that, you don't even think of using audacity  anymore...

---

