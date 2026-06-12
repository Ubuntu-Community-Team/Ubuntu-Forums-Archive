---
title: "Jaunty - NVIDIA GeForce 9600 GT Driver problems"
date: 2009-04-24
forum: Multimedia Software
---

### Post by AliasXNeo on 2009-04-24
**Please note:** I consider myself a Linux newbie so please try to simplify instructions accordingly. Thanks.

Hey guys,

I made a fresh install of the new release today and everything has gone fine. The problem started when I tried to find some drivers for my GFX card because I couldn't run things like compiz. I started by using the nifty System -> Administration -> Hardware Drivers tool which promptly told me that there was a NVIDIA driver (8.** Don't remember the minor version, but basically the latest NVIDIA driver) that I could install. So I proceeded to let it download and install the driver. After restarting my system Ubuntu started up in what seems like the typical terminal (black, no GUI at all). I can only assume something clearly went wrong with the driver installation because I couldn't get the GUI back no matter what. So I started over, made a fresh install, and tried it again only to get the exact same problem.

So clearly there's something wrong with the latest driver, at least for the 9600 GT. I tried to download and install the latest driver from the NVIDIA website (which was 180.51, I think the same as the one the Hardware Drivers app tried to download and install) but after running "sh NVIDIA-Linux-x86-180.51-pkg1.run" I get an error message saying "sh: Can't open NVIDIA-Linux-x86-180.51-pkg1.run." (I tried running sudo too)

So now I'm pretty lost as what I'm supposed to do. I can't run anything like compiz and I assume because my card is not being recognised. Can anyone please explain what I need to do to get this problem resolved? Thanks.

Regards,
Josh

---

### Post by inobe on 2009-04-24
Alias i have a 9400gt and it's working great with the 180.51 driver.

i did not use "hardware drivers" and certainly didn't install manually !


i added this to repository, i used the stable repo

