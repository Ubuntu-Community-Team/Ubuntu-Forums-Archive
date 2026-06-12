---
title: "Can't Get w32codecs to Work."
date: 2007-10-14
forum: Multimedia &amp; Video
---

### Post by DM was on fire! on 2007-10-14
Holaaa. 
I put in the Medibuntu repository, apt-get updated and everything, and installed it according to the directions on Medibuntu's site.
I still can't play anything that's a .wmv/.wma/et cetera in Totem. Was I supposed to check something on Totem so it'll recognize them, or did I install them wrong or what?

(Oh, and when I type sudo apt-get install w32codecs I get "E: Invalid operation instal" as output)

---

### Post by carlinuxlearner on 2007-10-14
see the attached file on a post in this thread.
[http://ubuntuforums.org/showthread.php?p=3533133#post3533133](http://ubuntuforums.org/showthread.php?p=3533133#post3533133)

C@RL

---

### Post by kostkon on 2007-10-14
> **DM was on fire! said:**
> Holaaa. 
I put in the Medibuntu repository, apt-get updated and everything, and installed it according to the directions on Medibuntu's site.
I still can't play anything that's a .wmv/.wma/et cetera in Totem. Was I supposed to check something on Totem so it'll recognize them, or did I install them wrong or what?

(Oh, and when I type sudo apt-get install w32codecs I get "E: Invalid operation instal" as output)

First of all, check if you have the package installed
```
dpkg -s w32codecs
```

Furthermore, did you follow [the instructions from the ubuntu documentation]("https://help.ubuntu.com/community/Medibuntu") in full? Did you add the key?

According to the error you get, it seems that you have a typo in the command you give. Do you give the right command in the terminal, like this
```
sudo apt-get install w32codecs
```

In my case, with *w32codecs* installed, I am able to playback with Totem wma and many other proprietary media formats.

---

### Post by DM was on fire! on 2007-10-15
I must've entered the wrong command for sudo apt-get (which is strange. o_o), but here's the response I got from the dpkg command:

> "Package: w32codecs
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 33580
Maintainer: The Medibuntu Team <medibuntu@sos-sts.com>
Architecture: i386
Version: 20061022-0medibuntu1
Replaces: libaviplay (<= 0.50-0.3), divx-codecs
Depends: libc6 (>= 2.3.4-1), libstdc++5 (>= 1:3.3.4-1)
Suggests: mplayer, gstreamer0.10-pitfdll
Conflicts: libaviplay (<= 0.50-0.3), divx-codecs, w32codecs-lite, qt6codecs
Description: Win32 codec binaries
 This package contains Win32 codec binaries, required for the
 decompression of video formats that have no open source
 alternative.
 .
 Homepage: [http://www4.mplayerhq.hu/](http://www4.mplayerhq.hu/)
 .
 This is in Medibuntu for it's non-free license.

And I'm positive that I entered the keys, but just to be safe, I added them again. 
I just tried to drag a .wma into Totem and got this as a response:

> Totem could not play 'file:///home/ashleigh1992/Desktop/riot.wma'.

Only a subtitle stream was detected. Either you are loading a subtitle file or some other type of text file, or the media file was not recognized.

O_O

---

