---
title: "Messed up installation ... need to re-install some drivers: please help"
date: 2009-02-08
forum: Multimedia Software
---

### Post by yankeeDDL on 2009-02-08
Hello, 
sometimes I think I should just keep my hands in my pockets ...
I think I totally messed up my installation today.
My problem was that with ATI drivers the video playback was very slow and the window with the playback was full of artifacts.
I removed ATI drivers followings ATI installation guide. Then I tried to install the MESA drivers (thinking that they were generic enough). I don't need hard-core 3D acceleration.

But anyway, that's a problem of the past ... because the MESA drivers did not work. I uninstalled them and ... boom! 
Ubuntu would startup in the non-GUI mode. Fortunately I remember startx command which did the trick. 
Trying to re-enable loading the GUI at every startup, I did a sudo apt-get gnome-gdm.
This fixed the startup (however I still see an error that fglrx could not be loaded).

However now:
- I cannot enable any desktop effect. In the sense that the entire panel is grayed out (I cannot even select "no effect").
- I cannot capture my audio via my webcam anymore. 
- I don't see the Screensaver item in my menu anymore
- The panel item to restart/shutdown/hibernate my computer has disappeared (I have added the shutdown button, but I liked the menu)
- VLC (videolan) disappeared. I re-installed via add/remove programs.

Note: if I run alsamixer I only see Card: Pulseaudio, Chip: Pulseaudio. However I can listen to video and MP3 correctly.

Please help: I think I need to reinstall a bunch of drivers/libraries ...
How do I clean up this mess I made without re-installing?


My hardware:
MB: Asus A8N-VM   (onboard audio controller)
Video: ATI HD2600 XT (I have disabled the onboard Nvidia graphic card via BIOS)
Webcam: Logitech Quickcam connect STX
CPU: Athlon 64 3200+
RAM: 4GB
I have Ubuntu 8.10 64bit installed

---

### Post by redroad55 on 2009-02-08
If you set up a new user account .. you can see what your defaults are and see how bad it is ..and then remove account later .. just an idea ..Best to you

---

