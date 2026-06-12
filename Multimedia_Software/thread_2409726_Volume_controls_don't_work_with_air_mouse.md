---
title: "Volume controls don't work with air mouse"
date: 2019-01-06
forum: Multimedia Software
---

### Post by Adam_Jacobs on 2019-01-06
I have recently bought an [air mouse]("https://www.mythtv.org/wiki/Air_mouse_rf_remote") to use as a remote control with my MythTV system.

Most things either work out of the box or can be made to work by playing around with key bindings. But the one important thing that isn't working is the volume control. The remote control has a mute button and volume up and down buttons. According to the link above, the mute button "should work" (but it doesn't) and "[COLOR=#252525][FONT=sans-serif]whether the volume control keys will work depends on the way the system audio is set up".

[/FONT][/COLOR]Well, my system audio is obviously not set up the right way. If I use the mute button, I get a little message on the screen saying "audio muted", but it isn't, and if I use the volume keys I get similar messages telling me that the volume is going up or down, but again, it has no effect on the actual volume.

If I try to set up key bindings with those keys, the MythTV key bindings editor doesn't recognise them as actual key presses.

Any ideas how I can get the volume and mute controls to work with MythTV?

MythTV 0.29 on Ubuntu 18.04.

---

### Post by chas94539 on 2019-01-29
I'm having the same problem with a Rii i8+ wireless mini-keyboard.  The problem appears to be another application is grabbing the volume control keys so they are not being passed to MythTV.  This can be verified by running xev from a terminal prompt (must be a terminal running under the X server such as Gnome, KDE, XFCE4, etc.).  Then put the cursor in the pop-up window.  Any key you press will then be displayed.  If you see the word "NotifyUngrab", this indicates another program has hijacked that key.  You can press alphabetical keys to see what it should look like when it is working properly.

I'm in the process of trying to figure out which program is grabbing it.  In Xubuntu 18.10, it was the pulseaudio panel plugin.  I removed the panel and the volume keys and all the other media keys (FFWD, FRWD, PAUSE) started working.  Now, I'm trying to track down the program grabbing the volume keys in Mythbuntu 16.10.

A big clue is a volume control bar appears in the upper right corner of the screen.  As I press the volume up and down keys, the bar moves to the right and the left, however, it has no effect on the volume.  All I need to do is figure out which program or plug-in is displaying that bar.  I'm thinking if I remove it, the volume keys will start working through MythTV.

Edit:  I found it!  On Mythbuntu 16.10, go to Applications | Settings | Session and Startup.  Click on "Application Autostart" tab.  About half-way down the list is "XFCE Volume Daemon (Pulseaudio)(Daemon managing the volume multimedia keys and displaying volume notifications for Pulseaudio)", I unchecked the box next to it, then rebooted the system.  The volume up and down keys on the remote now control the MythTV volume to the TV.  YEA!!!!x

Hope this helps!

---

