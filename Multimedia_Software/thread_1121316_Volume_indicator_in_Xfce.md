---
title: "Volume indicator in Xfce"
date: 2009-04-09
forum: Multimedia Software
---

### Post by R2D2! on 2009-04-09
When I used Gnome, I l&#305;ked the volume &#305;nd&#305;cator: when I pressed the volume keys on my keyboard, volume appeared graph&#305;cally. Now I use Xfce, and the keys work and everyth&#305;ng, but I don't see any &#305;nd&#305;cator (bes&#305;des that small one on the panel, of course).

AFAIK, the volume &#305;nd&#305;cator &#305;s managed by gnome-sett&#305;ngs-daemon, and &#305;f I run &#305;t on Xfce, I can have the volume &#305;nd&#305;cator, but &#305;s there a nat&#305;ve appl&#305;cat&#305;on for Xfce?

—Ilhu&#305;temoc &#948;

---

### Post by Brandon Williams on 2009-05-08
I've searched around a bit, and I can't seem to find a built-in way to get the notifications, so ... I wrote a script that wraps around amixer. It throws up a notification bubble whenever it's run to indicate the resulting mixer settings.

Here's the script:
```
$ cat bin/volume_ctl 
#!/bin/sh

if [ $1 = 'up' ]; then
    amixer set Master 2+
elif [ $1 = 'down' ]; then
    amixer set Master 2-
elif [ $1 = 'mute' ]; then
    amixer set Master toggle
else
    echo "Unknown control command: $1" >&2
    exit 1
fi

STATUS=$(amixer sget Master | awk '$1 == "Mono:" { print $NF; }')
if [ $STATUS = '[off]' ]; then
    VOLUME=MUTED
    ICON=notification-audio-volume-muted
else
    VOLUME=$(amixer sget Master | sed '/^ *Mono: /{s/^.*\[\(.*\)%\].*/\1/;p;};d;')
    if [ $VOLUME -eq 0 ]; then
        ICON=notification-audio-volume-off
    elif [ $VOLUME -lt 33 ]; then
        ICON=notification-audio-volume-low
    elif [ $VOLUME -lt 66 ]; then
        ICON=notification-audio-volume-medium
    else
        ICON=notification-audio-volume-high
    fi
    VOLUME="${VOLUME}%"
fi
/usr/bin/notify-send "Volume Control" "$VOLUME" -i $ICON
```

It works well for me with xfce4-notifyd, not so well with notify-osd, since xfce4-notifyd stacks up the bubbles, making it possible to see continuing changes to the mixer setting if I continue changing the volume. The new notify-osd only throws up one bubble at a time, so I have to wait a few seconds between key presses.

I added keyboard bindings that call this script whenever I press the up, down, or mute volume control buttons on the keyboard.

---

### Post by R2D2! on 2009-05-08
Thank you. Actually I found your solut&#305;on before &#305;n a google search, but the problem rema&#305;ns w&#305;th not&#305;fy-osd. It doesn't obey the -t command :(

—Ilhu&#305;temoc &#948;

---

### Post by snap on 2009-05-12
You can also use gnome-osd-client in that script.

---

### Post by R2D2! on 2009-05-12
Yeah, but that's not Notify-OSD

&#8212;Ilhu&#305;temoc &#948;

---

### Post by Who on 2009-05-22
Awesome, thanks. I was about to try and write this but it was already done :)

I changed from Mono: to Left: so I actually got an ouptu (the line for Mono is totally blank...)

Thanks. This works nicely with xfce4-notify - any idea how to use notify-osd to give the text-less popups with volume icons?

Also, any idea how to make the brightness notification use notification daemon not the ugly window? If notify-osd is running it works but not if I have xfce40notify.

Who

---

### Post by Who on 2009-05-22
Righty, I'm using this, which plays nicely with notify-osd :D

```
#!/bin/sh

if [ $1 = 'up' ]; then
    amixer set Master 2+
elif [ $1 = 'down' ]; then
    amixer set Master 2-
elif [ $1 = 'mute' ]; then
    amixer set Master toggle
else
    echo "Unknown control command: $1" >&2
    exit 1
fi
VOLUME=$(amixer sget Master | sed '/^ *Front\ Left: /{s/^.*\[\(.*\)%\].*/\1/;p;};d;')
STATUS=$(amixer sget Master | awk '$2 == "Left:" { print $NF; }')
if [ $STATUS = '[off]' ]; then
    ICON=notification-audio-volume-muted
else
    echo $VOLUME
    if [ $VOLUME -eq 0 ]; then
        ICON=notification-audio-volume-off
    elif [ $VOLUME -lt 33 ]; then
        ICON=notification-audio-volume-low
    elif [ $VOLUME -lt 66 ]; then
        ICON=notification-audio-volume-medium
    else
        ICON=notification-audio-volume-high
    fi
    VOLUME="${VOLUME}%"
fi
notify-send "Volume" -i $ICON -h int:value:$VOLUME -h string:x-canonical-private-synchronous:
```

---

### Post by R2D2! on 2009-05-29
> **Who said:**
> Righty, I'm using this, which plays nicely with notify-osd :D
[...]

That worked perfectly, thanks :popcorn:

BTW, how do I mark th&#305;s thread as [Solved]?

—Ilhu&#305;temoc &#948;

---

