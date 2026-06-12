---
title: "Problems with Pulse Audio Sources"
date: 2024-08-05
forum: Multimedia Software
---

### Post by deck on 2024-08-05
When I log out and later log back in the audio sources for Pulse audio change.  I have some drivers running under WINE that the output switches to instead of the better quality card that I use. The input sometimes switches to the crappy mike in the video camera that I use for online meetings or if it is on the audio card, it switches from the microphone input.  Where are the defaults set for the Pulse Audio inputs and outputs?

I am using Ubuntu 22.04 with the classic Gnome interface (I don't like the default interface because I have been around Linux since 1994.  Plus I hate the Windows 'Chiclet" interface since I first was forced to use Win 10 at work.)

deck

---

### Post by TheFu on 2024-08-05
You can set the default devices to be used in your personal settings. But since Pulse is going away for Pipewire, perhaps seeing if that makes the issue go away would be worthwhile?  But if you are like me, and know that "new" is the enemy of "stable", then I'd go with the client settings in ~/.config/pulse/client.conf
At the very top, there are settings for the default-sink, default-source and default-server.  If you don't have that personal settings file, copy the one in /etc/pulse/client.conf over.

Or you can run pacmd to set the defaults using names, if you like.
Find the device names with
```
$ pacmd list-sinks|egrep '\.name|name:|port|state'
```
and 
```
$ pacmd list-sources | egrep '\.name|name:|port|state'
```
There are shorter commands, but I like to get the names.

Then use something like, 
```
$ pacmd set-default-source alsa_input.usb-046d_HD_Pro_Webcam_C920_xyzabc12345-02.analog-stereo
```
to set the default. You can set the default sink similarly. I just don't have an example in my notes.

Add this into your X-Session startup list of commands to be run, after the login finished AND a GUI is started.  Obviously, you probably don't want to do this for all logins, since we use ssh logins all the time.

---

