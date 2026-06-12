---
title: "Mixer Applet on desktop &amp; No Sound"
date: 2013-01-22
forum: Multimedia Software
---

### Post by Mark_in_Hollywood on 2013-01-22
I have installed the Audio Mixer (Alsa Mixer) on my desktop as I could not control the audio volume in MythTV.

At first, the Master Volume moved the sound volume up and down. Then I added "Headphones" from Select Controls. After that, I have no sound in any application. VLC plays but no sound. MythTV shows tv picture but no sound. I have rebooted to see if that would correct itself. No I have not Muted the sound and missed the little X through the loudspeaker icon.

Audio Mixer title bar reads in full: Audio Mixer - HDA NVidia (Alsa mixer).

Sound card (pull down menu reads): HDA Nvidia (Alsa mixer)
USB Device 0x46d:0x807 (Alsa Mixer)
Playback: Built-in Audio Analog Stereo (PulseAudio Mixer)
next come capture devices. Is that relevant? See screenshot if relevant.

Moving the Audio Mixer applet to the desktop brought up a warning about "not executable" and trusted. I clicked Make Executable or some such. 

And each time I call (run) the Mixer Applet, the Master Volume's loudspeaker icon is set to Mute (x through it).

I find a related idea at: [https://bbs.archlinux.org/viewtopic.php?id=139723](https://bbs.archlinux.org/viewtopic.php?id=139723)

And this guy had to compile the Alsa driver - [http://www.debianuserforums.org/viewtopic.php?f=55&t=1969](http://www.debianuserforums.org/viewtopic.php?f=55&t=1969)

The following URL had a temporary fix.

[http://askubuntu.com/questions/65764/how-do-i-toggle-sound-with-amixer](http://askubuntu.com/questions/65764/how-do-i-toggle-sound-with-amixer)

Run this line:

for i in $(amixer |grep -o \'.*\'); do amixer set $i unmute; done

I may be goofy wrong about this but this bug seems to have fubar'd my panel icon for Thunderbird. It won't launch.
Anyone know what has happened here?

---

### Post by Yellow Pasque on 2013-01-23
Right click on the mixer icon (in the taskbar, not the desktop) and select "Properties" to select which card/channel you want, or if you're into terminal commands, here's an example to see which track is active:
```
xfconf-query -c xfce4-mixer -p /active-track
```

---

### Post by Mark_in_Hollywood on 2013-01-23
mark@Lexington-19:/$ xfconf-query -c xfce4-mixer -p /active-track
Property "/active-track" does not exist on channel "xfce4-mixer".

---

### Post by Yellow Pasque on 2013-01-23
Hmm. Maybe Ubuntu does xfconf differently than Debian because that command works for me. Anyway, you didn't mention whether you used the other technique:
> Right click on the mixer icon (in the taskbar, not the desktop) and select "Properties" to select which card/channel you want

---