[http://www.avenard.org/files/ubuntu-repos/](http://www.avenard.org/files/ubuntu-repos/)

add the key, applications> accessories> terminal

```
wget http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key && sudo apt-key add ubuntu-repos.key && rm ubuntu-repos.key 
```

to add the source go to system> administrator> synaptic> settings> repositories> third party software....

click add and paste

```
deb http://www.avenard.org/files/ubuntu-repos intrepid release
```

close software sources when done and click reload button on synaptic.

close synaptic.

you should then be notified, when this happens' install the upgraded driver and reboot.


every time a new driver is released you will get notified.

a big thanks to the fella that owns and maintains this site.

[http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html)

edit:**be sure to select the correct repo to your version of ubuntu, that repo is for intrepid**

[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

---

### Post by Cyr4x on 2009-04-24
Ubuntu's default 180.44 works for me, but only with compiz, etc. When i try to play a 3D OpenGL game (i.e. Enemy Territory), half of textures is black and speed oscillates around 15-20 fps. In Quake Wars i can't even see the menu, everyghing is blank. I've tried the 173 driver and even older 96 - the same result. On Ubuntu 8.04 everything was ok.

---

### Post by g1nsu on 2009-04-24
I'm having the same issue with the 180.44 Nvidia drivers.(9800gtx, AMD64) I just upgraded to 9.04 and booted to a blank screen with a frozen keyboard. I created a new xorg.conf with the nvidia tool which didn't make a difference. I purged all nvidia and re-installed with no luck. I have had to drop back to 177(173) drivers. They work without a problem... finding a fix would be nice tho.

---

### Post by AliasXNeo on 2009-04-24
Hey guys, thanks for the replies.

I tried the method you suggested inobe, however I got the exact same problem, restarted with a black console and no GUI. I also tried download the previous release (173) from the repositories and after installing I restarted with the same problem as before.

I'm starting to run out of ideas now and am beginning to wonder whether this is me installing the wrong software or the software simply not working properly. Any other ideas?

---

### Post by chessnerd on 2009-04-24
I recently went to Jaunty too and I had trouble booting into the GUI when it first started. I switched it to the default configuration and now it can boot, but my NVIDIA drivers won't activate now. I tried both the 173 and 96, neither work. 

I don't think that you installed anything incorrectly, I think that it is a bug in Jaunty. The drivers worked fine under 8.04 and 8.10, but 9.04 seems to have a problem with using them.

I'm pretty new to Linux, so I don't know how to fix this myself, but I'm gonna watch this thread to see if you can get a solution. If you do, it'll probably help me.

---

### Post by AliasXNeo on 2009-04-24
> **chessnerd said:**
> I recently went to Jaunty too and I had trouble booting into the GUI when it first started. I switched it to the default configuration and now it can boot, but my NVIDIA drivers won't activate now. I tried both the 173 and 96, neither work. 

I don't think that you installed anything incorrectly, I think that it is a bug in Jaunty. The drivers worked fine under 8.04 and 8.10, but 9.04 seems to have a problem with using them.

I'm pretty new to Linux, so I don't know how to fix this myself, but I'm gonna watch this thread to see if you can get a solution. If you do, it'll probably help me.

Should this be sent in as a bug report then?

---

### Post by chessnerd on 2009-04-24
> **AliasXNeo said:**
> Should this be sent in as a bug report then?

Maybe. Since several people seem to be having a similar problem with the new OS, I think it might be a bug.

---

### Post by g1nsu on 2009-04-24
i've found that there tends to be problems when tyring multiple drivers if you don't clean up. the following command has saved me some headaches. it removes the packages and the config files.

```
sudo apt-get --purge remove nvidia*
```

also, when you install the new drivers. go to applications>system>hardware drivers and make sure the driver is activated. also, make sure the driver is set to nvidia in your xorg.conf.

```
sudo nano /etc/X11/xorg.conf
```

instead of restarting everytime, you can alt-f2, login and type

```
sudo /etc/init.d/kdm restart or sudo /etc/init.d/gdm restart
```

---

### Post by AliasXNeo on 2009-04-24
I'll try that out.

If it worked on 8.10, isn't the only difference between 8 and 9 basically a new version of xorg and gnome? This new version might be causing problems, who knows. Is there anyway to revert back to an older version?

*UPDATE*

Tried your advice g1nsu, but once again it booted without a GUI. By the way you can't activate the driver without first restarting the system, which obviously doesn't work out too well.

---

### Post by 124c41 on 2009-04-25
I have the same problem with an NVIDIA GeForce 7650 GS. The 180.44 driver installed via envyng doesn't work and
neither does the 180.51 driver from the Nvidia website.

A similar problem with an ATI card is described here:
[http://www.kdedevelopers.org/node/3942](http://www.kdedevelopers.org/node/3942)

and the author has provided Xorg 1.5.2 debs for AMD64 here:
[http://www.davidfaure.fr/2009/xorg_debs.tar.bz2](http://www.davidfaure.fr/2009/xorg_debs.tar.bz2)

As I have an x86 installation, they are of no use to me, and I can't tell if Xorg 1.6 is the cause of the problem.

If I start the Xserver from the terminal via the "startx" command, I get this error after killing X with "rightALT+Print+k":
NVIDIA: could not open the device file /dev/nvidia0 (Function not implemented)
Do you get the same message or do I have a different problem?

---

### Post by 124c41 on 2009-04-27
I solved my problem.

When I had wanted to install Jaunty the first time, I got a kernel panic which I circumvented with the acpi=off bootflag.
So I thought maybe the nvidia problem was also related to the kernel and compiled the 2.6.29.1 kernel.
After I reinstalled the 180.51 nvidia driver, I got a different error message:

NVIDIA: could not open the device file /dev/nvidia0 (input/output error)

Referring to the nvidia readme chapter 8, I played around with the bootflags and could finally run the 180.51 driver with the these bootflags:
noapic pci=noacpi pci=biosirq edd=off
(I had to remove the previous acpi=off flag)

I don't know if I need all those flags (or if I really needed to compile a new kernel), but I just hope that they won't do any harm.

---

### Post by bowens44 on 2009-04-27
> **AliasXNeo said:**
> 
So clearly there's something wrong with the latest driver, at least for the 9600 GT. 
Josh

I disagree. I have a 9600 GT also and the 180 series driver in Jaunty works perfectly.

---

### Post by allensaucier on 2009-04-27
Well, I must add to this post:
asus p5q-vm
nvidia 9600GT
ubuntu 9.0.4

tried 173.14.16, 177, 180.44, 180.51, 185b and NONE worked for me at all.I continually get a black screen AND it hangs tighter than a drum instead of getting to the usual ubuntu log in screen.

Tried nvidia 8400GS & that worked w/ nvidia drivers

anyone have any work arounds?

envyng doesn't seem to work either.

---

### Post by asuastrophysics on 2009-04-28
> **allensaucier said:**
> Well, I must add to this post:
asus p5q-vm
nvidia 9600GT
ubuntu 9.0.4

tried 173.14.16, 177, 180.44, 180.51, 185b and NONE worked for me at all.I continually get a black screen AND it hangs tighter than a drum instead of getting to the usual ubuntu log in screen.

Tried nvidia 8400GS & that worked w/ nvidia drivers

anyone have any work arounds?

envyng doesn't seem to work either.

idk nothing seems to work quite right in jaunty. 
i have two computers: one with ATI and one with nVidia. Neither support compiz. Neither have proprietary drivers.
so much for "just switch to nVidia and your graphic problems will go away"

jaunty has also broken my wireless on my laptop. despite reinstalling it 4 times and deleting all madwifi drivers, wifi is slow, unresponsive, and disconnects all the time. 

i think that this release is not ready yet, and shouldn't be officially released until both ATI and nVidia have released drivers.

---

### Post by tj111 on 2009-05-01
Same problem here, made a post on a similar bug-report which was just recently closed. [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/339489](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/339489)  

@124c41, where do you set the boot flags?  Can anyone confirm if this fix worked for them?

---

### Post by Scrapper89 on 2009-06-17
I have exactly the same problem...
Though:

my 9600Gt works with 173 drivers, crashes on any later ones. But i need a later one since firefox lags with 173, even with optimizations.

i will try the boot flags now and tell the results

---

### Post by s.dalas on 2009-06-18
hey gues,

for me things are a little different...
i dual boot my system with jaunty and xp (for gaming). i bought 9600gt 521mb,gddr3. 
xp system runs but the card is not working almost at all. my system is almost not working!!
in jaunty the system doesn't load at all. it says " starting up... " and it freezes there. 
i dont know what to do. i am now on my igd graphics. 
anyone has any idea?? i can also return the card for an other one. so plz suggest me what to do.

---

### Post by IBamBam on 2009-08-26
OMG After 5 days I finally got sli working. I tried EVERYTHING that i could find on every form and board. This is what i did. GoodLUCK!

1) First step: you must reset the Xorg to its default conf. Before, you should backup it, to avoid any mistakes.

In the Terminal:

  sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
  sudo dpkg-reconfigure -phigh xserver-xorg

2) Installing packages and dependencies:

  sudo apt-get install build-essential linux-headers-`uname -r`

3) Remove old version drivers:

  sudo apt-get --purge remove $(dpkg -l | grep nvidia | awk '{print $2}')

Download the driver from nvidia website. You must repect your system architecture (x86, 64...)

4) In my case: Ubuntu 32:
 wget [http://download.nvidia.com/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg1.run](http://download.nvidia.com/XFree86/Linux-x86/185.18.36/NVIDIA-Linux-x86-185.18.36-pkg1.run) -O NVIDIA-Linux-185.pkg.run

5) Now, move the installer to /usr/src and link it. Follows:

  sudo install NVIDIA-Linux-185.pkg.run /usr/src/
  sudo ln -s /usr/src/NVIDIA-Linux-185.pkg.run /usr/src/nvidia-driver

