---
title: "Pulseaudio reinstall doesn't detect external sound card"
date: 2009-12-17
forum: Multimedia Software
---

### Post by deltaxxmintpie on 2009-12-17
Hello I'm having trouble with my SB live! external audio device. It worked normally until yesterday, I used the terminal command "sudo apt uninstall pulseaudio" in an attempt to fix WINE sound problems. 

However WINE audio problem won't go away- instead it kept giving me a message whenever I tried to configure audio in an application running in wine: "Setting related to direct sound has been modified. Setting will be valid after rebooting the computer". 
I have rebooted my pc a couple of time but the problem remained.

Hence I reinstalled pulse audio and after a reboot, my SB live! external audio device wasn't working. Normally it would show up in "sound preferences" panel as a device but it isn't here anymore.

 [IMG]http://s131.photobucket.com/albums/p296/deltaxxmintpie/?action=view&current=nosound.jpg[/IMG]

Any help would be nice, thanks :)

---

### Post by HappyFeet on 2009-12-17
After you uninstall something, do:
```
sudo apt-get clean && sudo apt-get autoremove
```
*Then* reinstall pulseaudio.

---

### Post by deltaxxmintpie on 2009-12-18
> **HappyFeet said:**
> After you uninstall something, do:
```
sudo apt-get clean && sudo apt-get autoremove
```*Then* reinstall pulseaudio.

It worked! :) thank you very much

---

