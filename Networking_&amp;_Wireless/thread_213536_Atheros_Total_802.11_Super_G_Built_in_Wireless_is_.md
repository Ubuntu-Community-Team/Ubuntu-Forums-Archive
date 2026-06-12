---
title: "Atheros Total 802.11 Super G Built in Wireless is not recognized."
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by clyde9999 on 2006-07-11
I have a Toshiba A75-S206 with built in wireless ( Total 802.11 Super G ). For the past couple of months I have been using Kubuntu on it and it worked fine, however after the last update with Kubuntu, the wireless is not working there too. I can load the live CD and it will works just fine. I can reinstall it and it works also, until I install the updates! Anyway, I am trying to fix that problem with Kubuntu (with little or no success thus far). I have also installed Ubuntu on this computer, and the live CD can see the wireless network interface but does not recognize it. My question is this, How can I get Ubuntu to recognize my internal wireless card??? 

I will admit that I am a bit discouraged with this situation because of how I am being treated with Kubuntu “Help the new guy”. Here is the address of the forum results so far where I have been attempting to get help from Kubuntu if it will help any. [http://kubuntuforums.net/forums/index.php?topic=6745.0](http://kubuntuforums.net/forums/index.php?topic=6745.0)

Thanks in advance to anyone willing to help.:-k

---

### Post by clyde9999 on 2006-07-11
I also checked which module I have by going to termimal and typing "uname -r" then I looked to see if I could find this module in Synaptic and could not find it. You will need to read the link in order to undrstand why I looked for this module.

the "uname -r" on this computer is 2.6.15-26-386

the installed "MADWIFI" is 2.6.15-23-386. There is not a module available that matches the one installed on my computer, if this makes any sence to anyone willing to help. please!

---

### Post by tturrisi on 2006-07-11
install the restricted modules for your kernel.

---

### Post by clyde9999 on 2006-07-11
> **tturrisi said:**
> install the restricted modules for your kernel.

I already went to synaptic and made sure everything is enabled, and still, i do not see any modules for my kernel "2.6.15-26-386." I am really not sure what to do next. ](*,)

---

### Post by tturrisi on 2006-07-11
> **clyde9999 said:**
> I already went to synaptic and made sure everything is enabled, and still, i do not see any modules for my kernel "2.6.15-26-386." I am really not sure what to do next. ](*,)
how is it your using kernel 2.6.15.26-386?  Is it a backport or rool your own?  That kernel is not available via synaptic.

---

### Post by clyde9999 on 2006-07-11
I will be the first one to tell you that I am NEW at Linux. Please help me to understand what you want me to know, or what you want to know. I do not understand what you are talking about with Backport and Rool. all I did was type "uname -r" it told me 2.6.15-26-386 .. What did I do wrong?

---

### Post by clyde9999 on 2006-07-11
Here is more, I decided to restart and make sure to boot into the 2.6.15-23-386 kernel. Both the 2.6.15-26-386 and the 2.6.15-23-386 are available to boot into. After bootup, I was able to see the Atheros wireless, and am in working order. It works!!! My Desktop is working in Ubuntu, Now if I can get kubuntu working on this computer also, it would be great. I have both operating systems on this computer.

---

### Post by tturrisi on 2006-07-12
The reason it works is because you have the restricted moduled for the kernel you booted to.  Go to System/Administration/Synaptic/Base System (restricted) and locate the linux-restricted-modules-386 for your newest kernel (the kernel that when you boot currently does not load atheros drivers).  Install these, it should then work.

---

### Post by maxesanu on 2007-11-24
I have a Toshiba satellite A215-S4697 laptop and an Atheros wireless card with the AR5006EG chipset and I couldn't get it working with madwifi drivers although they say my chipset is supported. I tried everything, from installing restricted modules in Synaptic for my kernel version, to installing the latest version of madwifi-ng and my iwconfig still shows only:

lo no wireless extensions.

eth0 no wireless extensions.

However it used to work perfectly with ndiswrapper, but I need it in monitor mode and I can't set it with ndiswrapper. I have placed the ath_hal in disabled modules and I have placed ath_pci in modules, however I think they do not appear when I type the command which shows me the loaded modules (can't remember it right now).

There are a whole bunch of how to's on ubuntu forums about how to get virtually any Atheros based card to work, even the newest threads on madwifi site says that Atheros cards should just work in Ubuntu.

I was wondering if you or anyone else could write a detailed how to on now to get the Atheros AR5006EG card working in Ubuntu running on a Toshiba laptop using the native linux drivers, for complete dummies like me. I would like to mention that I have the x86-64 version of Ubuntu 7.10. Thank you in advance. I hope to get help on this one. I promise to try your advices on a fresh installation of Ubuntu, so you don't have to worry that I messed up something trying to fix it.

Cheers.

---

### Post by kevdog on 2007-11-24
Ok, you need to download and compile the madwifi drivers from source code from the madwifi website.  You need to compile it against the header files for your current kernel, since its specific to the kernel version you are using.  

Here is the website:
[http://madwifi.org/](http://madwifi.org/)

Please read their tutorial on how to start for beginners.  It might take you a while but it will definitely work.

---

### Post by maxesanu on 2007-11-24
I have already done that and many other things on at least 4 fresh installations of ubuntu/kubuntu and nothing. While ubuntu is loading, I get this message: WiFi%: Unable to attach hardware. Hardware version not supported (Hal status 13).

There is one more thing. In Windows my chipset is shown as AR5007EG, but windows drivers for this chipset did not work when I tried them with ndiswrapper, it said that the drover is invalid.  I had to trust Ubuntu, which said that the chipet is AR5006EG, and then I got my card working, but allow me to repeat myself, I can't set it in monitor mode this way. 

As for the instructions on madwifi.org, I followed them them EXACTLY they were shown there, step by step. They gave some errors during make, but I have followed some more thorough instructions which showed how to install a compiler and this time I had absolutely no errors on instalation, after rebooting I got the same error as above.

In lsmod I did not see any ath_pci module so I added it manualy in /etc/modules and I tried to boot with ath_hal in the /etc/default/linux-restricted-modules-common and without it added there, just to go by trial and error, but none worked for me. I tried downloading from madwifi snapshots the madwifi-ng, it installed with no errors, but no success.

Any more ideas? Imagine a fresh installation of Ubuntu, either 64 bit or 32 bit (i don't care anymore), imagine the ath_hal loaded by default after the instalation, imagine the madwifi.org steps not working for me, what else can I do? Please... Anyone? What are the steps to do it from scratch?

---

