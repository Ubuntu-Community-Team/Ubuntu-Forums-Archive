---
title: "Ugraded from HardyHeron, and now Nvidia doesnt work"
date: 2008-07-02
forum: Multimedia Software
---

### Post by ccabal on 2008-07-02
I was using 7.10 quite happily, but I upgraded to Hardy Heron the other day, and when I did that, my Nvidia driver quit working.
I've done the upgrades whenever it asks me, so now I am currently at kernel 2.6.24-18-386.   My suspicion is that the latest kernel is incompatible with the latest Nvidia driver, but I have done google searches and have not found any other person seeing this an attributing it to the kernel version.

Here is what happens:  when I boot up, and gdm tries to start, it tells me its going to run in low-graphics mode. Well I try configure and that doesn't seem to do squat. I continue using low-res. graphics, and run nvidia-settings,and it says it "You do not appear to be using the NVIDIA X driver".  I try nvidia-xconfig as root, and that doesn't do jack.

Well I went to the NVIDIA site and downloaded the latest driver, killed GDM and ran the install script.  It doesnt find a precompiled kernel interface, cant find one at the nvidia site, and then tries to compile a kernel interface for my kernel.
Then I get an error:  "Unable to find the kernel source tree for the currently running kernel. blah blah blah.."
I've done apt-get install linux-source-2.6.24, and tried again and got the same result.  I then tried envyng, and that doesnt work either.

So now I am out of options.  Someone, please help me!!!!:confused:

---

### Post by kessaris on 2008-07-03
One thing I noticed before when I performed a kernel upgrade was that my nvidia drivers stopped working.

I think that the nvidia drivers are inserted as a module into the kernel and they are kernel-specific.

You might try reinstalling, or better yet uninstalling and reinstalling the nvidia drivers appropriate to your kernel.

I'm no expert unfortunately, but that's what I would do!

---

### Post by raf952 on 2008-07-03
I am running 8.04 for both i386 and AMD64 architectures with NVidia drivers working.

I don't recall the specific steps, but I believe that on one I needed to boot in recover/failsafe mode, reset the X windows configuration then re-enable the NVidia drivers through the System / Administration / Hardware Drivers menu.

I hope this helps.

raf

---

### Post by pcjunkie on 2008-07-03
I ran dpkg and system rescue from the boot menu. It mostly worked.

---

### Post by ccabal on 2008-07-03
I did some more experimenting around and searching, and yes I found out that the Nvidia drivers are very kernel version specific.  Down furthur in my grub list I found 2.6.24.16-generic, and booted using that and now it works.  So I set that as my default boot kernel and am OK now.  I guess I need to reject kernel upgrades more often,

---

### Post by kessaris on 2008-07-05
yea, there's always that option..

Usually I reject kernel upgrades unless I'm doing a clean install of some sort, like a new version.

---

