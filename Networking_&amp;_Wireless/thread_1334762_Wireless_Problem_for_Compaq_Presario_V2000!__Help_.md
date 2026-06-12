---
title: "Wireless Problem for Compaq Presario V2000!  Help needed :)"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by BonnyJ on 2009-11-22
Hey all, just signed up to this here forum for all your wise help and solutions!  

The laptop model in which I run Ubuntu (dualboots with XP)is a Compaq Presario V2000, and specs are: 
1.79 GHz
Processor 3000+
1.12 GB of RAM
Mobile AMD Sempron
60 GB of Harddrive space

So, I installed Ubuntu about a week ago, upon request of a friend who said it would be a welcome change to an old laptop.  I had been meaning to do something about the OS, I am currently typing this from XP (I installed Ubuntu in the way I can dualboot it at start up) as the wireless works and picks up signals.

**Now, to the problem**:  My wireless does not detect any connections.  In fact, I don't think it's even turned on during Ubuntu.  I have a button I can press to turn on the wireless.  By nature, it is on and lit up.  After starting Ubuntu, there is no light from the button nor does it respond after being pressed.

So far, I think Ubuntu is great, although I can't really do much with it without internet access and get more software and what not.  I'd much rather use Ubuntu than XP, as it seems to be faster and more lightweight.  I've googled the problem and found threads revolving around the same issue with this laptop and Ubuntu, but problem is, I'm not exactly computer literate.  I know some terminology, but nothing too advanced.  I tried inputting some terminal commands and found out that I have a Broadcom wireless card.  Hopefully that helps!

Thanks so much in advance!

---

### Post by BonnyJ on 2009-11-26
Does anyone have a fix?

---

### Post by coffeecat on 2009-11-26
> **BonnyJ said:**
> I have a Broadcom wireless card.  Hopefully that helps!

Thanks so much in advance!

I have no direct experience of Broadcom, but from what I have read in other threads, the firmware for Broadcom can't be included in a default install because of licensing issues.

Can you connect the laptop to the router with an ethernet cable for the time being? If you can do this, the network should connect automatically. Go to System > Administration > Update Manager and click on 'check'. It will download the package metadata. Don't install the updates just yet, but close Update Manager and go to System > Administration > Hardware Drivers. Is it showing anything for your Broadcom device? If so, click on 'activate' and it will download whatever is necessary and probably prompt you to reboot.

Now reboot without the ethernet card. When you get to the desktop, click on the network manager icon top right (next to sound icon). Do you see your network? If you do, click on it, put in your passkey where prompted and - hopefully - you should be good to go.

I'm sorry that no one picked up your thread. There are plenty of members here who seem to be knowledgeable about Broadcom. If my suggestion doesn't work, keep bumping your thread and someone should respond.

---

### Post by coffeecat on 2009-11-26
Would you believe? I'd bookmarked a useful post and forgotten about it. :rolleyes:

Have a look here:

[http://ubuntuforums.org/showpost.php?p=8371562&postcount=3](http://ubuntuforums.org/showpost.php?p=8371562&postcount=3)

I'll explain. The b43-fwcutter package is used to get the proprietary firmware. If you want to try that first, plug in your machine with an ethernet cable as before, but don't go to Update Manager. Instead, open System > Administration > Synaptic and click 'Reload' (same as 'check' in UM). Now look for and install b43-fwcutter. I don't know what happens next, but if that doesn't work now check Hardware Drivers which, according to that post, will install the STA driver. (Close Synaptic before opening Hardware Drivers.) The comment that poster makes about the minor issue only applies if you also have a Broadcom wired network device. If you are not sure, open a terminal and post the output of:

```
lspci
```

---

