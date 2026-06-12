---
title: "Hardy+nvidia - not working through reboot"
date: 2008-05-07
forum: Multimedia Software
---

### Post by Xiong Chiamiov on 2008-05-07
I know that the forums are full of this, but I haven't been able to find anything to get me to a complete solution yet.  Standard "upgraded to Hardy, now nvidia driver doesn't let me boot into X" problem.

When running nvidia-xconfig or in any way enabling the nvidia driver, X would not start.  After removing the nvidia-glx-new package and installing from the file from nvidia's site, I can run startx just fine and everything's dandy.  Problem is, it no longer works when I reboot, and I have to reinstall the driver.  I've tried stopping kdm first and relinking the gcc, g++ and cpp symlinks to the 4.1 versions (instead of 4.2), since the installer warned me about using a different version than my kernal was compiled with.  Neither of those has worked.  I've also tried installing nvidia-glx immediately afterwards, to no avail.

EDIT: BTW, envy doesn't work either.

EDIT2: Someone on IRC told me to add nvidia to my /etc/modules list, but that also failed to produce the desired effect.

---

### Post by Xiong Chiamiov on 2008-05-07
bump

---

### Post by briandu on 2008-05-08
use this link
[http://ubuntuforums.org/showthread.php?p=4908847&posted=1#post4908847](http://ubuntuforums.org/showthread.php?p=4908847&posted=1#post4908847)

---

### Post by Xiong Chiamiov on 2008-05-08
Thank you.  However, you'll notice by reading my post that, aside from deleting the restricted modules directly (which did not help, btw), those were the steps I had already taken.  Of course, since I'm using Kubuntu, I stopped kdm, rather than gdm, but that is an insignificant detail.

---

### Post by Xiong Chiamiov on 2008-05-09
bump.

Thinking about filing something on launchpad.

---

### Post by Xiong Chiamiov on 2008-05-11
one last bump.

---

### Post by Xizorbg on 2008-05-11
X-

Same problem here.  Got it working thru restarting X - but system still asks me to restart and poof!  away goes my logo, res, and rotation.

Certainly count me in for any resolutions.

BTW, I am using amd64 ver.

Take care,
X

---

### Post by itsjustarumour on 2008-05-11
Same here on 32-bit.

Whats going on????

---

### Post by Xiong Chiamiov on 2008-05-12
Well, at least I know it's not just me.  I'll broaden my searches to see what I can dig up.

---

### Post by itsjustarumour on 2008-05-12
> **Xiong Chiamiov said:**
> Well, at least I know it's not just me.  I'll broaden my searches to see what I can dig up.

I was originally getting the same problems as you, but now I'm not sure what my problem is, although I did get a new monitor 2 days ago with a 1920x1200 resolution instead of 1600x1200. The new monitor wasn't properly recognised by Ubuntu, and it was whilst I was "fiddling" to try and get the resolution and refresh rate etc configured correctly that I "broke" my system.  Right now, I only have 800x600 resolution... I have a hunch its something to do with kernel modules but I've checked and compared this installation with another identical Hardy installation on another box, and according to Synaptic I have all the same packages installed.  The "Hardware Drivers - Configure 3rd party and proprietary hardware drivers" utility tells me that my Nvidia driver is now installed and in use, but I still can't find any screen resolution settings bigger than 800x600. I've also tried copying my xorg.conf from the correctly-working box to this one, but still no joy...

---

### Post by itsjustarumour on 2008-05-12
OK, I'm all sorted now.  Looks like the problem was my fault too - I'd inadvertently (it was late, I was tired  ;-)  ) installed an unnecessary kernel module which seems to have caused some kernel mayhem somewhere!

So what I did was make a list (from Synaptic) of all the packages installed on my identical working Hardy box, searching on the keywords "nvidia" and "kernel". Then I installed/uninstalled whatever was necessary on my problem Hardy box to match this.  Then I copied across my xorg.conf again, and after a couple of reboots and some more fiddling with screen resolution and hardware settings, everything is working fine again.  A bit of a long-winded way to go about things, but it got me there in the end.... :-)

---

### Post by itsjustarumour on 2008-05-12
> **Xiong Chiamiov said:**
> Well, at least I know it's not just me.  I'll broaden my searches to see what I can dig up.

