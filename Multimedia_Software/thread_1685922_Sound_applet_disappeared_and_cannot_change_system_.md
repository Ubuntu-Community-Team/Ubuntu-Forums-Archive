---
title: "Sound applet disappeared and cannot change system volume."
date: 2011-02-11
forum: Multimedia Software
---

### Post by hitchhiker4242 on 2011-02-11
Hello. Recently I installed JACK and Ardour to try out. Later I decided against it and so I uninstalled them. After restarting my computer, I noticed that the sound applet has disappeared from the panel, although the battery and mail icons are still present. There is still sound coming out of my laptop speakers, but it is stuck at whatever volume I had it set on before the last time I shut down. Volume sliders inside Banshee and such still function, but I cannot change the overall system volume, and my keyboard shortcuts for this have stopped working as well. When I go into System->Preferences->Sound, all I get is a message that says "Waiting for sound system to respond." and nothing happens. I've tried searching around for a solution, but nobody I could find seems to have had a similar problem, and none of the various other solutions proposed have worked for me. I'm on Ubuntu 10.10 by the way. Any help would be appreciated!

---

### Post by Cracklepop on 2011-02-11
System > Preferences > Startups 

add gnome-volume-control-applet. 

I always remove the horrible and unnecessary Indicator Applet, and leave the Notification Area, add the vol control and use the power settings to add a battery indicator.

---

### Post by hitchhiker4242 on 2011-02-11
Thanks for the response. I tried entering "gnome-volume-control-applet" in a terminal without success. All I got was the following output, repeating itself every few seconds:

(gnome-volume-control-applet:4565): WARNING **: Connection failed, reconnecting...

I found a workaround. By using alsamixer I am able to control the volume, but I hope I'm not stuck this way b/c it's a tad inconvenient :???:. So alsa is working apparently. I went into System->Preferences->Multimedia Systems Selector. When trying to run a test using OSS, it says "Could not open audio device for playback." Using Pulse returns "Failed to connect: Connection refused." So something somewhere is failing to connect to another thing somewhere else?

---

### Post by Cracklepop on 2011-02-11
> **hitchhiker4242 said:**
> Thanks for the response. I tried entering &quot;gnome-volume-control-applet&quot; in a terminal without success. 

You didn't follow the instructions.  Don't enter it in a terminal, add it to Startup Apps.

---

### Post by hitchhiker4242 on 2011-02-11
Yeah, I've seen it suggested both ways in other threads. I figured if I couldn't even launch it in the first place then it wouldn't launch on start up either. Just to be safe I tried it just now. Added it to startups and rebooted, but no luck.

---

### Post by hitchhiker4242 on 2011-02-11
Well, I read somewhere that said if you get the message "Failed to connect: Connection refused" when trying to run Pulse, it means the Pulse daemon isn't running. I started installing random Pulse preferences managers in Software Center and voila! Suddenly everything is working again and gnome volume control applet appears in my panel. Added it to startups and this now works on reboot as well. Only thing is that in the notification that pops up when adjusting the volume using the keyboard the icon is all pixelated ](*,). But at least its working now, so I'll just have to live with it :).

---

