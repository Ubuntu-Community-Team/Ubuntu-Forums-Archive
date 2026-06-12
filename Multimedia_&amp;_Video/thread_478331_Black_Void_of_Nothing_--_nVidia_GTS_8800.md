---
title: "Black Void of Nothing -- nVidia GTS 8800"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by MasterXandrex on 2007-06-19
All,

I have recently upgraded to Windows Vista... after about ten minutes I realized that I hated it and am now going back to XP/Ubuntu dual boot environment. I've never had Ubuntu running properly on this PC, here are the relevant specs:


Asus A8N32-SLI-DELUXE Socket 939 Motherboard
AMD Athlon 64 FX60 Socket 939 CPU
nVidia GTS 8800 Graphics Card
-- Connected to a 20" monitor native at 1400x1050

I have been trying to install the newest version of Ubuntu 64-bit on this machine and am having significant problems with the graphics. Firstly, the normal install CD will not work, I get a black screen. When I boot to the alternate CD, I am able to do a text based install but the normal boot (after instillation) results in a black screen. Only when booting into runlevel1 (recovery mode) am I able to get even a CLI.

So, I thought, install or update the graphics drivers... I have tried these methods to on avail:
1) Drivers directly from nVidia and custom compiled.
2) apt-get install nvidia-glx
3) apt-get install nvidia-glx-new
4) Envy

Future plans of action:
1) Get lighter fluid
2) Spray lighter fluid on the PC
3) Get lighter
4) Self explanatory...

From what I've read a lot of (potential) Ubuntu users are having problems with this. It would seem, again from what I have read, that Fedora work quite well with this setup, but I would rather not go to Fedora. Please! Someone help.

Thanks,

Xan

---

### Post by empthollow on 2007-06-19
with similar display problems i've had it's been an xorg.conf problem.  make sure 1400x1050 is in the screen section, also you could try specifying a lower vsyn or hsync in the monitor section.  it's probably that your monitor is not handling whatever resolution/sync rate xorg is using.

---

### Post by MasterXandrex on 2007-06-19
I have tried specifying different resolution as this does seem non-standard. Also, the sync rate specified is within my monitors range. I am at work and will post some more specifics when I get home.

Any other ideas?

Xan

---

### Post by timcredible on 2007-06-19
use the 32 bit version of ubuntu (after all, you use the 32 bit version of xp and vista).  and then it's easy to install the video driver - just check out [www.ubuntuguide.org](www.ubuntuguide.org).  the resolution is not a problem, just install the nvidia driver first.

---

### Post by MasterXandrex on 2007-06-19
A few issues here:

One, I bought a 64-bit PC... thus, I want a 64-bit operating system.
Two, I know how to install drivers under normal circumstances and have done so many times... these are NOT normal circumstances.
Three, I am having a technical problem with using Ubuntu with my machine and posted here for help installing the applicable version for my hardware; not to have someone suggest that I ignore half the capability of my PC.

Just because Microsoft Operating Systems are incapable of actually operating a 64-bit system well, doesn't mean Ubuntu should settle for the same flaw. You should be encouraging the use of Linux and thus a PC to its full potential, not telling users to just settle for what Microsoft deems the standard. Thank you for your time, but your response is unacceptable. [-X


Xan

---

### Post by heldal on 2007-06-21
Ubuntu's nvidia packages (nvidia-glx-new) is missing a x-server module (WFB) that is required to make the 8800-series GPUs work (check /var/log/Xorg.0.log). The missing file comes in the form of a shared library (pre-compiled .so) binary that is supplied by Nvidia. It is suprising that it hasn't yet been solved as it is a simple omission in packaging that was reported by several people while feisty still was in beta.  To make matters worse, feisty is juggling about 3 different versions of the driver with its own method to keep track of conflicting kernel modules between these versions. This creates additional problems for those who give up on feisty's packages and want to install the driver they find on nvidia.com instead... unless they follow specific instructions found elsewhere in this forum. 

The most future-proof solution wrt maintenance updates is imho to stick to the nvidia-glx-new package in feisty and extract the single missing file from the tarball (make sure you get the right version) available from nvidia.com.

---

### Post by skreiner on 2007-08-03
I have had similar problems. Not all have been solved, but the rest of my problems are running dual 8800's in SLI. 

I think the problem lies with multiple drivers being installed. There are instructions on how to install the nvidia drivers elsewhere. The key for me was to install the most recent drivers from the nvidia web site, these are the runs you want to be running.

In linux-restricted-module-common you must add:

DISABLED_MODULES="nv nvidiafb nvidia_new nvidia_legacy"

adding simply "nv" did not work. 

I hope this helps.

---

### Post by tseliot on 2007-08-03
> **UbuntuUser3859 said:**
> 
4) Envy
Did you try Envy's latest release?

---

