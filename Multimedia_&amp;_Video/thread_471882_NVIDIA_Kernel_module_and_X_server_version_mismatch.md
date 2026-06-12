---
title: "NVIDIA Kernel module and X server version mismatch"
date: 2007-06-12
forum: Multimedia &amp; Video
---

### Post by NotAvailable23 on 2007-06-12
I have Ubuntu 7.0x & NVIDIA 8800TX. I tried to install NVIDIA 97.55 drivers. I also used NVIDIA Xconfig utility to update my xorg.conf file. As long I don't reboot the system everything works fine. When I reboot the system and do "startx" it gives me a message saying:

"Error: API Mismatch: NVIDIA Kernel module version is 1.0.71xx and X server version is 9755. Make sure both versions are the same" -something like that. If I install NVIDIA 9755 driver again everything workd fine untill reboot.

I read the forms and tried all different things but nothing worked. I'm starting to think Windows is so much better with all this installation and updating stuff. I mush also mention I started Linux a month ago so you see ..... Can some please make my life a little easier.

Also I want to update my NVIDIA drivers to 100.xx. How to update the X server version and NVIDIA Kernel module ?

---

### Post by osxdude on 2007-06-12
That happens to me when I use Envy. Obviously you updated your driver with Envy, and package conflicts happened. Just choose to manually install the nVidia driver, and choose the correct version. When asked to configure the Xorg.conf, choose No. Try that.

Edit: If your not using envy, [click here to download it.]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by NotAvailable23 on 2007-06-12
I never used Envy. I would like to do a manual install so I know how to do it in the future and what all the commands mean. I'll try Envy but if someone could write down some commands onhow to do a manual install (updating NVIDIA Kernel module and X server).

Thanks!

---

### Post by jacc1234 on 2007-06-12
I have has the same problem and this worked for me. When you boot and it kicks you to command line run:

sudo modprobe -r nvidia

then reboot and it should be fine. 

You might also need to remove the module then uninstall the drivers then reinstall if it still wont boot  but I have found it is usually fixed by removing the module. 

Jacc1234

---

### Post by bodhi.zazen on 2007-06-14
I just ran into this exact problem 

I just did a fresh install of Gutsy Tribe 1 ....

The nv driver *still does not recognize my nvidia card (was hoping it would) ...

Installed the nvidia Beta driver (1.0.71xx). Installed Beryl. Everything was working just fine ...

Had to boot another OS (Fedora) .... Rebooted Gutsy .... 

X crash -> back to the command line :(

he he he, now don't get me wrong, I am very comfortable with the command line and I nkow I am talking about running on the bleeding edge here (OH OK, slightly hemorrhaging ?), but it is not as if this issue is resolved in previous versions and I am bringing it on myself, more like : Arrrghh I cant believe this kind of problem does not seem to get addressed. 

BUT

I hope the developers can resolve this kind of problem soon. I think *many* are drawn to Linux (Ubuntu) because of Beryl. Greeting them with a crash to the command line should seem fairly high priority to fix.

:lolflag:

Before you flame me, yes I know all the issues, I know all about Beryl being Beta and the nvidia drivers being proprietary. I know all about installing the headers and manually configuring Beryl. Iused to run envy, but I don't like it any more (he he, it checks the version of ubuntu now and so will not work with bleeding edge).

BUT I do see Ubuntu falling behind other distros in this area and it is sad to see.

/rant

On the bright side, At least I don't have an ATI :twisted:

---

### Post by bodhi.zazen on 2007-06-15
> **jacc1234 said:**
> I have has the same problem and this worked for me. When you boot and it kicks you to command line run:

sudo modprobe -r nvidia

then reboot and it should be fine. 

You might also need to remove the module then uninstall the drivers then reinstall if it still wont boot  but I have found it is usually fixed by removing the module. 

Jacc1234

```
sudo modprobe -r nvidia
```

^^^ => That did not work.

I re-installed the nvidia driver and all was good again. I did not even have to reboot, but I rebooted to check the fix survived the reboot process and ~ The cube is back !

---

### Post by bodhi.zazen on 2007-07-04
This problem recurred after I installed compiz fusion. I was not able to resolve the error message so I am stuck with vesa.

I tried uninstalling then reinstalling nvidia-glx, nvidia-glx-new, sudo modprobe -r nvidia, and reinstalling the nvidia driver ...

No joy.

Any further advice ?

---

### Post by bodhi.zazen on 2007-07-06
OK, I found an answer 

In case anyone is having a similar problem, **it is a bug with Ubuntu involving the nvidia-glx-new**

Solution : ```
sudo rm /lib/linux-restricted-modules/.nvidia.new.installed
```

Nvidia bug report : [http://www.nvnews.net/vbulletin/showthread.php?t=93008&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=93008&page=2)

(see post # 31 top of page 3)

Ubuntu bug report : [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217)

---

### Post by H-Radical on 2007-07-06
I just had a similar problem. When I used envy I got the API mismatch error... all I had to do was look at the newer version number in the error message, download the corresponding driver from the nvidia site and install it. That took care of the API mismatch error.

---

### Post by tseliot on 2007-07-06
> **NotAvailable23 said:**
> I never used Envy. I would like to do a manual install so I know how to do it in the future and what all the commands mean. I'll try Envy but if someone could write down some commands onhow to do a manual install (updating NVIDIA Kernel module and X server).

Thanks!

Try my guide (maybe method 2 if you prefer a manual installation):
[http://ubuntuforums.org/showthread.php?p=2587126](http://ubuntuforums.org/showthread.php?p=2587126)

---

### Post by subhankar on 2007-08-20
Same problem with me. Uninstall nvidia-glx, linux-restricted-modules. Do a dpkg --purge on those as well. Then reinstall. 

Should work.

---

### Post by tseliot on 2007-08-20
> **bodhi.zazen said:**
> I used to run envy, but I don't like it any more (he he, it checks the version of ubuntu now and so will not work with bleeding edge).
Here's a workaround:
[http://albertomilone.com/wordpress/?p=107](http://albertomilone.com/wordpress/?p=107)

Of course you will have to follow point B of the instructions since you used NVidia's installer:
[http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)

---

### Post by tseliot on 2007-08-20
If you're using Nvidia's installer (and you're willing to continue using it) have a look at this page (read where it says "Debian GNU/Linux or [K]Ubuntu with Xorg 7.x"):
[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

---

### Post by bodhi.zazen on 2007-08-20
Thanks for the information tseliot (from those of us who live on the edge)

And thank you for all the work you have done with envy.

---

### Post by ffi on 2007-10-06
> **bodhi.zazen said:**
> OK, I found an answer 

In case anyone is having a similar problem, **it is a bug with Ubuntu involving the nvidia-glx-new**

Solution : ```
sudo rm /lib/linux-restricted-modules/.nvidia.new.installed
```

Nvidia bug report : [http://www.nvnews.net/vbulletin/showthread.php?t=93008&page=2](http://www.nvnews.net/vbulletin/showthread.php?t=93008&page=2)

(see post # 31 top of page 3)

Ubuntu bug report : [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/106217)

almost final and this very important bug is still present :x except the file was called .nvidia_new_installed for me

---

### Post by jagdave on 2007-10-25
I have been smitten by this **** also. However I dont have the slightest idea how to fix this kinds of things. I will do a reboot into linux later to try the commands found here. I'm in windows now, and cant help but think this could never have happened in windows. But i support ubuntu and the whole shebang, but its so much detailed work left.

edit. I ran sudo modprobe -r nvidia and was then able to enter the gui. Tiresome to do that every reboot.

---

