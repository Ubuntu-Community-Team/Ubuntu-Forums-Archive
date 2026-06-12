---
title: "Nvidia driver not working"
date: 2012-09-27
forum: Multimedia Software
---

### Post by xpbxkidx on 2012-09-27
So I'm relatively new to ubuntu I had 10 installed a while back on a laptop.   I usaully run fedora. In fedora the nvidia driver just installs via the  .run pkg from the nvidia website. I never had any trouble with that. (same machine)

I'm trying to get dual monitors to work.

Now with the fresh install, ubuntu installs the proprietary drivers automatically. It would boot only one screen .  I went into the nvidia x settings. The setting showed that BOTH monitors were not active. I thought it was odd. i activated both of them and then rebooted. 

Now when I boot both screens load at the same res  as in mirrors of one another(one is wide screen one is not[so one is stretched]). i feel like i could fix this in the same nvidia-settings. However this brings me to my big problem

when the environment loads it loads a message 
"
Could not apply the stored configuration for monitors
none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 72
CRTC 72: trying mode 1280x1024@77Hz with output at 1680x1050@51Hz (pass 0)
CRTC 72: trying mode 1280x1024@77Hz with output at 1680x1050@51Hz (pass 1)"

and when I try to load the nvidia settings it says the driver isn't in use. I run the suggested command and restart only xserver or the whole machine and I wind up in the same place

things I've tried
manual install with the nvida .run pkg ( wont load any graphics at all not even a loading screen

remove and reinstall the .deb via apt-get

various tinkering

I'm pretty sure there is conflicting .conf files but I cant figure out witch ones it would be

thanks
-kyle

---

### Post by pqwoerituytrueiwoq on 2012-09-27
remove drivers
```
sudo nvidia-uninstaller # or something like that use the tab key
sudo apt-get purge nvidia*
sudo rm /etc/X11/xorg.conf # just to be sure
```now lets get the latest driver
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-update
sudo apt-get update
sudo apt-get install nvidia-current
```if you end up in low graphics mode
```
sudo nvidia-xconfig
```you can use the .run file but you will have to reinstall it after every kernel update

---

### Post by xpbxkidx on 2012-09-27
Ah purge, quite helpful . thank you

Im now stuck with a black background on one ( fully functional environment) and white background on the other. it also has an x for an icon. I cant drag windows over either.

---

### Post by InonS on 2013-01-13
The SWAT ppa gives errors when I try to load it.
Also, as this post ends with the user facing a broken user interface, I'm not sure I'd like to try it. Is there a solution to this issue?

Also, link to [http://ubuntuforums.org/showthread.php?t=2104126&highlight=Could+-apply+the+stored+configuration+for+monitors%26quot%3B+%26quot%3Bnone+of+the+selected+modes+were+compatible+with+the+possible+modes%3A%26quot%3B+%26quot%3BTrying+modes+for+CRTC+72]("http://ubuntuforums.org/showthread.php?t=2104126&highlight=Could+-apply+the+stored+configuration+for+monitors%26quot%3B+%26quot%3Bnone+of+the+selected+modes+were+compatible+with+the+possible+modes%3A%26quot%3B+%26quot%3BTrying+modes+for+CRTC+72")

Finally, I found that a complete removal of both the nvidia-current and nvidia-settings packages, and then installation of those packages, followed by a reconfiguration of the nvidia X Server Settings returned things to their proper state...

32-bit ubuntu 12.01.1, GeForce 8500 GT

---

