---
title: "Dell Latitude  E6410 Wifi Light Constantly Blinking"
date: 2013-01-05
forum: Networking &amp; Wireless
---

### Post by snakeops on 2013-01-05
Hello! I just recently installed Ubuntu 12.10 on my Dell Latitude E6410. I've been looking all over the forum for a solution before repeating a thread like this, so I apologize in advance but I can't seem to find a solution anywhere. As the title states, the wifi light is constantly blinking and I've got iwlwifi, could anyone possibly help me out? this light is driving my insane... I'd be eternally grateful! :P Thank you!

---

### Post by Pjotr123 on 2013-01-05
It's normal. In Ubuntu, for most wireless chipsets the wifi light blinks whenever data is being sent or received. Makes more sense than a non-blinking light to me, so I got used to it myself, and don't want to miss it anymore. :)

That said, I'm sure that there will be some tweak available for disabling it, but I don't know it myself.....

---

### Post by EmmEight on 2013-01-05
Snakeops,

Is the flashy light your main concern? I mean, we can always disconnect the wires ):P

Is your "wifi" working?

Do you have issues "connecting" to the internet?

If it is a flashy LED that bugs you, I suggest you:

A: Ignore it
B: Re-build the computer to your special specs (Without said LED)
C: Destroy said LED 
D: Pursue the company the creates your "computer" and ask them to create a linux-based program/app that will bypass your wifi LED light at your dismay

---

### Post by PhilGil on 2013-01-05
I've just learned to ignore it on my E4300, but if you're up to creating and/or modifying a configuration file you may be able to fix it using these instructions:
[http://www.tomdesair.com/blog/2012/04/stop-the-blinking-wireless-led-in-linux/](http://www.tomdesair.com/blog/2012/04/stop-the-blinking-wireless-led-in-linux/)

Don't know how familiar you are with Ubuntu, but you will need elevated privileges to edit the file, so enter something like this in the terminal:

```
$ sudo gedit /etc/modprobe.d/wlan.conf
```

---

