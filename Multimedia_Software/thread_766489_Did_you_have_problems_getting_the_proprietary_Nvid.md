---
title: "Did you have problems getting the proprietary Nvidia drivers going in Hardy?"
date: 2008-04-25
forum: Multimedia Software
---

### Post by nirudha on 2008-04-25
Before going to video I do like to note that Hardy gave me no grief about the on board IDE controller, phew!

Anyway the first problem I had after finishing the install was that it wouldn't let me enable the Compiz Fusion effects. Each time I tried this in Appearance it would just give up.

In System->Administration->Hardware Drivers I had to disable the option to use proprietary NVIDIA drivers and then after a restart enable them again. Bad QA it seems. Oh and the update and driver downloads took ages and for awhile I thought it wasn't going to do anything! Looks like a LOT of people have just upgraded to Hardy and are hitting the servers quite hard.

In the end I opted to download the beta driver from NVIDIA itself and install it.

This required me to install the build-essentials package (though Linux headers were already installed.) The installation didn't work until I removed the nvidia-glx-new and nvidia-kernal packages via synaptic (the add remove programs equivalent) and added NV to the list of blocked restricted modules in /etc/default/linux-restricted-modules-common. Perhaps the bullet-proof X feature which auto detects stuff kept trying to switch to the built in NVIDIA driver...

What I really want to know is did you have similar issues or was it smooth sailing?

p.s. I didn't see the pulseaudio app which lets me set per app/stream volume levels.

---

### Post by kpkeerthi on 2008-04-25
No. All I just had to enable the driver under System -> Admin -> Hardware Drivers and I was all set after a reboot. 

I then installed nvidia-settings, so I can tweak color settings for my LCD.
```
sudo aptitude install nvidia-settings
```

---

### Post by Hugolp on 2008-04-25
Yes a lot of people are having similar problems. Seems a lot of Nvidias are not working with Hardy. Check here: [http://ph.ubuntuforums.com/showthread.php?p=4789708](http://ph.ubuntuforums.com/showthread.php?p=4789708)

I tryed to install the propietary drivers but did not work.

Hugo

---

### Post by tekuro on 2008-04-25
i have a geforce3, its old yes, but still, it should be more than fast enough for some internet browsing. I have enabled propriety drivers and rebooted, it sais that everything is ok, but it is not. I can feel it that i have no hardware acceleration. please advise

---

### Post by wobster on 2008-04-25
Got problems here. I'm running plain metacity now. Which is more than unfortunate in a multi-monitor setup. (gf 8600GT)

---

### Post by lancern on 2008-04-25
Im out of cds so I used update manager to upgrade to Xubuntu 8.04 and after reboot I got the little pop up saying resticted drivers installed and in use..My vid card is GF FX 5200
and all is working for me..I dont use fusion but all my wine games and stuff work fine:)

---

