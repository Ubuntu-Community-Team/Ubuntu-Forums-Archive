---
title: "shut down with remote control"
date: 2010-05-12
forum: Mythbuntu
---

### Post by jvels on 2010-05-12
Hi

I have a mythbuntu 10.04 running with a MCE remote control:
[http://www.hauppauge.co.uk/site/product](http://www.hauppauge.co.uk/site/product) … emote.html

It work nice in mythtv, but I would like to use the remote control button to turn off the computer.

Which config files do I need to edit? and what do I need to add?

There are some colored buttons at the remote control, they have not any function in mythtv, how do I add fuction to them?

/Jesper

---

### Post by volkswagner on 2010-05-12
Sorry I can't help your exact request.  I would be a little hesitant with power off on the remote, think sitting on the button when returning to the couch with some chips...LOL

I am not sure if you are aware, but you can do it from within mythtv menu.  It may be a couple extra button presses, but not much more if you were to set a "confirm power off" OSD.

In depending on your mythtv version, you can set the menu to allow power off and or reboot, when exiting mythtv.

Mythfrontend > Utilities/setup > Setup > General > page 8.

Customise exit menu options "show quit and shutdown" or "quit, reboot and shutdown"

Now when you escape out of mythfrontend, you can select shutdown or reboot.
Hope this helps.

---

### Post by laffinet on 2010-05-12
Here's what you need:

1. A script that shuts down the computer, e.g.

```
#!/bin/bash
#
#restart computer
#
sudo shutdown -h now
```

2. Modified lirc

```
begin
prog = irexec
button = *whatever_button_you_want_to_use_for_shutdown*
config = *path_to_script/shutdownscript*
end
```

To find the right name for whatever button you want to use, type the following in a terminal:
```
irw
```
Then press the button on the remote. This should give you an output similar to this:
```
000000037ff07ba3 00 Green mceusb
```
Use that button name in the lirc file

3. enable shutdown without password:
In a terminal, enter
```
sudo visudo
```
add the following line at the bottom, replacing *user* with your username
```
%*user *ALL = NOPASSWD:  /sbin/shutdown
```

---

