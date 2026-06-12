---
title: "Firefox ( and maybe another apps ) sound problems after installing PulseAudio/Jack"
date: 2011-12-07
forum: Multimedia Software
---

### Post by thamurath on 2011-12-07
Hi all,

I want to do some screencast using recordMyDesktop and had some audio problems.

After a lot of reading around here I found the way to get it all working ... almost.

I have installed PulseAudio Decive Chooser and Jack Control.

When I want to record something I just type:

pactl load-module module-jack-sink
pactl load-module module-jack-source

in the terminal, choose the appropiate sound set up and everything seems to work. I can record anything in my desktop but for the browsers!

I have tried Firefox and Chrome but without any success. 

Anyone knows how to solve this?

Thanks in advance!


P.S.: I am using Ubuntu 10.10 on a i386 laptop with and Intel HDA sound card.

Thanks again

---

### Post by MoreOrLess on 2011-12-07
When you use those commands, you're temporarily pausing pulseaudio in favor of jack. The problem with firefox (and other alsa apps) is that they're set to to use the pulse asound plugin. You'll have to set your alsa apps to use the jack asound plugin, see this example and put it in /etc/asound.conf
[http://www.alsa-project.org/main/index.php/Asoundrc#JACK_plugin](http://www.alsa-project.org/main/index.php/Asoundrc#JACK_plugin)

---

### Post by thamurath on 2011-12-09
Thanks for your replay.

I have write the file /etc/asound.conf but nothing seems to have changed.


I am still unable to record any sound.


What I am doing wrong?

---

