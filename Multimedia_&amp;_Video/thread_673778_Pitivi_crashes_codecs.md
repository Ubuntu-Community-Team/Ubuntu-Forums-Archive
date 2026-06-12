---
title: "Pitivi crashes codecs"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by doomsdaydave11 on 2008-01-21
Ok, I boot up Ubuntu Studio AMD-64, then open up a video that is in an avi format with a video player. It plays perfectly fine with video and audio. Then I go into Pitivi to try to create a project and import a video. First Pitivi crashes, and then it seems to mess up the video codecs so I can't watch videos any more.

---

### Post by philc on 2008-01-21
Make sure you have the very latest version of the Gstreamer FFmpeg plugin installed.

I had a nasty PiTiVi bug that I could not work around. Editing a VOB file in the advanced view resulted in a Gstreamer buffer overflow.

I upgraded my Gstreamer FFMPEG plugin version - from 0.10.2 to 0.10.3. This has resolved the bug.

I downloaded 0.10.3 from here:

[http://gstreamer.freedesktop.org/src/gst-ffmpeg/](http://gstreamer.freedesktop.org/src/gst-ffmpeg/)

Configuring the package made me install gstreamer dev files (libgstreame0.10-dev), gstreamer plugin dev file (libgstreamer-plugins-base0.10-dev) and liboil dev files (liboil0.3-dev). I installed all of these via Synaptic. Once these were installed I could configure gst-ffmpeg, make and then install.

Whether it was the upgrade of gst-ffmpeg or the installation of the dev files I can't say, but this has resolved my bug. Regardless, I'd suggest upgrading to the latest gst-ffmpeg to see if it resolves issues you may be having.

---

### Post by doomsdaydave11 on 2008-01-21
I've downloaded it, but how do I install it? I've only used Linux for a little while. In Windows all you had to do is click on it and it would hold your hand. I'm still grasping how Linux does it..

---

### Post by philc on 2008-01-21
Alright, let's see how we go here.........

Firstly, go to System>Admin>Synaptic Package Manager. Search for the following three packages:

libgstreame0.10-dev
libgstreamer-plugins-base0.10-dev
liboil0.3-dev

Once found, check each of them for installation, accept any pop-up about dependencies and other things that need to be installed and then Apply everything.

When you downloaded the Gstreamer-FFmpeg plugin, it should have been this file:

gst-ffmpeg-0.10.3.tar.gz

Dated December 4 in the download directory I linked to.

I'm going to assume you downloaded this to your home directory.

Start a terminal window - Applications>Accessories>Terminal

It will start in your home directory. Type ls to see a list of files in this directory, one of them should be gst-ffmpeg-0.10.3.tar.gz. If it isn't there type cd Desktop - this is the next most likely place for where you have downloaded the file. Once you've  found the file, type:

tar -xzvf gst-ffmpeg-0.10.3.tar.gz

This will extract all the files into a directory called gst-ffmpeg-0.10.3 Type cd gst-ffmpeg-0.10.3 to enter that directory.

Now type ./configure

This is configuring the package for your system, checking all dependencies. Because we installed the three packages at the beginning, and because you already have PiTiVi installed, everything should go fine. If it doesn't, look for whatever package name is missing - configure will tell you. Search for it again through Synaptic package manager. 

Once configure has run without errors, type on the command line:

sudo make 

Type in your password when prompted.

Hopefully this will also run without errors. Next type:

sudo make install

This will install the package you have just made. All being well you have now not only installed Gstreamer FFmpeg plugin, but also learned how to install applications in Linux when they aren't all neatly packaged up in Synaptic.

If you strike problems, paste the error message when asking for help.

---

### Post by helmingstay on 2008-04-30
On hardy, no luck using either apt-get or compiling from source (just pitivi, not deps) with pitivi-0.11.1...  Incidentally, the gst-ffmpeg package appears to now be called gstreamer0.10-ffmpeg.
```

sys:1: Warning: invalid unclassed pointer in cast to `GstBuffer'

(pitivi:8147): GStreamer-CRITICAL **: gst_mini_object_ref: assertion `GST_IS_MINI_OBJECT (mini_object)' failed
Segmentation fault

```

---

