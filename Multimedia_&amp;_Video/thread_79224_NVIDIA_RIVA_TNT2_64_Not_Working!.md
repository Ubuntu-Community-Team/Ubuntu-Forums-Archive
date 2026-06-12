---
title: "NVIDIA RIVA TNT2 64 Not Working!"
date: 2005-10-19
forum: Multimedia &amp; Video
---

### Post by tidalwav1 on 2005-10-19
This is the millionth post like this on these forums, but I haven't really seen a straight answer.

The very first thing I noticed about Breezy is that it there was no 3D support for my RIVA TNT2 64. I figured that was fine and good, and I'd be able to use the method from [http://ubuntuguide.org/](http://ubuntuguide.org/) that worked with Hoary. Obviously, that failed.

My next approach was to look through the official Ubuntu Wiki, and I found this page:

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

Because my RIVA TNT2 is a legacy card, I tried the legacy drivers first. When those didn't work, I tried the regular driver, but that didn't work either (I'm still pretty sure I need to use legacy drivers.) When I changed the used driver from 'nv' in xorg.conf to 'nvidia', I get this message when X tries to start:

```

FATAL: Error inserting nvidia (/lib/modules/2.6.12.9-686/volatile/nvidia.ko): No such device
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

Typing 'modprobe nvidia' when X is working (using 'nv' instead of 'nvidia') still yields this message:

```

FATAL: Error inserting nvidia (/lib/modules/2.6.12.9-686/volatile/nvidia.ko): No such device

```

Why's this happening?

---

### Post by poofyhairguy on 2005-10-20
[QUOTE=tidalwav1]This is the millionth post like this on these forums, but I haven't really seen a straight answer.

The very first thing I noticed about Breezy is that it there was no 3D support for my RIVA TNT2 64. I figured that was fine and good, and I'd be able to use the method from [http://ubuntuguide.org/](http://ubuntuguide.org/) that worked with Hoary. Obviously, that failed.

My next approach was to look through the official Ubuntu Wiki, and I found this page:

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

Because my RIVA TNT2 is a legacy card, I tried the legacy drivers first. When those didn't work, I tried the regular driver, but that didn't work either (I'm still pretty sure I need to use legacy drivers.) When I changed the used driver from 'nv' in xorg.conf to 'nvidia', I get this message when X tries to start:

```

FATAL: Error inserting nvidia (/lib/modules/2.6.12.9-686/volatile/nvidia.ko): No such device
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

Typing 'modprobe nvidia' when X is working (using 'nv' instead of 'nvidia') still yields this message:

```

FATAL: Error inserting nvidia (/lib/modules/2.6.12.9-686/volatile/nvidia.ko): No such device

```

Why's this happening?[/QUOTE]

You need to go into your xorg.conf and delete the "glx" and "dri" modules. Use the legacy drivers, or just change "nvidia" back to "nv". Really.  Ask if thats foreign to you, I'm in a rush now.

---

### Post by tidalwav1 on 2005-10-20
Deleting those two modules and using the legacy driver still produces that same error message about nvidia.ko. It's really pissing me off. :(

---

### Post by tseliot on 2005-10-20
If the xserver gives you problems with the nvidia module you can try this:

sudo rmmod nvidia [perhaps you will have to do it more times (until it says that no nvidia module has been found) this depends on how many times you used the command "modeprobe nvidia" before following my method]

Then

sudo modprobe nvidia

---

### Post by tidalwav1 on 2005-10-20
The problem is that the module is NEVER inserted because it keeps failing (whether the x server tries to use it, or whether I type modprobe nvidia.)

---

### Post by tseliot on 2005-10-20
[QUOTE=tidalwav1]The problem is that the module is NEVER inserted because it keeps failing (whether the x server tries to use it, or whether I type modprobe nvidia.)[/QUOTE]
1) Nonetheless I encourage you to try my method. I guess you have nothing to lose and it might work for you. In other words: trust me.

2) If it doesn't work you can try an alternative method described in my guide (remember to download driver 7174: you will understand after you read my guide)

