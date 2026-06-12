---
title: "2 days ago Totem Movie player worked - now it doesn't."
date: 2011-04-23
forum: Multimedia Software
---

### Post by blackdalek on 2011-04-23
Two days ago, Totem Movie player could play AVI files and DVD discs with no problem. Now it struggles to even put a picture up on the screen.

Playback of AVIs is slow, choppy and intermittent. It is like watching a still picture slide show.

DVD playback is even worse. Can barely navigate the DVD menus with all the freezing.

There must have been an update applied within the last 2 days which has caused this.. Any ideas?

Oddly, VLC has no issues and behaves like normal... but I can't use my USB remote with that because VLC disables multimedia keys (my USB remote works by mimicking the multimedia keys on a keyboard)

---

### Post by cantormath on 2011-04-23
Are you using the codecs from the medibuntu repository.  I would make sure the codecs are installed from there.  Also, looking in synaptic for package history or /var/log/dpkg.log to see what was updated.

---

### Post by blackdalek on 2011-04-24
There are so many items in the log which were updated, it could be anything. That, coupled with the fact that I don't exactly know when it stopped working makes it difficult for me to trace the offending update. How do I trace the update which caused the problem?


Below is everything updated or upgraded since 22nd April -

```

2011-04-22 11:33:45 upgrade dhcp3-client 3.1.3-2ubuntu3.1 3.1.3-2ubuntu3.2
2011-04-22 11:33:47 upgrade dhcp3-common 3.1.3-2ubuntu3.1 3.1.3-2ubuntu3.2
2011-04-22 11:33:50 upgrade logrotate 3.7.8-4ubuntu2 3.7.8-4ubuntu2.1
2011-04-22 11:33:50 upgrade sysvinit-utils 2.87dsf-4ubuntu17 2.87dsf-4ubuntu17.1
2011-04-22 11:33:51 upgrade sysv-rc 2.87dsf-4ubuntu17 2.87dsf-4ubuntu17.1
2011-04-22 11:33:53 upgrade initscripts 2.87dsf-4ubuntu17 2.87dsf-4ubuntu17.1
2011-04-22 11:33:58 upgrade libk5crypto3 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.9
2011-04-22 11:34:12 upgrade libgssapi-krb5-2 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.9
2011-04-22 11:34:16 upgrade libkrb5-3 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.9

2011-04-22 11:34:18 upgrade libkrb5support0 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.9
2011-04-22 11:34:21 upgrade libgssrpc4 1.8.1+dfsg-2ubuntu0.8 1.8.1+dfsg-2ubuntu0.9
2011-04-22 11:34:25 upgrade libgstreamer0.10-dev 0.10.32-1~lucid1 0.10.32.2-1~lucid2
2011-04-22 11:34:30 upgrade libgstreamer0.10-0 0.10.32-1~lucid1 0.10.32.2-1~lucid2
2011-04-22 11:34:39 upgrade gir1.0-gstreamer-0.10 0.10.32-1~lucid1 0.10.32.2-1~lucid2
2011-04-22 11:34:41 upgrade libgstreamer-plugins-base0.10-dev 0.10.32-1~lucid1 0.10.32.2-1~lucid7
2011-04-22 11:34:46 upgrade libgstreamer-plugins-base0.10-0 0.10.32-1~lucid1 0.10.32.2-1~lucid7
2011-04-22 11:34:53 upgrade gstreamer0.10-alsa 0.10.32-1~lucid1 0.10.32.2-1~lucid7
2011-04-22 11:34:54 upgrade gstreamer0.10-gnomevfs 0.10.32-1~lucid1 0.10.32.2-1~lucid7
2011-04-22 11:34:56 upgrade liborc-0.4-0 1:0.4.12-1~lucid1 1:0.4.13-1~lucid1
2011-04-22 11:34:57 upgrade gstreamer0.10-plugins-base 0.10.32-1~lucid1 0.10.32.2-1~lucid7
2011-04-22 11:35:00 upgrade gstreamer0.10-tools 0.10.32-1~lucid1 0.10.32.2-1~lucid2
2011-04-22 11:35:01 upgrade gstreamer0.10-plugins-base-apps 0.10.32-1~lucid1 0.10.32.2-1~lucid7
2011-04-22 11:35:03 upgrade gstreamer0.10-plugins-bad 0.10.21-1~lucid1 0.10.21.2-1~lucid2
2011-04-22 11:35:08 upgrade gstreamer0.10-plugins-good 0.10.27-1~lucid2 0.10.28.2-1~lucid2
2011-04-22 11:35:31 upgrade gstreamer0.10-plugins-ugly 0.10.17-1~lucid1 0.10.17.2-1~lucid2
2011-04-22 11:35:40 upgrade gstreamer0.10-pulseaudio 0.10.27-1~lucid2 0.10.28.2-1~lucid2
2011-04-22 11:35:42 upgrade gstreamer0.10-x 0.10.32-1~lucid1 0.10.32.2-1~lucid7
2011-04-22 11:35:44 upgrade kdepimlibs-data 4:4.4.5-0ubuntu1 4:4.4.5-0ubuntu1.1
2011-04-22 11:35:50 upgrade kdepimlibs5 4:4.4.5-0ubuntu1 4:4.4.5-0ubuntu1.1
2011-04-22 11:35:55 upgrade libavcodec-unstripped-52 4:0.5.1-1ubuntu1.1 4:0.5.1-1ubuntu1.1+medibuntu1
2011-04-22 11:35:55 upgrade libavutil-extra-49 4:0.5.1-1ubuntu1.1 4:0.5.1-1ubuntu1.1+medibuntu1
2011-04-22 11:35:56 upgrade libavcodec-extra-52 4:0.5.1-1ubuntu1.1 4:0.5.1-1ubuntu1.1+medibuntu1
2011-04-22 11:36:02 upgrade libavformat-extra-52 4:0.5.1-1ubuntu1.1 4:0.5.1-1ubuntu1.1+medibuntu1
2011-04-22 11:36:05 upgrade libpolkit-gobject-1-0 0.96-2 0.96-2ubuntu0.1
2011-04-22 11:36:06 upgrade libpolkit-agent-1-0 0.96-2 0.96-2ubuntu0.1
2011-04-22 11:36:07 upgrade libpolkit-backend-1-0 0.96-2 0.96-2ubuntu0.1
2011-04-22 11:36:08 upgrade libpostproc-extra-51 4:0.5.1-1ubuntu1.1 4:0.5.1-1ubuntu1.1+medibuntu1
2011-04-22 11:36:11 upgrade libslp1 1.2.1-7.6 1.2.1-7.6ubuntu0.1
2011-04-22 11:36:11 upgrade libswscale-extra-0 4:0.5.1-1ubuntu1.1 4:0.5.1-1ubuntu1.1+medibuntu1
2011-04-22 11:36:12 upgrade linux-firmware 1.34.4 1.34.7
2011-04-22 11:36:21 upgrade linux-generic 2.6.32.30.36 2.6.32.31.37
2011-04-22 11:36:22 upgrade linux-image-generic 2.6.32.30.36 2.6.32.31.37
2011-04-22 11:37:23 upgrade linux-headers-generic 2.6.32.30.36 2.6.32.31.37
2011-04-22 11:37:27 upgrade linux-libc-dev 2.6.32-30.59 2.6.32-31.61
2011-04-22 11:37:32 upgrade policykit-1 0.96-2 0.96-2ubuntu0.1
2011-04-22 11:37:36 upgrade sysvutils 2.87dsf-4ubuntu17 2.87dsf-4ubuntu17.1
2011-04-22 11:37:37 upgrade w32codecs 1:20110131-0.1medibuntu2 1:20110131-0.1medibuntu3
2011-04-24 09:03:59 upgrade libtiff4-dev 3.9.2-2ubuntu0.6 3.9.2-2ubuntu0.7
2011-04-24 09:04:00 upgrade libtiffxx0c2 3.9.2-2ubuntu0.6 3.9.2-2ubuntu0.7
2011-04-24 09:04:01 upgrade libtiff4 3.9.2-2ubuntu0.6 3.9.2-2ubuntu0.7
2011-04-24 09:14:53 upgrade python-totem-plparser 2.30.0-0ubuntu1.1 2.30.0-0ubuntu1.1
2011-04-24 09:14:54 upgrade totem 2.30.2-0ubuntu1 2.30.2-0ubuntu1
2011-04-24 09:14:55 upgrade totem-common 2.30.2-0ubuntu1 2.30.2-0ubuntu1
2011-04-24 09:15:03 upgrade totem-plugins 2.30.2-0ubuntu1 2.30.2-0ubuntu1
2011-04-24 09:15:05 upgrade totem-plugins-extra 2.30.2-0ubuntu1 2.30.2-0ubuntu1
2011-04-24 09:17:42 upgrade gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1ubuntu2 0.9.1.1+cvs20080215-1ubuntu2
2011-04-24 09:17:43 upgrade gstreamer0.10-plugins-bad-multiverse 0.10.18-0ubuntu1 0.10.18-0ubuntu1
2011-04-24 09:17:43 upgrade gstreamer0.10-plugins-ugly 0.10.17.2-1~lucid2 0.10.17.2-1~lucid2
2011-04-24 09:17:46 upgrade gstreamer0.10-plugins-ugly-multiverse 0.10.14-0ubuntu2 0.10.14-0ubuntu2
2011-04-24 09:17:47 upgrade totem 2.30.2-0ubuntu1 2.30.2-0ubuntu1
2011-04-24 09:17:48 upgrade totem-gstreamer 2.30.2-0ubuntu1 2.30.2-0ubuntu1
2011-04-24 09:17:49 upgrade ubuntu-restricted-extras 39 39
2011-04-24 09:27:45 upgrade bluez-gstreamer 4.60-0ubuntu8 4.60-0ubuntu8
2011-04-24 09:27:46 upgrade brasero 2.30.2-0ubuntu1.1 2.30.2-0ubuntu1.1
2011-04-24 09:27:47 upgrade gir1.0-gst-plugins-base-0.10 0.10.32.2-1~lucid7 0.10.32.2-1~lucid7
2011-04-24 09:27:48 upgrade gir1.0-gstreamer-0.10 0.10.32.2-1~lucid2 0.10.32.2-1~lucid2
2011-04-24 09:27:49 upgrade gnome-codec-install 0.4.2ubuntu2 0.4.2ubuntu2
2011-04-24 09:27:51 upgrade gnome-media 2.30.0-0ubuntu1 2.30.0-0ubuntu1
2011-04-24 09:27:52 upgrade gstreamer0.10-alsa 0.10.32.2-1~lucid7 0.10.32.2-1~lucid7
=011-04-24 09:27:52 upgrade gstreamer0.10-esd 0.10.27-1~lucid2 0.10.27-1~lucid2
2011-04-24 09:27:53 upgrade gstreamer0.10-ffmpeg 0.10.11-1~lucid1 0.10.11-1~lucid1
2011-04-24 09:27:54 upgrade gstreamer0.10-gnomevfs 0.10.32.2-1~lucid7 0.10.32.2-1~lucid7
2011-04-24 09:27:55 upgrade gstreamer0.10-nice 0.0.10-2build1 0.0.10-2build1
2011-04-24 09:27:55 upgrade gstreamer0.10-pitfdll 0.9.1.1+cvs20080215-1ubuntu2 0.9.1.1+cvs20080215-1ubuntu2
2011-04-24 09:27:56 upgrade gstreamer0.10-plugins-bad-multiverse 0.10.18-0ubuntu1 0.10.18-0ubuntu1
2011-04-24 09:27:56 upgrade gstreamer0.10-plugins-base 0.10.32.2-1~lucid7 0.10.32.2-1~lucid7
2011-04-24 09:27:57 upgrade gstreamer0.10-plugins-base-apps 0.10.32.2-1~lucid7 0.10.32.2-1~lucid7
2011-04-24 09:27:57 upgrade gstreamer0.10-plugins-good 0.10.28.2-1~lucid2 0.10.28.2-1~lucid2
2011-04-24 09:28:01 upgrade gstreamer0.10-plugins-ugly 0.10.17.2-1~lucid2 0.10.17.2-1~lucid2
2011-04-24 09:28:04 upgrade gstreamer0.10-plugins-ugly-multiverse 0.10.14-0ubuntu2 0.10.14-0ubuntu2
2011-04-24 09:28:05 upgrade gstreamer0.10-pulseaudio 0.10.28.2-1~lucid2 0.10.28.2-1~lucid2
2011-04-24 09:28:05 upgrade gstreamer0.10-tools 0.10.32.2-1~lucid2 0.10.32.2-1~lucid2
2011-04-24 09:28:06 upgrade gstreamer0.10-x 0.10.32.2-1~lucid7 0.10.32.2-1~lucid7
2011-04-24 09:28:07 upgrade gxine 0.5.904-2ubuntu3.1 0.5.904-2ubuntu3.1
2011-04-24 09:28:10 upgrade libdmx1 1:1.1.0-2 1:1.1.0-2
2011-04-24 09:28:10 upgrade libdvdnav4 4.1.3-6 4.1.3-6
2011-04-24 09:28:11 upgrade libgnome-media-dev 2.30.0-0ubuntu1 2.30.0-0ubuntu1
2011-04-24 09:28:12 upgrade libgnome-media0 2.30.0-0ubuntu1 2.30.0-0ubuntu1
2011-04-24 09:28:12 upgrade libgstreamer-plugins-base0.10-0 0.10.32.2-1~lucid7 0.10.32.2-1~lucid7
2011-04-24 09:28:14 upgrade libgstreamer-plugins-base0.10-dev 0.10.32.2-1~lucid7 0.10.32.2-1~lucid7
2011-04-24 09:28:16 upgrade libgstreamer0.10-0 0.10.32.2-1~lucid2 0.10.32.2-1~lucid2
2011-04-24 09:28:18 upgrade libgstreamer0.10-dev 0.10.32.2-1~lucid2 0.10.32.2-1~lucid2
2011-04-24 09:28:21 upgrade libnice0 0.0.10-2build1 0.0.10-2build1
2011-04-24 09:28:21 upgrade libtotem-plparser-dev 2.30.0git201000413-0ubuntu1 2.30.0git201000413-0ubuntu1
2011-04-24 09:28:22 upgrade libtotem-plparser17 2.30.0git201000413-0ubuntu1 2.30.0git201000413-0ubuntu1
2011-04-24 09:28:23 upgrade libvcdinfo0 0.7.23-4ubuntu2 0.7.23-4ubuntu2
2011-04-24 09:28:23 upgrade libxine1 1.1.17-1ubuntu3 1.1.17-1ubuntu3
2011-04-24 09:28:24 upgrade libxine1-bin 1.1.17-1ubuntu3 1.1.17-1ubuntu3
2011-04-24 09:28:25 upgrade libxine1-ffmpeg 1.1.17-1ubuntu3 1.1.17-1ubuntu3
2011-04-24 09:28:26 upgrade libxine1-misc-plugins 1.1.17-1ubuntu3 1.1.17-1ubuntu3
2011-04-24 09:28:28 upgrade libxine1-x 1.1.17-1ubuntu3 1.1.17-1ubuntu3
2011-04-24 09:28:28 upgrade libxinerama-dev 2:1.1-2 2:1.1-2
2011-04-24 09:28:29 upgrade libxinerama1 2:1.1-2 2:1.1-2
2011-04-24 09:28:29 upgrade phonon-backend-gstreamer 4:4.4.0-0ubuntu2 4:4.4.0-0ubuntu2
2011-04-24 09:28:30 upgrade pulseaudio 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu14
2011-04-24 09:28:31 upgrade python-gst0.10 0.10.21-1~lucid1 0.10.21-1~lucid1
2011-04-24 09:28:33 upgrade python-totem-plparser 2.30.0-0ubuntu1.1 2.30.0-0ubuntu1.1
2011-04-24 09:28:34 upgrade sound-juicer 2.28.1-2 2.28.1-2
2011-04-24 09:28:43 upgrade totem 2.30.2-0ubuntu1 2.30.2-0ubuntu1
2011-04-24 09:28:45 upgrade totem-common 2.30.2-0ubuntu1 2.30.2-0ubuntu1
2011-04-24 09:28:51 upgrade totem-gstreamer 2.30.2-0ubuntu1 2.30.2-0ubuntu1
2011-04-24 09:28:52 upgrade totem-mozilla 2.30.2-0ubuntu1 2.30.2-0ubuntu1
2011-04-24 09:28:52 upgrade totem-plugins 2.30.2-0ubuntu1 2.30.2-0ubuntu1
2011-04-24 09:28:53 upgrade totem-plugins-extra 2.30.2-0ubuntu1 2.30.2-0ubuntu1
2011-04-24 09:28:54 upgrade totem-xine 2.30.2-0ubuntu1 2.30.2-0ubuntu1
2011-04-24 09:28:54 upgrade ubuntu-restricted-extras 39 39
2011-04-24 09:28:55 upgrade vlc 1.0.6-1ubuntu1.6 1.0.6-1ubuntu1.6
2011-04-24 09:28:57 upgrade gstreamer0.10-plugins-bad 0.10.21.2-1~lucid2 0.10.21.2-1~lucid2
2011-04-24 09:28:59 upgrade libxine1-console 1.1.17-1ubuntu3 1.1.17-1ubuntu3
2011-04-24 09:29:00 upgrade libxine1-plugins 1.1.17-1ubuntu3 1.1.17-1ubuntu3
2011-04-24 09:29:44 update-alternatives: run with --install /usr/bin/gstreamer-codec-install gstreamer-codec-install /usr/bin/gnome-codec-install 85
2011-04-24 09:32:00 upgrade libdvdread4 4.1.3-8ubuntu1 4.1.3-8ubuntu1
2011-04-24 09:32:14 upgrade libdvdcss2 1.2.10-0.3medibuntu1 1.2.10-0.3medibuntu1
2011-04-24 09:33:05 upgrade libdvdcss2 1.2.10-0.3medibuntu1 1.2.10-0.3medibuntu1
2011-04-24 09:33:06 upgrade libdvdnav4 4.1.3-6 4.1.3-6
2011-04-24 09:33:06 upgrade libdvdread4 4.1.3-8ubuntu1 4.1.3-8ubuntu1

```

