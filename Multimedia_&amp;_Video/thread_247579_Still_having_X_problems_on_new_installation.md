---
title: "Still having X problems on new installation"
date: 2006-08-30
forum: Multimedia &amp; Video
---

### Post by ekard14 on 2006-08-30
Hello,

Being somewhat new to Linux, I'm hoping these forums can help me get up and running so I can learn more. So here's my problem: 

A few months ago I installed Ubuntu 5.10 on my desktop. The installation went great but when I started up I got a "Failed to start the X server" error, exactly as described in the green notice on the homepage of these forums. I only had access to a command line at that point. I tried some troubleshooting at the time, but eventually gave up.

Earlier today I decided to take another shot. After doing some reading, I found the notice regarding the problems with the recent version of X server. Following the instructions (on this page: [http://www.ubuntu.com/FixForUpgradeIssue](http://www.ubuntu.com/FixForUpgradeIssue) and [http://www.ubuntuforums.org/showthread.php?t=241254)](http://www.ubuntuforums.org/showthread.php?t=241254)), I updated X server to no avail.

I decided to do a fresh install using 6.06. The installation was smooth and X started! Unfortunately, I have a widescreen monitor and my resolution was not available. I added a modeline to [FONT="Courier New"]/etc/X11/xorg.conf[/FONT] in an attempt to correct my resolution problem. After a reboot, though, I got the same "Failed to start the X server" error from before. In the output, it says, “Fatal server error: no screens found.” I've done an upgrade, but it appears I have the latest version of everything.

My graphics card: ATI Radeon X300 SE (128MB, PCI)
My monitor: Dell 2007WFP 1680x150

I’m thinking it might be a problem with my graphics card, but I’m pretty puzzled at this point. Any assistance would be greatly appreciated. Please tell me if I can provide any additional details that might help. Thanks!

---

### Post by huwshimi on 2006-08-30
The instructions that you have been following are for a specific X problem. What I suggest you do is go to a terminal and type:
```
sudo sudo dpkg-reconfigure xserver-xorg
```

Take specific note of the screen resolution section (you can probably just say yes to most other options).

If it still doesn't work then try:

```
sudo nano /etc/X11/xorg.conf
```
And go down to device and change the driver to "radeon". The device section should look something like this (depending on your card and options):
```

Section "Device"
        Identifier      "ATI Radeon X300 SE"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
EndSection
```
Now hopefully you should have X back. Post back and we'll have a look at getting your resolution working.

Cheers.

---

### Post by ekard14 on 2006-08-30
Thanks for the quick reply. You're soultion worked. I had tried reconfiguring X many times before and selecting my screen resolution, but it was changing the driver to "radeon" that did the trick. This had been set to "ati".

The only problem now is the my screen is shifted too far to the right and far right edge gets cut off, but I think I can figure out how to correct this.

Again thanks for your help. I will be posting here more often in the future.

---

### Post by huwshimi on 2006-08-30
No worries I'm glad to be able to help.

Cheers.

---

### Post by maxxum on 2006-09-01
Hi, I am new to linux and learning. I decided to keep Ubuntu after trying out many distros. I am having the same problem except that I haven't installed it yet, I am just trying to run it from the CD. 
I have a Dell 9150 Desktop (Core Duo, 1 GB, integrated Intel NIC, ATI Radeon X300 graphics) and a Dell 20 inch wide screen digital LCD monitor. I use DVI to connect it. Initially I would get "DVI-D: Cannot display mode" error from the monitor. But I could get past it and see the OS load when I chose 800x600 24 bit resolution. After loading everything, it failed to load the X server. 
I first tried reconfiguring it as you mentioned, and answered all questions keeping default values. It gave me a "screen not found" error. I tried your second solution, edited the xorg.conf to replace "ati" by "radeon". Now I get a different error - 
Fatal server error: AddScreen/ScreenInit failed for driver 0
XI): fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with o events remaining.

Is it because ekard14 had installed the OS and installed additional ATI drivers before editing xorg.conf that this worked for him?
Do you suggest I try installing it first? it is very strange since Knoppix liveCD works just fine. Thanks!

---

