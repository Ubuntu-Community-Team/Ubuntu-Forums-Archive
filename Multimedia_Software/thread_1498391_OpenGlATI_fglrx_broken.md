---
title: "OpenGl/ATI fglrx broken"
date: 2010-05-31
forum: Multimedia Software
---

### Post by Nebukadnezar II. on 2010-05-31
Hi there, community,

I haven't been working with any graphical applications since some weeks, but I have ran different updates etc. since. Now, today, I wanted to start Blender. It didn't work. Terminal told me the following:

```

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Compiled with Python version 2.6.5.
Checking for installed Python... got it!
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  27
  Current serial number in output stream:  27

```First, I saw that I seem to have some problem with sound support, but no matter, it would be more important for the moment to get Blender running, and that doesn't seem to stop it from working.
Interesting is this "X Error of failed request" and the following stuff.
In forum archives, I found some older threads concerning this, where it is described as a problem of graphics drivers and a common solution seemed to be reinstallation of drivers. So I downloaded a new version from ati/amd website, installation worked fine and didn't give any error messages, but it didn't work at all. The Blender error message kept the same. 
Other apps that I'd argue to use OpenGl, e.g. The Gimp(although I'm not exactly shure whether it uses OpenGl), did work though. 
So after that, I found that a look into System/Administration/Hardware Drivers might be interesting. There, it displayed that the ATI driver fglrx was not activated. I tried activating it, but my proxy settings prevented this tool to do it directly. 
So, I fired up Synaptic, installed the fglrx package and everything that comes with it and installed, which was actually successfull. Then, after a reboot, there still obviously was a working driver, since the computer still supported HD resolutions and everything it doesn't support directly after install, but the fglrx driver was not activated and Blender wasn't working anyway. After clicking Activate again in this Hardware Drivers window, it said that activation failed and that I might want to have a look into /var/log/jockey.log. There was:

```

2010-06-01 00:30:48,892 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-01 00:30:48,981 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-01 00:30:49,094 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-01 00:30:49,178 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-01 00:30:49,297 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-01 00:30:49,384 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-01 00:30:50,867 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-01 00:30:50,948 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-01 00:30:51,202 WARNING: modinfo for module fglrx failed: ERROR: modinfo: could not open /lib/modules/2.6.32-22-generic/kernel/drivers/char/drm/fglrx.ko: No such file or directory

2010-06-01 00:30:51,203 WARNING: /sys/module/fglrx/drivers does not exist, cannot rebind fglrx driver
2010-06-01 00:30:51,203 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-06-01 00:31:00,049 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-01 00:31:00,140 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-01 00:31:02,354 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-01 00:31:02,441 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-01 00:31:02,548 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-01 00:31:02,631 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-01 00:31:02,757 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches
2010-06-01 00:31:02,837 DEBUG: XorgDriverHandler(fglrx, fglrx, fglrx): xorg.conf driver matches

```I don't know too much about that. 
Another thing that I found was to check ```
hwinfo --gfxcard
``` for the driver output, which was:
```
  Driver Info #0:
    Driver Status: fglrx is not active
    Driver Activation Cmd: "modprobe fglrx"

```Obviously, fglrx isn't active, but modprobe fglrx resulted in 
```
FATAL: Could not open '/lib/modules/2.6.32-22-generic/kernel/drivers/char/drm/fglrx.ko': No such file or directory

```which is an error already occuring in jockey.log.
Now, few tests with reinstalling fglrx package or the driver directly from ATI/AMD website didn't bring any better results than what is already posted.

Has anyone any idea, what could be the reason?

Thanks in advance, 
Nebukadnezar II.

---

### Post by Nebukadnezar II. on 2010-05-31
Oh, and I forgot, if that is of any interest: I'm running Ubuntu 10.04 Lucid Lynx on 64 Bit, with a HD 5870 Graphics Card.

---

### Post by Nebukadnezar II. on 2010-06-02
Well, I just did a complete reinstall of Ubuntu from scratch on another HDD. I installed most parts of the usual software I used on my other system(e.g. Gmusicbrowser, pidgin etc.) and the UbuntuStudio packages and copied the home folder I had on my other HD to the new installation. And actually, it doesn't work again. But this time, it's different. The installed Blender 2.49 won't start with the same error message, other apps using gtk will(I tried yo frankie! and a binary download of blender 2.5), but extremely slowly. Yo Frankie! is a not too demanding game, but it runs with about 6 to 8 FPS in lowest settings on a computer with a HD 5870 graphics card. That just can't be right. 

So, how could this come? Seems as if some of the configurations in the home folder are damaging anything, or the software I installed else is...

Greetings,
Nebukadnezar II.

---

