---
title: "(OpenGL?) Unigine Benchmark (...and Nvidia Optimus...driver issues and OpenGL...)"
date: 2013-04-12
forum: Multimedia Software
---

### Post by [::AP::] on 2013-04-12
Hello,

**[Background]**
I have a Lenovo Y470 laptop, with an Intel HD 3000 and an Nvidia 550m discrete GPU, activated normally through Nvidia Optimus in Windows. 
My GPU isn't critical to the main topic of this thread, but it is involved in my end goal.

I would like to benchmark the graphics performance of my laptop without the graphics card enabled, using the free/demo Unigine benchmarking tools. Later on, if/when I get Bumblebee (Primus?) working, I would like to compare results, so that I am sure Optimus is working. In the end, I just want to play Minecraft on Xubuntu with a decent FPS :P

I'm aware of glxgears and glxspheres, however, from my understanding, these are not true graphical benchmarks. Besides, it looks like they are VSync'd, which doesn't show me much. 
I cannot seem to get Unigine Heaven/Valley to work. I've done my best diagnostic, but I'm not sure where to go from there.  Also, alternative video benchmarking tool suggestions are welcome! (phoronix?)

**[Problem]**
I am running Xubuntu 12.10. As is with any *buntu install on an Nvidia system, the Nouveau drivers are installed. They work fine for day to day activities, but from my understanding, they are limited in the video performance department. 
To install Nvidia drivers, I ran the installer script from UbuntuExtreme ([http://ubuntuxtreme.com/howto/how-to-install-or-upgrade-nvidia-video-drivers/)]("http://ubuntuxtreme.com/howto/how-to-install-or-upgrade-nvidia-video-drivers/"). I looked at the script before running it - it seemed to take care of everything, saving me from doing manual work. 
I kick myself for not copying the output in Terminal, but, I did end up taking two screenshots.

[I]Screenshots (also included as attachments)
[/I][http://s24.postimg.org/65a5tsc05/Screenshot_04122013_02_06_26_PM_driver_remov.png](http://s24.postimg.org/65a5tsc05/Screenshot_04122013_02_06_26_PM_driver_remov.png)
[http://s24.postimg.org/3mogt3q9x/Screenshot_04122013_02_10_15_PM.png](http://s24.postimg.org/3mogt3q9x/Screenshot_04122013_02_10_15_PM.png)

I'm not sure if the drivers installed were the latest and greatest - the 304.88 was installed, and I believe that a 310.xx and a 313.xx beta (with the groundwork of Optimus built in!) are floating around.

Prior to that, I had downloaded Unigine Valley 1.0, and I could not get it to run (I assume all you must do is extract the .run, open the script in the folder?) I have played with the settings, but every time I click "Run", the button is pressed, it seems to load, and then returns to normal, like nothing ever happened. 
Terminal output was not insightful before I installed the Nvidia graphics, I assume it was just saying that I needed the propietary drivers? 

[I]Unigine Valley 1.0 terminal output (after Nvidia script)
[/I]```
Loading "/home/aparsons/Desktop/Unigine_Valley-1.0/bin/../data/valley_1.0.cfg"...
Loading "libGPUMonitor_x64.so"...
Loading "libGL.so.1"...
Loading "libopenal.so.1"...
Set 1280x720 windowed video mode
Xlib:  extension "GLX" missing on display ":0.0".
GLAppWindow::create_visual(): glXChooseFBConfig(): failed
Engine::video_restart(): can't set 1280x720 windowed video mode

Can't set video mode
GLAppWindow::create_visual(): glXChooseFBConfig(): failed
Engine::video_restart(): can't set 1280x720 windowed video mode

Set 1280x720 windowed video mode
Xlib:  extension "GLX" missing on display ":0.0".
GLAppWindow::create_visual(): glXChooseFBConfig(): failed

Unigine fatal error
GLAppWindow::create_visual(): glXChooseFBConfig(): failed
Engine::video_restart(): can't set 1280x720 windowed video mode
Shutdown
AL lib: ReleaseALC: 1 device not closed


```

I just downloaded/ran Unigine Heaven 4.0, which also did not work. The terminal output seems to be the same
*Lots of information is given....but I still can't interpret it. :P

*Unigine Heaven 4.0 output*
```
Loading "/home/aparsons/Desktop/Unigine_Heaven-4.0/bin/../data/heaven_4.0.cfg"...
Loading "libGPUMonitor_x64.so"...
Loading "libGL.so.1"...
Loading "libopenal.so.1"...
Set 1280x720 windowed video mode
Xlib:  extension "GLX" missing on display ":0.0".
GLAppWindow::create_visual(): glXChooseFBConfig(): failed
Engine::video_restart(): can't set 1280x720 windowed video mode

Can't set video mode
GLAppWindow::create_visual(): glXChooseFBConfig(): failed
Engine::video_restart(): can't set 1280x720 windowed video mode

Set 1280x720 windowed video mode
Xlib:  extension "GLX" missing on display ":0.0".
GLAppWindow::create_visual(): glXChooseFBConfig(): failed

Unigine fatal error
GLAppWindow::create_visual(): glXChooseFBConfig(): failed
Engine::video_restart(): can't set 1280x720 windowed video mode
Shutdown
AL lib: ReleaseALC: 1 device not closed

```

To avoid problems, I ran both Unigine benchmarks in the "Basic" mode. 

The question is, where to now? It bothers me that I cannot get this to work, although it is not necessarily needed for me to get to my end goal (minecraft!)

I am thinking that I because I do not have Bumblebee/Primus setup yet, Unigine tries to access my GPU but runs into issues and *aklnssdknlasdknlakaslknanllkad* happens.
But, I would think that it should default down to the Intel 3000? 

**Note:** I sorta-kinda started to set up Bumblebee/Primus before Unigine and installing the real Nvidia drivers. Not sure if this would be causation for any issues. 
On a previous Bumblebee install, I did end up getting optirun to work, but I ended up reinstaling that Xubuntu install.
On my current install, before doing everything else...

I stumbled upon Primus here: [http://www.webupd8.org/2012/11/primus-better-performance-and-less.html](http://www.webupd8.org/2012/11/primus-better-performance-and-less.html) and followed the 'guide' (just PPA downloads, really)
And I have a special case, some bug with the Y470/570s. So, I used the technique described in post #12 (2nd one of page two) here: [http://ubuntuforums.org/showthread.php?t=2036010&page=2](http://ubuntuforums.org/showthread.php?t=2036010&page=2) 

[B]In summary:
Unigine Benchmarking doesn't work
I want to benchmark my Intel 3000, then my Nvidia 550m
Things aren't working, what do?[/B]

Thanks, 

Andrew

---

### Post by [::AP::] on 2013-04-13
**Update:**

Hmmmm.....I might end up doing a fresh install, just to start...fresh.

I think I have a problem with OpenGL. Which explains why glxgears and glxspheres don't work, and might be related to all graphics stuff?
Day to day activites work fine, it is just using OpenGL. I think. I'm certainly no expert, nor do I feel like I understand what is going on :P

Anyways, here is why I think OpenGL is broken. I think that is the root of my problem. 

When I run [I]glxinfo

[/I]```
$ glxinfo
```

This results...

```

name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

Pretty much the same happens with *glxgears* or *glxspheres. *I assume all *glx** commands will result in similar outputs.

```
$ glxgears
```

Results with...

```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```

Also, the ```
Xlib:  extension "GLX" missing on display ":0.0".
```
is seen in the Unigine errors. So that looks like it is the issue. **[EDIT: Driver stuff, see next post]**

So...meh. I'm not sure how to proceed at this point, other than going through my favorite fixing procedure....reinstall! :( 
I'll poke around. Google, here I come.

---

### Post by [::AP::] on 2013-04-13
Things aren't looking good.

Here is why (not in any order, and only skimmed):

[http://stackoverflow.com/questions/8545291/opengl-glx-extension-not-supported](http://stackoverflow.com/questions/8545291/opengl-glx-extension-not-supported)
[http://theiszm.wordpress.com/2010/06/27/glx-missing-on-display/](http://theiszm.wordpress.com/2010/06/27/glx-missing-on-display/)
[http://ubuntuforums.org/showthread.php?t=1746571](http://ubuntuforums.org/showthread.php?t=1746571)
[http://askubuntu.com/questions/67567/extension-glx-missing-on-display](http://askubuntu.com/questions/67567/extension-glx-missing-on-display)
[http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work](http://askubuntu.com/questions/36930/how-well-do-laptops-with-nvidia-optimus-work)
[http://askubuntu.com/questions/222846/xlib-extension-glx-missing-on-display-0-0-error-couldnt-find-rgb-glx-vi](http://askubuntu.com/questions/222846/xlib-extension-glx-missing-on-display-0-0-error-couldnt-find-rgb-glx-vi)
[http://www.kubuntuforums.net/showthread.php?48254-Solved-Xlib-extension-quot-GLX-quot-missing-on-display-quot-0-0-quot](http://www.kubuntuforums.net/showthread.php?48254-Solved-Xlib-extension-quot-GLX-quot-missing-on-display-quot-0-0-quot)
[http://ubuntuforums.org/showthread.php?t=1930433](http://ubuntuforums.org/showthread.php?t=1930433)
[http://www.linuxquestions.org/questions/linux-software-2/xlib-extension-glx-missing-on-display-0-0-a-930969/](http://www.linuxquestions.org/questions/linux-software-2/xlib-extension-glx-missing-on-display-0-0-a-930969/)
[http://forums.debian.net/viewtopic.php?f=6&t=73028](http://forums.debian.net/viewtopic.php?f=6&t=73028)

 I could probably fix it but that might turn into a headache, and I'd rather start "fresh" than feel like things have been patched back together.

I sorta-kinda understand the problem, it is caused by the Nvidia driver. Basically my installs of drivers have messed things up.

From my understanding so far, **it looks like I will be reinstalling Xubuntu**, and I will be needing some **guidance with properly setting up Bumblebee** (because of issues on the Y470/570, as seen in post 2 of [http://ubuntuforums.org/showthread.php?t=2036010&page=2](http://ubuntuforums.org/showthread.php?t=2036010&page=2)). But, I'll save that for another thread, unless anyone wants to pipe in here. (Or I'll just wait until a more up to date kernel fro *buntu comes out (3.9?), and go for a standard Bumblebee install, on a fresh system. I'm currently on 3.5, See here: [https://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo#lenovo-ideapad-y470y570-and-toshiba-satellite-p870](https://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo#lenovo-ideapad-y470y570-and-toshiba-satellite-p870))

**EDIT: 13.04 will have a kernel that works nicely with Bumblebee. I can wait a few weeks in order to have a cleaner solution. **

---

