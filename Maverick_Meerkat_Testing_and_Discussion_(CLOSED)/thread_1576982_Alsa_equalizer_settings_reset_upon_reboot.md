---
title: "Alsa equalizer settings reset upon reboot"
date: 2010-09-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by hype on 2010-09-18
Hi there, just wondering if any of you had this kind of issue:

i always use the internal equalizer of my Sound card, Audigy 2, to remove bass by activating the "Tone" setting in alsamixer. (there used to be a gui for that, but not anymore since Lucid Lynx, anyway)

The issue is that this setting resets at every reboot.

I filled a bug on lp [https://bugs.launchpad.net/ubuntu/+bug/641884](https://bugs.launchpad.net/ubuntu/+bug/641884)

Although i filled this bug only for the reboot issue, im' wondering why there isnt any default gui to be able to display all of the options available on my sound card, ie the "Tone" setting.


Thanks for help!

---

### Post by dino99 on 2010-09-18
have you seen into synaptic: ld10k1 package ? (dont know what exactly it does)

---

### Post by lykeion on 2010-09-18
Have you tried this?
```
sudo alsactl store 0
```
Ref: _[SoundTroubleshooting - Saving Sound Settings]("https://help.ubuntu.com/community/SoundTroubleshooting#Saving%20Sound%20Settings")_

---

### Post by hype on 2010-09-18
Not sure about the package Dino99: i'm installing it and check if that changes anything.

lykeion, your command can be a solution, but i think it's not normal that these settings are reset; never happened in Lucid lynx by exemple.

---

### Post by hype on 2010-09-18
> **dino99 said:**
> have you seen into synaptic: ld10k1 package ? (dont know what exactly it does)
Installing this package didnt change anything. I still get the bug after reboot.
Didn't understand the man page anyway so.... ;)

I tried to 
```
sudo alsactl store 0
```
and check at next reboot.

---

### Post by Reiger on 2010-09-18
Try removing pulseaudio and related packages. That fixed similar issues (volume always reset to 100%) for me.

---

### Post by ranch hand on 2010-09-18
The gui is gnome-alsamixier.  I have installed it on all my 10.10 installs from the repos.  It is there.

Been installing it as one of the basics for several releases.

---

### Post by hype on 2010-09-18
> **ranch hand said:**
> The gui is gnome-alsamixier.  I have installed it on all my 10.10 installs from the repos.  It is there.

Been installing it as one of the basics for several releases.

Yep, but before ubuntu lucid, you just had to go to sound preferences to get it (it was better looking, probably not the same application)

And gnome-alsamixer doesnt display values next to sliders: not practical.

---

### Post by mc4man on 2010-09-18
I would think there'd be a config file you could use but if  nothing is working out and your bug isn't addressed ( wouldn't hold your breath on pulseaudio bugs) then you can use amixer in a variety of ways to do what you want.
The 2 commands your looking at are these (don't know if you can make it one), where 0 is the card number and %20 is the bass volume (adjust as needed
amixer -c 0 -- sset Tone unmute
amixer -c 0 set Bass 20%

you could use a launcher or small script, a start up script would also probably work out ok, might possibly have it sleep a few seconds to avoid any conflict

Edit: tested a start up script w/ audigy 2, works fine

---

### Post by plun on 2010-09-18
Maybe the PulseAudio Equalizer script is something for you....  ?

[http://ubuntuforums.org/showthread.php?t=1308838](http://ubuntuforums.org/showthread.php?t=1308838)

I havent seen "psyke83" for a while and maybe he can comment this if he sees it ?

EDIT

Sorry it seems to be broken....

..

---

### Post by Reiger on 2010-09-18
The commandline program alsamixer is very easy to use. Try using one of these modes:
alsamixer -V playback
alsamixer -V capture
alsamixer -V all

---

### Post by hype on 2010-09-19
> **Reiger said:**
> The commandline program alsamixer is very easy to use. Try using one of these modes:
alsamixer -V playback
alsamixer -V capture
alsamixer -V all

I do use a small alsamixer launcher that sit in awn.

It sure is a great tool, but the thing is i used to have default settings preserved upon reboot. :(

---

### Post by hype on 2010-09-19
> **mc4man said:**
> 
Edit: tested a start up script w/ audigy 2, works fine

Where do you put this script to have it executed before gdm starts?
/etc/rc.local is ok ?

---

### Post by mc4man on 2010-09-19
> Where do you put this script to have it executed before gdm starts?
/etc/rc.local is ok ? 
Beats me, sounds good -  I didn't bother, just put in a bin in path (~/bin here.), made executable and added to my user Start Applications. I'm the only user here so don't care about any 'global' setting or "before gdm starts"
What I used, you wouldn't need sleep if it runs earlier

```
#!/bin/bash
sleep [COLOR="Blue"]3[/COLOR]
amixer -c 0 -- sset Tone unmute 
amixer -c 0 set Bass [COLOR="Blue"]20[/COLOR]%

```

Feel free to improve, whatever..

---

### Post by hype on 2010-09-20
mc4man thanks mate; putting this

```
# By default this script does nothing.
amixer -c 0 -- sset Tone unmute
amixer -c 0 set Bass 0%
exit 0
```

into /etc/rc.local did the trick.
I'll keep it where it is and forget it, hope the bug will be resolved anyway :P

---