[http://ubuntuforums.org/showthread.php?t=75074]("http://ubuntuforums.org/showthread.php?t=75074")

---

### Post by tidalwav1 on 2005-10-20
[QUOTE=tseliot]1) Nonetheless I encourage you to try my method. I guess you have nothing to lose and it might work for you. In other words: trust me.

2) If it doesn't work you can try an alternative method described in my guide (remember to download driver 7174: you will understand after you read my guide)

[http://ubuntuforums.org/showthread.php?t=75074]("http://ubuntuforums.org/showthread.php?t=75074")[/QUOTE]

I *did* try your method, and I get the same error message. At least that's what I was trying to say.

The very first thing I tried was your guide (and that obviously didn't work,) except won't 7174 not support my card because it's a legacy card? You say it's a legacy card in your notes section.

---

### Post by tseliot on 2005-10-20
[QUOTE=tidalwav1]I *did* try your method, and I get the same error message. At least that's what I was trying to say.

The very first thing I tried was your guide (and that obviously didn't work,) except won't 7174 not support my card because it's a legacy card? You say it's a legacy card in your notes section.[/QUOTE]
Actually "7174" was the last unified driver. It should work for you.

---

### Post by tidalwav1 on 2005-10-20
Interesting! I just figured out that the driver does indeed work when I boot with the 386 kernel as opposed to the 686 kernel...now why would THAT be happening?

---

### Post by tseliot on 2005-10-20
[QUOTE=tidalwav1]Interesting! I just figured out that the driver does indeed work when I boot with the 386 kernel as opposed to the 686 kernel...now why would THAT be happening?[/QUOTE]
You need the restricted modules for your 686 kernel. Type this (as it's written below)

sudo apt-get install linux-restricted-modules-`uname -r`

then try the drivers with your 686 kernel.

---

### Post by tidalwav1 on 2005-10-20
I already had the correct version of linux-restricted-modules installed. I tried apt-get remove --purge-ing it and reinstalling it, and I still get the module insertion/no screens found error.

---

### Post by tseliot on 2005-10-20
[QUOTE=tidalwav1]I already had the correct version of linux-restricted-modules installed. I tried apt-get remove --purge-ing it and reinstalling it, and I still get the module insertion/no screens found error.[/QUOTE]
Try 7174 (manually) then or you can also go and ask in the unofficial nvidia forums (see the link in my guide)

---

### Post by tidalwav1 on 2005-10-20
7174 finally installed with no problems, but it still doesn't work on 686. Only 386.  There's no hope, is there.

---

### Post by tidalwav1 on 2005-10-20
Would posting the X server log help?

---

### Post by tidalwav1 on 2005-10-21
tseliot, I'm pretty sure there are some flaws in your NVIDIA HOWTO ([http://ubuntuforums.org/showthread.php?t=75074)](http://ubuntuforums.org/showthread.php?t=75074)). I've sent a PM to you directing you to this post.

After inquiring about the problem at the nvidia forums, I was able to resolve the issue. It basically involved uninstalling linux-restricted-modules and then reinstalling 7174.

First of all, you should mention IN your HOWTO (and not several posts below it) that you need 7174 if you have a legacy card and want to do a manual driver install.

Second, after my experiences, I'm pretty sure installing the restricted modules package on a 686 kernel only supports one version of the NVIDIA driver (I'm not sure which, I don't remember, and the nvidia forums appear to have just gone offline.) which may not work for all cards.

Thanks for your help, everyone.

---

### Post by tseliot on 2005-10-22
[QUOTE=tidalwav1]After inquiring about the problem at the nvidia forums, I was able to resolve the issue. It basically involved uninstalling linux-restricted-modules and then reinstalling 7174.[/QUOTE]

This can cause some problems if you need the restricted modules for another device (e.g. my webcam)

[QUOTE=tidalwav1]First of all, you should mention IN your HOWTO (and not several posts below it) that you need 7174 if you have a legacy card and want to do a manual driver install.[/QUOTE]

That's a good point. I'll modify my guide.

---

