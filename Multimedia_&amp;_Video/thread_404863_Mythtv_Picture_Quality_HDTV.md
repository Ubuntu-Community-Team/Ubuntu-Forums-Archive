---
title: "Mythtv Picture Quality HDTV"
date: 2007-04-09
forum: Multimedia &amp; Video
---

### Post by Erlander on 2007-04-09
I have installed Mythtv on a pc (Specifications in my signature) using Feisty and have been disappointed with picture quality on HDTV.  Dropped frames showing up as a jerky picture and stuttering sound.  This is still there to a lesser extent with the standard definition DVB channels too.

In addition I have installed Myth Frontend on a second pc with similar specs but with an ATI 9700 Pro display card.  Not surprisingly it is worse.  Both pc's have the Restricted Drivers installed.

However on both pc's I also installed Kaffeine and it does not have these display problems.

I have Googled to try and find an answer, have altered settings in the frontend Utilities-Setup/Setup/TV Settings/Playback but so far have not had any improvement.

Does anyone have suggestions on this?

TIA

Rob

---

### Post by Erlander on 2007-04-12
Well after turning off Closed Captions and Advert Detection and playing with decoder settings I now have acceptable viewing on the box listed in my signature.  HDTV is still using 60% of cpu and SD 20-40%.  Based on my Windows experience this is still rather high for this setup.

My other box with the ATI 9700 Pro is still struggling although under Windows it had more than enough grunt.  I am guessing that this is ATI drivers and a decoder issue.

It has an AMD Athlon XP 3200+ on a Gigabyte Asus A7V600-X, 1Gb ram and the ATI 9700 Pro.

Any suggestions?

Rob

---

### Post by electronikjunkie on 2007-04-13
I found that compiling the latest Nvidia driver is better than just installing nvidia-glx. I have less stuttering when XvMC is in use. Also make sure "Extra audio buffering" is checked in MythTV Frontend to help decrease stuttering.

