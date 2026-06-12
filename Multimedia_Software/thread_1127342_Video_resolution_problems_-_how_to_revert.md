---
title: "Video resolution problems - how to revert?"
date: 2009-04-16
forum: Multimedia Software
---

### Post by kronix_00 on 2009-04-16
Okay, I screwed up.  Short version:

(**1**) Sound and video working just find.  No problems.

(**2**) While attempting to get my PCI modem recognized, I installed a HSF modem driver from Linuxant ([here]("http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php")) as instructed by the output from ScanModem.  Synaptic informed me that I needed to install ALSA audio drivers ([here]("http://www.linuxant.com/alsa-driver/")).

(**3**) After doing so, all sound stopped working, and I got an error message informing me about problems with GStreamer plugins.  Following a lead from the forums ([here]("http://ubuntuforums.org/archive/index.php/t-615513.html")) I stupidly thought I knew what was going on, and followed the advice to do the following:

*sudo aptitude install linux-ubuntu-modules-2.6.22-14-386*

My kernel version (I think) is: 2.6.24_23_generic.  I suspect I've installed (and overwritten?) the wrong linux-ubuntu-modules files because...

(**4**) When I reboot, I get a warning that my video card is not recognized, and the resolution defaults to some low value.  I've tried selecting what (I thought was) my video card driver should be, but Ubuntu claims it's not compatible.

Help!  **How do I revert or undo an sudo apt install command?**  I don't think I want to **remove** the install (do I?), but I want to revert to whatever I overwrote... Alternatively, how do I get Ubuntu to figure out which video drivers I need?  It somehow managed this when I first installed the OS... can I tell it to auto-check again, ignoring any driver information I might have screwed up?

I'll worry about (correctly) troubleshooting the sound problems once I've recovered from my video mistake.

Thanks for your kind patience toward this Linux newbie.

---

### Post by kronix_00 on 2009-04-16
I guess I also need to verify what my **sudo aptitude install **command really was (ie, which linux-ubuntu-modules package I really installed) -- I may have been smart enough to try and match the kernel number, and got it wrong.  I just don't quite remember.  Can I check what the last install command was in some obscure log file?

---

### Post by kronix_00 on 2009-04-17
It appears I'm making things worse. :(  I attempted the following:

(1) **apt-get remove linux-ubuntu-modules-2.6.22-24-386**

I verified that this was the package I installed.  I figured if I could remove it, perhaps things would revert.  They did not.  In fact, even though Ubuntu told me the package was successfully removed, it still shows up on grub when I reboot.

(2) Using the 'lspci' command, I found my video card to be: **01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420] (rev a3)**

So, I tried downloading the drivers from nVidia Corp. The file was *NVIDIA-Linux-x86-96.43.11-pkg1.run*.  nVidia's website says to open a shell and type 'sh (filename)', but the install aborts and tells me I can't do that with Xserver running.

I logged in using the 'recovery mode' of my old kernel (pre-installing the blasted -386 package).  From there, I can get to a root prompt, but nVidia's package *still* aborts.

I'm at a loss -- changing video resolution settings hasn't helped, and I can't seem to install the correct drivers.  **Anyone have an idea of how to proceed?**

---

