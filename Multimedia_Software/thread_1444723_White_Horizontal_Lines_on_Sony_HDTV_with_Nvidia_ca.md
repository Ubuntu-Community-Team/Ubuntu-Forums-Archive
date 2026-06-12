---
title: "White Horizontal Lines on Sony HDTV with Nvidia card via HDMI"
date: 2010-04-01
forum: Multimedia Software
---

### Post by ven_ on 2010-04-01
Hi,

I'm an annoying newbie, so please be gentle!  

I've had a look and can't find this particular problem on the boards (feel free to correct me if there is something useful already though).  I've recently gotten a Sony HDTV, and have hooked it up via HDMI to an Nvidia GeForce graphics card.  

Surprisingly enough, I'd like to watch movies/TV this way :)  However I'm experiencing flickery horizontal white lines on the desktop, and horizontal lines through video.  I generally use VLC to play stuff, and have the 805 Nvidia proprietary driver installed.

So far I've tried:

Changing the resolution and refresh rate (Including the native TV ones)

[LIST]
[*]Using Twinview, Separate X Screen and unplugging my monitor altogether.
[*]Uninstalling the Nvidia Drivers and using the standard ones
[*]Re-Installing the Nvidia Drivers
[*]Xine Player
[*]Changing video output of VLC to X11
[*]Using Force scaling (I think, it's a tv-specific setting to compensate for differences in native resolution)
[*]Switching desktop effects on and off
[/LIST]
In short, it doesn't seem to be an issue with drivers, resolution, refresh rate, video files, codecs or players.

If anyone has any suggestions as to how to stop these flickery lines it would be very much appreciated, I wouldn't like to have to give up on the OS over one problem :\

Many thanks in advance, I hope to see you all around :KS

---

### Post by brinamaree on 2010-04-01
Sorry dont have anything to input about the problem you are having but wanted to ask how you got your computer to connect through hdmi? I have a motherboard that has the hdmi connector, i can go to Nvidia x server settings and see that i am connected to tv but cannot seem to get video or sound to go to the tv...

---

### Post by ven_ on 2010-04-02
In this case it 'just worked', although I cannot play sound through the TV via HDMI.   I think there are quite a few threads about audio with HD and it should be fixable if you find them :)
 
As for setting up the TV, I plugged in the HDMI cable and installed the Nvidia proprietary drivers as you have done.   
 
[LIST]
[*]In the x server settings, if you choose 'X server display configuration'  there is a 'configuration' combo box (twinview or separate x screen should work, i chose twinview)
[*]If you like, you can change the resolution here, you will probably have to try a few to get it right.
[*]Then change 'Position' to whatever you want, 'clones' will just mirror the screen on both monitors.
[/LIST] 
This should give you output on the TV if you click 'Apply' - and you must save the settings for them to take effect if you log out/restart.  I had to change the permissions on xorg.conf to allow this.
 
I hope this makes some sense, and that you get your TV working happily :KS

---

