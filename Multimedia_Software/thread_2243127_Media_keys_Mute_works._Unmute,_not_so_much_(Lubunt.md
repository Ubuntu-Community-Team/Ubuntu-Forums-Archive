---
title: "Media keys: Mute works. Unmute, not so much (Lubuntu 14.04)"
date: 2014-09-06
forum: Multimedia Software
---

### Post by Andre_Bogus on 2014-09-06
Hi there,

I have Lubuntu 14.04 on my Lenovo Z510, and it works very well. One small thing that bugs me is that the media keys work for muting the sound, but not for unmuting. This is because openbox calls "amixer -q sset Master toggle" when pressing the mute button. However, amixer doesn't just mute the Master, but also Headphones and Speakers, while if muted it just unmutes the master, leaving Headphone and Speaker channels muted. 

Now, if I call "amixer -q sset Speaker toggle; amixer -q sset Headphone toggle; amixer -q sset Master toggle" when sound is muted, it correctly unmutes the sound. However, this does not work in reverse. And anyway, I'd like amixer to just mute Master and leave Headphone and Speaker alone. Note that alsamixer also shows the erroneous behavior.

Is there some ALSA configuration that could alleviate this problem? If not, where in the code should I search for the problem?

Regards,
Andre

---

### Post by fuchs-1337 on 2015-01-05
Hi,

i think it is this problem. [http://ubuntuforums.org/showthread.php?t=1956323](http://ubuntuforums.org/showthread.php?t=1956323)
I have the same issue but the solution don't work for me. 

Best regards, Alex

---

### Post by nicklas3 on 2015-01-21
I had this issue as well (running Lubuntu 14.10 on an 8-yo Dell Latitude D830). I think I read somewhere that it has something to do with amixer (ALSA) not wanting to play nice with something or another. I've read a lot of posts...). Anyway, I have figured out a solution using pactl (PulseAudio) instead. 

Navigate to your openbox configuration xml file (mine is ~/.config/openbox/lubuntu-rc.xml).

Edit this file by finding the lines which say something like 
```
    <keybind key="XF86AudioMute">
      <action name="Execute">
        <command>amixer -q sset Master toggle</command>
      </action>
    </keybind>
```

and change it to:
```

    <keybind key="XF86AudioMute">
      <action name="Execute">
        <command>pactl set-sink-mute 0 toggle</command>
      </action>
    </keybind>
```

This fixed the mute/unmute problem for me, but I also like the volume adjust buttons to automatically unmute as well, so I went ahead and changed the following lines of my rc.xml
```
    <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
        <command>amixer -q ...more stuff... 3%+</command>
      </action>
    </keybind>
    <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
        <command>amixer -q ...more stuff... 3%-</command>
      </action>
    </keybind>
```

to this

```
    <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
        <command>pactl set-sink-mute 0 0</command>
      </action>
      <action name="Execute">
        <command>pactl set-sink-volume @DEFAULT_SINK@ -- +2%</command>
      </action>
    </keybind>
    <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
        <execute>pactl set-sink-mute 0 0</execute>
      </action>
      <action name="Execute">
        <command>pactl set-sink-volume @DEFAULT_SINK@ -- -2%</command>
      </action>
    </keybind>
```

Now my audio mute button correctly toggles the audio mute and any volume change automatically turns off the mute. This works for both speakers and headphones (for me at least... YMMV).

EDIT:
This also has the added (and unforeseen) benefit (quirk) of changing the state of the headphones and speakers separately. It is possible for one to be muted while the other is not, and for one to be at a certain volume level and the other a different one. This could probably be fixed with some argument change to pactl, but I kind of like it.

---

### Post by Jakobdkp on 2015-10-23
Hi,

Thank you for this solution! However, there is a problem with getting volume up/down to work. The last bit of code doesn't work any more because pactl code has changed to omit the -- before the volume specification. At this point, changing volume with the code given is broken. The new code should be:

```
    <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
        <command>pactl set-sink-mute 0 0</command>
      </action>
      <action name="Execute">
        <command>pactl set-sink-volume @DEFAULT_SINK@ +2%</command>
      </action>
    </keybind>
    <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
        <execute>pactl set-sink-mute 0 0</execute>
      </action>
      <action name="Execute">
        <command>pactl set-sink-volume @DEFAULT_SINK@ -2%</command>
      </action>
    </keybind>
```

---

