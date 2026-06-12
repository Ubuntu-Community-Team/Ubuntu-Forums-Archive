---
title: "Need help with usb wifi driver"
date: 2011-05-02
forum: Networking &amp; Wireless
---

### Post by ShatterPoints on 2011-05-02
Hi,


    My name is James I am a beginner with linux I downloaded and installed 11.04 on my pc. I don't have the ability to connect via hardwire so I tried connecting to my wireless network which did not work. So I went searching for the solution, and wouldn't you know it I have a linksys AE1000 adapter. I found the link everyone gives to fedora and ralink for the RT3572 driver. I downloaded the .zip and was wondering if anyone could help me with the configuration/ install of the driver. I have a general idea of what and how I need to do but am unsure of a few things. For instance I don't know if I should be concerned with unloading the blacklist modules, or how do to that and I am also unfamiliar with the make and install code.

here is the link for reference 

[http://forums.fedoraforum.org/showthread.php?t=244215](http://forums.fedoraforum.org/showthread.php?t=244215)

ps. can I make the changes to the .zip in windows and then install it in ubuntu?

thanks for any help.

---

### Post by chili555 on 2011-05-02
I don't think, in Ubuntu, you need to do this step:> Step 6) Create a modprobe.d config file to make sure the modules load. Should also blacklist other conflicting modules:
Code:

sudo su -c "echo -e 'alias ra0 rt3572sta\nblacklist rt2800usb' > /etc/modprobe.d/rt3572sta.conf"

I don't think you have to blacklist anything. I don't agree with this step; I think he made a typo:> sudo modprobe ra0He means:```
sudo modprobe rt3572sta
```Otherwise, the tutorial is solid.> ps. can I make the changes to the .zip in windows and then install it in ubuntu?I think it's a tar.gz file, not a zip. Do you have tar and sed in Windows? I think you can download the file in Windows and transfer it to Ubuntu. All the other steps are better done in Ubuntu, in my opinion.

Please open Applications > Synaptic and be sure you have installed build-essential and linux-headers-generic. I beleive, as of 11.04, they are installed by default (Yay!!!) but check to be sure. These two packages are required to compile.

I compiled this myself on my 11.04 machine a few minutes ago; it compiles with warnings but no errors.

---

### Post by ShatterPoints on 2011-05-02
I'm still having problems, I read that I need to have gcc-v and make-v or something but I cant even enter super user in my terminal. It asks for a password and then does not authenticate. Besides that I still cant perform the steps in the instructions. I'm not sure what to do right now...

---

### Post by chili555 on 2011-05-02
> I read that I need to have gcc-v and make-v or something They will be installed when you do as I suggested:> be sure you have installed build-essential and linux-headers-generic. > It asks for a password and then does not authenticate.The password doesn't show up, but its taken. Just type it and press Enter.> Besides that I still cant perform the steps in the instructions. Which step are you stuck on? I'll be happy to help.

Please check Private Messages at the top right of this forum.

---

