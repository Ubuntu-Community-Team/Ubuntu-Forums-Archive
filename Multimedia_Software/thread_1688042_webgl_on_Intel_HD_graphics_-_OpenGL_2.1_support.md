---
title: "webgl on Intel HD graphics - OpenGL 2.1 support?"
date: 2011-02-14
forum: Multimedia Software
---

### Post by Ryan S Kingsbury on 2011-02-14
Hi everyone,
    I've been playing with the Firefox 4.0 and Chromium betas to try and get webgl graphics working properly.  I run an Intel i5 Clarkdale processor with integrated "HD" graphics. 

I know, I know, generally speaking it seems that Intel graphics + Linux + webgl = fail

But I want to understand why.  I've set up my browsers according to an older tutorial posted her:
[http://learningwebgl.com/blog/?p=11](http://learningwebgl.com/blog/?p=11).  I'm able to use webgl with software rendering (via libosmesa as described in the article), but hardware accelerated webgl definitely does not work.  As such, I can use webgl sites but performance is SLOW.

The article states that the main reason Intel graphics tends not to work with webgl is lack of support for OpenGL 2.0.  I'm running the latest Intel drivers and the 2.6.37 kernel, and if I run

```
glxinfo | grep OpenGL
```

I get

```
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Desktop GEM 20100330 DEVELOPMENT
OpenGL version string: 2.1 Mesa 7.11-devel
OpenGL shading language version string: 1.20
OpenGL extensions:
```

Which indicates to me that my drivers support OpenGL 2.1.  So what's the problem?  Clarkdale graphics have been supported in Linux for a while now, and OpenGL on its own works fine.

I also see the follow lines in the full glxinfo output:

```
server glx vendor string: SGI
server glx version string: 1.4
```

```
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
```

```
GLX version: 1.4
```

Do these indicate that something on my system is still running OpenGL 1.4?

I'd really appreciate any help in understanding what's going on.  I understand Intel graphics are generally problematic but it really seems like my drivers support the required standards.  Thanks!

---

### Post by Ryan S Kingsbury on 2011-02-18
I made a bit of progress.  I noticed that during boot I was getting the following in my dmesg output:

 ```
[drm] MTRR allocation failed.  Graphics performance may suffer.
```and

```
mtrr: type mismatch for e0000000,10000000 old: write-back new: write-combining
```Adding the following to my /etc/default/grub file resolved the problem. 

in /etc/default/grub, add:
```
GRUB_CMDLINE_LINUX="enable_mtrr_cleanup mtrr_spare_reg_nr=1"
```then run
```
sudo update-grub
```This tweak appears to have boosted webgl performance in Chromium.  It's still poor  though (about 6 fps at Google's Body Browser) and didn't seem to help  Firefox 4.0 at all.  It's not clear to me whether Chromium is using  hardware or software rendering, but I'm pretty sure it's software.

I should have mentioned I'm running Ubuntu 10.10 x64 with 4GB of ram on an Intel i5-650, Gigabyte H55M-USB3 motherboard.

---

### Post by bwiklak on 2011-02-21
Hi,

I have the same problem, core i3-370.

The body demo works, but the whole model is black.
To make things worse, I tried to work with orx game engine ant it seems to work bad probably because of poor OpenGL support in intel driver.

I'm looking forward for any news, please let us know if you find something.

---

### Post by bwiklak on 2011-02-22
Ok, I solved it!

The google body browser works great, blazing fast and without any errors.