Kill X:
6) Time to stop X  GDM. So, press "Ctrl+Alt+F1", login and stop gdm:

  sudo /etc/init.d/gdm stop

7) Installing:

  sudo sh /usr/src/nvidia-driver

(press yes to all questions)

8) When it is done, restart your computer:

  sudo reboot

After boot up, 

9) press "Ctrl+Alt+F1", login and stop gdm:

  sudo /etc/init.d/gdm stop

10) Change Flag

  sudo nvidia-xconfig   (you might not HAVE to do this one but I did)
  
  sudo nvidia-xconfig -a    (this one you have to do)



11) enable SLI

  sudo nvidia-xconfig --sli=AFR

NOTE* I had to change my Bus ID BEFORE I could enable SLI (#11) also. It was swaped (5 was where 4 was supposed to be and 4 was where 5 was to be) Go Figure!!

  open a terminal to see your settings

  lspci              (shows your Bus Info)

  gksu gedit /etc/X11/xorg.conf    (is where you would change it. "be 

 careful if you mess the config file up you have wipe it                                "sudo dpkg-reconfigure -phigh xserver-xorg"   and start at #9 again)

12) Reboot

   sudo reboot

I hope I got all this right. Each system may be a little different. But this worked for me! WAAHOO I got my SLI, Time for bed :)

---

### Post by inobe on 2009-08-26
> **inobe said:**
> Alias i have a 9400gt and it's working great with the 180.51 driver.

i did not use "hardware drivers" and certainly didn't install manually !


i added this to repository, i used the stable repo

[http://www.avenard.org/files/ubuntu-repos/](http://www.avenard.org/files/ubuntu-repos/)

add the key, applications> accessories> terminal

```
wget http://www.avenard.org/files/ubuntu-repos/ubuntu-repos.key && sudo apt-key add ubuntu-repos.key && rm ubuntu-repos.key 
```

to add the source go to system> administrator> synaptic> settings> repositories> third party software....

click add and paste

```
deb http://www.avenard.org/files/ubuntu-repos **intrepid **release
```

close software sources when done and click reload button on synaptic.

close synaptic.

you should then be notified, when this happens' install the upgraded driver and reboot.


every time a new driver is released you will get notified.

a big thanks to the fella that owns and maintains this site.

[http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html)

hey guys' that's the intrepid repo, look in the link for separate repos for jaunty or 8.04.

[http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://www.avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

---

### Post by peepingtom on 2009-08-26
So long as we're revisiting the past, this PPA is better.
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

---

