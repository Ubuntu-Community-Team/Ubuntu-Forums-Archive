---
title: "Audio and Video out of sync esp Netfix"
date: 2015-01-01
forum: Multimedia Software
---

### Post by Jonners59 on 2015-01-01
I am having trouble with audio/video sync and sometimes on Netflix I also get jitter...

The PC is connected to our LG 42" 42LE8900 TV via an HDMI cable, and I wonder if this may be the cause.  A good user interface is lacking.

The motherboard is an Ausu Rampage IV Extreme, The RAM is 32Gb Kingstone Hyper Beast DDRS, The processor is an Intel i7 8 core and the graphics card an AMD GT430 (yes, a little light given the rest of the kit!), and it is over clocked using one of the built in standard profiles.

I have tried all these, which are solutions in other threads or sites I have found, but none worked for me.

```
pactl load-module module-loopback

sudo sh -c ' echo "load-module module-loopback" >> /etc/pulse/default.pa '

pavucontrol

Moonlight

pulseaudio -k

sudo apt-get install libasound2-plugins:i386
```

Even tried reinstalling Netflix, though the problem is not limited to just netfix, though certainly wose of all the apps.

```
sudo apt-add-repository ppa:ehoover/compholio

sudo apt-get update

sudo apt-get install netflix-desktop
```

shift+alt then right click mouse button to get comands, does not work on Netflix

Have tried to delete delete the hidden directory [PHP].netflix-desktop[/PHP], but can not find it....

Any help anyone, please?

Happy New year

---

### Post by Jonners59 on 2015-02-20
No one came to my rescue.  I resolved this when I was forced to do a complete system rebuild.

---

### Post by SeijiSensei on 2015-02-20
The preferred solution for services like Netflix that rely on Microsoft Silverlight is "[pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html")".

---

### Post by Jonners59 on 2015-02-20
Thanks SeijiSensi
I had also tried pipelight and it hadn't worked, but all is fine now with the rebuild.  Maybe something went wrong with the first install.

---

