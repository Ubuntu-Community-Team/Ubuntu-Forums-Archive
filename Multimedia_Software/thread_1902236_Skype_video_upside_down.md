---
title: "Skype video upside down"
date: 2011-12-30
forum: Multimedia Software
---

### Post by zaibotrenktas on 2011-12-30
Hello,

I'm using Xubuntu 11.10 64-bit on my Asus N73Jn laptop. Video is upside down in skype, but not in Cheese.

I've tried many solutions, but none worked for me.

Many people suggest trying LD_PRELOAD. In my case I can start skype with LD_PRELOAD without any error only with ```
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
```
since /usr/lib/libv4l/ doesn't exist (why?).

I've also tried Video4Linux(v4l2ucp), but hflip and vflip don't work for some reason.

I'd really appreciate any help.

---

### Post by Paddy Landau on 2011-12-30
I'm also having problems with Skype.

Try each of the following to see if any of them will work.
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
XLIB_SKIP_ARGB_VISUALS=1 skype
```

---

### Post by zaibotrenktas on 2011-12-30
> **Paddy Landau said:**
> I'm also having problems with Skype.

Try each of the following to see if any of them will work.
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
XLIB_SKIP_ARGB_VISUALS=1 skype
```

First two don't work since there is no libv4l folder in /usr/lib.
And last two don't make any changes to skype video.

---

### Post by Paddy Landau on 2011-12-30
Sorry. As I say, I'm also [having problems with Skype]("http://ubuntuforums.org/showthread.php?t=1900142"). Unfortunately, Skype does not support Linux well at all, and that's a pity because Skype is an excellent product. If it were not closed source, I imagine that we'd get better solutions -- and some fantastic add-ons.

---

### Post by resander on 2011-12-30
Try this:

export LIBV4LCONTROL_FLAGS=3
LD_PRELOAD=/usr/lib/libv4lcompat.so skype

It worked for me for a 32-bit Fujitsu netbook using Ubuntu 10.04.03 LTS.

---

### Post by zaibotrenktas on 2011-12-30
> **resander said:**
> Try this:

export LIBV4LCONTROL_FLAGS=3
LD_PRELOAD=/usr/lib/libv4lcompat.so skype

It worked for me for a 32-bit Fujitsu netbook using Ubuntu 10.04.03 LTS.

No luck with this.

```
ERROR: ld.so: object '/usr/lib/libv4lcompat.so' from LD_PRELOAD cannot be preloaded: ignored.

```

---

### Post by resander on 2011-12-31
I had difficulties too and posted thread 'Inbuilt webcam captures caller upside down' in the Ubuntu Absolute Beginner Talk forum:

[http://ubuntuforums.org/showthread.php?t=1896543](http://ubuntuforums.org/showthread.php?t=1896543)

In this Lechien73 referred to a blog by Radu Cotesco. This did not help me, but might be worth trying.

I then googled on permutations of 'Skype, upside down, Linux' and got matches. The first provided the solution, but there were more that may provide hints.

Are you using the internal webcam or a clip-on separate USB webcam? If a clip-on camera you may have to goto Skype->Options->Video Devices when online to Skype and select the USB camera. Our USB webcam, a Logitech C130 was shown as UVC Camera (046d:081b) (/dev/video0) and the internal netbook camera as OEM Camera (/dev/video1). The (046d:081b) is the USB identifier of the Logitech webcam reported by the lsusb command. I have noticed Skype 2.2.beta for Linux (latest version?) sometimes reverts to the the OEM Camera when started. Don't know why.

If you were using an internal web camera, could you try an external USB webcam?

Hope you can solve this.

---

### Post by zaibotrenktas on 2012-01-01
> **resander said:**
> I had difficulties too and posted thread 'Inbuilt webcam captures caller upside down' in the Ubuntu Absolute Beginner Talk forum:

[http://ubuntuforums.org/showthread.php?t=1896543](http://ubuntuforums.org/showthread.php?t=1896543)


Thank you very much! :D

Those two lines from your link did the job:

```
export LIBV4LCONTROL_FLAGS=3
LD_PRELOAD=/usr/lib32/libv4lcompat.so skype
```

---

### Post by Teiseii on 2012-07-14
> **zaibotrenktas said:**
> Thank you very much! :D

Those two lines from your link did the job:

```
export LIBV4LCONTROL_FLAGS=3
LD_PRELOAD=/usr/lib32/libv4lcompat.so skype
```

For Ubuntu 12.04:

```
export LIBV4LCONTROL_FLAGS=3
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

---

### Post by Paddy Landau on 2012-07-14
You may want to try the new Skype released for Linux. Against expectations, Microsoft (which bought Skype) has released version 4 for Linux!

My experience of Skype 4 is far better than Skype 2 — no errors whatsoever, and everything worked the first time without any workarounds.

I can only hope that you would have the same experience.

To install Skype 4:

[LIST]
[*][Skype download page]("http://www.skype.com/go/download/") > hover over Download Now > Ubuntu 10.04 (32-bit or 64-bit according to your machine) > Save the file.
[*]Go to the file in Nautilus > double-click (or right-click > Open) > Install.
[/LIST]

---

