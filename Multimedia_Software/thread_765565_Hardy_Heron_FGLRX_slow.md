---
title: "Hardy Heron FGLRX slow?"
date: 2008-04-24
forum: Multimedia Software
---

### Post by ftaylor on 2008-04-24
I've just installed Hardy Heron 8.04 32 bit.  I have a Dell Inspiron 6400 Laptop with a 256mb ATI Radeon Mobility x1400 graphics card.  

Similarly with Ubuntu 7.10 I installed the fglrx drivers and xserver-xgl.  With Gutsy everything ran smoothly after this.  With Hardy everything is sluggish.  Any suggestions anyone?

Cheers

---

### Post by scradock on 2008-04-24
You should not need xserver-xgl with hardy. The fglrx driver works with the Composite extension, so compiz and so on run without Xgl.

There are still issues, but Xgl is definitely NOT necessary - I found it would not even run on early Hardy installs.

---

### Post by st0nedpenguin on 2008-04-24
I had better performance with the fglrx driver without xserver-xgl when running Compiz.

I'm using the included open source driver out of the box now though, working video is purty.

---

### Post by ftaylor on 2008-04-25
I've realised that now and removed XGL. But it is still slow. I get around 2500 FPS on glxgears, and the performance really drops when I begin to open applications.

Any ideas folks?

---

### Post by Torgas Prim on 2008-04-25
It is the ATI drivers I found. Once I enabled the restricted driver, CPU usage went to 90-100% almost all the time. I disabled and installed the driver through Envy, and CPU dropped to 10-20%, but games like Guild Wars run at 1fps. And Firefox and all screens that you have to scroll through lag and look like they are refreshing at 640x580.

