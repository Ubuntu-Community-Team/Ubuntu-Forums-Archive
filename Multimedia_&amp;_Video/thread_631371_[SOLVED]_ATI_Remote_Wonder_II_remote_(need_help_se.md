---
title: "[SOLVED] ATI Remote Wonder II remote (need help setting it up)"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by cipher_nemo on 2007-12-04
I'm using MythTV 0.2x on Gutsy, and I need some help setting up and configuring an ATI Remote Wonder II.

I visited [http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder_II](http://www.mythtv.org/wiki/index.php/ATI_Remote_Wonder_II) which explains all about configuring it with LIRC, but it also mentions the module "ati_remote2" at the top of the article. I'd rather avoid LIRC since people have noted that it doesn't utilize the built-in mouse functionality.

Is there a guide out there for setting up this remote with that ati_remote2 module? Or is anyone willing to give me some steps or tips in getting it working?

Also, I purchased two of these for use with my HTPC running Ubuntu and MythTV. Does anyone know if I need to attach both RF receivers, or can I use one to capture commands from both remotes?

Thanks! :)

---

### Post by cipher_nemo on 2007-12-26
Wow, it looks like no one could help? Shame. :P

Well, I found all of my answers after many painful hours of 'Googling' and troubleshooting trial and error. I'm posting it for future prosperity in case someone 'Googles' down the same path as me, then marking this thread as solved...

***The solution:*** apparently ubuntu (linux kernel) doesn't like to function with the ati_remote2 module for modprobe unless LIRC is installed and active. That fixed my issue. Doing just a module load (modprobe ati_remote2) wasn't enough.

So now with LIRC installed and running, my ATI Remote Wonder II works perfectly.

***Note to those using this in the future:*** the developers who created the ati_remote2 module failed to include mappings (event triggers reported by xev) for the following buttons:[LIST]
[*]Ok
[*]Channel +
[*]Channel -
[*]ATI button
[*]Info button (small i)[/LIST]Also, the volume up/down and mute buttons are hard coded to the default (slot 0 alsa sound card) device's "Master" or "Analog Front" volume. I haven't found a way to direct this to control other volumes, or any gains for that matter. Not a huge problem if you have only one sound card, but definitely annoying if you have a sound card and forgot/didn't disable a motherboard's built-in sound.

Finally, if you use more than one ATI Remote Wonder II, do not attach more than one transmitter. Doing so will cause each button to be sent to your PC twice. You can use multiple remotes with a single transmitter.

What I've done to tweak my ATI remote (brief):[LIST=1]
[*]Install and load LIRC
[*]Load ati_remote2 module with modprobe
[*]Attach remote transmitter and test remote
[*]Use xev to find keycodes of remote buttons pressed
[*]I tested xmodmap of each keycode to switch to something else to make sure the key names were correct. This is important, since each key name is case sensitive.
[*]Created a script file of keycode= commands to remap to keyboard commands
[*]Set the script to run on boot-up
[*]Works with MythTV just fine[/LIST]Kudos to those who wrote the  [XfceMultimediaKeys page]("https://help.ubuntu.com/community/XfceMultimediaKeys"). Also, [this]("http://web.mit.edu/answers/xwindows/xwindows_xmodmap.html") is a good reference as well.

---

