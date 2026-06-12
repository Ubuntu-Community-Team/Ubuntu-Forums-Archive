---
title: "Procedure to get videocam driver support for Skyp doesn't work in 64-bit Ubuntu 14.04"
date: 2015-05-04
forum: Multimedia Software
---

### Post by jurgen-manycolored on 2015-05-04
In trying to make the videocam (Logitech 9000) driver compatible with V4L1, several suggestions were made to provide an executable file to do this and get the webcam working in Skype 4.3 (Ubuntu 14.04 64-bit) and place one of the following in the file:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so /usr/bin/skype
 
#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l2convert.so /usr/bin/skype

#!'bin/bash
Exec=env PULSE_LATENCY_MSEC=60 LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype %U

MultiArch support was enabled and my .Skype directory in my home directory was removed to prevent any override by it when Skype ran. I went to the proper repository to install Skype 4.3, which is supposed to proved the 32-bit support. I also tried downloading it separately and then installing Skype.

However, lib32 does not exist; i386-linux-gnu does not exist; libv4l, v4l1compat.so, libv4l1, and v412convert.so are all in my x86-64 directories, so no path is found using the executable file.

I followed very closely the recommended install procedures for Skype 4.3, and tried a few other approaches. The fact that these files do not exist in 32-bit directories on my system has left me befuddled. I can't quite figure out how others got their webcams running in Skype.  Does anyone have any suggestions? 

I hate the goddamn program, but my sweetie in Japan has it, so I have to try and use it.  I do get audio if I just install it straight up without trying to make the video driver compatible.  I have no idea if this conversion approach will work, as Skype shows me the camera works but no video out.

---

### Post by blm-ubunet on 2015-05-05
You did run both of these commands to enable multiarch for i386 ?
```
# dpkg --add-architecture i386
# apt-get update
```

This web page has some more clues:
[https://wiki.debian.org/skype](https://wiki.debian.org/skype)
"If **Enable Skype Video** is disabled when Skype starts it will never find your webcam.."

---

### Post by jurgen-manycolored on 2015-05-07
Here is what I did, in a clearer fashion:

I have a logitech quickcam pro 9000 installed on my system, which is 64-bit Ubuntu Trusty, and I installed Skype 4.3  First I enabled multiarch, updated aptitude, and since Skype uses v4l driver, and my camera uses a v4l2 driver, I have no video out but I see it in preview mode on Skype.

The recommended procedure(s) to fix this problem in order to make Skype compatible with the camera, is to install libv4l-0:i386 amd libv4lconvert0:i386 which create the libv4l directory and the only two packages in the directory:  v4l1compat.so and v4l2convert.so

Then you create a file /usr/local/bin/skype  and insert either the lines

    !#/bin/bash 
    LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so or

    !#/bin/bash
    LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so

save the file, and make it executable with

    sudo chmod a+x /usr/local/bin/skype

Then reboot, start Skype and the video is supposed to work.  It doesn't.  At this point I don't know how to proceed.  Any suggestions?

---

### Post by jurgen-manycolored on 2015-05-07
And yes, Skype video is enable and set to start automatically when I make a call.

---

### Post by blm-ubunet on 2015-05-07
I've never used Skype so this is guesswork.

You have installed the "lib32-v4l-utils" package ?

If you are seeing something in preview mode does this not suggest some other setting is wrong ?
Are there options for video compression/encoding or output rendering?
Maybe Skype does not like the video rendering method used by graphics driver or the composite manager?
Does Skype allow use in window &/or full screen ?

Try adding this to your cmdline or script:
```
XLIB_SKIP_ARGB_VISUALS=1 
```

---

### Post by jurgen-manycolored on 2015-05-08
I believe the libv4l utils are loaded with the libvl4-0:i386 files, since the I listed the conversion packages for you; they were the ones used by people who were successful in getting their camera to work.  I will add that line and try it, but the problem is that the video does not start at all; that line would not seem to address the problem. Thanks for your efforts.  I'll let you know.

---

### Post by jurgen-manycolored on 2015-05-08
lib32-v4l-utils is not a package in the trusty repositories.  With that line added, the
video starts (or attempts to) when I start the phone call, which I suppose is an improvement, but does not work.  Video works in Skype preview. Skype works in fullscreen or small window. There are options for compression with a Ubuntu utility, but the problem is that I get zero video, and the libraries I put in my script file are supposed to make Skype compatible with a camera using a v4l2 driver, but don't. I would assume if Skype had a problem with my graphics output it would show me some sort of distorted or choppy video but it shows nothing out.

---

### Post by blm-ubunet on 2015-05-08
Yes, lib32-v4l-utils package disappeared in trusty with multi-arch support in v4l-utils etc.

I think it is likely the video preview window is just a slideshow of bitmaps/images not a surface for video rendering.
Doesn't mean video rendering is not an issue.

A possible solution (and more secure/sandboxed) could be to install 32 bit ubuntu into virtual machine (e..g. virtualbox) & install Skype in that 32bit environment.
This would require the webcam to be made available to virtual machine. May not be possible.

---

