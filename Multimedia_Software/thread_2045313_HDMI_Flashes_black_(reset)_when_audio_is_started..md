---
title: "HDMI Flashes black (reset?) when audio is started."
date: 2012-08-20
forum: Multimedia Software
---

### Post by johnsky on 2012-08-20
I grant that this could be the issue of the TV, but it could also be an issue with drivers etc, so I'm hoping to get a troubleshooting process going.

Issue : When a program or task is started which contains audio, the screen flashes black for a split second (coming back fine), and audio engages a second later.

The same sometimes occurs when Audio disengaged.

For example : If I open a youtube video, the screen will flash black for half a second, and the audio will engage one second into the video. There are no further issues provided the video remains open. The same occurs when playing video files, or even with audio notifications such as with chat programs (in which case the first notification is missed, but subsequent sounds play fine.)

As far as I can gather, it seems to me like the video output disengages momentarily while the audio can be patched through the HDMI output of the video card. I could of course be wrong.

My first instinct is to assume that audio is disengaged when not in use, and given that it's fed through the HDMI port, that the video drivers have to re-start (or something similar) to combine the audio.
Hence, my hope is that it's a simple matter of finding a way to tell the audio not to disengage when not in use, or to tell the video driver to always have the audio patched.

Heck, I'm a total rookie in these matters, I'm used to troubleshooting network issues, not audio/video issues. I could be way off base with the cause here.

Which is obviously why I'm turning to you guys.

Setup : 
Ubuntu 12.04 64bit (no modifications other than proprietary driver)
All updates installed as of today.
MB : 970A-D3
CUP : X8 Bulldozer
Video Card : AMD Radeon HD 5450
Video Driver : ATI/AMD Proprietary FGLRX graphics driver
Connected to : LG surround sound + LG 47" tv
Via : HDMI

---

### Post by johnsky on 2012-10-16
Alright, it had been two months, and nobody responded.

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

Anyways, I found the solution on my own after two months.
No thanks to anyone else.

---

