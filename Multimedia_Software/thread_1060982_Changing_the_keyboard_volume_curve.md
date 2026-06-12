---
title: "Changing the keyboard volume curve"
date: 2009-02-05
forum: Multimedia Software
---

### Post by fastfret79 on 2009-02-05
Hi,

The volume up/down buttons on my keyboard work perfectly apart from the adjustment of one press is too much. Currently it takes 16 presses to go from 0% to 100% volume but I would prefer it to be more like 32 presses.

I'm guessing the volume curve is stored in a configuration file somewhere but I can't find it and there's nothing in the GUI to adjust it. 

Any ideas?

---

### Post by fastfret79 on 2009-02-06
I found that I can use the program keytouch to customise what happens when each button is pressed and can assign the following to volume up:

```
aumix -v +3
```

This will increase the volume by 3% which is exactly what I want. The problem now is that keytouch isn't capturing the key presses. I get the following from the command line:

```
Warning: Not all keys can be grabbed by this program. This
         can be caused by another program which is already
         grabbing these keys.
```

---

### Post by fastfret79 on 2009-07-28
Wow, after nearly six months I have finally solved my problem!!!

All you need to do is first make sure that the Volume up and down are disabled in the normal 'Keyboard Shortcuts' settings.

Then install the CompizConfig Settings Manager:

```
sudo apt-get install compizconfig-settings-manager
```

Then launch the utility and under the 'General' category, enable the 'Commands' module. THen under the 'Commands' tab, set the following for Command Line 0:

```
amixer set Master 3%+
```

Then on the 'Key Bindings' tab, set the 'Run Command 0' to 'XF86AudioRaiseVolume' (may be different in your case - use the buttons to grab your keypress)

Then repeat the process using a different slot (and change the '+' to a '-' in the command line) and bind to the Volume Down key... et voila!

If you are using metacity and not compiz, you can run 'gconf-editor' and under 'Apps > Metacity' there are similar settings under 'global_keybindings' and 'keybinding_commands'

Hope this helps someone else too :D

btw - there is space for up to 12 commands that you can set custom keystrokes for, plus button bindings and edge bindings too - lots of possibilities!

---

### Post by Sepanderi on 2009-07-29
> **fastfret79 said:**
> Wow, after nearly six months I have finally solved my problem!!!

Wow! Great stuff, thanks for sharing! :) I've been bugged with this issue lately as well (music always too loud or too quiet) so it's good that you posted the solution even if the thread seems like a monologue. Have to try this out soon.

It's very annoying to Google around and find posts like "Thanks for all the tips but I got it working now by myself" and no info for others with the same problem! :mad:

---

### Post by fastfret79 on 2009-07-29
Hey thanks Sepanderi, 

Sharing is always good, plus it's a good way for me to write a note for myself as I'll probably have forgotten how I did this once Karmic comes out!

I always found it an annoying problem and had all but given up on it - it's something that seems so simple but I couldn't find anyway of doing what was needed before. 

I recently switched from using the Gnome menu and panels to using tint2 and gnome-do and had lost the volume control in the sys tray (and is no longer needed) so the problem reared it's head again!

Let me know if you need any help setting this up and if any of my instructions aren't clear

---

### Post by fastfret79 on 2009-08-08
Hopefully the final entry to my mostly one-way conversation ;)

One thing I miss is the nice new notifications that came with Jaunty, so I modified a script I found that wraps amixer and uses the notify-send command to ... er ... notify you:

```
#!/bin/sh

if [ $1 = 'up' ]; then
amixer set Master 3%+
elif [ $1 = 'down' ]; then
amixer set Master 3%-
elif [ $1 = 'tinyup' ]; then
amixer set Master 1%+
elif [ $1 = 'tinydown' ]; then
amixer set Master 1%-
elif [ $1 = 'mute' ]; then
amixer set Master toggle
else
echo "Unknown control command: $1" >&2
exit 1
fi
VOLUME=$(amixer sget Master | sed '/^ *Mono: /{s/^.*\[\(.*\)%\].*/\1/;p;};d;')
STATUS=$(amixer sget Master | awk '$2 == "Mono:" { print $NF; }')
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

Just save the code and make it executable - I saved it to a file called 'VolChange' in my home folder.

Then in the compizconfig-settings-manager command section, I set the command for Volume Up to the following:

```
sh ~/VolChange up
```

Similarly, I changed the Volume Down command but with 'down' at the end. I have also added a 'tinyup' and 'tinydown' that alters the volume by 1% and assigned it to ctrl+Volume Up/Down for when you want small changes

---

