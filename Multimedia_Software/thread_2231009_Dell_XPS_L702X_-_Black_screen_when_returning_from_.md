---
title: "Dell XPS L702X - Black screen when returning from suspend"
date: 2014-06-22
forum: Multimedia Software
---

### Post by padnoter on 2014-06-22
Hi,

I'm running 12.04 64bit on a Dell XPS L702X - this has a builtin Intel graphics and the GeForce GT550M card.

Occasionally when the pc returns from suspend I just get a blank screen with a mouse.. from the sound I know the applications have started (connected dings etc), but the screen doesn't display. All I can then do is the safe reboot I read about (ALT-Printscreen & R,E,I,S,U,B) - which works, but it is a pain having to restart & re-open all the apps & docs.

I've googled and found some ideas, but nervous about messing up the machine.... everything is running well apart from this every-now-and-again glitch, but would like to know if anyone can help? Not sure what logs to look at/upload when this problem happens?

On a separate note (or is it related?) I have installed bumblebee & can access both video cards - glxspheres64 & optirun glxspheres64. But when I run "Nvidia X Server Settings" it is completely blank i.e no rules, no profiles... should it be? And in System Settings>Details>Graphics the Driver is Unknown and Experience is Standard. Is that related?

Any help with the suspend issue or nvidia settings will be appreciated

thanks

---

### Post by padnoter on 2014-06-22
another piece of info.
In system settings>additional drivers (after the search)
I don't get any proprietary drivers listed...
no nvidia

---

### Post by Yellow Pasque on 2014-06-23
> But when I run "Nvidia X Server Settings" it is completely blank i.e no rules, no profiles... should it be? 
Did you run it using optirun?

> the Driver is Unknown and Experience is Standard. Is that related?
[https://bugs.launchpad.net/ubuntu/+bug/946620](https://bugs.launchpad.net/ubuntu/+bug/946620)

> I don't get any proprietary drivers listed...
There shouldn't be any listed for hybrid/Optimus graphics. If you installed the nvidia driver like you would on a non-hybrid GPU, it would bork the intel driver.

---

### Post by padnoter on 2014-06-24
Hi,
Thanks for reply.
No I didn't use optirun to start "Nvidia X Server Settings". I have just tried it with optirun, but it's still all empty.

I followed the bug info & my driver is now showing as; Intel Sandybridge Mobile. Thanks

I don't think I installed any nvidia driver - didn't the bumblebee install do that? (or maybe it was part of those instructions - that was a long time ago & I can't really remember).

My main problem is the black screen from suspend... which happens periodically, but enough to be a right pain!

---

### Post by Yellow Pasque on 2014-06-24
I see a few bug reports (though none with any answer/resolution) about suspend/resume on this model after installing bumblebee. Sometimes, suspend issues get fixed with a newer kernel and/or BIOS update, but often not...
> I don't think I installed any nvidia driver
Check:
```
optirun glxinfo
```

---

### Post by padnoter on 2014-06-24
yes optirun sees the nvidia.... doesn't mention a driver, but i'm assuming this is ok
[FONT=courier new]optirun glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: VirtualGL
server glx version string: 1.4
...
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GT 550M/PCIe/SSE2
OpenGL version string: 4.2.0 NVIDIA 304.116
OpenGL shading language version string: 4.20 NVIDIA via Cg compiler
[/FONT]...

as opposed to just
[FONT=courier new]glxinfo
name of display: :0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
...
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
...
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile 
OpenGL version string: 3.0 Mesa 9.0
OpenGL shading language version string: 1.30
...[/FONT]

---

### Post by padnoter on 2014-06-24
any ideas where & what logs I should look at the next time the suspend resume goes black & forces a reboot?
maybe that will help find an answer

---

### Post by Yellow Pasque on 2014-06-24
For nvidia-settings, have you tried:
```
optirun -b none nvidia-settings -c :8
```

> **padnoter said:**
> yes optirun sees the nvidia.... doesn't mention a driver
Actually, it does: NVIDIA 304.116

> any ideas where & what logs I should look at the next time the suspend resume goes black & forces a reboot?
[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

---

### Post by padnoter on 2014-06-24
yes i see that driver version in the output from the new command - it brings up the nvidia x server settings with lots of information, which i'm afraid i don't understand.... should i do something with it?

thanks for link on logs, i'll take a read... and wait for next black resume.

---

### Post by padnoter on 2014-07-01
got a blank screen yesterday after a resume..

in Xorg.log I found

[FONT=courier new][ 13226.757] (WW) intel(0): flip queue failed: Invalid argument
[ 13226.757] (WW) intel(0): Page flip failed: Invalid argument[/FONT]

- which when I googled, I found this bug; "Resume from suspend leaves me with black screen or a screen of the desktop before it suspended."
[URL="https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/966744"]https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/966744
[/URL]- but reading through it, it's supposed to be fixed.. and i couldn't find the other bug links, for some people saying it wasn't fixed!

I'm running;
uname -a
Linux xps-Dell-System-XPS-L702X 3.2.0-65-generic #98-Ubuntu SMP Wed Jun 11 20:27:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by padnoter on 2014-07-01
I've raised a bug - see what happens;
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1336227](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1336227)

---

