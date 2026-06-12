---
title: "Skype video problem"
date: 2009-01-10
forum: Multimedia Software
---

### Post by george24 on 2009-01-10
Hi, all.

I am writing to ask a question about setting up video on skype. 

_The problem is that the video image flickers at the test screen_. By flickering I mean that the normal image and white screens are being displayed. I get to see video,white,video,white...

My video camera is Chicony USB 2.0 (I have a Toshiba laptop). My distro's mint 6.

I've searched various solutions. For example I've tried forcing skype to use the libv4l instead of the libv4l2.

The solution that I applied was, 

instead of running
```

$skype

```
to run this "hack" that supposedly forced skype to use the libv4l.
```

$LD_PRELOAD=/usr/local/lib/libv4l/v4l1compat.so skype

```

However the problem persisted. While running skype from the terminal, the output is:
first a repeated series of 
```

ALSA lib pcm_bluetooth.c:1619:(bluetooth_init) BT_GETCAPABILITIES failed : Input/output error(5)

```

after opening the options, enabling the test video, and closing the options I get

```

Starting the process...
Skype Xv: Xv ports available: 4
Skype XShm: XShm support enabled
Skype Xv: Using Xv port 131
libv4l2: error dequeuing buf: Invalid argument

```

**If I do a video conference my contact sees my video properly**. However I cannot see properly neither my video, nor my contact's video.

Additionally,
while trying different settings I noticed that **by disabling compiz the flickering stopped**. However when I tried to restore compiz I got some errors of the form:
```

/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```
, and compiz wouldn't start :P (actually It would fail and mess up my window bars etc).

After fixing compiz again the skype problem persists. 

Any ideas/suggestions for the video problems?
Also, does anyone know what these *ALSA bluetooth* errors mean?

Thank you in advance for any replies! :D

---

### Post by george24 on 2009-01-11
Just posting to revive the thread!:guitar:

---

### Post by ang-man on 2009-02-14
Hello Anyone, can someone please respond to george24 question with any suggestions?workarounds?
got the same issue and appreciate anyone giving some links/suggestions to try out

Thank you

---

### Post by matthewgarysmith on 2009-03-10
I found the answer to this problem [over on the compiz forums]("http://forum.compiz-fusion.org/showthread.php?t=7471").

To summarize, you need to disable textured video. Here are the **detailed** steps:

1) open a Terminal window (Applications > Accessories > Terminal)

 2) **optionally**, in the terminal run the following command to backup the xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

3) in the terminal run the following command to open the xorg.conf for editing

```
sudo gedit /etc/X11/xorg.conf
```

4) now find the **Device Section**, it will look something like this:

```

Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

```

5) now add the following line to that section:

```
    Option      "TexturedVideo" "Off"
```

6) when you are done it should look like this:

```

 Section "Device"
    Identifier  "Configured Video Device"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
    Option      "TexturedVideo" "Off"
EndSection

```

7) save and close the xorg.conf

8) give your machine a reboot, and enjoy some flicker free video


*Hope this helps.*

---

### Post by Excedio on 2009-08-08
george24,
 
Did this help? I'd like to know your results befoer testing myself.

---