I think I will blow this install until an updated release comes out with the fixes. I hate to say it, but Windows, here I come again :(

---

### Post by firefeather on 2008-04-25
> **scradock said:**
> You should not need xserver-xgl with hardy. The fglrx driver works with the Composite extension, so compiz and so on run without Xgl.

There are still issues, but Xgl is definitely NOT necessary - I found it would not even run on early Hardy installs.

> **Torgas Prim said:**
> It is the ATI drivers I found. Once I enabled the restricted driver, CPU usage went to 90-100% almost all the time. I disabled and installed the driver through Envy, and CPU dropped to 10-20%, but games like Guild Wars run at 1fps. And Firefox and all screens that you have to scroll through lag and look like they are refreshing at 640x580.

I think I will blow this install until an updated release comes out with the fixes. I hate to say it, but Windows, here I come again :(

I found the former-quoted fix worked for me. Scrolling in Firefox is as fast as before for me. I'd say don't be so hasty to go back to Windows; file a bug (don't forget to include your xorg log) and see if someone can help you make your life on Ubuntu a little easier! (I wish I could offer some tips but I'm no linux hacker.)

---

### Post by Torgas Prim on 2008-04-25
How do you disable or remove xserver-xgl ?

---

### Post by hugsrwarmy on 2008-04-25
to remove xserver-xgl, use the terminal, with sudo.

I did this already, but there is no difference, since I have the same problem with my laptop. My ATI is a Xpress 200M, running the proprietary driver (should be fglrx?).  It's very slow with Compiz Fusion, runs even SLOWER without Compiz Fusion enabled (compiz switch), and every action I do except typing or clicking makes the CPU (1.4 Ghz) jump to 100%.  Is there a solution or workaround to this? o_O

It was working fine when Gutsy was installed. Is there a way to revert back without any uninstallation of anything else? =/
I want to use this as a workaround for now, or wait a few weeks.

I'm an amateur on anything in Ubuntu >_<

---

### Post by hugsrwarmy on 2008-04-26
Ok, um, I tried using (and currently using now) EnvyNG to install the ATI drivers. It works, and everything is back to regular speed...however, one extra problem.  There is now a constant flickering for any program that goes into fullscreen, or utilizes the GPU alot (games, wine).  Does anyone know how to fix this? =/

---

### Post by SRTS on 2008-04-26
hi, uninstall compiz completely, and relogin or reboot.
compiz which is installed by default on ubuntu 8, will disable your direct rendering, resulting in slow/sluggy gfx.

---

### Post by k66473 on 2008-04-26
oh, remove xserver-xgl makes my system runs smoother. Thanks all guy

---

### Post by omicrondelta on 2008-04-26
> **Torgas Prim said:**
> 
I think I will blow this install until an updated release comes out with the fixes. I hate to say it, but Windows, here I come again :(


Don't give up yet... It's not Hardy Vista... It's Linux the way it used to be...

---

### Post by hugsrwarmy on 2008-04-26
> **SRTS said:**
> hi, uninstall compiz completely, and relogin or reboot.
compiz which is installed by default on ubuntu 8, will disable your direct rendering, resulting in slow/sluggy gfx.

Ok, I uninstalled compiz completely, and there's no more flickering.

Is there a way to have compiz enabled, with direct rendering? I'd like to keep the aesthetic effects on my laptop.

---

### Post by mjantz on 2008-04-26
I found that if I remove xserver-xgl, the x server won't boot. Any ideas?

---

### Post by techrolla on 2008-04-26
Hey guys, it's possible you are having problems with a runaway process, as I noticed lots of sluggishness with heron (and I have X1600 mobility radeon), but once I removed my .gtkrc-2.0 file it seems a lot faster.  Check this thread: [http://ubuntuforums.org/showthread.php?p=4802226#post4802226](http://ubuntuforums.org/showthread.php?p=4802226#post4802226)

---

### Post by quinnten83 on 2008-04-26
> **techrolla said:**
> Hey guys, it's possible you are having problems with a runaway process, as I noticed lots of sluggishness with heron (and I have X1600 mobility radeon), but once I removed my .gtkrc-2.0 file it seems a lot faster.  Check this thread: [http://ubuntuforums.org/showthread.php?p=4802226#post4802226](http://ubuntuforums.org/showthread.php?p=4802226#post4802226)


Nope, 
I don't have one. Usually I create one myself, but this is a fresh install.
I have the same problems with my compaq evo n610c. It has a Mobility M7 LW (radeon Mobility 7500). I didn't have xserver-xgl installed and it was sluggish. So I installed it, and it is still slugish.
when starting up de effects can not be enabled. And my card is not recognized and never asked for the ati drivers. I installed the drivers in the repos, and compiz-fusion-icon and had to restart the window manager and then the effects would work. Ubuntu itself keeps telling me the effects could not be enabled.
The thing is that the alpha didn't give me any trouble and I could get beryl working in Feisty on the same laptop.

---

### Post by hugsrwarmy on 2008-04-27
> **quinnten83 said:**
> Nope, 
I don't have one. Usually I create one myself, but this is a fresh install.
I have the same problems with my compaq evo n610c. It has a Mobility M7 LW (radeon Mobility 7500). I didn't have xserver-xgl installed and it was sluggish. So I installed it, and it is still slugish.
when starting up de effects can not be enabled. And my card is not recognized and never asked for the ati drivers. I installed the drivers in the repos, and compiz-fusion-icon and had to restart the window manager and then the effects would work. Ubuntu itself keeps telling me the effects could not be enabled.
The thing is that the alpha didn't give me any trouble and I could get beryl working in Feisty on the same laptop.

Go to the Synaptic Package Manager in System -> Administration and search for "compiz" to see if you have it installed. If you don't, check "compiz" and it should install everything needed, except the compiz-settings-manager.

I finally found a way to make my ATI working again for Hardy.  I installed and ran EnvyNG, let it install my ATI drivers and stuff, and uninstalled compiz (completely) and reinstalled it along with compiz-switch to switch back, since direct rendering is disabled when Compiz Fusion is enabled (thanks to SRTS), and causes flickering.  It's running as smooth as it used to be. =)

---

### Post by Miikee on 2008-04-27
I'm also having problems with the new upgrade.  When I first installed it I couldn't even do anything through the desktop.  I was having to ask for help through lynx, the posts are somewhere on this forum.
The xserver-xgl uninstall did help.  It mostly helped with scrolling in firefox, and helped with the choppy frames on the desktop.  My computer fan is also a lot more steady and a little more quite.
I'm still noticing though that it is a good bit slower than 7.10.  Top is showing that firefox is taking and 44% cpu and Xorg 33% (these are averages).  Are these normal numbers or does anyone know how to boost the speed a little more.  Thanks for the xserver-xgl fix it helped a lot, I was really disappointed to see Ubuntu performing like it was.(I just switched over 2 months ago).
Also loading time in firefox is taking a really long time now.

---

### Post by trashjedi on 2008-04-28
> **scradock said:**
> You should not need xserver-xgl with hardy. The fglrx driver works with the Composite extension, so compiz and so on run without Xgl.

There are still issues, but Xgl is definitely NOT necessary - I found it would not even run on early Hardy installs.

This worked for me, thanks. Just went to the synaptics package manager and removed xserver-xgl, rebooted, and it all works wonderfully smooth now! :) 

I have a Dell inspiron 6400, with ati x1400 and was considering going back to gutsy because of the sluggish scrolling, and low performance graphics-wise.
I am now happy as a bunny! :KS

---

### Post by danradigan on 2008-04-29
> **scradock said:**
> You should not need xserver-xgl with hardy. The fglrx driver works with the Composite extension, so compiz and so on run without Xgl.

There are still issues, but Xgl is definitely NOT necessary - I found it would not even run on early Hardy installs.

If I disable the xgl package I get a white screen when starting compiz.  If I enable xgl compix will run, but the system is dog slow.

Thoughts?

Dan

---

### Post by oxinosch on 2008-04-29
Hello everyone,

Had the same problem but it's solved now. I have an inspiron 9400 with mobility radeon 1400. Here are the steps:
1. Uninstall xserv-xgl
2. Uninstal all compiz related packages
3. Install envyNG
4. Restart
5. Install ati driver through envyNG
6. Install compiz
7. System -> Hardware admin -> enable ati driver

...and you are good to go! Hope this helps.

Cheers,
Charalambos Oxinos

---

### Post by AdrianStrays on 2008-04-29
EVERYONE is having problems with this! There are like a million threads about the same issue, and people are costantly flooding the IRC Channel with this problem.....  I'll try all of this, thanks guys.

---

### Post by metalgtr on 2008-04-29
Finally! Thank you oxinosch, this worked for me. I am back in the 3000 FPS range with my ATI Mobility Radeon 9600 and compiz working perfectly.
> oxinosch
1. Uninstall xserv-xgl
2. Uninstal all compiz related packages
3. Install envyNG
4. Restart
5. Install ati driver through envyNG
6. Install compiz
7. System -> Hardware admin -> enable ati driver

---

### Post by CarpKing on 2008-05-01
> **SRTS said:**
> hi, uninstall compiz completely, and relogin or reboot.
compiz which is installed by default on ubuntu 8, will disable your direct rendering, resulting in slow/sluggy gfx.

This is incorrect.  Compiz requires direct rendering in order to function.  You may be thinking of XGL, which provides direct rendering to Compiz at the exclusion of every other program.  Compiz does, however, cause some OpenGL apps to behave in odd ways (flickering, etc) due to their content not being redirected (this is what DRI2 will fix).

---

### Post by whythankyou on 2008-05-02
Yes, this! Worked perfect.  Thanks very much... actually I lied.  One issue.  Video in VLC only works in full screen otherwise I get a black screen.  I'll find a fix though, otherwise performance is just like it was in Gutsy.

> **oxinosch said:**
> Hello everyone,

Had the same problem but it's solved now. I have an inspiron 9400 with mobility radeon 1400. Here are the steps:
1. Uninstall xserv-xgl
2. Uninstal all compiz related packages
3. Install envyNG
4. Restart
5. Install ati driver through envyNG
6. Install compiz
7. System -> Hardware admin -> enable ati driver

...and you are good to go! Hope this helps.

Cheers,
Charalambos Oxinos

---

### Post by jward3010 on 2008-05-13
I'm having different trouble. I NEED xserver-xgl installed to run compiz on my laptop based Mobility Radeon X600. I get "The composite extension is not available" if I try to enable any compiz effects from "Normal" to "Extra" and the problem is with XGL enabled ubuntu runs like a pig. How do I not install XGL and still get compiz like everyone is saying?

---

### Post by JJoel on 2008-05-29
I'm still having problems. I've tried the fix suggested. XGL is not installed. I also tried installing the newest ATI drivers (8.5). No such luck. When large windows are open or watching video (basically all forms of video playback) and compiz is running, they flicker and jump really badly, especially Firefox. Large windows only flicker or jump during the use of Desktop effects. Any suggestions?
I have an ATI x1600.
It all worked incredibly well on gutsy with XGL. What's going on now?
I need compiz to work...

---

### Post by Jouke74 on 2008-05-29
First of all, after you have changed the drivers make sure it is correctly installed and that you are not using the "mesa" driver, which is slow and sluggish. Type glxinfo in the command prompt and it should state what is working (big output). 

Second, if you have an ATI card of any type, check if the FGLRX driver is still working for your specific (older) model. There are also open source Ati drivers available for the older models, which are preferred by Ubuntu.

Third, XGL server use enabled the use of composite if your video card driver did not support it. With the new FGLRX and open source ati drivers this is not required anymore for any ATI video card (under Hardy). However, if you did enable it, it changes a lot of system settings. Some of these settings may remain after the uninstall which cause problems with Compiz, the window manager and the X server.

Fourth, using compiz results in the video overlay flickering with the FGLRX video driver. I tried to solve that by adjusting the settings of several programs, but the best result, keeping Compiz enabled, I got was with the following steps:

sudo --aticonfig ovt off (this turns of the video overlay)

And then in the VLC media player under advanced options at video output set the video output module to X-server.

---

### Post by Ahrk on 2008-06-03
Hi everyone, I had this same issue on my laptop Compaq Presario V2000, with an ATI Radeon Xpress 200M video card (I use the ATI drivers). I uninstalled xserver-xgl and the performance improved a lot, but it was still a bit slow. After that I ran  sudo dpkg-reconfigure -phigh xserver-xorg to reconfigure my xorg.conf file and my system runs smoothly now! I guess there were some wrong settings there from when I was messing with that file trying to get compiz to work back in Gutsy. By the way, I don't have compiz installed anymore, my computer just can't take it:( 

Thanks for the help!:guitar:

---

### Post by canakas on 2008-06-20
Caramba, it worked for me too. Connect3d Radeon 9600 128mb pci, on a shuttle fn41, amd athlon xp 2800

And just to throw in some hardy heron ubuntu sunshine, my s-video out worked out of the box on a PAL-H tv, and still no problems... no xorg.conf mysteries no xrandr...

Thanks so much community!

-canakas

> 
Originally Posted by oxinosch View Post
Hello everyone,

Had the same problem but it's solved now. I have an inspiron 9400 with mobility radeon 1400. Here are the steps:
1. Uninstall xserv-xgl
2. Uninstal all compiz related packages
3. Install envyNG
4. Restart
5. Install ati driver through envyNG
6. Install compiz
7. System -> Hardware admin -> enable ati driver

...and you are good to go! Hope this helps.

Cheers,
Charalambos Oxinos

---

### Post by relugrigorescu on 2008-12-14
After installing fglrx ubuntu hardy works slow.
uninstall fglrx works for me

---

