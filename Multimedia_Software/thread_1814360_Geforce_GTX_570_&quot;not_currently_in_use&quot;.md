---
title: "Geforce GTX 570 &quot;not currently in use&quot;"
date: 2011-07-29
forum: Multimedia Software
---

### Post by Maggeych on 2011-07-29
Hi,
I just got my new Hardware together and thought I'd try 11.04 ...
The problem is that my GTX 570 doesn't seem to use the official nvidia driver at least that's what "Additional Drivers" says ("not currently in use"...
Dragging windows for example is where it gets really apparent.

What I tried so far:
- latest swat repos driver
- deinstalling everything related to nvidia, reboot, reinstall, reboot
- letting nvidia-settings rewrite my xorg.conf
- running glxgears but it doesnt even start just freezes everything and I need to kill X, same in Ubuntu Classic

Note I'm running on 64-bit
Intel i5 2500k
Asus p8p67
Geforce GTX 570

I wonder if x86 would be any better but that really wouldn't be a solution for me since I got 8gb of ram...

Any thoughts on how to solve this? It really sucks having a new system running but always knowing it's not doing what it'd be capable of...

---

### Post by SAEconomist on 2011-07-29
Hey Man,

So I just (finally) registered on this forum to answer your question. I also have 8GB of RAM, am running Ubuntu 10.04 LTS 64bit and have a Nvidia GTX 570 (I have the SC version). I, however, have them all working together. This is how:


[LIST=1]
[*]Go to: [http://www.nvidia.com/object/linux-display-amd64-275.21-driver.html](http://www.nvidia.com/object/linux-display-amd64-275.21-driver.html) and download that driver. Note that is a 32 bit and 64 bit compatible driver that does support the GTX 570.
[*]You will probably try and encounter a "You are running an X-Server error" if you try to execute the script immediately. So you will need to console it:
[LIST=1]
[*]Hit Ctrl+F1 and you will find yourself in a terminal view.
[*]Type in your username and password
[*]Then you will need to kill the X-Server (This is the .XAuthority software from Xorg used for your Gnome display). To do this type: sudo /etc/init.d/gdm stop.
[*]Now you have killed the X-Server and you should be able to install the driver. Type sudo '<path to wherever you downloaded the script>'
[/LIST]
[*]At this point I let NVidia do all the work and I selected yes for most things (incl. 32 bit additional support). Make sure you say yes to updating the X-Server config
[*]Now reboot "sudo reboot"
[*]And now your GTX 570 should be working and you should be able to do as you wish
[/LIST]
A few cautionary notes. Try and avoid killing the process directly using ps aux or ps -x followed by a gruesome kill command. You don't know what can happen. And also if something goes terribly wrong, to get back to your GUI (before killing the X-Server hit Ctrl+F6 (or 7)) or to start the X-Server again simply type startx. 

Also, I am using gnome. I do not know what would happen with Unity or KDE. 

I hope that this was of some assistance.

---

### Post by Maggeych on 2011-07-29
wow first off thanks alot!!
I already had that driver downloaded but thought maybe it's best to stick with the drivers from the repos to not cause any conflicts or to easily have them updated/removed/whatever "the usual way"...

Well anyways I guess I'll try it right away then...
I'll report back - fingers crossed ;)

---

### Post by Maggeych on 2011-07-29
well... it didn't really change anything...
I still got rough window dragging, additional drivers lists nothing now though.
1080p files play smooth but they did so before and I don't know if that's really the CPU and not because of hardware acceleration. Glxgears still freezes.

How do I know if my card is working? It is listed as supported but there must be something wrong here.
Choppy window dragging is really not cool :(

---

### Post by BicyclerBoy on 2011-07-29
I would try to avoid the nvidia installer method..
xorg-edgers ppa has the latest driver..

Post your
/var/log/Xorg.0.log
as a file attachment (.txt) 

Have you used nvidia-settings to turn on openGL vsync ?

glxinfo

If you are using composite desktop effects, there is yet another config tool (CCSM ?) to control the vsync tearing ...

---

### Post by Maggeych on 2011-07-29
I got CCSM installed. But my problem is not really tearing. It's more like the window is moving along in small jumps when I drag it. It lags behind and moves in a pretty bad stuttering manner, no tearing really so I guess VSync is not what I'm looking for is it?
Oh and I noticed when I disable OpenGL in CCSM, most of the decorations are gone, unity is pretty much destroyed but window dragging is fine then! Ubuntu Classic drags windows ok too but glxgears doesn't work either.

I attached the files but cut out some unrelated lines due to filesize limitations. Not that I really know what they're saying but from a quick look I guess nvidia driver is loaded right? So there's something wrong with OpenGL since glxgears just freezes?
As mentioned earlier HD movies run fine. Or could that be just the CPU?

---

### Post by SAEconomist on 2011-07-30
Hey,

That is rather strange. I realized just now that I also, in fact, have the same processor as you too (I recently got this new computer).  After doing what I did, I noticed a few changes: the display was good and there was no problems enabling desktop effects. I do not notice any of the dragging issues you have ...

When you run "nvidia-settings" in the terminal, it will open your X-Server settings. Does your system recognize (Under the GPU0 tab) that you are running a "Ge Force GTX 570"? If it does, then your problem is most likely to be stemming from Unity rather than from your hardware. I have been looking for a "Nvidia-usage-monitor" type of software to see whats happening, and I have been rather unsuccessful. Have you considered trying out Gnome 3 yet? 

As to whether or not your CPU could be doing all the work, yes. All i-series processors come with on-board graphics handling.

Regards

---

### Post by Maggeych on 2011-07-30
In fact nvidia-settings does list GTX 570 as GPU. I added the edgy repo BicyclerBoy mentioned and installed quite a few updates regarding the nvidia but also others. I understand that this is rather the experimental side? Well what I'm trying to say is that these updates made glxgears run. But glxgears pretty much confirms the issues. I'm getting 60 FPS which can't be the real thing with that system.

EDIT: OK I double checked glxgears and I noticed if I disable VSync for OpenGL in nvidia-settings glxgears freezes again. With VSync enabled 60 FPS should be good since it's my monitor refresh rate?

Just for laughs I'll boot the live CD and check that. Not that I'm expecting it to be any different but I'm starting to run out of ideas :confused:

EDIT2: live cd boots into ubuntu classic :(

---

### Post by realzippy on 2011-07-30
Post your /etc/X11/xorg.conf please...

---

### Post by Maggeych on 2011-07-30
here it is...

---

### Post by realzippy on 2011-07-30
nothing wrong.
So run 

```
sudo nvidia-bug-report.sh
```

and post created file (home folder)

---

### Post by Maggeych on 2011-07-30
there you go...

---

### Post by realzippy on 2011-07-30
No errors.According to bug report your driver is working.
Maybe you should test the 280.beta or an older version (think your card is supported since 260.xx).Sorry.

---

### Post by Maggeych on 2011-07-30
Well thank you for having a look at it anyway.
Does that mean it's not really driver related but more a Unity kind of problem?

---

### Post by realzippy on 2011-07-30
Well,you could sort this out when you start the "Classic" session...

---

### Post by BicyclerBoy on 2011-07-30
All your log files seem fine.
Don't place too much importance to glxgears behaviour..Your video card could be so fast it crashes glxgears. This program is just a simple openGL test & vsync check.

Do you have any openGL intensive games to try ?
Penumbra ?

If could be possible that Unity does not recognise your video card.
It has a blacklist file somewhere...

---

### Post by Maggeych on 2011-07-30
hmmm... unity support test is fine too :confused:

```
caughtfire@caughtfire-System:/usr/lib/nux$ sudo ./unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 570/PCI/SSE2
OpenGL version string:  4.1.0 NVIDIA 280.11

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
```

Ok  Penumbra Overture Demo runs good I guess... Full details AA and  everything at 1920x1080. Only bright lights or bright surfaces got a bit  of "film grain" over them. Could be that it is intended idk.
This can't be only CPU rendering right?

Well if we assume OpenGl -can- work what is Unity missing then?!

---

### Post by Maggeych on 2011-07-31
Ok so just a little heads up here in case someone else has the same issues with that card.
I am now back to 10.04 LTS and after installing the latest nvidia drivers (not through the 10.04 repositories but with the official installer) everything seems to be as it should.
Gonna try to install gnome3 now to get a bit of a more modern feeling :)

If anybody got 11.04 running with a GTX 570 and nvidia drivers actually "in use" let me know!

---

### Post by realzippy on 2011-08-02
*...after installing the latest nvidia drivers (not through the 10.04 repositories but with the official installer)...*

So you did not try to install driver manually 1n 11.04 (as suggested?)...
anyway,you can set thread as "solved" (threadtools..)

---

