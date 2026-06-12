---
title: "Unable to build the NVIDIA kernel module"
date: 2011-02-26
forum: Multimedia Software
---

### Post by molm on 2011-02-26
Hello all,

Ok, before i get a lot of annoyed responses, I did check the forum and found a couple older previous threads on this topic, but they don't seem to really explain any real solutions to the problem im having.

Here's the story- I was looking around for instructions and found this "howto guide" on installing nvidia display driver ([http://ubuntuforums.org/showthread.php?t=336412](http://ubuntuforums.org/showthread.php?t=336412)).

I went through the steps he listed: 
downloaded the driver packages, install the dependencies from the shell, 
and then i pressed CTRL+ALT+F2 to get out of X and into text mode. I stopped my gdm with the command:  sudo /etc/init.d/gdm stop
and then i tried to install the driver using: sudo sh (on my NVIDIA driver- his version was a bit outdated compared to the one I downloaded)

But here is where the problem starts, as I go through the installation process and click yes, i reach the "progress bar" then the screen says "unable to build the NVIDIA kernel module". and then it just exits. What is going on here? Am I missing some other package or file? 

ps. i Have the linux header package 2.6.35-25 installed as well as the generic one and the generic-pae

Thanks for any help

-molm

---

### Post by jlanawalt on 2011-04-30
For others running into this problem, try installing the nvidia-current module from a terminal window or the console and watch for the 'failed to build...missing kernel source' message. Then, don't take it literally and check if you have the right linux-headers. In my case I had the linux-headers-generic, but not linux-headers-generic-pae to match the installed generic-pae kernel.

---

