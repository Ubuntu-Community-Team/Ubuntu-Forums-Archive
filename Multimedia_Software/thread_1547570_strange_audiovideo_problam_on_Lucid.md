---
title: "strange audio/video problam on Lucid"
date: 2010-08-06
forum: Multimedia Software
---

### Post by 2xd on 2010-08-06
hi all,
I'm using Ubuntu 10.04 (Lucid Lynx) and just few hours ago installed ALSA 1.0.23 that fixed my audio problem (i'm using HP Pavilion Dv3-2150ej)

since the installation  i can play any mp3 | avi | mov | etc... 
but, for some strange reason, something like 1 hour after i log in my ubuntu account the playing option is like shutting down and none media player is willing to play my files, mp3 nor avi or mov.. the player (totem or media player) is starting, showing me the file length and just freeze there.

so every time i must log off and log in again to see another movie.

it didn't happened to me while i was watching but only after pausing or closing and reopening the player.

any one have any ideas ?

---

### Post by lidex on 2010-08-06
Try running your player from a terminal. Leave the terminal up the entire time until the error occurs and look for error messages. Check dmesg as well.

---

### Post by 2xd on 2010-08-07
I've open Totem throw Terminal and this is what I've got:

right after opening:

(totem:19685): Totem-WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name

sometime during the play:

(totem:19685): GLib-GObject-WARNING **: value "10752000" of type `guint' is invalid or out of range for property `connection-speed' of type `guint'


anyone ?

---

### Post by 2xd on 2010-08-07
btw, those error i mentioned above are appear to be not related to the problam as even after them everything kept working until like 2 hour after when it was became not working again

---

### Post by 2xd on 2010-08-08
any one ? 

btw, I have made some searching regarding that gnome-settings-daemon but could not find any solution for Lucid 10.04... can any one help ?

---

### Post by lidex on 2010-08-09
Make sure you have gstreamer configured properly. Do 'Part 1' here:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

