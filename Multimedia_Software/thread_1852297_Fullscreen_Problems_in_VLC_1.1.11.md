---
title: "Fullscreen Problems in VLC 1.1.11"
date: 2011-09-29
forum: Multimedia Software
---

### Post by PrimordialAstronaut on 2011-09-29
Hi guys, 

I've tried researching this problem all over and just haven't found a solution. Maybe someone here can help me.

Basically my issue is this: I just installed the latest version of VLC on Ubuntu 11.04, and when I play a video I get sound fine, and video fine... unless I try to fullscreen, enlarge the screen area, or in any other way click away from VLC player and then come back to it. Am I just missing a codec or something here?

Thanks for any suggestions!

---

### Post by WasMeHere on 2011-09-30
My ubuntu (studio) 11.04 is up to date and I have VLC 1.1.9, so you have a newer version than in the repositories. There may be some compatibility problem with the new 1.1.11 version.

Are you sure that you need the newest version, or would it be OK to delete it and install VLC from the repositories?

In general, I recommend that you try this thread: [_**[COLOR="Red"]Comprehensive Multimedia & Video Howto[/COLOR]**_]("http://ubuntuforums.org/showthread.php?t=766683")
It may take some time, but the result is very good, you will get a solid multimedia system.

Have fun
Olle

---

### Post by PrimordialAstronaut on 2011-09-30
Oh thanks Olle! I didn't realize this version might be too new. I will give 1.1.9 a try and see if that fixes my problems. I did go through the procedures listed in that thread, with no result. But it could just be a version problem like you said, so I'll try 1.1.9 and see if that solves my problem. Much appreciated!

---

### Post by PrimordialAstronaut on 2011-09-30
Okay so I tried downloading 1.1.9 through the terminal option... and I still seem to have 1.1.11 running on my system so I must have done something wrong. Can you suggest a good place to find 1.1.9 for download? 

Sorry, I'm kind of a Linux noob so I'm probably making some stupid mistake here...

---

### Post by WasMeHere on 2011-09-30
How did you install 1.1.11? Did you use a .deb file? In that case that same file may have an *uninstall* option. I think it is important to uninstall before you try to install a previous version (uninstall 1.1.11 before installing 1.1.9). If there is no uninstall option, you can try ```
sudo apt-get remove vlc
sudo apt-get purge vlc
``` but I am not sure that it works. If these tips cannot help you, we call for help from someone who knows more about uninstalling software.

---

### Post by PrimordialAstronaut on 2011-09-30
Okay so I was able to uninstall 1.1.11 but the problem I'm still having is that I cannot find anywhere to download 1.1.9... every single download I find on VLC is the brand new version.

---

### Post by PrimordialAstronaut on 2011-09-30
Maybe I should also specify that I am having similiar issues with other media players. For instance, Banshee and GNOME media players won't play video at all. So I really think the root of the problem is with my system. I just don't know what I'm missing.

---

### Post by WasMeHere on 2011-09-30
> **PrimordialAstronaut said:**
> Maybe I should also specify that I am having similiar issues with other media players. For instance, Banshee and GNOME media players won't play video at all. So I really think the root of the problem is with my system. I just don't know what I'm missing.

Did you try this thread: [_Comprehensive Multimedia & Video Howto_]("http://ubuntuforums.org/showthread.php?t=766683")?
It may take some time to do the tasks in the first post 'the how-to', but the result is very good, you will get a solid multimedia system.

*Or* you may have a general problem with the *video driver*. What graphics card/chip do you have? Run the following terminal command:```
sudo lshw -businfo | grep display
``` If you have nVidia, nForce or GeForce or Quadro, you should install a proprietary nvidia driver.

By the way, how much effort and time have you invested in your Ubuntu system? Would it be worthwhile to test some live systems and make a new system installation. My experience is that Linux Mint has fully working multimedia support out of the box, and it is based on Ubuntu. GeeXbox is a 'persistent' live usb media player.

---

### Post by PrimordialAstronaut on 2011-09-30
This is what I got when I ran that command:

pci@0000:01:00.0               display     Rage 128 PF/PRO AGP 4x TMDS

So I'm not sure what that means exactly...

As to how much time I've put into the system... not very much. I just installed last week and I'm just trying to get everything set up how I want it still. I went for Ubuntu because it was suggested by a friend who liked it, but maybe I should try Mint as well. I assume I can try it out without installing?

Anyway thanks for your help. I'll keep researching and trying to solve the problem. I hate to switch to a whole new system when this one is otherwise working perfectly fine.

---

### Post by WasMeHere on 2011-09-30
Look at this thread about a similar card: [http://ubuntuforums.org/showthread.php?t=1122749]("http://ubuntuforums.org/showthread.php?t=1122749") Some guy with 'your' card has also posted in this thread. Sometimes it works, but sometimes it is hard to tweak.

You can also search for *linux Rage 128 PF/PRO AGP 4x TMDS* with an internet browser. With good luck or hard work a solution will appear out of the cyberspace ;-)

Yes, you can try Linux Mint without installing. Download an iso file for the DVD version with gnome if you are using 'vanilla' Ubuntu with gnome! Then you can make a live DVD or live USB. The advantage with Mint is that the multimedia toolbox works directly with the live system, so that you will know without having to install to your hard disk:
*linuxmint-11-gnome-dvd-32bit*
if your graphics card works with Mint. Some people would suggest -64bit if you have a 64 bit system.

If your computer is getting old you can consider the light-weight LXDE version:
*linuxmint-11-lxde-cd-32bit*

---

### Post by PrimordialAstronaut on 2011-10-01
Awesome, I will have to give all that a try tomorrow. Thanks again!

---

