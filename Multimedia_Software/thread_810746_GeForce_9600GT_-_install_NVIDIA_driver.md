---
title: "GeForce 9600GT - install NVIDIA driver"
date: 2008-05-28
forum: Multimedia Software
---

### Post by yoghurt on 2008-05-28
Hi Guys,
I've seen the same question being discussed couple of times all over the boards, but I didn't want to add more confusion to somebody else's thread.

For starters; when installed the card to the PC and ran Ubuntu for the first time, it wouldn't start the GDM. From the 4-piece menu selected "automatically reconfigure X" (or something along those lines) and proceeded.

I could get into Xserver (using my screen's full resolution). I then wanted to make it all correct and wanted to install the Nvidia drivers for this card. All attempts have failed though

- downloaded the driver from NVIDIA's website
- Ctrl+Alt+F1
- stopped X-server (sudo /etc/init.d/gdm stop)
- executed the script

Nvidia installer said:

```

No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
```


I picked "yes". After some gibberish in the installation's log file, there's this:


```
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64' (169.12):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Would you like to run the nvidia-xconfig utility to automatically update you
   r X configuration file so that the NVIDIA X driver will be used when you res
   tart X?  Any pre-existing X configuration file will be backed up. (Answer: Y
   es)
-> Your X configuration file has been successfully updated.  Installation of
   the NVIDIA Accelerated Graphics Driver for Linux-x86_64 (version: 169.12) is
   now complete.

```

Unfortunately, when rebooted the PC, X-server failed to load and I had to copy some older xorg.conf over the nvidia one. Now it looks quite bare:

```

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

```

I was wondering if anyone would have some encouraging words what have I done wrong? One time during the driver's installation I was asked if I also wanted to install 32-bit OpenGL libraries (I'm running 64-bit Ubuntu Hardy Heron) so perhaps I shouldn't have done that.

PS: this xorg.conf has enabled me to run Ubuntu in my default screen resolution 1680 x 1050 and the Preferences -> screen resolution even displays the correct screen type (!).

Cheers...

---

### Post by briandu on 2008-05-28
Because I updated my PC the video went crazy so I followed this instructions to the letter and corrected it again.

[http://ubuntuforums.org/showthread.php?p=5064980#post5064980](http://ubuntuforums.org/showthread.php?p=5064980#post5064980) msg #430

Just follow step by step and yes let it create your x config.

Cheers.

---

### Post by yoghurt on 2008-05-29
That's pretty much the same what I did - except I didn't remove the older drivers first (thinking of it now; this MIGHT have been the problem).

Going to give it a go...will post the results here :)

---

### Post by yoghurt on 2008-05-29
So...followed Briandu's advice and:

- everything seemed to progress in the same way as yesterday
- I did check Nvidia's website and downloaded the new driver that was released just yesterday (May 28, 2008)
- was again notified by the Nvidia installer there are missing kernel modules and if I wanted to compile one <yes>

My /etc/X11/xorg.conf now looks:
```

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Which is kinda similar to yesterday. Furthermore, when I go to System -> Adminsitration -> Hardware drivers, I can't see any restricted drivers listed (and I believe Nvidia's drivers ARE restricted - or am I mistaken)?

Then I tried to set up the screen effects in System -> Preferences -> Appearances and visual Effects tab to "normal" (I had to have it to "none" before todays' try) and it worked(!).

So my only remaining question is whether the Nvidia drivers are restricted?

---

### Post by Artemis3 on 2008-05-29
> **yoghurt said:**
> 
Nvidia installer said:

```

No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site (ftp://download.nvidia.com)? (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.
```


I picked "yes".

You are not supposed to say yes there, and when you reach that state i'm not sure you'll be able to recover...

Oh never mind, it didn't found the kernel (phew).

Here is [my guide](http://ubuntuforums.org/showpost.php?p=4131809&postcount=9), it still works i guess.

---

### Post by yoghurt on 2008-06-04
I think most of these "guides" are pretty similar - the only difference I can see is the amount of stuff you remove before you actually run the installer.

I've noticed that couple of days ago, my ubuntu downloaded new kernel module (perhaps I'm mistaken though) so if I did this now then maybe the kernel module would already be present.

The only good thing about this "mess" with the drivers is that it teaches you something... :)

Thanks to all for their words of wisdom guys!

---

