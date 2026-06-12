---
title: "Pulseaudio command to turn up / down volume via terminal"
date: 2009-12-28
forum: Multimedia Software
---

### Post by Azathoth_ on 2009-12-28
Hi,

I have two sound cards and I use LIRC to control music, videos, ...

Since I use pulseaudio I cannot use the remote control to turn up volume to both sound cards at the same time.
I used the following command to turn up volume and have a notification of the volume

```
amixer -set Master 7%+; notify-send -i /usr/share/pixmaps/gnome-logo-icon.png -t 1000 "`amixer -c 1 sget Master | tail -2 | cut --delimiter=" "  --fields=6 | tail -1` volumen"
```

Now, the only way to turn up volume to both sound card that I know is:


```
amixer -c 0 set Master 7%+; amixer -c 1 set Master 7%+; notify-send -i /usr/share/pixmaps/gnome-logo-icon.png -t 1000 "`amixer -c 0 sget Master | tail -2 | cut --delimiter=" "  --fields=6 | tail -1` volumen card 0"; notify-send -i /usr/share/pixmaps/gnome-logo-icon.png -t 1000 "`amixer -c 1 sget Master | tail -2 | cut --delimiter=" "  --fields=6 | tail -1` volumen card 1"
```

Is there any way to use a terminal command to turn up/down volume in Master/PCM to both sound card in one way?
I use also pavucontrol to redirect sound between programs and sound cards.

Thanks in advance.
Best regards

---

### Post by uriel1998 on 2012-02-10
I was using this up until... well, today.  Unfortunately, using the ALSA mixer causes problems when you're dealing with multiple sinks in PulseAudio.  

I'm using a ruby script that actually changes *all* sinks at the same time - which comes in handy when you've suddenly started using an external USB speaker and all your keybound scripts work with only one sink.

I can't take credit for most of it - I forked and tweaked it a tiny bit.  The original script is here: [https://gist.github.com/814634](https://gist.github.com/814634);  I couldn't get it to run because of something in the muting code, so I fixed that and added in some output in case someone wants to send it to notify-osd or somesuch.  Mine's at: [https://gist.github.com/1791270](https://gist.github.com/1791270).

---

