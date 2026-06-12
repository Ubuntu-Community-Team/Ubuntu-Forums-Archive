---
title: "MIDI application advice needed."
date: 2016-01-01
forum: Multimedia Software
---

### Post by hoosemon61 on 2016-01-01
Greetings and Happy New Year.


I purchased an M-Audio Ozone MIDI controller/keyboard, hoping that I'd figure out what to do with it.

It's been sitting long enough, and I'd like to use it to make music.

I'm more interested in using it to play live than for recording or anything else.

I'm looking for advice on open source software that you'd recommend, that will function as a synth I can play live with the controller.

Less complicated would be better.  I'm mostly interested in organ, piano and clav voices.  Sampled would be preferred, but I'm not super picky.

I've looked at Rosegarden, but it seems to be much more than I'm looking for.

I'm a total noob with Midi with a very basic comfort level with Linux - mostly Ubuntiu.

Thanks for any advice you can offer.


Hoosemon

---

### Post by Keith_Beef on 2016-01-03
I'm also trying to set up some kind of home music studio, but don't often have more than an hour at a time to devote to it.

So far, I've found that JACK seems to be the most widely suggested method for routing MIDI signals to synthesizers and audio signals from them into the sound card. To do this requires PusleAudio to be temporarily suspended.

Try reading these:
[http://jackaudio.org/faq/](http://jackaudio.org/faq/)
[https://rafalcieslak.wordpress.com/2012/08/29/usb-midi-controllers-and-making-music-with-ubuntu/](https://rafalcieslak.wordpress.com/2012/08/29/usb-midi-controllers-and-making-music-with-ubuntu/)
[http://askubuntu.com/questions/8425/how-to-temporarily-disable-pulseaudio](http://askubuntu.com/questions/8425/how-to-temporarily-disable-pulseaudio)
[http://linux-sound.org/knowing-jack.html](http://linux-sound.org/knowing-jack.html)
[http://www.linux-magazine.com/content/download/63041/486886/version/1/file/JACK_Audio_Server.pdf](http://www.linux-magazine.com/content/download/63041/486886/version/1/file/JACK_Audio_Server.pdf)

---

### Post by hoosemon61 on 2016-01-03
Thanks for the info KB!

---

### Post by Bucky Ball on 2016-01-03
Do you have Ubuntu installed?

---

### Post by hoosemon61 on 2016-01-05
Yes, I have one PC with Ubuntu 14.04 and one running Xubuntu.  

I managed to trash the sound on the Xubuntu unit by trying to replace Pulse with Alsa. Successfully removed Pulse, but Alsa didn't install successfully.  Actually I was following a tutorial directing me to install Jack, a virtual midi keyboard and a synth app (can't remember the name) and the sound died.  The attempted change from Pulse to Alsa was because the tutorial was written assuming Alsa was in use, so I tried to change it.  I will probably back up the small amount of data saved on that computer and reinstall Xubuntu.

I have Jack installed on the Ubuntu box but none of the other apps I tried on the trashed computer.  The sound is working fine, but I don't know if it's using Pulse or ALSA.

---

### Post by Bucky Ball on 2016-01-06
If you're going to reinstall and your machine has the grunt, why not install Ubuntu Studio (which uses the xfce4 desktop environment too) or install Xubuntu and then install 'ubuntustudio-audio'. That will drag in Jack and more or less everything else you'll need.

You could go one step further and go for a minimal install, add xfce4, ubuntustudio-audio, pulse, pavucontrol and the few other things you might need. Sleek.

---

### Post by hoosemon61 on 2016-01-06
Thanks BB, I'll try it!

Hoosemon

---

### Post by Bucky Ball on 2016-01-06
[Minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD"), if you choose to go there. Don't choose a machine profile when you get to that bit (tasksel). Reboot when finished and you have installed the Ubuntu kernel ONLY. You will be at a CLI (giant terminal). Login and:

```
sudo apt-get install xfce4 ubuntustudio-audio pulse pavucontrol lightdm
```

... is basically it. Reboot. You should have a login screen and that should take you to the xfce4 desktop environment, same as Xubuntu and Ubuntu Studio's.

You might want just a few apps from Ubuntu Studio Audio bundle instead of the whole box and dice, so install individually instead. As you wish. You may also want a different desktop manager than lightdm.

---

### Post by hoosemon61 on 2016-01-10
I went for the full Ubuntu Studio install.  

It seems to be working great.  

It's one flavor I've never tried, so I'll play with it for a while, before tinkering with which apps to keep.

I think it's time to get more horsepower.  Both my Linux computers are just Celeron processors.


Thanks a ton for the advice, you've got me moving in a whole new direction - more to learn!

Take care,

Hoosemon

---

### Post by Bucky Ball on 2016-01-10
Great news! Yea, Celeron and audio/visual recording/editing is not a good mix. In the process of selecting the bits for a digital workstation myself at the moment.

Good luck. :)

---

