---
title: "gutsy + nvidia-glx-new = broken 3D accel"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by remi_2 on 2007-11-07
Hi guys,

after upgrading to gutsy the 3D accel on my GF7100 is broken,

First I've used synaptic to upgrade to nvidia-glx-new, 3D accel ceased working.
Then, I downgraded to nvidia-glx, resolution went down to 640*480
Then, still using synaptic, I downgraded to nvidia-glx-legacy, and got a X failure, so right now I'm using the nv driver.

The whole desktop is sluggish and I've got CPU spikes each time I move a window, or got GUI stalls when some number crunching process is running on the CPU !

My previous feisty install used to work with nvidia-glx 1:1.0.9631+2.6.20.5-16.29

is there a way to install that feisty driver in gutsy?

today gutsy only has newer or really older drivers :

nvidia-glx-new 100.14.19+2.6.22.4-14.9
nvidia-glx 1:1.0.9639+2.6.22.4-14.9
nvidia-glx 1.0.7185+2.6.22.4-14.9

another one bites the dust! :guitar:
thanks

---

### Post by eye208 on 2007-11-07
> **remi_2 said:**
> First I've used synaptic to upgrade to nvidia-glx-new, 3D accel ceased working.
Why didn't you use Restricted Drivers Manager?

---

### Post by remi_2 on 2007-11-07
Hi again,

I did not use the restricted driver manager because I thought it was just a front end for apt-get, and I needed to install other packages at the same time.


Now I've made some progress using the Envy installer.

Envy removed the nvidia-glx-new, nvidia-glx and nvidia-glx-legacy from the system and downloaded, installed and configured the latest nvidia binary driver from the web.

Now it seems  that 3D acccel is working (glxgears reports 2000 fps).

The problem I have now is when trying to activate the desktop effects via the System->Prefs->Appearance applet, I get a popup telling me that I need to install the restricted drivers to activate the effects :confused:.

I finally though it could make sense  since none of the ubuntu's official nvidia-glx* packages can be found in the system anymore, and it could be that  the bleeding edge nvidia driver might not be recognized by that desktop effects applet.

Any how, I installed the compiz settings manager I can see all plugins listed and configure them, but I cannot activate compizfusion via this applet either! 

How do I proceed next? I really want the "expose" and  "drag windows past the border" functionality back !

cheers

---

### Post by remi_2 on 2007-11-08
Got some more progress  and could launch compiz

using ALT+F2, typing "compiz --replace" launched compiz, but  all window borders and title bars disappeared.

anyone experiencing the same disappear problems?

EDIT: 
Its really hard to believe Canonical did not stumble upon this problems during the beta/RC cycles !

---

### Post by mariourk on 2007-11-08
I'm having the same problem with my *7600GS Silent*
I noticed this in the logs though:
```

nvidia: module license 'NVIDIA' taints kernel.

```
Back in my gentoo days I simply switched to another kernel, that usually did the trick. I have no idea how to fix this with Ubuntu :/

---

### Post by remi_2 on 2007-11-08
I think this message is a "political statement" or "ethical warning", not a technical warning.

---

### Post by Rumo on 2007-11-08
Also similar problem with GF 7300LE.

I tried almost anything already - Installation with Restricted Driver Management, envy, editing xorg.conf, using VGA instead of DVI...

Does ANYONE have any idea what is wrong? I also have an Intel i855gm chipset on my board but that doesn't work either (i915 on my laptop works flawlessly).

This problem is really annoying. I never had any problems with nvidia-3D acceleration before (probably compiz/aiglx problems?).

---

### Post by mariourk on 2007-11-09
It turned out my new NV7600GS has an external power connector. I hadn't noticed it when it janked it in my pc. After putting a powercable into the socked, it went fine.

I'm still unable to install the driver with the restricted driver manager. But with Envy I was able to install the driver properly.

Another thing was, once I had it working, I got a black screen. I turned out that the driver picked my beamer (turned off) as the primary screen. I used nvidia-settings to configure my beamer and my screen as clones. After that it all worked fine. I have my monitor on DVI and my beamer on VGA. So, if you finally get something working and and up with a black screen, try the other connector on your videocard. Who knows.

---

### Post by wolfen69 on 2007-11-09
it seems many other people are having the same issues, as evidenced by the number of bugs filed on launchpad. i imagine there is a fix in the works. this video bug is the reason i keep feisty around.

---

### Post by remi_2 on 2007-11-27
I eventually Got it sorted :

installed ENVy, did automatic installation of latest nvidia driver through ENVY
completely removed compiz and all its dependencies (sudo apt-get  autoremove)
reboot
installed restricted driver though the restricted drivers management tool (it looks like it re-installed the nvidia-glx-new.deb  that was created by envy)
reboot
installed through synaptic compiz and  compiz config manager
reboot
now I have the decoration plugin for compiz which was missing from the fresh gutsy install

system->appearance->extra

and baoum, I have compiz running with metacity decorations.

The only thing that still sucks is that the system beep got activated somehow, and I cannot activate the window flashing option meant to replace the system beep from the system->sounds menu.
 I had to rmmod pcspkr to get rid of the beeps.

---

