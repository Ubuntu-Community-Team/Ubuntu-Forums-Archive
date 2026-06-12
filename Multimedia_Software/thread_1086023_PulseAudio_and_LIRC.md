---
title: "PulseAudio and LIRC"
date: 2009-03-03
forum: Multimedia Software
---

### Post by drumfire420 on 2009-03-03
I'm attempting to set it up so I can change the volume on my system via a remote with LIRC.  There is a package called "pulseaudio-module-lirc" and i have it installed, however the all the documentation I can find for it is the read me (/usr/share/doc/pulseaudio-module-lirc/README) that is simply > For more information see [http://pulseaudio.org/](http://pulseaudio.org/)

the best I can find online is [_PulseAudio's Wiki for module-lirc_]("http://pulseaudio.org/wiki/Modules#module-lirc")

how do I configure this?!!!?!??

any help appreciated
thanks

---

### Post by drejom on 2009-03-22
hello

I got this package working on intrepid (at least) after lots and lots of googling...

add this to your lircrc file (where the *remote name* and *button names* come from lircd.conf)

```

begin
remote = [*your remote name*]
prog = pulseaudio
config = volume-down
button = [*your vol_down button name*]
repeat = 0
end

begin
remote =  [*your remote name*]
prog = pulseaudio
config = volume-up
button = [*your vol_up button name*]
repeat = 0
end

begin
remote =  [*your remote name*]
prog = pulseaudio
config = mute-toggle
button = [*your mute button name*]
end
```

and then edit the pulse config 
```
sudo pico /etc/pulse/default.pa
``` add the line

```

load-module module-lirc

```

finally, reload pulse

```
killall pulseaudio
pulseaudio -D
```

There you are! Back to only needing one remote...

---

### Post by drumfire420 on 2009-04-02
Thanks that is exactly what I wanted, and couldn't find. :p

---

### Post by njee on 2009-05-12
This worked great for me too - the only problem is that my soundcard volume is controlled by PCM channel not Master! Is it possible to get lirc to control the PCM channel?

---

### Post by drumfire420 on 2009-05-13
I had a similar issue, I seemed to fix it by changing what the default mixer track was

System > Prefrences > Sound: Default Mixer Tracks

I had to set that to controll the Pulseaudio card,and not ALSA

---

### Post by d3snoopy on 2009-08-09
Here's a bit more help with respect to settings:

I'm using a twinview setup to use a single box as both desktop and mythtv box.  I have two sound cards, one for the desktop in general, and the second (not default) for mythtv.

I changed myth's sound output to the non-default via pulse's volume control utility.

I couldn't figure out how to get myth to control the correct card/device, so I took volume control away from mythtv, and used pulse's module-lirc to make my remote control volume/muting.

I did all as drejom did, with the exception of a modified line in /etc/pulse/default.pa:

```
load-module module-lirc sink=[*your sink name*]
```

where I got the sink name from pulseaudio manager:

```
paman
```

flip to the "devices" tab, and copy the name of the sink that you want the lirc module to control.

---

### Post by knife on 2009-11-08
This is not working for me in Karmic. 

I have lirc working - if I run irw, I can see the expected output when I press the volume/mute buttons on my remote.  

I've set everything up as per the example above, and i've got remote and button names in the lircrc file that match what's in lircd.conf. When I run paman, it shows module-lirc in the list on the modules tab. But when I press the buttons in the remote, nothing happens in pulse or to my sound.  

Any ideas?

Fresh install of karmic (not an upgrade), HP HDX16 laptop. RC6 remote.

---

### Post by knife on 2009-11-09
OK, I spoke too soon.  When I restarted the computer, it was working.  For me, adding the "sink" parameter to the module-lirc line did not work.  When I deleted that parameter, lirc started working to control pulse's volume.

Now the only thing missing is the on screen display I get when I press the multimedia buttons on the keyboard.

---

### Post by Chareos on 2009-11-12
May I ask you,
Any news about the On Screen notification ?

---

### Post by MeduZa on 2011-05-18
> **Chareos said:**
> May I ask you,
Any news about the On Screen notification ?

I have "On Screen notification" working on 11.04, but, I don't use the pulseaudio licr module (I want the On Screen notification)

I use this configuration:

```
begin
        prog = irexec
        button = Vol_Up
        config = echo KeyStr XF86AudioRaiseVolume | xmacroplay $DISPLAY
        repeat = 1
        delay = 5
end
begin
        prog = irexec
        button = Vol_Down
        config = echo KeyStr XF86AudioLowerVolume | xmacroplay $DISPLAY
        repeat = 1
        delay = 5
end
begin
        prog = irexec
        button = Mute
        config = echo KeyStr XF86AudioMute | xmacroplay $DISPLAY
        repeat = 0
end
```

you need to install xmacroplay ( used xmacroplay becase irxevent don't works fine with some keys)

---

### Post by ArielEnter on 2011-08-02
Don't forget to install **pulseaudio-module-lirc** from the repos.

---