OK, I spoke too soon  :-(  Been working for a couple of hours, rebooted and back to square 1 - minimum 640x480 resolution  :-(  What is going on?????

---

### Post by briandu on 2008-05-12
Use the following linbk:

[I][http://ubuntuforums.org/showthread.php?p=4908847&posted=1#post4908847](http://ubuntuforums.org/showthread.php?p=4908847&posted=1#post4908847) 			

it is still working after several days now  - no probs.
[/I]

---

### Post by itsjustarumour on 2008-05-12
> **briandu said:**
> Use the following linbk:

[I][http://ubuntuforums.org/showthread.php?p=4908847&posted=1#post4908847](http://ubuntuforums.org/showthread.php?p=4908847&posted=1#post4908847) 			

it is still working after several days now  - no probs.
[/I]

OK, downloaded the driver from the NVidia site and now all working OK again. Thanks Briandu.  :-)

---

### Post by Xizorbg on 2008-05-13
Dear X-

I have tried these gents' fixes -to no avail.  I will keep an eye out, too - let me know....

Does anyone know how to debug/troubleshoot the exact cause here?

Thanks,
X:)

---

### Post by Xiong Chiamiov on 2008-05-13
> **briandu said:**
> Use the following linbk:

[I][http://ubuntuforums.org/showthread.php?p=4908847&posted=1#post4908847](http://ubuntuforums.org/showthread.php?p=4908847&posted=1#post4908847) 			

it is still working after several days now  - no probs.
[/I]
That's actually the 2nd time your post has been linked to in this thread.  However, this time (it's like the 20th time reading it for me), I caught something from it:
> **briandu said:**
> 
downloaded the NVIDIA driver - I used 173.08 from the archives.

I remembered seeing that I was using 169.something, which made me curious.  If you take a look at the [Unix drivers page]("http://www.nvidia.com/object/unix.html"), it lists 169.12 as the latest version, which is what I had been using.  However, on [this page]("http://www.nvidia.com/object/linux_display_archive.html"), you can download 173.08, which is a beta version.  And guess what?  That one worked for me!  Amazing!

It probably has something to do with the last line in the release notes:
> 
Restored compatibility with recent Linux 2.6 kernels.


---

### Post by itsjustarumour on 2008-05-13
> **Xiong Chiamiov said:**
> That's actually the 2nd time your post has been linked to in this thread.  However, this time (it's like the 20th time reading it for me), I caught something from it:

I remembered seeing that I was using 169.something, which made me curious.  If you take a look at the [Unix drivers page]("http://www.nvidia.com/object/unix.html"), it lists 169.12 as the latest version, which is what I had been using.  However, on [this page]("http://www.nvidia.com/object/linux_display_archive.html"), you can download 173.08, which is a beta version.  And guess what?  That one worked for me!  Amazing!

It probably has something to do with the last line in the release notes:

Good to see you got that cleared up.  I was a bit wary of installing the 173.08 driver as it was described as "beta", but everything is still working fine so far as far as I can tell...

---

### Post by Xizorbg on 2008-05-13
I am using the 96._..driver as I have and older GeForce4 chipset.  Anyone been able to make this one work?

-X

---

### Post by Xiong Chiamiov on 2008-05-14
> **Xizorbg said:**
> I am using the 96._..driver as I have and older GeForce4 chipset.  Anyone been able to make this one work?

-X
Hmm, [that driver page]("http://www.nvidia.com/object/linux_display_x86_96.43.05.html") has the same "Improved compatibility with recent Linux 2.6 kernels." note.  That said, even though NVIDIA directs me to that page when I say I have a Geforce4 series card, I don't see any of those listed on the compatability page, since it seems to use the same page for all the drivers.  I don't suppose you've tried using a newer one?

---

### Post by itsjustarumour on 2008-05-16
> **itsjustarumour said:**
> Good to see you got that cleared up.  I was a bit wary of installing the 173.08 driver as it was described as "beta", but everything is still working fine so far as far as I can tell...

Spoke too soon, today's updates broke this for me again.  Back to stage one, 800x600... :-(

---

### Post by itsjustarumour on 2008-05-16
> **briandu said:**
> use this link
[http://ubuntuforums.org/showthread.php?p=4908847&posted=1#post4908847](http://ubuntuforums.org/showthread.php?p=4908847&posted=1#post4908847)

OK, I'm back up and running again. Although the how-to on the above link really should come with the warning:

******NOTE: With this method, your system will break again every time there is a kernel update and you will have to reinstall the driver again******

Considering that the NVidia driver worked perfectly for me 100% of the time in Gutsy, this seems like a shocking regression on the part of Hardy 8.04.  To be having to mess around reinstalling drivers and packages at the command line, not to mention that every time I do this it screws up my Compiz-Fusion and Screenlets, is a real hassle.  And I find it hard to believe that this is due to "a bug with the NVidia driver" as stated elsewhere on the forums when exactly the same drivers work perfectly in Gutsy. Its.... just shocking, really. :frown:

---

### Post by Xizorbg on 2008-05-16
Dear X-

I have not tried all the new drivers.  Does anyone have this consistenly working with the older chipsets and newer drivers?

Thanks alot,
X

---

### Post by Xiong Chiamiov on 2008-05-17
Well, I think they're working on my Xubuntu fileserver, which has an FX 5200 in it...  I don't remember having to do anything odd besides running some special options with nvidia-xconfig (I think that's the name?), but it's outputting solely through s-video to a tv, rather than a monitor.  I'll check later and see what driver it's running and get back to you.

---

### Post by Xiong Chiamiov on 2008-05-17
Ok, my Xubuntu machine has just the plain old nvidia-glx and nvidia-kernel-common packages installed (and in use), and it's working just fine (oddly enough, I couldn't get it to run on anything but vesa on Gutsy).  [Here's]("http://pastebin.com/f2d315383") its xorg.conf.

---

### Post by Xizorbg on 2008-05-20
Dear X-

No go.  I am using a Ti4200 GeForce 4 card by ASUS that is just fine for what I need it for.  Any ideas on why the system wants me to reboot once I successfully install it only to go back to crashing?

Thanks,
X

---

### Post by Xiong Chiamiov on 2008-05-21
> **Xizorbg said:**
> Dear X-

No go.  I am using a Ti4200 GeForce 4 card by ASUS that is just fine for what I need it for.  Any ideas on why the system wants me to reboot once I successfully install it only to go back to crashing?

Thanks,
X
Wait, the system tells you to reboot after installing the drivers?  That's odd.  For me, everything installed just fine and I was able to run startx and get into my desktop just fine - it was just when rebooting that X would fail to start.  What exactly is happening with you?  It could be related to something else, though there are too many weird things hapenning to know for sure what the cause of something is.  Did you have this working on an earlier version of *buntu?

---

