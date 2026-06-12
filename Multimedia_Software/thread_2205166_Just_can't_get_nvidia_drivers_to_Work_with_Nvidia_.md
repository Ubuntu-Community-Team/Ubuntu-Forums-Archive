---
title: "Just can't get nvidia drivers to Work with Nvidia NVS 310"
date: 2014-02-12
forum: Multimedia Software
---

### Post by Chance_Harris on 2014-02-12
going to have to use windows for my dev box if I can't get this working. I really don't want that.:mad:


lspci | grep -i vga yields :

03:00.0 VGA compatible controller: NVIDIA Corporation GF119 [NVS 310] (rev a1)

I've figured out that I need "nomodeset" both during the install, and as a grub option. So I'm able to login to unity in 800x600 mode.

After several attempt, via clean reinstalls of both 13.10 and 12.04 (both 64 bit)  it seems that any nvidia driver causes the black screen of death. I.e. you don't even get a shot at logging in. You just get a black screen with a blinking white cursor.

I've tried several different versions of several different nvidia drivers both from the default and from ubuntu-x-swat and xorg-edgers. But I've about exhausted all the possibilities of the "try everything like a blind monkey" approach and don't really know what to look for to figure out if this doable of just impossible.

Also, the thing is, I don't really need any advanced graphics stuff going on here. I just need xterm, eclipse, emacs and mozilla and I'm fine. But I don't know how to get anything beyond 800x600 resolution without nvidia drivers (is that even possible?), so any debuging or work around ideas would be appreciated. I get the feeling I should be looking at more logs or something somewhere, but don't know to even start.

---

### Post by oldfred on 2014-02-12
I have nVidia and years ago had similar issues. Often trying to install the driver from nVidia or from ppa causes more issues. Only if you need some very advanced new feature that the newest driver has, should you install from anything but the repository. And since dpkg does not know about externally installed drivers you have to manually rebuild initramfs. So best to just use repository.

And if you install one version but then change to another you must totally purge all traces of old version or you get conflicts.
       sudo apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

Then I have used either System Settings to add nVidia or command line.
And if command line current & settings must be same version.
      
 # Install version you prefer
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett* 
nvidia-settings-experimental-310

---

### Post by Chance_Harris on 2014-02-12
I have not been doing dpkg-reconfigure as a routine part of my attempts.

So I tried above (with nvidia-current-updates and nvidia-settings-updates), after a fresh reinstall of 12.04.

No luck.

---

### Post by oldfred on 2014-02-12
Is this a laptop with Intel Video also?

---

### Post by Chance_Harris on 2014-02-13
It's not a laptop. It's a Desktop. Dell Precision T5600.


But I don't really know how to answer the question of "does it have Intel Video also"

---

### Post by oldfred on 2014-02-13
A lot of newer laptops have dual video, Intel for low power and nVidia for performance. 

If just nVidia, then it should be the driver that supports your card.

---

### Post by Chance_Harris on 2014-02-16
at the end of the day .... well really, at the end of the week my final problem was that my monitor was too old. The clue was that I couldn't get to bios setup.

I ended up switching to Mint and using these directions for directly installing the nvidia driver outside of the package management system:

[http://forums.linuxmint.com/viewtopic.php?f=59&t=154932](http://forums.linuxmint.com/viewtopic.php?f=59&t=154932)

After I did that in MINT, I was at least able to always boot into a shell after X failed to start, and then when I plugged in a new monitor, it started working.

---

