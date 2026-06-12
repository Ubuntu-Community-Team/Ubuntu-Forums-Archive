---
title: "Pulseaudio and alsamixer 5.1 problems"
date: 2011-08-21
forum: Multimedia Software
---

### Post by smeagol271006 on 2011-08-21
Hi people. Managed to get pulseaudio working but with some problems.

I'm using alsamixer and Preferences > Sound (also active in your taskbar).

If I try 

```
speaker-test -c 6 
```I only get audio in Front Left and Front Right

Nevertheless can hear surround sound and adjust sound of all the speakers via alsamixer (can mute for example front and use only surround ones).

With pulseaudio applet I have
```

Balance
Fade
Subwoofer
```I compare the two programs side by side

```
FL=FrontLeft
FR=FrontRight
SL=SurroundLeft
SR=SurroundRight
C=Center
SW=SubWoofer
```If I change balance to the right FL and SL decrease their volumes. Center and LFE decrease too. FR and SR keep the same.
That works fine either way (right or left)

Fade is supposed to work like balance for front-surround.

When I slide fade it only changes general master (alsamixer) volume. Not the desired effect. Also balance seems to move with fade sometimes ...

Currently have modified daemon.conf with two following lines (they appear to have no effect though)

```

default-sample-channels = 6
default-channel-map = front-left,front-right,front-center,rear-left,rear-right,lfe

```Also the applet and pavucontrol seem to be really wrong with the sliders. They block altogether and tend to reset alsamixer settings which tends to get me  :mad: 

I'm talking monkey ****; or has someone had this problem?

Also could it be that I have only a stereo alsa config which gets mirrored in front and surround?

Thanks

---

### Post by smeagol271006 on 2011-08-22
bumping

---

### Post by smeagol271006 on 2011-08-22
Bump II

---

### Post by GreekFreak on 2011-08-23
Hey Smeagol,

This might not be the exact answer to your question, but since I've had similar problems (still battling with some) here are 2 links that might help you:

[http://ubuntuforums.org/showthread.php?t=1773115&page=2](http://ubuntuforums.org/showthread.php?t=1773115&page=2) (Read from post #12 onwards)

[http://ubuntuforums.org/showthread.php?t=1640574](http://ubuntuforums.org/showthread.php?t=1640574) (I haven't tried these yet)

Hope this help you.

PS: Don't bump so frequently. I know it's annoying when something doesn't work when it should, but the people that maintain the forum (and help a LOT) are busy helping many of us. Wait a day or 2 before you bump ;P

---

### Post by smeagol271006 on 2011-08-23
Thank you very much. Will check the links and inform if solved.

PS: Will not bump so frequently! Sorry for that. Thought that message could go to black hole if not bumping ... Will take that into account

---

### Post by smeagol271006 on 2011-08-26
Uninstalled pulseaudio in the end. GUIs do not seem to behave properly and continous reset of my volumes presets was driving me nuts.

speaker-test -c 6 -Dplug:surround51

Outputs that everything works well. :lolflag:

Alsactl gives me the presets that I want. So I learned some things !

Will give pulse some years before trying it again.

Thanks ! :guitar:

---

