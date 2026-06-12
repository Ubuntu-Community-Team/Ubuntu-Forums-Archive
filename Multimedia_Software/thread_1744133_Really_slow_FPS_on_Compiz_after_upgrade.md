---
title: "Really slow FPS on Compiz after upgrade"
date: 2011-04-30
forum: Multimedia Software
---

### Post by Cetra on 2011-04-30
Hey guys,

Just upgraded to 11.04 and compiz runs like absolute dogshit.

I'm using ATI Proprietary drivers which worked amazingly before the upgrade.

Any suggestions?

---

### Post by sikander3786 on 2011-04-30
This should help.

[http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

---

### Post by Cetra on 2011-04-30
Thanks but that hasn't resolved it.

It seems to be when I moved windows around that the FPS drops.  I have a feeling Unity is playing havoc

---

### Post by sikander3786 on 2011-04-30
Which graphics card model is there and which version of proprietary drivers are you using?

Also, please post the output of this command.

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by Cetra on 2011-05-01
ATI Radeon HD 5870 x 2.  Like I said, it worked fine before distro upgrade.

Output of the command:

```
cetra@cetra-desktop:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5800 Series
OpenGL version string:  4.1.10665 Compatibility Profile Context

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

---

### Post by Cetra on 2011-05-02
Bumperage, it's really annoying!

---

### Post by sikander3786 on 2011-05-03
In another Thread which I am unable to find right now, the OP solved some kind of same issue by booting in to Safe Graphics Mode, removed the proprietary drivers, rebooted, again booted in to Safe Graphics Mode, installed the recommended drivers. Rebooted and had improvements in FPS.

Or try downloading the latest drivers from ATI website and install those.

---

### Post by Cetra on 2011-05-03
Yeah I've tried all of that.  I've tried both the distro and ati's website version of the drivers.

It doesn't make sense that it's the drivers since I only see the slowness when the window is being moved around on the screen (with alt+left click, or grabbing it by the titlebar)

---

### Post by Cetra on 2011-06-02
Bumping this.  It's only when the windows are moved around.  Minimising, Maximising etc.. has an initial pause then seems to be fine.

Any clues?  Anyone else with this same problem?

---

### Post by Cetra on 2011-06-15
Bump!

---

### Post by mauf on 2011-06-17
Hello fellow ubuntu users,

I have the same problems as you mentioned above low fps and some nasty glitches while moving windows. 
I'm using the ATI Radeon HD 5870 graphics adapter. I tried the proprietary driver delivered with ubuntu,
also the latest driver from ATI it self and the 3d Gallium with cypress support.
Nevertheless I was not able to get satisfactory results while testing them
with glxgears and fgl-glxgears, the fps was horrible, the average value was about 60 fps.

My system is a Dell Studio XPS 7100
AMD Phenom(tm) II X6 1055T Processor
8GB DDR 3 RAM
Radeon HD 5870

At this point I have no clue what might cause these problem because
the driver installations itself went very well.

I hope somebody is able to verify my results with the same system specifications or can give helpful advices to solve this damn problem.

Sincerely yours, mauf

---

### Post by Duncan Williams on 2011-06-17
I have had this problem on and off with nvidia and ati cards.
I have come to the conclusion that it is the windows manager and have resolved it on my system here.

[http://peppermintos.net/viewtopic.php?f=10&t=3733](http://peppermintos.net/viewtopic.php?f=10&t=3733)

Mind you I had no compiz/unity to start with.

---

### Post by mauf on 2011-06-17
After a few test this morning with the latest ATI Driver and only bad results I tried to install the driver not from gnome environment with compiz and unitiy active, so I switched to generic gnome mode without any fancy stuff active (the boring one ;) ).

After installing the driver the results where amazing the tests with glxgears give me an average value of 9.5k - 10k fps, compared to the results yesterday (average value of 60.0 fps in glxgears) it's a tremendous improvement.

These results let me think about the installation process it self, maybe I've made some mistakes, so I switched back to the fancy gnome mode (compiz & unity active) and test it with glxgears again. In the moment I hit return the terminal window freezed and the gears began to rotate everything was very slow even the fps was at 800.0 - 900.0, this is 10 times lower than the results in generic gnome mode with the SAME driver installation.

So, is it possible that the real problem in this case is not the driver, but rather compiz it self or maybe the unity stuff?

Now I'll give gnome 3 a try, maybe these problems only affect gnome 2 with unity.

I'll be back soon, hopefully with good news.

********* Update Fr 17. Jun 17:20:18 CEST 2011 *********

The try with gnome 3 went terrible wrong so I decided to do a fresh installation and followed the steps I've mentioned above.
After the installation process was finished I started Ubuntu Classic Mode without effects and installed the 3d acceleration with the proprietary ati driver shipped with Ubuntu 11.04. Test with glxgears give me ~10k fps.
Everything works fine.
The next step was switching to gnome classic (in this mode compiz is active). I installed the compiz-config-settings-manager and turned vsync off also
enabled best quality settings booth in the opengl module of ccsm.
Next step was starting a terminal and give glxgears a try. First everything freezes and then the terminal starts to print the fps of glx gears ~1500fps -2000fps. I minimized the glxgears window, and began to wonder - the fps rate increase to ~10k fps - the same rate I had in gnome mode classic without effects - after reopening the glxgears window the frame rate dropped to 1.5k.

I can't imagine that compiz uses this much resources of  the graphics adapter that the fps while rendering glxgears is ~8 times below the rate while not rendering another opengl application.

So I guess the problem is indeed compiz.

I hope somebody has a hint what cause this problem, maybe it's only a little tweak or something which will solve it.

---

### Post by Duncan Williams on 2011-06-17
As per my last post.
I have resolved the issue on my system after a couple of months of having response times affected by video, audio, browsing, etc.
The process of setting up compiz, xcompmgr 
and the the other steps mentioned 
as well as adding and using `Compiz Fuzion Icon'

Seems to stabilize the compiz installation.

somehow?

but I need to load and run `Compiz Fuzion Icon'
and select `reload window manager'
each time I boot the computer.

I am also using Avant rather than unity.

I ended up with 3 windows managers by default
Metacity
Dropbox
Compiz
There is a possibility that they were clashing.
Compiz Fuzion Icon displays the managers and allows you to choose which one.

---

### Post by mauf on 2011-06-19
After reading some bug reports which poited to similar problems while moving windows, I've tested this workaround

> CCMS -> Composite -> Disable Auto Refresh Rate -> turn refresh rate to 120 -> System Restart .

Window movement is very smooth no lags anymore but glxgears give me a fps value of 60 but this can also be a bug :( .

I can live with the workaround but I hope in the next release of Ubuntu this fall these kind of problem are gone.

-------
mauf
-------

---

### Post by handy on 2011-06-19
I don't know if this is any help to you guys:

[http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html](http://ubuntu4beginners.blogspot.com/2011/04/unity-choppy-with-ati-graphics-card-and.html)

---

### Post by mauf on 2011-06-20
Thanks for your help but this was my first move getting rid of 

> **Sync to VBlank**

but unfortunaely this has not changed anything for me.
Also my previous posted workaround does not work properly after restarting my machine, bad window movement was back :(.


So after more digging in some german ubuntu related forums, someone posted this [_[COLOR="Blue"]link[/COLOR]_]("http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html").

After following the instructions to downgrade compiz, everything works like a charm. But be aware of losing your actual compiz configuration, Unity and also the new windows 7 like snap effect.

Best regards
mauf

---

### Post by Yellow Pasque on 2011-06-20
Fglrx just doesn't play well with Unity. Also, if you were getting 60fps, some kind of vsync setting was on, whether it was from the driver, Unity, or Compiz. In the Catalyst Control Center, the setting is under Display Options -> Tear Free (this will turn vsync off, but an app (like Unity or Compiz) can still enable it. In the Unity settings, the vsync option is in the 'quality' section. In the ccsm, the setting is in genreal Options -> 'Display'.

---

