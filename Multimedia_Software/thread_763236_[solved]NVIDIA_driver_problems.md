---
title: "[solved]NVIDIA driver problems"
date: 2008-04-22
forum: Multimedia Software
---

### Post by Enthrall on 2008-04-22
Im am a complete newbie to linux just so you know and I think its great so far. I've been on the edge of giving up and just booting back into vista but I've finally solved my problem and I'd like to share with others that may have the same problem. So far its maybe taken me ~6 hours to figure out. Its was like re-inventing the wheel. But besides that.

I have the geforce 9600 gt so I used the beta drivers which are out i think 173.08. heres my guide:

1. intall the driver from the internet <--edit sorry i didnt make it clear.
just go to the site you get your driver from.

2. press ctrl+alt+f1

3. you have some options. you can log into root, use _su_ command just _su_ then log into root or you can use sudo before your commands. Its not that hard. For example when it asks for my username i type root then for password my root password. You can edit this in system--->admin--->users and groups. and just change the pass to what ever you want.

4. Next step is to type the following go ahead and use sudo for good measures. But if your logged into root I dont think its needed. Im a newb so dont flame.command - sudo /etc/init.d/gdm stop
this will stop the x server which is basically the gui. Correct me if im wrong.

5. next is to get a kernal. My problem was when I was installing the first time it said the kernal module was missing. so type- sudo apt-get install update
the type- sudo apt-get install build-essentials
Worked for me but I really dont know what it does or what a kernal is even for. I'd like to know so could someone enlighten me?

6. next is to run the driver. type- sh '/**/NVIDIA-Linux-x86-173.08-pkg1.run'

** depends on your file location. for example mine was
 sh '/home/enthrall/Desktop/NVIDIA-Linux-x86-173.08-pkg1.run'

7. follow the instructions on screen. say yes to every thing. **YES** 

8. when its done type- sudo /etc/init.d/gdm start 

9. once logged back in do the following. [U]this is a very important step do not miss or you will have to re install on next boot which was my 
problem.[/U]
go to applications then terminal and type- nano /etc/default/linux-restricted-modules-common
go down the page where is says something like DISABLED_MODULES= ""
In between the quotations type _nv_ and save this. To use the commands at the bottom use the ctrl key with the letter example- ^c-cancel 
you would press ctrl c. When you do this it asks if you want to save this type y and press enter. Then press enter again and restart the system. VOILÀ it should be working now.:)

---

### Post by Amshu on 2008-04-23
Thank you so much for posting this. I've been having a tough time with my 9800gtx. Right now I'm doing a fresh install of 8.04 then I'll try your method. One question though. In step one what patch are you talking about? :)

---

### Post by Enthrall on 2008-04-23
oh sorry I didnt make that clear. I edited it. It should say install your driver from the internet. Nivdia website. Oh if yours is the nvidia 9 series go to nvidia and make sure to install the latest beta driver for the 9 series.

---

### Post by Amshu on 2008-04-24
:) It works 
 TY

---

### Post by Azraelthe7th on 2008-04-28
Hi, I tried using your guide, but I can't even get "build-essentials".  Running Hardy Heron.

---

### Post by zhinker on 2008-04-28
Excellent guide, I've finally got the Nvidia driver working now

Once fix though, it's supposed to be:

sudo apt-get install build-essential , not build-essentials.  There's not 's' at the end

Also, just so you know, you can run the build-essential line from the terminal before any other step.

---

### Post by fh_scott on 2008-04-28
worked perfect, thanks!

---

### Post by Azraelthe7th on 2008-04-29
> **zhinker said:**
> Excellent guide, I've finally got the Nvidia driver working now

Once fix though, it's supposed to be:

sudo apt-get install build-essential , not build-essentials.  There's not 's' at the end

Also, just so you know, you can run the build-essential line from the terminal before any other step.

It says that my build-essential package is the newest, and it still can't find a precompiled kernel.  :confused:  So, no 9600 GT on Hardy for me yet.

---

### Post by zhinker on 2008-04-29
> **Azraelthe7th said:**
> It says that my build-essential package is the newest, and it still can't find a precompiled kernel.  :confused:  So, no 9600 GT on Hardy for me yet.
it was my impression that build-essential allows the driver to compile it's own kernel (but I could be wrong), since it couldn't find a preocompiled kernel when I tried installing it either, but I clicked okay/yes to all the options and ended up with a 3D desktop

---

### Post by Azraelthe7th on 2008-04-29
> **zhinker said:**
> it was my impression that build-essential allows the driver to compile it's own kernel (but I could be wrong), since it couldn't find a preocompiled kernel when I tried installing it either, but I clicked okay/yes to all the options and ended up with a 3D desktop

That's pretty much what I did, but it's just not finding it.  When I start up GDM after I install the driver, the kernel panics and it says that it can't find a proper X server configuration.  It's, as one would say, frustrating.

---

### Post by Novega on 2008-04-30
This guide worked for me :)  I had no problems whatsoever. Hopefully those that are experiencing difficulties can get them resolved soon as well.

I did have a quick question though: when a new kernel is released, will those who used this guide have to re-install the driver? ...and do we use the same method?

