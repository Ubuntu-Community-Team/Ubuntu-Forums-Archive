---
title: "Nvidia driver problem!!!!"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by burntphoenix_7 on 2008-02-13
OK, so this is what I did:
I went to the NVIDIA website and downloaded the pkg1.run packge. I typed sudo apt-get install build essentials and it asked me for my CD, which I inserted an it installed all the needed interfaces and what not.
Then I pressed ctrl+alt+f1 and logged in as root. shutdown the xserver by /etc/init.d/gdm stop.
then I typed sh '/the location of the driver' and the installation started. It got to the part where it says that it wants to check for precompiled kernel interfaces on the nvidia website but there were non so it compiled them for me and the installation went ok. In the end it asks me to replace my x file automatically so I choose yes.
Then I restarted the xserver and I saw all the desktop effects and everything was fine but then when I reebooted my computer ubuntu tells me that itis running in low graphics mode because my monitor and my video card could not be detected correctly. so I choose them my self from the screens and graphics menu but they revert to vesa all the time. I tried manually editing the Xorg.conf file but to no avail.
Can you plz help me? I also tried restricted drivers manager but it poses the same problem. I am using ubuntu 7.10 gutsy and my PC specs are:
Intel D945gnt
Nvidia 6600 video card.
160GB hard drive
1GB RAM
3.2ghz cpu.
I have the generic linux kernel running in case you wanted to know that.
Help plz.

---

### Post by overdrank on 2008-02-13
> **burntphoenix_7 said:**
> OK, so this is what I did:
I went to the NVIDIA website and downloaded the pkg1.run packge. I typed sudo apt-get install build essentials and it asked me for my CD, which I inserted an it installed all the needed interfaces and what not.
Then I pressed ctrl+alt+f1 and logged in as root. shutdown the xserver by /etc/init.d/gdm stop.
then I typed sh '/the location of the driver' and the installation started. It got to the part where it says that it wants to check for precompiled kernel interfaces on the nvidia website but there were non so it compiled them for me and the installation went ok. In the end it asks me to replace my x file automatically so I choose yes.
Then I restarted the xserver and I saw all the desktop effects and everything was fine but then when I reebooted my computer ubuntu tells me that itis running in low graphics mode because my monitor and my video card could not be detected correctly. so I choose them my self from the screens and graphics menu but they revert to vesa all the time. I tried manually editing the Xorg.conf file but to no avail.
Can you plz help me? I also tried restricted drivers manager but it poses the same problem. I am using ubuntu 7.10 gutsy and my PC specs are:
Intel D945gnt
Nvidia 6600 video card.
160GB hard drive
1GB RAM
3.2ghz cpu.
I have the generic linux kernel running in case you wanted to know that.
Help plz.

HI and welcome, when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and  then use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

### Post by burntphoenix_7 on 2008-02-14
I tried that but it just reconfigures the xorg.conf file to use the nv driver instead of the nvidia driver. I want to use the restricted drivers but when I do it reverts to vesa mode after evey reboot!
Help plz!

---

### Post by berzerke on 2008-02-14
If it's any consolation, I'm having the same issue. I'm not sure if it was the last kernel update, or the last set KDE updates (I run Kubuntu). I didn't reboot right away after the kernel update since it wasn't a pressing issue. Now, I'm stuck using the nv driver. It works for everything except one graphics intensive program I use a lot.](*,)  If I try to use the real nvidia drivers, X doesn't start at all. I've tried the official ones too.

It's even more frustrating as I have the gutsy no virtual terminal problem, so it's a full reboot into recovery mode every time I try to fix this. And no, the modprobe solution for the virtual terminal problem does not work for me.

Possible Fix: It appears I've found a way to make it work for me. I had to install the nvidia-glx-legacy package, then enable it. One more reboot and it works. Depending on your card, you may need the nvidia-glx package instead.

---

### Post by burntphoenix_7 on 2008-02-14
Forget it! not even the Linux Gods can help me with this one. I am gonna uninstall ubuntu for now. I'll check hardy heron when it comes out but for now astalavista ubuntu!

---

### Post by Whiffle on 2008-02-14
woah woah...23 hours and already giving up?  Ouch.

