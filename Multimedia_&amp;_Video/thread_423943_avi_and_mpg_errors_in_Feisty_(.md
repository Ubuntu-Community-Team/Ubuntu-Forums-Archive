---
title: "avi and mpg errors in Feisty :("
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by WinterWeaver on 2007-04-26
I recently installed Feisty, but now all my videos are messed up.

The video is not smooth, basically it's stuttering, and the audio is out of sync.

I have installed all the normal gstreamer stuff I need. Video's were playing normally on Edgy.

any help will be appreciated, because I Love Feisty thus far, and don't want to go back to Edgy.

Thanks,

WW

---

### Post by Kobalt on 2007-04-26
Did you install the drivers for your graphic card ?

---

### Post by WinterWeaver on 2007-04-27
ya, everything is installed properly... but now I've had a new thought.

I remember that I had a massive power spike this weekend. The PC literally switched of and on. Windows was still going (was playing WOW at the time). but everything was stuttering, even when moving the mouse.

I rebooted, and this all seemed to be fixed.

I'm wondering if this could have killed something on my motherboard or something the like.

How can I run a proper diagnostics on my system to see if ram, cpu and everthing is optimal?

Thanks,

WW

---

### Post by WinterWeaver on 2007-05-01
My videos are running perfect under windows. But not in Feisty.

does anyone know the solution ?

recap: Videos Stutter in Feisty

in Windows they play Perfectly
in Edgy they used to play Perfectly

I've tried both VLC and Totem
I have all GStreamer codecs installed

I have my video card drivers installed (along with Beryl)

---

### Post by mikuton on 2007-05-05
Hi WinterWeaver. I think I'm experiencing the same problem as you. Video playback used to be flawless in Breezy, Dapper and Edgy, but now it is stuttering and skipping with all players that I have tested (Totem, Mplayer, Gxine) in Feisty. My video card is nVidia GeForce Go 7300 and I have tried playback with both the "nv" and the accelerated "nVidia" driver (which I installed via the Restricted Drivers Manager). Video is stuttering with both drivers, so I don't think it is a driver related problem.  And at least in my computer the problem is not specific to video playback, but instead it seems that the whole distribution is suffering from general sluggishness.

Unfortunately I do not have a solution for this yet, but I noticed something strange that might lead to the real problem: When I start glxgears (or similar application) when I'm watching videos the stuttering is gone and playback is again as it used to be with Edgy (!?).  Similar effect can be observed for example with xscreensaver modules, which are by-default very laggy in my Feisty laptop, but when i start glxgears in another window in the same time the fps amount jumps to normal speed. E.g., if i say "/usr/lib/xscreensaver/atunnel -fps", I get something like 15-18 FPS (and lots of jerky movement from the tunnel), but if I start glxgears in another console the FPS amount normalizes to >80 FPS, and the movement is as smooth as it should.

If someone has any ideas what could cause this, please let me know.

---

### Post by WinterWeaver on 2007-05-07
hmmm... THAT... is very interesting... I'll give it a go

Here is something else I noticed.

I installed the Enlightenment E17 Desktop, to see what the look and feel is. The Videos Play perfectly in the players on E17. So I've been logging into E17 everytime I want to watch something, which is kinda annoying.... However your GLXgears solution seems simpler. I'll give that a go soon.

Ta for the reply!

---

### Post by mikuton on 2007-05-10
Hmm. It seems that (at least in my case) this problem is caused by the "2.6.20-15-generic" kernel that was installed with Feisty. I noticed that when I unplug the power cord of my laptop and go to battery-mode my laptop runs at normal speed (!), and when I reconnect the AC it's back to the old slow motion again. Perhaps this is some ACPI related issue that is specific to my laptop model (Asus A6VM)? Anyways, I installed the 2.6.20-15-386 kernel and the problem was gone.

---

### Post by WinterWeaver on 2007-05-10
ok, I've tried the GLX gears thing, and it does not work for me.

Kernel you say. hmm... I'll wait for the kernel update then, and see what happens. I guess I can swap back and forth to E17 to watch movies for the time being.

ta again for your input.

---

### Post by JeanJean on 2007-06-04
> **mikuton said:**
> Hmm. It seems that (at least in my case) this problem is caused by the "2.6.20-15-generic" kernel that was installed with Feisty. I noticed that when I unplug the power cord of my laptop and go to battery-mode my laptop runs at normal speed (!), and when I reconnect the AC it's back to the old slow motion again. Perhaps this is some ACPI related issue that is specific to my laptop model (Asus A6VM)? Anyways, I installed the 2.6.20-15-386 kernel and the problem was gone.

I've got the same problem, I've got ASUS A6Vc laptop and with glxgears on I get normal fps
Thx for the solution. Is this already posted as bug ?

JeanJean

---

