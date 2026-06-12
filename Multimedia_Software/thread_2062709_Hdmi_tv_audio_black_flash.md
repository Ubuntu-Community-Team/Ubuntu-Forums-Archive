---
title: "Hdmi tv audio black flash"
date: 2012-09-25
forum: Multimedia Software
---

### Post by johnsky on 2012-09-25
From what I gather, every time a sound plays on Ubuntu through HDMI (whether it's a system notification sound, audio from a game, audio from a video, anything) the audio has to be combined with the HDMI output.

This results in the HDMI flashing black as it re-syncs. It's only about half a second, but it can get rather distracting.

Now, I noticed something interesting. If one audio source is already active (like playing a video), and another audio source chimes in (like chat notifications) they come through just fine, with no re-syncing of the HDMI video feed.

This tells me that all we need to do is somehow keep the Audio output active. Either by telling it not to de-combine when not used, or by sending a constant audio signal to output (dead air?).


So essentially, I need to keep the audio active through HDMI right from the moment of startup.
I have no idea how I'd do this.

---

### Post by johnsky on 2012-10-16
I began just rampaging through the system files myself, I've solved the problem, and left a wake of destruction behind... to the point that I'll need to start over fresh again... but the point is I found the cause.


For those of you like me with this issue : here's how to fix it.

1 : open a terminal (I'm fond of ctrl-alt-t)
2 : type >  sudo nano /etc/pulse/default.pa 
3 : type your password when prompted
4 : scroll down until you find this entry 
> ### Automatically suspend sinks/sources that become idle for too long
load-module module-suspend-on-idle
THIS is the cause of your headache. Look at it, hate it, point your finger at it, yell at it, berate it... JUST UNLEASH YOUR FURY AND VENGEANCE UPON THIS LINE!!!!

... and then comment the line out by adding # infront of > load-module module-suspend-on-idle to make it > #load-module module-suspend-on-idle

5 : press ctrl-x and it will ask you if you want to save, yes, yes you do. Then it will ask where, just press enter to overwrite the original file.

Now log out, or restart, and log back in.
The first sound that plays will still flash your screen black.
But every sound after that will come through without causing issues.

HECK YES!!!!
You see, the primary problem all along was with combining audio and video together through HDMI, I didn't solve this part...
but the exacerbating part of the problem was that pulseaudio likes to "suspend" when not in use. Which means the next sound your computer plays has to recombine the audio and video ALL OVER AGAIN.
Which meant EVERY chat notification, EVERY system sound, EVERY any sound caused the screen to flash black for a second or two.

---

### Post by shrimpy89 on 2012-12-31
A poster who comes up with his own fix and is thoughtful enough to post it for others?  You're my favorite kind of person.

Fixed my problem on Xubuntu 12.10!  Thanks!

---