when you reboot your computer, run 'lsmod' and look for nvidia.  Sounds to me like the nvidia kernel module isn't getting loaded and/or something is interfering w/ it.  I had to remove *all* ubuntu nvidia kernel packages on mine to make it work, and just used the nvidia one.  works like a charm.

---

### Post by samwyse on 2008-02-14
**nvidia-glx-new** is the correct package for a 6600 ([http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)).

**nvidia-glx** is for the first list of chips and **nvidia-glx-legacy** for the second list of chips here: [http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html).

---

### Post by PmDematagoda on 2008-02-14
In fact if the OP had decided to stick around, I think I would have been able to solve his/her problem, it just goes to show that you need patience in order to use Linux and solve problems. If the OP(burntphoenix_7) is willing to keep trying then post here.

Also samwyse has a good point.

---

### Post by firefly76 on 2008-02-14
> **burntphoenix_7 said:**
> OK, so this is what I did:
when I reebooted my computer ubuntu tells me that itis running in low graphics mode because my monitor and my video card could not be detected correctly. so I choose them my self from the screens and graphics menu but they revert to vesa all the time. I tried manually editing the Xorg.conf file but to no avail.
Can you plz help me?
Help plz.

Install ENVY, which can be run from the terminal.  You can choose which version of the nvidia drivers to install, and bypass the restricted drivers manager althogether.

Once ENVY installs your drivers, it will happily configure your xorg.conf file as well.

You can install envy using this guide: [install ENVY guide]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by samwyse on 2008-02-14
Does Envy update the driver after kernel updates? I'm not sure I'd recommend it over the nvidia-glx packages. Doesn't the Restricted Drivers tool install the correct package in Ubuntu? That should be the first thing to try (in Kubuntu it didn't work).

---

### Post by PmDematagoda on 2008-02-14
> **samwyse said:**
> Does Envy update the driver after kernel updates? I'm not sure I'd recommend it over the nvidia-glx packages. Doesn't the Restricted Drivers tool install the correct package in Ubuntu? That should be the first thing to try (in Kubuntu it didn't work).

No it does not unless the nvidia-glx packages are updated at the same time, in any case it is useful if you learn how to compile and install the Nvidia driver manually since it can help a lot in such situations as the one currently under discussion.

Edit:- And it does not matter if you use the nvidia-glx packages or the Restricted Drivers Manager since they are both the same.

---

### Post by burntphoenix_7 on 2008-02-15
Ok! I am willing to try! hit me with your suggestions. I can't install envy as it says that dependency not satisfiable: xserver-xorg. OH and it hasn't been 22 hours, I have trying to fix this for 5 days now.

---

### Post by PmDematagoda on 2008-02-15
Open a modules file for editing using:-
```
sudo nano /etc/default/linux-restricted-modules-common
```

Then edit the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```

Save the file and then reinstall the driver one more time, then see if the driver works.

---

### Post by burntphoenix_7 on 2008-02-16
OK! so that seems to have had worked but now when I select extra desktop effects everything goes fine but I can't use the jelly effect and also I am limited to only 2 workspaces. I can't change them. I set the value of columns at 4 but they stay at 2. Any help on this?

---

### Post by jellybaby on 2008-02-17
Hi! I had a similar problem with my GeForce FX 5200 AGP. After days of installing drivers with apt, synaptic, add/remove, envy, run-files from nvidia, and lots of editing of xorg.conf still I never got more than 800x600 (generic vesa driver) and constantly had to click away the screen telling me that my card and monitor could not be recognized. I finally got everything working: I used envy to *uninstall* the nvidia drivers. After a reboot I used envy again to install the drivers; another reboot and everything's fine. Can't tell you why this worked, but at this stage, I'm just happy it did.
(VIA K8T Neo2, Athlon 64, SATA HDD, GeForce FX 5200 AGP)

Regards

---

### Post by burntphoenix_7 on 2008-02-17
Yeah! Envy doesn't work for me and the previous solution worked but now I can't use wobbly windows, Compiz-config-settings-manager and 3 or more workspaces. Any help?

---

### Post by Cavanagh on 2008-02-19
Thanks alot PmDematagoda!

I've been having this problem for about a week now, and that solution fixed everything for me.

---

