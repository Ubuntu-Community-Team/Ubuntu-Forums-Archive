---
title: "Global hotkeys to control Banshee/Rhythmbox/etc volume with PulseAudio"
date: 2010-01-14
forum: Multimedia Software
---

### Post by BinaryMn on 2010-01-14
For awhile now, I've been trying to set two global hotkeys to control my volume level in Banshee. Before anyone comes in here and says to use the Volume Up/Volume Down keybinds in gnome-keybinding-properties, that does not work. That controls the master volume. I'm looking for a global hotkeys that control JUST the application volume.

I've been playing around now, and I think I might have found a way. Since 9.10, Pulseaudio is integrated and the default sound manager. It also allows controlling the application volume level. While changing the volume would be through Pulseaudio and not in the specific application, this would work.

My question is if there's a way to set a keybind to control a specific application's volume within Pulseaudio? Or even a way to set a keybind to the event that happens when a specific application's volume is turned up or down within Pulseaudio.

---

### Post by BinaryMn on 2010-01-15
Bump.

---

### Post by BinaryMn on 2010-01-16
Bump.

---

### Post by BinaryMn on 2010-01-18
Bump.

---

### Post by BinaryMn on 2010-01-21
Bump.

---

### Post by BinaryMn on 2010-01-23
Bump.

---

### Post by BinaryMn on 2010-01-23
Bump.

---

### Post by BinaryMn on 2010-01-25
Bump.

---

### Post by chewearn on 2010-01-25
I admire your persistence. ;)  And as a reward, I spend several hours time on Google to find a solution for you.

Read here: [http://pulseaudio.org/wiki/CLI](http://pulseaudio.org/wiki/CLI)

The command you want to investigate are:

1. list-sink-inputs
This will let you identify Banshee application in the sink input lists.  E.g.
```
pacmd "list-sink-inputs"
```2. set-sink-input-volume
This will let you set the volume.  E.g.
```
pacmd "set-sink-input-volume $index $volume"
```Unfortunately, I have Ubuntu Intrepid; the pacmd commands only appear to work properly in interactive mode.  The example command above don't work but I got them from:
[http://ubuntuforums.org/showthread.php?t=1132200](http://ubuntuforums.org/showthread.php?t=1132200)
[http://blog.robinpecha.cz/command-line-cli-switch-for-switching-default-sound-card-in-ubuntu-pulse-audio/](http://blog.robinpecha.cz/command-line-cli-switch-for-switching-default-sound-card-in-ubuntu-pulse-audio/)

---

### Post by jviktor on 2010-06-16
It's not a pulseaudio way, but can be useful:

Rhythmbox has a cli client application that you can use to control:

```
jv@eee:~$ rhythmbox-client --play-pause
jv@eee:~$ rhythmbox-client --volume-up
jv@eee:~$ rhythmbox-client --volume-down
```
etc.
So simply just set a keyboard shortcut (System=>Preferences=>Keyboard Shortcuts) to bind a key to these commands. It works for me ;)

jv

---

### Post by gunith on 2011-06-12
As for Banshee, type ```
banshee --help-playback
``` in your terminal to get the list of the commands.

From those, I find ```
banshee --next, banshee --previous and banshee --toggle-playing
``` most useful.

I of course use compiz-config or ccsm to do the shortcut binding with the commands.. I find that easier...

Good luck!

---

### Post by ChazZeromus on 2013-02-21
> **jviktor said:**
> It's not a pulseaudio way, but can be useful:

Rhythmbox has a cli client application that you can use to control:

```
jv@eee:~$ rhythmbox-client --play-pause
jv@eee:~$ rhythmbox-client --volume-up
jv@eee:~$ rhythmbox-client --volume-down
```
etc.
So simply just set a keyboard shortcut (System=>Preferences=>Keyboard Shortcuts) to bind a key to these commands. It works for me ;)

jv
This is the best answer!

---

### Post by codemaniac on 2013-02-21
Old thread closed.

---

