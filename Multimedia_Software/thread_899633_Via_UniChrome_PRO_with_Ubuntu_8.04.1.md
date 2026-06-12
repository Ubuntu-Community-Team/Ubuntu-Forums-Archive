---
title: "Via UniChrome PRO with Ubuntu 8.04.1"
date: 2008-08-24
forum: Multimedia Software
---

### Post by padlefot on 2008-08-24
I've been having huge issues on making this card work with Ubuntu 8.04.1, now i finally got it working, so I felt i should write down how.
This is basically a summary from a now closed thread.
(My lspci displays:
VGA compatible controller: VIA Technologies, Inc. UniChrome Pro IGP (rev 01))


Download drivers:
First, go to [http://linux.via.com.tw/support/downloadFiles.action]("http://linux.via.com.tw/support/downloadFiles.action") choose 'ubuntu', and download the right driver for your platform. 

To check what platform you have, use the command:
```
lshw
```
Download & extract the drivers, then run the install script (view readme file)

This worked perfectly for me, but I had to try two different drivers before i got it working because they both matched my platform. If you run into the same thing, remember to uninstall the first driver before you install another one.

The only problem I had after installing the drivers was that my computer hung up on me when i tried to play movies in VLC or Mplayer. They only seemed to want to run as root. To fix this I used the command:
```
chmod a+r /usr/lib/libGL.so.1.2.via_unichrome
```note that "libGL.so.1.2.via_unichrome" may have a different name depending on what driver you downloaded.

After doing this, Xorg booted in 1024x768 pixels, I changed it manually in xorg.conf, the "Change Resolution" window in ubuntu didnt want to give me any higher res, so i simply changed the screen section from:
```
Section "Screen"
        Monitor  "Monitor"
        SubSection "Display"
                Modes  "1024x768"
                Virtual 1024 768
                Depth  24
        EndSubSection
        Identifier      "Default Screen"
        Device          "Configured Video Device"
EndSection
```
to
```
Section "Screen"
        Monitor  "Monitor"
        SubSection "Display"
                Modes  "1280x1024"
                Virtual 1280 1024
                Depth  24
        EndSubSection
        Identifier      "Default Screen"
        Device          "Configured Video Device"
EndSection
```
then hit ctrl+alt+backspace to restard X.
This worked out fine.

The Readme file that came with the driver said it was possible to make Desktop Effects (compiz) work, but I've had no luck with this.
Anyways, I hope this is helpful to someone.

---

