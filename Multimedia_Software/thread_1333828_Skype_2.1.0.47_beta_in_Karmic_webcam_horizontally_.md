---
title: "Skype 2.1.0.47 beta in Karmic: webcam horizontally flipped (not upside-down)"
date: 2009-11-21
forum: Multimedia Software
---

### Post by tereg on 2009-11-21
```
tereg@tereglap:~$ uname -a
Linux tereglap 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
``````

tereg@tereglap:~$ lsusb
<snip>
Bus 005 Device 004: ID 0c45:613c Microdia PC Camera (SN9C120)
<snip>

```I have this webcam connected to an IBM ThinkPad T61 laptop with a stock installation of Karmic.

```
tereg@tereglap:~$ lsmod | grep video
videodev               36736  1 gspca_main
v4l1_compat            14496  1 videodev
video                  19380  1 i915
output                  2780  1 video
``````
tereg@tereglap:~$ lsmod | grep gspca
gspca_sonixj           20796  0 
gspca_main             22812  1 gspca_sonixj
videodev               36736  1 gspca_main
```I had originally installed skype via direct download from skype's website, and I experienced the same symptoms described in this thread (the green staticky video when testing the webcam): [http://ubuntuforums.org/showthread.php?t=1306368](http://ubuntuforums.org/showthread.php?t=1306368)

I followed the workaround instructions to open skype using the compatibility layer provided by v4l1compat.so and was able to see a clear picture with my webcam.

/usr/bin/skype was the following:
```

#!/bin/sh

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so  /usr/bin/skype.real

```However the image was flipped horizontally/reversed (like a mirror). *(see attached image)*


I then realized I could have installed skype via the medibuntu repositories, so I uninstalled skype, then installed skype from the medibuntu repositories, which actually implements the same workaround that I tried before.  The results were the same after installation.

I also changed /usr/bin/skype to

```
#!/bin/sh

#LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so  /usr/bin/skype.real "$@"
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so  /usr/bin/skype.real "$@"
```But this also yielded the same behavior.

If I open any other application that uses the webcam without using the workaround (like VLC or cheese), the image is correct.  So, I know that displaying the image properly is possible.

I have this version of libv4l-0 installed
```
tereg@tereglap:~$ sudo apt-cache showpkg libv4l-0
Package: libv4l-0
Versions: 
0.6.0-1 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages) (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic_main_binary-i386_Packages
                  MD5: c482bc980808bd5f98fab3f1c2e9ab5e


Reverse Depends: 
  skype-static,libv4l-0
  skype,libv4l-0
  xawtv-plugins,libv4l-0 0.5.0
  vlc-nox,libv4l-0 0.5.0
  libpt-1.10.10-plugins-v4l2,libv4l-0 0.5.0
  came,libv4l-0 0.5.0
  amsn,libv4l-0 0.5.0
  libv4l-dev,libv4l-0 0.6.0-1
  libsane,libv4l-0 0.5.0
  libpt2.6.4-plugins,libv4l-0 0.5.0
  kopete,libv4l-0 0.5.0
  gstreamer0.10-plugins-good,libv4l-0 0.5.0
Dependencies: 
0.6.0-1 - libc6 (2 2.4) 
Provides: 
0.6.0-1 - 
Reverse Provides: 
```I also have a Logitech Quickcam E3500 (046d:09a4) on another computer that also has a stock installation of Karmic and the same version of Skype that I can confirm works correctly.  If I plug that webcam into the laptop and open Skype using the workaround method, the image is a mirrored image.  However, if I open skype like this:
```

tereg@tereglap:~$ /usr/bin/skype.real

```and bypass the workaround, the webcam displays the image correctly.

Because of this, I suspect that the culprit is libv4l, but I'm not really sure if it actually is or what steps to take next.

I have found posts and blog articles of uses who have the issue I'm having, but they are posts that have been appended to the end of other closely-related posts and which I can find no response or solution for.

Any help or assistance would be greatly appreciated.  Thanks. :)

---

### Post by tereg on 2009-11-23
*bump*

Can someone point me in the right direction as to what steps I can take from here?  I'm kind of stuck.  Is this question better suited at the skype Linux community forums?

One additional thing I have tried is running cheese in the following way from terminal

```

$LD_PRELOAD=/usr/lib/lib4vl/v4l1compat.so /usr/bin/cheese

```This displays the webcam image correctly

If I run skype in the following way from terminal immediately afterward

```

$LD_PRELOAD=/usr/lib/lib4vl/v4l1compat.so /usr/bin/skype.real

```the image in the video test box is mirrored.

If you need any additional information, I will be more than willing to provide it.  Thanks.

---