There is very interesting post at xbmc forum: [ [http://forum.xbmc.org/showthread.php?t=86581]("http://forum.xbmc.org/showthread.php?t=86581") ]
The first part of it is a tutorial how to easily and quickly install the newest intel drivers in Ubuntu.

[cite: alanwww1 @ [http://forum.xbmc.org/showthread.php?t=86581]("http://forum.xbmc.org/showthread.php?t=86581") ]

I created a guide for people having Intel Core i3 integrated motherboard, with onboard gpu.

[...]

We will need an Ubuntu Maverick install (mini or full)

If you have a minimal install, start with installing basic packages and add you to the video group.( this is actually important, because without this xserver can not access your gpu directly and falls back to software rasterizer) 


```
sudo apt-get update
sudo apt-get install udisks upower xorg alsa-utils mesa-utils
sudo adduser YourUserName video
sudo adduser YourUserName audio
sudo reboot
```
Than let's start the real work.
We will update the intel drivers ([http://intellinuxgraphics.org/index.html]("http://intellinuxgraphics.org/index.html")) to the very bleeding edge fresh git version as we need these for this hw at the moment. Later all these drivers get into the Linux kernel so we won't need this step in the near future. Luckily we don't have to compile anything. Because the ubuntu X-team has a great ppa with the newest packages. [https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")(Please read the disclaimer here!)

```
sudo apt-get update
sudo apt-get install python-software-properties
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade 
sudo apt-get install libva1 vainfo i965-va-driver libva-glx1 libva-dev
sudo reboot
```

Good luck!
Bartek

---

### Post by Ryan S Kingsbury on 2011-02-28
AWESOME!  Thank you!

adding my user to the audio and video groups was key
I think upgrading the libva-related packages helped, too.  I had already upgraded the driver packages but didn't realize libva would play such a key role.

I still don't have this working under Firefox 4.0, but it's terrific on Chromium.

---

### Post by lsaplai on 2011-03-06
Hi guys,

This is very interesting and would like to ask one of you if you could try one of Opera latest build with hardware acceleration (my own hardware couldn't handle it for now and I'm not as proficient as you to test this)

The test built can be found here: [http://labs.opera.com/news/2011/02/28/](http://labs.opera.com/news/2011/02/28/)

Many thanks for taking the time to report back to us.

---

### Post by Ryan S Kingsbury on 2011-03-07
> **lsaplai said:**
> Hi guys,

This is very interesting and would like to ask one of you if you could try one of Opera latest build with hardware acceleration (my own hardware couldn't handle it for now and I'm not as proficient as you to test this)

The test built can be found here: [http://labs.opera.com/news/2011/02/28/](http://labs.opera.com/news/2011/02/28/)

Many thanks for taking the time to report back to us.

I'd be happy to test, but it looks like the test builds are only available for Windows, which I don't have  installed on my machine.

You might have better luck at a forum that's not specific to Linux :-)

---

### Post by lsaplai on 2011-03-07
:P Silly me! Of course. I'm so used of having the latest version of Opera running on my Linux machines that I forgot this was a Windows only version. For now...

I guess I'll come back with the same question once the Linux version is out (I'm not planning on a hardware upgrade anytime soon so my technical limitations will remain the same)

Thank you for taking the time to reply.

Cheers!

---

### Post by Ryan S Kingsbury on 2011-03-10
For those still trying to get this working with Firefox 4.0 - the problem appears to be that most X11 graphics drivers are "blacklisted" by Firefox due to crash problems.  BUT, you can force-enable your driver if it is on the blacklist.

The following page from the Mozilla Wiki has some good information (excerpt below)
[https://wiki.mozilla.org/Blocklisting/Blocked_Graphics_Drivers](https://wiki.mozilla.org/Blocklisting/Blocked_Graphics_Drivers)

> Regarding OpenGL drivers, only the NVIDIA proprietary driver is  currently whitelisted because of many crashes in other drivers (see [bug 616416]("https://bugzilla.mozilla.org/show_bug.cgi?id=616416"), [bug 622294]("https://bugzilla.mozilla.org/show_bug.cgi?id=622294"), [bug 621699]("https://bugzilla.mozilla.org/show_bug.cgi?id=621699"), [bug 589546]("https://bugzilla.mozilla.org/show_bug.cgi?id=589546")), and difficulty determining driver info without risking crashing ([see this conversation]("http://lists.freedesktop.org/archives/mesa-dev/2011-February/005267.html")). Define the **MOZ_GLX_IGNORE_BLACKLIST** environment variable to bypass that. 
WebGL is enabled by default, so it works if your driver is whitelisted or if you bypass the blocking (see above). 


I haven't gotten to test force-enabling my Intel driver yet but will post results when I do.

---

### Post by Ryan S Kingsbury on 2011-03-10
UPDATE

Webgl is working on Firefox 4.0! You must start firefox using this command in order to circumvent the Intel driver blacklist:


```
MOZ_GLX_IGNORE_BLACKLIST=1 firefox-4.0
```Performance will be poor unless you go into about:config from firefox and set the following options:

[B]webgl.force-enabled=true
[/B]**layers.acceleration.force-enabled=true**

With these settings I got similar performance in Firefox 4 as on Chromium.  5 fps with 50 fish on the [Webgl Aquarium]("http://webglsamples.googlecode.com/hg/aquarium/aquarium.html") (with a bunch of other tabs open) compared to 6 fps in Chromium with no other tabs. The little control panel doesn't render properly on FF though.

So far no stability problems or crashes. I've tried a variety of Webgl experiments. I wish performance were better, but maybe future driver releases will helps things in that department.

---

### Post by Ryan S Kingsbury on 2011-04-01
One last update.  If you want to fix it so that Firefox ALWAYS starts with webgl enabled (i.e. without blacklisting the Intel driver), edit the top of your /usr/lib/firefox-4.0/firefox.sh script so that it looks like the following (add the bold bits):

```
PROFILE=$HOME/.mozilla/firefox
LIBDIR=/usr/lib/firefox-4.0
NAME=`which $0`
MOZ_APP_LAUNCHER=$NAME
SERIES=4.0
DISPLAYNAME="Firefox"
EXE=firefox-bin
APPNAME=firefox
**MOZ_GLX_IGNORE_BLACKLIST=1**

export MOZ_APP_LAUNCHER
**export MOZ_GLX_IGNORE_BLACKLIST**
```

---

### Post by aldeby on 2011-10-02
Forcing hardware acceleration on Intel HD graphics (included Tungsten Graphics, Inc -- Mesa DRI Intel(R) Sandybridge Mobile) with 2.1 Mesa 7.11 or earlier results in *massive* Firefox memory leaks. In a few minutes it will eat more than 2 Gb or RAM, in 30 minutes over 4 Gb. This applies to Firefox 5, 6 and 7.

---

### Post by antistress on 2011-10-24
Are these leaks confirmed for Firefox/WebGL on Sndy Bridge ?

---

