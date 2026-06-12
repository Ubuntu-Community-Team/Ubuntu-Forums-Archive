---
title: "Jack Audio with Wine"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by slick1537 on 2007-03-01
Suppose this questions could go in a number of forums but basically I have been looking to setup starcraft on ubuntu.  I was able to install it with wine, however after going to winecfg it tells me I need to setup jacklib.so to use jack audio.  I tried using regular audio but it starts skipping and what not.  I tried installing jack from the the respritory and also tried to do it manually however none of the jack commands like jackd return anything besides command not found.  Wine returns these errors when I click on the audio tab in winecfg...

slick@Slick-Room:~$ wine winecfg
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

Please excuse me guys If I sound like a noob I am! :D

---

### Post by Amaroq on 2007-03-02
This topic helped me solve the jack problem. The rest of the errors are something else though.

[http://ubuntuforums.org/showthread.php?t=290871](http://ubuntuforums.org/showthread.php?t=290871)

---

### Post by Amaroq on 2007-03-04
Oh, to solve that seq one, just do the following:
```
sudo modprobe snd-seq
```

Not sure what good it even does though.

---

### Post by rybec on 2007-03-14
The xfree86-DRI error is a problem with the video configuration.  I was able to fix mine by adding these lines to the end of /etc/X11/xorg.conf:

Section "Extensions"
        Option "Composite" "Disable"
EndSection

I am not sure exactly how they helped, but it fixes an issue where Xorg uses the Mesa openGL drivers rather than those specifically designed for your video card.  I got this information from another forum.  It seems to have worked.

(If you are using an ATI Radeon, or FireGL card with the fglrx driver, you can run 'fglrxinfo' before, and after the changes.  It will tell you what openGL driver Xorg is using for it.  Don't forget to restart the X server after making the changes.)

---

### Post by rybec on 2007-03-14
Oh, I missed something.  To fix the Jack problem, if you have jack installed,
make a symbolic link named libjack.so to libjack-0.100.0.so.0:

sudo ln -s /usr/lib/libjack-0.100.0.so.0 /urs/lib/libjack.so

If you cd to /usr/lib, you can omit the paths, and just use the filenames.
It helps prevent mistakes.  (I put /etc/lib for the first path when I did it, and
created an invalid link.)

---

### Post by mwolfe on 2007-03-18
>  	Oh, I missed something. To fix the Jack problem, if you have jack installed,
make a symbolic link named libjack.so to libjack-0.100.0.so.0:

sudo ln -s /usr/lib/libjack-0.100.0.so.0 /urs/lib/libjack.so

If you cd to /usr/lib, you can omit the paths, and just use the filenames.
It helps prevent mistakes. (I put /etc/lib for the first path when I did it, and
created an invalid link.)

I believe the above has a typo, it should be
sudo ln -s /usr/lib/libjack-0.100.0.so.0 /usr/lib/libjack.so

I suppose most would figure that on there own but thought i would point out that it is
usr not urs

---