I'm a new user and just trying to think ahead :P

---

### Post by zhinker on 2008-04-30
> **Novega said:**
> This guide worked for me :)  I had no problems whatsoever. Hopefully those that are experiencing difficulties can get them resolved soon as well.

I did have a quick question though: when a new kernel is released, will those who used this guide have to re-install the driver? ...and do we use the same method?

I'm a new user and just trying to think ahead :P

Good point.  More importantly, will the nvidia drivers update themselves automatically?

---

### Post by vexorian on 2008-05-01
They don't update themselves automatically.

You will have to reinstall the driver everytime the kernel is updated (often by the security repo)

So, if after a kernel update everything breaks, don't panic, just execute the .run again.

When a new version of ubuntu comes and you want to update, make sure to uninstall nvidia's driver first.

---

### Post by lswest on 2008-05-01
> **Azraelthe7th said:**
> It says that my build-essential package is the newest, and it still can't find a precompiled kernel.  :confused:  So, no 9600 GT on Hardy for me yet.

Are you sure you downloaded the beta nvidia drivers for the 9 series?  And i'm envious :P my graphic cards both in my PC and in my laptop are low-end :P

---

### Post by techstop on 2008-05-01
Thanks mate! Worked a treat on my 9600GT!

---

### Post by Novega on 2008-05-10
So like I said, this worked 100% perfect for me on my 32 bit Ubuntu system

**BUT** ... Now I'm setting up a x64 ***(K)***ubuntu system (*with KDE4, if it makes any difference?*), following this guide exactly isn't gonna work I don't think.

So how would I change the commands to suit a x64 KDE build ?

---

### Post by vexorian on 2008-05-10
I think it should probably work as long as you download the 64 nvidia driver.

---

### Post by Novega on 2008-05-10
> **vexorian said:**
> I think it should probably work as long as you download the 64 nvidia driver.

ok cool, so instead of "gdm stop" do I use "kdm stop" b/c it's kde and not gnome?

---

### Post by cjhermann on 2008-05-10
Thanks for the howto enthrall :)

As an aside, I've installed nvidia proprietary drivers before without hassle, but this time for some reason the nvidia installer errored saying I didn't have the libc development headers installed and wouldn't work (Fresh install of Hardy Heron).

If this happens to you, just stay in your Ctrl+Alt+F1 prompt and type 
```
sudo apt-get install libc6-dev
```
That will install libc6 and libc6-dev (about 14MB worth to download I think), after which you can run the nvidia installer again successfully.
Don't forget to edit /etc/defaults/linux-restricted-modules-common as described in the first post.

Thanks!

---

### Post by zr0gee on 2008-05-19
This worked without a hitch for the GeForce 9800 GTX aswell.

I recently got hold of a 9800GTX, and a couple of days after I decided to completely switch over to Ubuntu and nuke my Windows partition ;)

Initially, I had problems installing this nVidia beta driver, because I was missing the last step (the step where you start-up the x-server again, and edit a config-file before rebooting), which the OP describes in the how-to. 

So.. thx alot for this howto, and I'm thrilled to say I'm not going back to vista :)

---

### Post by Mortosa on 2008-05-23
I sure hope this works when i get home. I have a 9600GT as well. I have no problems installing the beta drivers. my problem is when i reboot I suddenly get low graphics mode issues. They only thing I did not do was disable the NV module.

---

### Post by techstop on 2008-05-28
> **Mortosa said:**
> my problem is when i reboot I suddenly get low graphics mode issues. They only thing I did not do was disable the NV module.

The part where Enthrall says;

> _this is a very important step do not miss or you will have to re install on next boot which was my problem._

??? :confused:

It probably helps to follow the instructions!

---

### Post by atariluc on 2008-05-28
Hi, i am also new with this ubuntu thing. It was everything perfect with ubuntu 7. Then i upgraded to 8. Since then i can not use the nvidia. I have tried everything but nothing works for me.

The same with this. The part that does not work is this:

luciano@akari:~$ sh '/home/luciano/desktop/NVIDIA-Linux-x86-169.12-pkg1.run'
sh: Can't open /home/luciano/desktop/NVIDIA-Linux-x86-169.12-pkg1.run

nothing happens... 

Maybe with the uprgade something went wrong... Please help!!!

---

### Post by Novega on 2008-05-28
> **atariluc said:**
> Hi, i am also new with this ubuntu thing. It was everything perfect with ubuntu 7. Then i upgraded to 8. Since then i can not use the nvidia. I have tried everything but nothing works for me.

The same with this. The part that does not work is this:

luciano@akari:~$ sh '/home/luciano/desktop/NVIDIA-Linux-x86-169.12-pkg1.run'
sh: Can't open /home/luciano/desktop/NVIDIA-Linux-x86-169.12-pkg1.run

nothing happens... 

Maybe with the uprgade something went wrong... Please help!!!

I'm really new to Ubuntu myself, so take what I'm going to say with a grain of salt... maybe use ```
sudo sh '/home/luciano/desktop/NVIDIA-Linux-x86-169.12-pkg1.run'
```

If nothing else, it's a free bump for your thread :p

---