### Post by J Brian Slinger on 2008-04-25
:(
Yes, but I have a different problem. 

My problem is that my dual core AMD 64 machine with built-in Geforce 6100  will only give 800X600 or 640X400 pixel displays (@ 61 Hz). I want to use 1280X1024@61. I do not mind the absence of acceleration since I do not play games. Previously, with Gutsy, I got the required display without using the nvidia driver.

"System/Administration/Hardware Drivers" shows that 'nvidia_new' is enabled but 'Not in Use'. I cannot find any graphical tool to adjust the display.

I tried "lsmod | grep nvidia_new". Only got a blank response. 

I would be very grateful for help.
Regards

---

### Post by Fire_Chief on 2008-04-25
J Brian...
You could try```
sudo dpkg-reconfigure xserver-xorg
sudo nvidia-xconfig

```Then reboot and run Nvidia-X-Settings control panel (found in System -> Administration) to adjust your display. If you don't have the control panel, install it with```
sudo apt-get install nvidia-settings
```

Cheers!

---

### Post by rotten777 on 2008-04-25
I had huge problems. I used lynx to go to nvidia.com and download it and install it that way. That's the only way I got it fix. nvidia-xconfig didn't work as it only let me go up to 640x480

---

### Post by Enlitend on 2008-04-25
Hi,
I just did a fresh install of Hardy 64bit last night. It all went flawlessly and upon reboot it automatically detected my nv 8800gt and set the resolution correctly to my monitor's native resolution. 

A quick check in the "Hardware Drivers" shows that the the restricted driver is enabled but the Status is "not in use". Next thing I do is grabbed the EnvyNg and download the the latest Nvidia driver and it's all good to go. Not a problem at all.

---

### Post by sloggerkhan on 2008-04-25
I just enabled restricted drivers and was fine. However, I was rather annoyed that doesn't include nvidia settings with the driver install, so I had to install nvidia setting separately and tweaka couple of things.

---

### Post by flower71 on 2008-04-25
I had the "640x480" problem when I tried using the Restricted Drivers Manager; after a couple weeks of trying various things, I turned it off in Restricted Drivers Manager, installed EnvyNG through Synaptic, tweaked with nvidia-xsettings, and it's been smooth sailing ever since.

In my case, I did learn that my monitor is reporting bad EDID data and I think that's why the default behavior came up badly; x-server wasn't autodetecting what to do with it.  

The nvidia-xsettings added some values to the config file that enable my monitor to work with decent resolutions (alternately, copying my /etc/X11/xorg.conf file from Gutsy overrides the x-server autodetection and fixed the problems).  I'd rather be able to leave my config file minimal and let X do the autodetection, but until support for my monitor is fixed, this is the workaround.

You can read [this bug report]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760") to learn how to tell if you're having EDID problems, and if you are please file a bug so this can get fixed upstream!  (Don't just add comments to bug 194760, it's easier for developers if each monitor problem is kept separately.)

Here's the bug that I filed, I know for me the biggest deterrent was not wanting to figure out what to put in all the fields.  This may give you that head start you need:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/211098]("http://https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/211098")

Meghan

---

### Post by sloggerkhan on 2008-04-26
fyi, don't know if the has any bearing on your guy's problems, but ther are at least **2 different** nvidia **proprietary** driver packages in the repos. Maybe you have the wrong one of the two? Also, Envy is in the repos.

---

### Post by rturner on 2008-04-26
> **Fire_Chief said:**
> J Brian...
You could try```
sudo dpkg-reconfigure xserver-xorg
sudo nvidia-xconfig

```Then reboot and run Nvidia-X-Settings control panel (found in System -> Administration) to adjust your display. If you don't have the control panel, install it with```
sudo apt-get install nvidia-settings
```

Cheers!

This finally worked for me.  After clean-installing hardy, I had the similar problems others had with their Nvidia cards (I have a GeForce 6600). When enabling the restricted drivers, I could only get a lower screen resolution.  Trying various solutions I found in the forums, including envy, I usually ended up in total low-res mode, 640 x 480 and couldn't get out.  I reinstalled Hardy.  This time I ran the reconfigure Fire_Chief posted.  

The first time, in the configuration settings, I opted not to have it redetect my keyboard.  The result was another 640 x 480 mess.  I'm not sure if that was because I didn't re-detect the keyboard, or because I had the restricted drivers for the nvidia card un-ticked. The second time I ran it, I opted to re-detect the keyboard, ticked the restricted nvidia settings and after rebooting I came back up into the 1080 x whatever that had been the maximum I could achieve with the restricted nvidia drivers in Hardy.  But I went into the Nvidia-X-Settings and was able to set it up to a 1280 x 1040 that I need.  

Finally!  I couldn't do this back when I first tried the Hardy beta, and ended going back to Gutsy, thinking it was just "that's why they call it beta".  When the same problems came up in the 8.04 LTS version, I'm glad I found this post.

---

### Post by Fingers &amp; Thumbs on 2008-04-26
Unlike previous distros that prompted me automatically and directed itself, Hardy didn't. synaptic didn't offer any solution even through additional repositories, but everything I needed was under add/remove. so no more problems.

---

### Post by cogadh on 2008-04-26
Well, I've gone through four different clean installs (Ubuntu once, Kubuntu once and Kubuntu Remix twice) and they all seem to have the same problem. Even though the restricted driver is installed, enabled and in use, hardware acceleration and OpenGL shader support on my 7600 GS is completely missing. I have tried using both the built-in restricted drivers manager and I even bit the bullet and tried Envy for the first time. Nothing seems to correct the problem. I don't believe it is an install problem, because the driver is obviously installing correctly (or at least without errors). It seems more like some kind of configuration problem, but every configuration I have tried, both automatic and manually applied, do not fix the problem. This is the first Ubuntu version to give me any kind of serious problems with the video, and I've been using Ubuntu since Breezy.

---

### Post by cor2y on 2008-04-26
Its something to do with the monitor detection i believe, in the open source drivers in kernel -16 my monitor is correctly detected and setup, install the closed source drivers the monitor is listed as plug and play after reboot  and although the resolution and refresh rate are correct, the closed drivers show as installed but not in use setting it to the correct monitor results in a wonky screen that i have to fix by reconfiguring xorg. This only happens in the -16 kernel go back to -12 and the hardware drivers work.
The closed source drivers were working in the beta version of hardy with the -16 kernel although there was a HAL error for a few users.

---

### Post by Respen on 2008-04-26
> **nirudha said:**
> In the end I opted to download the beta driver from NVIDIA itself and install it.

This required me to install the build-essentials package (though Linux headers were already installed.) The installation didn't work until I removed the nvidia-glx-new and nvidia-kernal packages via synaptic (the add remove programs equivalent) and added NV to the list of blocked restricted modules in /etc/default/linux-restricted-modules-common. Perhaps the bullet-proof X feature which auto detects stuff kept trying to switch to the built in NVIDIA driver...

What I really want to know is did you have similar issues or was it smooth sailing?

Personally I prefer NVIDIA's driver, and I was reminded why yesterday.  I enabled the nvidia-glx-new driver for my card and it worked... okay.  It was noticeably sluggish, so I decided to go for NVIDIA's driver like I did in Feisty.  However, xorg would crash on boot up.  Once the driver was installed (post boot up) everything ran great.  Restarting would cause the crash again, and thus, a reinstall of the driver.

When I was to the point of smashing things, I found this post.  Editing my /etc/default/linux-restricted-modules-common file to block the repository video drivers fixed my problem.  So I would like to thank you for mentioning that file.

I suppose on boot up X kept trying to use a built-in video driver instead of NVIDIA's driver that I installed.  Anyway, now things work great! :D

---

### Post by Vinno on 2008-04-27
First install of Hardy, didnt go too well, it finished and was going to load up gnome display manager but it never showed up just the wallpaper of the install still for 15mins. Gave it a reboot, reinstalled in safe graphics mode.

Installed this time and went to the desktop, nvidia driver was installed but not in use. Didnt know how the heck to enable it so i just used envy installer instead. Works great.

---

### Post by Cuppa-Chino on 2008-04-27
3 days later still working on it, have tried literally everything. worst of all it was working up until last week, it was even working fine in the RC but something got bungled since then.

---

### Post by MatthewAPeters on 2008-05-03
Cross post: [HOW-TO: NVIDIA GeForce 6600GT with twinview in Hardy Heron]("http://ubuntuforums.org/showthread.php?t=780777")

I finally got my twinview on GeForce 6600GT working.  Hope this helps someone else!

---

### Post by satellite360 on 2008-05-04
Upgraded to 8.04 and have just swapped my old nvidia geforce 7300 for an 8800GT.  Running Compiz and it is working fine - no tweaking, it just works.

---

### Post by Twitch3z on 2008-05-05
I have tried most everything described here, and had no luck getting anything other than VESA on a 7600GT. The only thing I haven't done yet is "sudo dpkg-reconfigure xserver-xorg", which I'll try in the morning. I've been truly frustrated by this for a week.

---