As you can see, a lot of it relates to video and DVD playback packages. But how do I know which package/s to downgrade/uninstall out of so many?

---

### Post by blackdalek on 2011-04-25
So how do I get back to a working installation? Do I have to make a fresh install from the DVD and never apply any updates?

---

### Post by cotcot on 2011-04-25
Maybe you get a useful error message when you start totem from terminal and then open your dvd.

---

### Post by blackdalek on 2011-04-25
all that comes up in terminal is...
** (totem:5123): WARNING **: Could not create element 'gconfvideosink'

---

### Post by blackdalek on 2011-04-26
from googling, I worked out that gconfvideosink is part of the gstreamer "good" package" -but I've already removed and re-installed that package several times to try and fix this problem.
So I am still no further ahead.

Any other ideas?

---

### Post by K_45 on 2011-04-26
Try running the file (.avi) for example  with vlc from the command line:

[CODE]vlc *file*[/CODE

and post what the command line tells you.

---

### Post by blackdalek on 2011-04-27
Well, as I mentioned earlier in the thread, VLC isn't exhibiting any obvious problems.

Anyway, here is what appears in the terminal during playback and exit.

```
VLC media player 1.0.6 Goldeneye
Remote control interface initialized. Type `help' for help.
vlc: could not connect to socket
vlc: No such file or directory
[0x94b08a0] lirc interface error: lirc initialisation failed
[0x94b08a0] main interface error: no suitable interface module
[0x9413668] main libvlc error: interface "lirc,none" initialization failed
[0x9413668] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x97d1178] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:192000
[0x97dd4f0] pulse audio output: No. of Audio Channels: 2
status change: ( stop state: 0 )
status change: ( quit )
Segmentation fault
```

---

### Post by blackdalek on 2011-04-27
I should also probably mention that I get this error from totem too - I just didn't realise it was a different error to the 'gconfvideosink' error at first glance.

** (totem:2992): WARNING **: Could not create element 'gconfaudiosink'

---

### Post by K_45 on 2011-04-27
Try removing and reinstalling:

```
sudo apt-get remove -purge totem gstreamer*
```

Then reinstall

```
sudo apt-get install totem gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly gstreamer0.10-plugins-nice gstreamer0.10-plugins-base
```

---

### Post by wkulecz on 2011-04-27
Have you installed gstreamer from a PPA?

The names in you log file look similar to what I had when I tried it.  It broke my system too, so I had to revert to the standard repo versions.

Search for PPA purge if this is the case and you'll have to remove the PPA from your apt sources list before re-installing.

I filed a bug report and the PPA developers quickly marked it "bogus".  Use PPA at your you risk!

Vlc works because its a seperate program with its own multi-media subsystem and doesn't use anything from gstreamer.  Totem depends on gstreamer, hence broken gstreamer breaks it.

---

### Post by blackdalek on 2011-04-28
> **wkulecz said:**
> Have you installed gstreamer from a PPA?



Yes. My sources file contains this -
[http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu](http://ppa.launchpad.net/gstreamer-developers/ppa/ubuntu)

---

### Post by blackdalek on 2011-04-28
> **K_45 said:**
> Try removing and reinstalling:



I already tried that. It didn't work.

I haven't tried it with the PPA gstreamer repo disabled tho... I will try that now.

---

### Post by blackdalek on 2011-04-28
> **K_45 said:**
> 

sudo apt-get remove -purge totem gstreamer*

K_45, using your command doesn't work - it has both purge and remove, so I left out 'remove'. It asks if I want to remove 44 other packages.

Is this safe?

---

### Post by wkulecz on 2011-04-28
> **blackdalek said:**
> I already tried that. It didn't work.

I haven't tried it with the PPA gstreamer repo disabled tho... I will try that now.

You need to get the ppa-purge package, see this thread:

[http://ubuntuforums.org/showthread.php?t=1705159](http://ubuntuforums.org/showthread.php?t=1705159)

Undoing the damage from the PPA was not fun :(

---

### Post by blackdalek on 2011-04-28
Thanks wkulecz. I managed to get rid of all the PPA stuff and re-install everything that got removed. Totem is working properly again now.

---

### Post by K_45 on 2011-04-28
> **blackdalek said:**
> K_45, using your command doesn't work - it has both purge and remove, so I left out 'remove'. It asks if I want to remove 44 other packages.

Is this safe?

 It does work, and gstreamer has a lot of packages, but seeing as you solved it . . . mark the thread as solved using thread tools.

---

### Post by pawel k on 2011-05-03
Maybe this information be helpful for somebody.


I've got the same problem. I resolved it by installing gstreamer0.10-gconf package.

---

