---
title: "Ubuntu 16.10 no wma encoder"
date: 2016-11-02
forum: Multimedia Software
---

### Post by lammert-nijhof on 2016-11-02
I use 16.04 and 16.10 in dual boot. I use 16.10 to try out new apps, 16.04 is my normal system. Some weeks ago I upgraded 14.04 to 16.04 without major problems and I upgraded 16.04 to 16.10 and since than my wma music does not play anymore. Mp3 and mp4/m4a work OK. The same effect occurs with Clementine, Quod Libet and Rhytmbox. I have reinstalled restricted extras using apt-get and the software center, but that did not change anything. 

I have 27GB of music and since 2006, my windows days 95% is wma. My conversion to Ubuntu has been with 10.04.

What to do next, except filing a bug report?

---

### Post by T.J. on 2016-11-02
Have you tried installing the restricted-extras package for your version?  You should also install the gstreamer plugin packages: ugly, bad and good that contain the various codecs. WMA is a proprietary format and does not playback on Linux without adding extra codecs to decode them.  The extra codecs may be illegal in your jurisprudence, so use them at your own risk. I recommend you either convert them to a neutral format or repurchase them if possible.

---

### Post by kostkon on 2016-11-02
Lots of things you could try.

First of all, you could try clearing you package cache before attempting to reinstall ubuntu-restricted-extras again, i.e.
```
sudo apt-get clean && sudo apt-get install ubuntu-restricted-extras --reinstall
```

Also, you could try installing both the 32bit and 64bit versions of the package.

Finally, ubuntu-restricted-extras only installs the gstreamer1.0 plugins; you could try installing the older gstreamer0.10 and its plugins alongside it, just in case.

---

### Post by monkeybrain20122 on 2016-11-02
Works here. tested with Clementine.

---

### Post by mc4man on 2016-11-02
For gstreamer decoding of most wma install 
```
sudo apt install gstreamer1.0-libav gstreamer1.0-plugins-ugly
```

If still issue try removing the .bin file in .cache/gstreamer-1.0/

As far as gstreamer0.10 - in 16.10 it's gone.
As far as these codecs being illegal - they're not for end user decoding or encoding.

---

### Post by lammert-nijhof on 2016-11-02
@kostkon: OK, I tried cleaning and reinstalling and it did not solve the problem, but now I understand what is wrong. During a short moment of stupidity, I followed your advice by accident on 16.04 and I noticed a lot of other packages where re-installed like e.g the gstreamer and the ms-fonts package. In 16.10 only the package itself "[COLOR=#000000][FONT=&amp]ubuntu-restricted-extras" has been re-installed and nothing else. It looks like dependencies[/FONT][/COLOR][COLOR=#000000][FONT=&amp] for the [/FONT][/COLOR]"[COLOR=#000000][FONT=&amp]ubuntu-restricted-extras"[/FONT][/COLOR][COLOR=#000000][FONT=&amp] are missing in 16.10[/FONT][/COLOR][COLOR=#000000][FONT=&amp]. I don't care to get it corrected now in my 16.10 instance, since 16.10 is only for play, my main system is 16.04 and everything is fine there. My personal interest is to get it corrected in the future and especially for 18.04.[/FONT][/COLOR][COLOR=#000000][FONT=&amp] In that case I think I should file a problem report.

@mc4man: gsstreamer 1.0-libav and [/FONT][/COLOR][COLOR=#000000][FONT=&quot]gstreamer1.0-plugins-ugly, the newest versions were already installed.[/FONT][/COLOR]

---

### Post by mc4man on 2016-11-02
> **lammert-nijhof said:**
> 

@mc4man: gsstreamer 1.0-libav and [/FONT][/COLOR][COLOR=#000000][FONT=&quot]gstreamer1.0-plugins-ugly, the newest versions were already installed.[/FONT][/COLOR]
Maybe try 2 specific wma types, wmapro & wmal, see if they work.

```
wget 'http://samples.mplayerhq.hu/A-codecs/WMA9/wmapro/New%20Stories%20(Highway%20Blues)-1.wma'
```

```
wget http://samples.mplayerhq.hu/A-codecs/lossless/luckynight.wma
```

---

### Post by Yellow Pasque on 2016-11-05
If previous suggestion of installing gstreamer1.0-libav does not work, here are some commands that may give us an idea of what is going on:
```
sudo apt-get install gstreamer1.0-tools
gst-inspect-1.0 | grep -i wma
ffmpeg -codecs | grep -i wma
```

EDIT: Also, if you can't play the files mc4man linked to using the media players you listed, I'd try something that uses ffmpeg/libav directly (like mpv) to see if gstreamer is the issue. All 3 players you referred to (Clementine, Quod Libet and Rhythmbox) use gstreamer.

```
sudo apt-get install mpv
mpv whateverfile.wma
```

---

### Post by plansk on 2017-03-28
This is a known problem with the gst-libav1.0 package, see [https://bugs.launchpad.net/ubuntu/+source/gst-libav1.0/+bug/1661842](https://bugs.launchpad.net/ubuntu/+source/gst-libav1.0/+bug/1661842)

An  updated package with a bug fix is available for 16.04 (Xenial) at  [https://launchpad.net/ubuntu/+source/gst-libav1.0/1.8.3-1ubuntu0.2](https://launchpad.net/ubuntu/+source/gst-libav1.0/1.8.3-1ubuntu0.2)

For  those like me on 16.10 (Yakkety), I got around it by downloading the  xenial package  [https://launchpad.net/ubuntu/+archive/primary/+files/gst-libav1.0_1.8.3.orig.tar.xz](https://launchpad.net/ubuntu/+archive/primary/+files/gst-libav1.0_1.8.3.orig.tar.xz)  and then building it so:
```

tar xvf gst-libav1.0_1.8.3.orig.tar.xz
cd gst-libav-1.8.3
sudo apt-get install liborc-0.4-dev # You may have to install other dev packages.
./configure
make
sudo make install
cd /usr/lib/x86_64-linux-gnu/gstreamer-1.0
sudo mv libgstlibav.so libgstlibav.so.old
sudo ln -s /usr/local/lib/gstreamer-1.0/libgstlibav.so

```

---

### Post by exhile on 2017-04-22
I have the same problem with .wma music files and playing them on Rhytmbox. I tried Clementine and .wma files work perfectly however my computer freezes and I have to do a hard reset on my computer to get it running again. Could there be a bug because Rhytmbox doesn't crash my computer.

---

