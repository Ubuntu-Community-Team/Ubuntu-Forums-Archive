---
title: "Problem opening/running games that require fullscreen graphics"
date: 2008-07-11
forum: Multimedia Software
---

### Post by AndrewEsther on 2008-07-11
I'm running 8.04 with a GeForce 6200 OC (256meg). My first attempt to install the drivers I used the restricted drivers manager, which promptly caused me to only be able to use 800x600 res. After some fooling around and much googling, I was able to get 1024x768 (still not what I prefer, 1280x1024, but closer). Whenever I ran games with my previous configuration (using restricted manager), they would lock up the entire computer, desktop, mouse, and game, every few minutes and would stay locked up for 10-30 seconds, and then resume everything as normal. Also, the game would occasionally run windowed, even though it was commanded to run full screen, and this would cause all sorts of locking up and the colors on my screen would do a slow fade to lighter and lighter colors the longer I let it sit until I just gave up and did a hard restart.

So, I did some looking around, and found some great instructions on an alternative way to install the drivers supplied by NVidia, and it worked. This time there was no starting out at 640x480 and having to weasel my way back to higher resolutions (although I am still stuck with 1024x768). However, Ubuntu is STILL not detecting my monitor, and when I select it from the list (Compaq 7500 CRT), the computer promptly freezes and I am forced to restart. And now, any 3d application commanded to run full screen will not even start. There is a brief black flash, and then nothing. No minimized window, no process, nothing.

Some help? I'm still new to Linux, although I am getting the hang of how this all works slowly but surely. I'd appreciate it if someone could help me get this figured out... I need my FPS fix badly, as I nuked my WinXP install... *sigh*

Thanks!

---

### Post by AndrewEsther on 2008-07-11
Oh, and here is a copy of the error message I get when running any 3d full screen 

[IMG]http://infinitedark.sunlit-waters.net/screen shot.jpg[/IMG]

---

### Post by AndrewEsther on 2008-07-16
thread bump.


anyone...? this is extremely frustrating.

---

### Post by uberlube on 2008-07-16
Use ENVY to install your nvidia drivers and then instal GLX from the repos and that should get you going.

---

### Post by AndrewEsther on 2008-07-16
I currently have the drivers installed using restricted drivers manager. If I use ENVY, will I have to uninstal them first?


[EDIT] The only results I see for ENVY are for sound cards.... am I confuzzled about something, or not looking in the right spot?

---

### Post by uberlube on 2008-07-17
Since you are using 8.04 you will need to install envyNG i believe it is in the repos. If its not there you can grab it from its homesite [here]("http://www.albertomilone.com/nvidia_scripts1.html"). After it is installed it will appear in the menu, launch it and use the gui to install the appropriate driver. (You may want to run the uninstall nvidia driver option first to get rid of your current driver and then use the installer) Once your driver is installed and you do your reboot to initialize the driver go into synaptic and install GLX. Hope this helps.

---

