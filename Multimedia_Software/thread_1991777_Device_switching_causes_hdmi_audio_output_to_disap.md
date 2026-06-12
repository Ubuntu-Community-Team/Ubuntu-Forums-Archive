---
title: "Device switching causes hdmi audio output to disappear."
date: 2012-05-30
forum: Multimedia Software
---

### Post by jozeph78 on 2012-05-30
Hello. I am using ubuntu for my htpc. It is connected to a dedicated video processor (DVDO Edge). When I switch for a long time, I lose the audio device. I also have the position and size of the get reset. I have a script to deal with the latter, but the only way to get audio back is to reboot the machine. This sucks, and I know we can do better. 

I experienced this on Windows as well, so I realize this is most likely something with losing the HDCP handshake or other related to the way my Video Processor deals with switching. However, is there a way to reset this via a script to avoid the reboot? I'd like to prevent it from hapening entirely, but if I can use lirc to run a script that gets me functional that's good enough. 

Thanks for reading. Hope someone can help

---

### Post by the_pod on 2012-06-05
I'm having something of a similar problem.  

Do you get a resolution change as well?  I ask b/c my default status is 1080p.  On occasion - typically after turning off / on the receiver (receiver receives & transmits HDMI) or when using some Ubuntu native apps (firefox, calculator, etc...), it will switch to 720p and I lose the sound thatway.  A reboot / logoff fixes the issue but it is annoying.

Perhaps not related, but losing audio on hdmi after delays seemed a common thread.

---

### Post by jeliocranch on 2012-11-05
these threads are connected....
[http://ubuntuforums.org/showthread.php?p=12338550#post12338550](http://ubuntuforums.org/showthread.php?p=12338550#post12338550)

Any luck?  I don't know the mechanism for instantiating an hdcp handshake.  If anyone does, we can write a script to re-instantiate periodically.  Still, its merely a band-aid....

---

### Post by SushiAddiction on 2012-11-05
see this thread
[http://ubuntuforums.org/showthread.php?t=1961114](http://ubuntuforums.org/showthread.php?t=1961114)

This was one of the several bugs in unity that annoyed me for over a year... until I switched to gnome. Cinnamon  is good too. I have no idea why : /

Now I don't lose HDMI audio or have kernal panic for ATI on shutdown or Modal dialogues appearing on the wrong monitor :P  

I like ubuntu but unfortunately there are too many bugs. They can't keep going on like this :(

---

