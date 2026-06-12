---
title: "Ubuntu 13.04 HD playback slow and grainy"
date: 2013-09-04
forum: Multimedia Software
---

### Post by victor10 on 2013-09-04
I did my best to search over the forums for a solution to this problem but, unfortunately, I found none particularly useful.

I recently installed Ubuntu 13.04 in a computer that came with Windows 8, which was a hassle, and there were a couple of minor errors, and I don't know if that's the reason playback is so bad, as I had tried Ubuntu on other machines and everything was really great about it.

To the point now, I've tried using Totem, XBMC, VLC and Smplayer, all to no avail. My 720p and 1080p videos all look grainy, with some issues regarding audio (it sometimes falls out of sync) and it gets all choppy. I've tried some tweaks with the codecs that people in the forum said might help, but it didn't. I'm really confused about this, as Youtube HD streaming works really smooth and clear. Any help is much appreciated.

Specs: 
-Computer-
Processor        : 4x Intel(R) Core(TM) i3-2348M CPU @ 2.30GHz
Memory        : 3912MB
Operating System        : Ubuntu 13.04
-Display-
Resolution        : 1366x768 pixels
OpenGL Renderer        : Mesa DRI Intel(R) Sandybridge Mobile 
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HDA Intel PCH

---

### Post by Yellow Pasque on 2013-09-04
For Smplayer, what video output are you using? Intel GPU should work best with libva/VA-API.

Check output of vainfo:
```
sudo apt-get install vainfo
vainfo
```

---

### Post by victor10 on 2013-09-04
I ran vainfo and it gave me this:
> libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit



---

### Post by Yellow Pasque on 2013-09-04
Do you have i965-va-driver package installed?

---

### Post by victor10 on 2013-09-04
I'm not sure, how can I check?

---

### Post by victor10 on 2013-09-04
Sorry for double post.
I downloaded the drivers from the intel page, and proceeded to install, but the contents couldn't be unpackaged. There seemed to be an error with the old drivers, I uninstalled them and then I could install the new ones, which did make playback a lot better. Thanks for the help!

Edit:
The problem seems to have been solved only for 720p videos. The 1080p videos still look really choppy from time to time, and you can see the line where one segment of the frame looks dislodged.

---

### Post by Yellow Pasque on 2013-09-04
> I downloaded the drivers from the intel page, and proceeded to install,
Sigh... that's not what I said/meant... :\ I was asking about the i965-va-driver package (that's a libva backend, not an intel video driver). If you want to upgrade your drivers, you should use xorg-edgers PPA.

Check vainfo again:
```
sudo apt-get install i965-va-driver
vainfo
```

---

### Post by victor10 on 2013-09-04
Sorry, as you might have guessed, I'm not Ubuntu-savvy.

Ran vainfo and it came up with this:

libva: VA-API version 0.32.0
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/x86_64-linux-gnu/dri/i965_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA-API version: 0.32 (libva 1.0.15)
vainfo: Driver version: Intel i965 driver - 1.0.17
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :    VAEntrypointVLD
      VAProfileMPEG2Main              :    VAEntrypointVLD
      VAProfileH264Baseline           :    VAEntrypointVLD
      VAProfileH264Baseline           :    VAEntrypointEncSlice
      VAProfileH264Main               :    VAEntrypointVLD
      VAProfileH264Main               :    VAEntrypointEncSlice
      VAProfileH264High               :    VAEntrypointVLD
      VAProfileH264High               :    VAEntrypointEncSlice
      VAProfileVC1Simple              :    VAEntrypointVLD
      VAProfileVC1Main                :    VAEntrypointVLD
      VAProfileVC1Advanced            :    VAEntrypointVLD

---

