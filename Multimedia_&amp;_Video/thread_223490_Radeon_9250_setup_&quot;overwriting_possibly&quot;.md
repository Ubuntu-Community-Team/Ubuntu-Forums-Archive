---
title: "Radeon 9250 setup &quot;overwriting possibly&quot; error"
date: 2006-07-26
forum: Multimedia &amp; Video
---

### Post by TimJBart on 2006-07-26
I checked my graphics using ```
glxinfo | grep rendering
``` and realised my direct rendering wasn't working on a MY FIRST FRESH INSTALL.

So, I took the next step in the help file:

> #1
Install the xorg-driver-fglrx package from the Restricted repository

#2
You now need to configure the computer to use the new driver so run this command in a terminal:

sudo dpkg-reconfigure xserver-xorg
		
#3    
When the dialogue appears and asks whether to do automatic detection of your video, pick Yes.
When asked to select a driver, pick fglrx.
		
#4
Follow the remaining instructions as appropriate.

However, when i get to the screen which asks whether I want my graphics at 24bit, I hit enter and an error comes up:

```
xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.20060726181822

```

Why has it gone crazy? :confused:

---

### Post by Paerez on 2006-07-26
That means "I found a file at /etc/X11/xorg.conf, and I am going to overwrite it, but you might have put stuff there, so I am going to warn you, move the old file to a backup, and overwrite it with the new file"

It's not bad, it's just letting you know what going on.

---

### Post by TimJBart on 2006-07-26
> **Paerez said:**
> That means "I found a file at /etc/X11/xorg.conf, and I am going to overwrite it, but you might have put stuff there, so I am going to warn you, move the old file to a backup, and overwrite it with the new file"

It's not bad, it's just letting you know what going on.

ok thanks for the info.  I have just seen a thread talking about NEW ATI drivers.  should I in fact download these and install them or do they come preloaded with the newest ubuntu disk?

Are the new drivers in the package manager?

---

### Post by Paerez on 2006-07-26
The newest drivers usually are not in the repository. Just look at the "version" on the xorg-driver-fglrx package. I think its currently at 8.25, but ATI has released 8.26.

---

### Post by TimJBart on 2006-07-26
> **Paerez said:**
> The newest drivers usually are not in the repository. Just look at the "version" on the xorg-driver-fglrx package. I think its currently at 8.25, but ATI has released 8.26.

I would really rather install the driver from the repository rather than trying to install the new one myself using this guide on the forums:[http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

Seems like a lot of people have problems and if I do I don't have a clue how to fix it.

Is there that much of a difference between 8.25 and 8.26?

---

### Post by Paerez on 2006-07-26
yeah, 8.26 supports xorg 7.

---

### Post by TimJBart on 2006-07-28
> **Paerez said:**
> That means "I found a file at /etc/X11/xorg.conf, and I am going to overwrite it, but you might have put stuff there, so I am going to warn you, move the old file to a backup, and overwrite it with the new file"

It's not bad, it's just letting you know what going on.

the problem is though that it stops the xorg setup at that point.  It won't go any further than that.  Or is choosing the colour mode the final step in the setup?

Do I merely reboot after the overwriting message?

---

### Post by Paerez on 2006-07-28
yeah I think color bit depth is last.

In general:
Warning = something may be bad, but everything finished, check it out to make sure its ok.

Error = I could not finish because of a problem.

---

### Post by TimJBart on 2006-07-28
thank you for the info

---

