---
title: "Can't watch CNN videos with Hardy"
date: 2008-05-06
forum: Multimedia Software
---

### Post by MountainX on 2008-05-06
All other multimedia functions are working. I can watch YouTube without issues. But CNN video doesn't work for me. Here is an example of a URL that doesn't do anything except show me a blank black background.

[http://www.cnn.com/video/live/live.html?stream=stream1](http://www.cnn.com/video/live/live.html?stream=stream1)

CNN Radio doesn't work either:
[http://www.cnn.com/audio/radio/cnntv.html](http://www.cnn.com/audio/radio/cnntv.html)

Any suggestions? Thanks.

UPDATE: I found [this thread]("http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4845829&postcount=32"): 

"Found a fix or rather a work around! uninstalled firefox 3.0b5 and reinstalled 2.0.0.14, now everything works like it did before!! Still have no idea why!!"

Wow - no way am I going to get rid of FF3. Anyone know of another solution? Thanks.

---

### Post by MountainX on 2008-05-07
I tried a variation on the advice in this thread:
[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4847342&postcount=34](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4847342&postcount=34)

**Unfortunately, it did NOT work.** :(

Here was the suggestion (and the steps I did are listed below).

> Go to the Synaptic package manager and search for flash and *remove* everything but these packages
libswfdec-0.6-90 (0.6.4-2)
flashplugin-nonfree (9.0.124.0ubuntu2)
ubuntu-restricted-extras (15)

I didn't have ubuntu-restricted-extras or libswfdec-0.6-90. The only packages I had installed were flashplugin-nonfree and one other package that I removed. When I selected the other two packages listed above for installation, the following packages were installed.

```

cabextract (version 1.2-2) will be installed
gstreamer0.10-pitfdll (version 0.9.1.1+cvs20080215-1) will be installed
gstreamer0.10-plugins-bad (version 0.10.6-5) will be installed
gstreamer0.10-plugins-bad-multiverse (version 0.10.6-1) will be installed
gstreamer0.10-plugins-ugly-multiverse (version 0.10.7-1) will be installed
icedtea-gcjwebplugin (version 1.0-0ubuntu5) will be installed
libaccess-bridge-java (version 1.22.0-0ubuntu5) will be installed
libcdaudio1 (version 0.99.12p2-3) will be installed
libfaad0 (version 2.6.1-2) will be installed
libiptcdata0 (version 1.0.2-2) will be installed
libmjpegtools0c2a (version 1:1.8.0-0.2ubuntu5) will be installed
libmms0 (version 0.3-6) will be installed
libopenspc0 (version 0.3.99a-2) will be installed
libquicktime1 (version 2:1.0.0+debian-5) will be installed
libsoundtouch1c2 (version 1.3.0-2.2) will be installed
libswfdec-0.6-90 (version 0.6.4-2) will be installed
libwildmidi0 (version 0.2.2-2) will be installed
msttcorefonts (version 2.4) will be installed
openjdk-6-jre (version 6b09-0ubuntu2) will be installed
openjdk-6-jre-headless (version 6b09-0ubuntu2) will be installed
openjdk-6-jre-lib (version 6b09-0ubuntu2) will be installed
tzdata-java (version 2008b-1ubuntu1) will be installed
ubuntu-restricted-extras (version 15) will be installed
unrar (version 1:3.7.8-1) will be installed

```

During installation I received this message. I clicked "forward" and didn't do anything else.

```

Msttcorefonts uses the DEbian FOnt MAnager (defoma). If you wish to use the fonts provided by this package under the X Window System, you must configure it to use defoma fonts.

The easiest way to do so is to use the x-ttcidfont-conf package. For more information, install the x-ttcidfont-conf package and consult its documentation under /usr/share/doc/x-ttcidfont-conf.

For uses of msttcorefonts not related to the X Window System (e.g. printing) this is not required.

```

In the end, I have only the 3 "flash-related" packages listed in [the original post referenced above]("http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4847342&postcount=34") installed, so I ended up following that advice. But it didn't work.

---

### Post by MountainX on 2008-05-07
bump - I haven't found a solution yet. Thanks for any help.

---

### Post by gargouille on 2008-05-07
I had the same problem and found the solution was to install the following via synaptic package manager:

ubuntu-restricted-extras
libswfdec-0.6-90

I also have VLC media player installed, but I am unsure if this makes a difference.  I also am using Firefox 2.

I found the above info:

[http://ubuntuforums.org/archive/index.php/t-489339.html](http://ubuntuforums.org/archive/index.php/t-489339.html)

original post:
[FONT="Courier New"]leopards
April 30th, 2008, 06:16 PM
Work around was not a good answer as no plug-ins could be installed properly in FF2 Found the real answer in another part of the forum! Go to the Synaptic package manager and search for flash and remove everything but these packages
libswfdec-0.6-90 (0.6.4-2)
flashplugin-nonfree (9.0.124.0ubuntu2)
ubuntu-restricted-extras (15)
version no.s in () got rid of all other stuff and now can see CNN videos again and have my plugins and add ons!!!
[/FONT]

---

### Post by MountainX on 2008-05-08
> **gargouille said:**
> I had the same problem and found the solution was to install the following via synaptic package manager:

ubuntu-restricted-extras
libswfdec-0.6-90

I also have VLC media player installed, but I am unsure if this makes a difference.  

I also am using Firefox 2.



I think the difference is that you are using FF2. I also had no problems with CNN video in FF2. However, I want to find a solution that works with Firefox 3.

BTW, I have those packages installed. I also have VLC installed. Thanks.

---

### Post by MountainX on 2008-06-07
this is still unsolved

---

### Post by jlo_sandog on 2008-06-07
The "Live Video" requires a plugin modification. Details are given on the thread you already found. You don't need to uninstall ff3. That guy was clueless.

---

### Post by wolfen69 on 2008-06-07
it says on the website that you must use windows media player or a mac (with plugin)

---

### Post by jlo_sandog on 2008-06-07
There's a work around. It requires modifying mplayerplug-in. Here's the link again. 
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=489339&page=3](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=489339&page=3)

---