If your using Edgy or less check out here: [http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

The Envy script works great.

For Feisty go here: [http://ubuntuforums.org/showthread.php?t=296933](http://ubuntuforums.org/showthread.php?t=296933) (this post might be a bit dated, but you should get the idea.)

Just my .02 cents...

---

### Post by Erlander on 2007-04-14
Thank you.

I have extra audio buffering checked but cannot use Envy as I'm running Feisty.  Not sure how the Linux Restricted Drivers Install compares to Envy though.

I have now managed to stop frames being dropped on HDTV by trying various decoder settings.

However the real difference between Ubuntu and Windows here is that I've so far not been able to get hardware acceleration working.  Messages tell me that XvMC is not initialised.  I'm really wondering why I bothered to buy a decent reasonably powerful Nvidia card if this cannot be done.

Rob

---

### Post by electronikjunkie on 2007-04-14
Make sure you have in /etc/X11/XvMCConfig 
```
libXvMCNVIDIA_dynamic.so.1
```
Choose "Standard XvMC" in MythTV-Frontend. If you see a black/white OSD then XvMC is working.

---

### Post by Erlander on 2007-04-15
Thank you for that.

The file is there and does list libXvMCNVIDIA_dynamic.so.1  Yes the standard XvMc does give the black and white on screen display and cpu usage is 40-60% on HDTV.  Some dropped frames at the start though.  Will try more tweaking and see what happens.

Interestingly with the VIA chipset on this motherboard the VIA XvMc uses nearly 100% cpu with a lot more stuttering.

While doing this tweaking I'm running mythtv in a window, starting it from terminal and having System Monitor running as well.  This gives me a better idea how its going.

Rob

---

### Post by Erlander on 2007-04-15
I have acceptable picture quality using the Kernel alogarithm and standard XvMC but it is producing a lot of errors as shown in the code below.

CPU Usage is 40-60%

Can anyone suggest what I ned to do to remove some of these errors.

Rob

```
rob@Ubuntu:~$ mythfrontend
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 171
  Major opcode:  149
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
2007-04-15 20:34:43.756 Using runtime prefix = /usr
2007-04-15 20:34:43.800 Gnome-Screensaver support enabled
2007-04-15 20:34:43.801 DPMS is active.
2007-04-15 20:34:44.045 New DB connection, total: 1
2007-04-15 20:34:44.066 Connected to database 'mythconverg' at host: 192.168.2.3
2007-04-15 20:34:44.067 Total desktop dim: 1024x768, with 1 screen[s].
2007-04-15 20:34:44.086 Running in a window
2007-04-15 20:34:44.087 Using screen 0, 1024x718 at 0,25
2007-04-15 20:34:44.096 Current Schema Version: 1160
2007-04-15 20:34:44.096 mythfrontend version: 0.20.20060828-3 www.mythtv.org
2007-04-15 20:34:44.096 Enabled verbose msgs:  important general
2007-04-15 20:34:44.618 Total desktop dim: 1024x768, with 1 screen[s].
2007-04-15 20:34:44.619 Running in a window
2007-04-15 20:34:44.620 Using screen 0, 1024x718 at 0,25
2007-04-15 20:34:44.620 Switching to square mode (G.A.N.T.)
2007-04-15 20:34:44.646 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2007-04-15 20:34:45.064 Joystick disabled.
2007-04-15 20:34:45.539 Loading from: /usr/share/mythtv/themes/G.A.N.T./base.xml
2007-04-15 20:34:45.655 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-04-15 20:34:45.713 Registering Internal as a media playback plugin.
2007-04-15 20:34:49.591 New DB connection, total: 2
2007-04-15 20:34:49.593 Connected to database 'mythconverg' at host: 192.168.2.3
2007-04-15 20:34:49.626 Connecting to backend server: 192.168.2.3:6543 (try 1 of 5)
2007-04-15 20:34:49.640 Using protocol version 31
2007-04-15 20:34:49.660 TV: Attempting to change from None to WatchingLiveTV
2007-04-15 20:34:49.661 Using protocol version 31
2007-04-15 20:34:49.864 DPMS Deactivated 
2007-04-15 20:34:50.019 NVP: Disabling Audio, params(-1,2,44100)
2007-04-15 20:34:50.039 VideoOutputXv: XvMCTex: Init failed
2007-04-15 20:34:50.041 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0x1a6
2007-04-15 20:34:50.732 TV: Changing from None to WatchingLiveTV
2007-04-15 20:34:50.743 The realtime priority setting is not enabled.
2007-04-15 20:34:50.852 Video timing method: USleep with busy wait
[mpegts @ 0xb7355ec0]Parser not found for Codec Id: 94211 !
2007-04-15 20:34:51.639 VideoOutputXv: XvMCTex: Init failed
2007-04-15 20:34:51.640 VideoOutputXv: XvMC Adaptor Name: 'NV17 Video Texture'
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  14
  Resource id:  0x1a6
2007-04-15 20:34:52.175 VideoOutputXv: ProcessFrameXvMC: Tried to reuse frame but failed
2007-04-15 20:34:52.175 VideoOutputXv: ProcessFrameXvMC: Called without frame
2007-04-15 20:34:52.176 AFD: Opened codec 0x919a020, id(MPEG2VIDEO_XVMC) type(Video)
2007-04-15 20:34:52.177 AFD: Opened codec 0x9cdca90, id(AC3) type(Audio)
2007-04-15 20:34:52.194 Opening OSS audio device '/dev/dsp'.
2007-04-15 20:34:52.201 NVP: Enabling Audio
XvMC: picture structure FRAME
2007-04-15 20:34:52.764 NVP: prebuffering pause
2007-04-15 20:34:53.411 NVP: prebuffering pause
2007-04-15 20:34:53.683 NVP: prebuffering pause
2007-04-15 20:34:56.741 NVP: prebuffering pause
2007-04-15 20:34:56.756 NVP: prebuffering pause
2007-04-15 20:35:18.199 VideoOutputXv Error: ProcessFrameXvMC: Failed to get OSD lock
2007-04-15 20:36:12.885 VideoOutputXv Error: ProcessFrameXvMC: Failed to get OSD lock
2007-04-15 20:37:13.244 NVP: prebuffering pause
2007-04-15 20:37:13.250 NVP: prebuffering pause
2007-04-15 20:37:13.271 NVP: prebuffering pause
2007-04-15 20:37:26.319 VideoOutputXv Error: ProcessFrameXvMC: Failed to get OSD lock
2007-04-15 20:37:33.997 VideoOutputXv Error: ProcessFrameXvMC: Failed to get OSD lock
2007-04-15 20:37:49.412 TV: Attempting to change from WatchingLiveTV to None
2007-04-15 20:37:49.800 TV: Changing from WatchingLiveTV to None
2007-04-15 20:37:49.842 DPMS Reactivated.
rob@Ubuntu:~$ 
```

---

### Post by electronikjunkie on 2007-04-15
I was just visiting the MythTV-Users list and I saw a post about adjusting the CONFIG_HZ to 300 in the kernel, [link.](http://mythtv.org/pipermail/mythtv-users/2007-April/177061.html)

What kernel version are you using? It might be worth while to compile a new one. Check out this [link.](http://ubuntuforums.org/showthread.php?t=56835)

I also have the VIA chipset, I did have problems in the past with stuttering and prebuffering pauses. I eventually stopped getting them by doing all the things listed above. I also disabled all of my hardware devices not being used, by going into the BIOS and making sure the are disabled. Stuff like the parrell port, firewire, etc... I also turned off "plug and play" in the bios, that way only the hardware enabled will be used by the OS. This frees up IRQs and could possibly help.

I'm sure you've seen this [link](http://mythtv.org/wiki/index.php/XvMC), but check it out if you havn't. It has some good tips on XvMC.

---

### Post by Erlander on 2007-04-16
I'm running Feisty with the latest kernel 2.6.20-15.  The latest kernels have more support built in.  I didn't have to install any drivers for my tuner unlike what happened in Edgy.

I'll have another read of those links later and a further tweak and test of settings later.

Thank you.

Rob

---

### Post by majoridiot on 2007-04-17
you might try adding:

> Option "NVAGP" "1"

to the "device" section of your xorg.conf.  a value of "1" or "2" has been known to help prebuf pauses

also, you might try adding:

> Option "UseEvents" "True"

as well, as it has been known to help.

for interlacing, BOB is really your best bet for HD, more times than not.

---

### Post by Erlander on 2007-04-17
Thanks Major.

I'll give it a try later today.

Up to now I have been reluctant to edit my xorg.conf due to possible problems with Feisty upgrades.  However this late in the piece I'm willing to give it a try as after Thursday I'll probably download the final version and re-install some time just to be sure it is clean after all my tinkering with the Beta.

Thank you.

Rob

ps After my work on PAL DVB-T closed captions I had to turn them off due to increased stuttering.

---

### Post by NT4usB on 2007-04-17
Don't fret, backup!
& email yourself a copy and stash it on another machine.
I spent hours getting my xorg.conf the way I like it, for my mouse, TV, etc.
Now I just let the software do whatever it wants to it, then go in and overwrite it.
Finally learned how to ssh into my mythbox and it's cool!
Tweak xorg, gdm restart, and look over my shoulder to see what the TV did.
If I don't like it, repeat as required. No more editing on the big black screen. ssh runs in a terminal window so it's way easier to read, copy/paste, etc.

ed: I'm trying to sort out stuttering HD playback too. 
Recorded the NASCAR race this weekend and can't get it to playback for a darn. The first two seconds when I start playback sound fine, then everything slows down and stutters.
Thought it was because of trying to play a 21GB file across the network so I moved it over to the master. Same result.
Strange thing is, it played fine on the slave with it's pos ATi 9600 pro. Now that it's on the master, the slave stutters too.

---

### Post by Erlander on 2007-04-17
Will do.

I also hold copies of xorg.conf and smb.conf etc in my home folder and have found a usb stick very good for moving them from one pc to the other.

Good luck with the 9600 Pro.  My 9700 Pro doesn't handle HDTV at all well.  OK on SD though.

Rob

---

### Post by majoridiot on 2007-04-17
> **NT4usB said:**
> Strange thing is, it played fine on the slave with it's pos ATi 9600 pro. Now that it's on the master, the slave stutters too.

the biggest impact is on the frontend, so if you are having rough playback, 9 times out of 10 that's the bottleneck. 
it consumers surprisingly few resources to record and stream HD... playing it back is another matter entirely.

---

### Post by NT4usB on 2007-04-17
I'd a thunk it would play better on the system listed in my sig (master fe/be) than the slave I recorded it on.
It's an old p4 3.0 (533fsb) on a  i850 board with a gig of 1066 rambus rimm and the aforementioned 9600 pro.
Does it matter what I'm feeding the signal to? a 15" lcd on the slave vs. the clunky old 27" crt tv?

Funny story on the xorg.conf in the home folder...
[my recent nvidia driver upgrade]("http://ubuntuforums.org/showpost.php?p=2466923&postcount=881")

I know the box is screwed up but geeze...

---

### Post by majoridiot on 2007-04-18
> **NT4usB said:**
> I'd a thunk it would play better on the system listed in my sig (master fe/be) than the slave I recorded it on.
It's an old p4 3.0 (533fsb) on a  i850 board with a gig of 1066 rambus rimm and the aforementioned 9600 pro.
Does it matter what I'm feeding the signal to? a 15" lcd on the slave vs. the clunky old 27" crt tv?

Funny story on the xorg.conf in the home folder...
[my recent nvidia driver upgrade]("http://ubuntuforums.org/showpost.php?p=2466923&postcount=881")

I know the box is screwed up but geeze...

by the looks of things, not much will run very well on that box until you get it straightened out.  :confused:

---

### Post by NT4usB on 2007-04-18
nah... the box is fine. It's doing what I need it to do (pretty much) for now. 
It was my first attempt at Linux and a pvr, all at the same time, I learned a bunch in the process... kinda' envious though. you kids have been at this less time than I and you're way better at it.
Some day, I'll find reason to break it ant then I'll put it together proper. Or, maybe just build another.
I been having fun replacing windows on the computers I have laying around. Scrounging up old tuner cards to see if I can get anything with them.
Soon as The Shield finishes recording I'm gonna try some of the suggestions above and see if I can get better HD playback.

---

### Post by NT4usB on 2007-04-21
Solved my stuttering by adding XvMCConfig to /etc/X11.

Now to get rid of the little line of ant fights across the top of the display...

---

### Post by majoridiot on 2007-04-21
you can do that by adjusting the overscan settings in frontend setup-->tv playback

---

### Post by NT4usB on 2007-04-21
Thanks for the tip.
I've seen that solution posted before.
I haven't messed with it yet but first thought that comes to mind is can the overscan be set specific to which card made the recording...
Programs recorded on the PVR-150's don't have ant fights. It's only on the recordings from the Aver A180.
I'm not sure I want to trim all the playback just to get rid of a couple pixels width of noise off the top of some programs.
Anyway... I'm going to mess with it and see what happens.
Thanks!

---

### Post by majoridiot on 2007-04-21
afaik, the overscan settings are not bindable to one card only... but chances are that the "races" will go away with
an overscan correction of as little as 1%. (btw, those overscan settings are in %, not pixels, etc.)

i have to correct the overscan for my pvr-150s and a 2% correction to the firewire stream (which doesn't need it)
really is not noticable at all, so i settled for that.

you might see if there is an overscan setting native to the driver for that device... one that you could set on boot
before the backend uses that input?  might be worth looking into if you don't like the overscan correction.

glad you're getting it going tho.  it's always better to be futzing with configs than it is fighting installs! :D

---

### Post by NT4usB on 2007-04-21
> **majoridiot said:**
> ...it's always better to be futzing with configs than it is fighting installs! :D
Yup...
...until I break it and have to start over!#-o

---

