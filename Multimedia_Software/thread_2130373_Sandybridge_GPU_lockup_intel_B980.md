---
title: "Sandybridge GPU lockup intel B980"
date: 2013-03-29
forum: Multimedia Software
---

### Post by rpaco on 2013-03-29
12.04 Precise 3.5.0-26 generic 64 bit with Gnome classic on Zoostorm Style Note 8GB mem 500GB hd Intel B980 Sandybridge.

At random time from boot, (including login page on one occasion) I am getting a display freeze. This often but not always unfreezes itself within 30sec. Sometimes though, a hard reboot is the only way out. 

Usually but not always an error report window appears asking if I want to submit details. (options: cancel or continue) If I hit continue a report box opens and it takes another minute or longer to generate a report in the window. This window is not copyable. Additionally another window opens asking if I know what to do, with 5 options, all of which eventually derogate to Ubuntu support front page. It also says that a report will not be sent to Launchpad since Precise is no longer in development. 

Picked from the report I see the words "Crash" "Sandybridge" "GPU lockup"

Sometimes the error report appears without a "noticeable" screen freeze, but it may just be too quick to see. 

This started about 6 days ago after a routine update. (No I don't remember what was updated) 

There are several reports of this or similar on launchpad all claiming to be solved  but they are mostly dated over a year ago. This is a new problem. I think it is more to do with a recent  update, I would guess to the video drivers or xorg.

 I have tried both going back  to a previous version kernel (-24) and re-installing the xorg intel drivers  but to no difference (xorg was probably already updated in the repository so I probably re-installed the same version)

If this has been solved please point me. 

I have also tried adding lines to grub as follows and hashing then out again since they had no effect on the problem;
<
#mod to try and stop freeze [http://ubuntuforums.org/showthread.php?#t=1999543&highlight=GPU+lockup](http://ubuntuforums.org/showthread.php?#t=1999543&highlight=GPU+lockup)
#quiet splash pcie_aspm=force acpi=noirq i915.i915_enable_rc6=1

#Second attempt to stop lockup
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.semaphores=0"
# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter #to Linux
#GRUB_DISABLE_LINUX_UUID=true
>
From Launchpad I have also tried the lines:
<
apt-add-repository ppa:brian-rogers/graphics-fixes
apt-add-repository ppa:glasen/855gm-fix
apt-add-repository ppa:glasen/intel-driver
apt-get udate
>
However nothing had any effect, actually the  Brian Rogers ppa was 404.

Have I fiddled with the kernel? Yes, each time there is a new kernel version I have to rebuild it to include the Realtek wireless/bluetooth drivers. BUT it was all working fine until a few days back. 

In the words of Sheldor rpaco AFK.

---

### Post by TheElfinGuy on 2013-03-29
I'm having the same problem on 12.10 64-Bit on the Acer Aspire V3 731-4473 with Intel Pentium B960.. I'm digging for a solution. I'll try what you have tried and see if I get any effect.

---

