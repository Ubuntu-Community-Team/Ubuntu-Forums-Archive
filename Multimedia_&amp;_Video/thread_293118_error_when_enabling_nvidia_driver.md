---
title: "error when enabling nvidia driver"
date: 2006-11-04
forum: Multimedia &amp; Video
---

### Post by kcy29581 on 2006-11-04
Hi all,

I installed the "linux" package and verified that all the correct generic packages are installed.

I then installed "nvidia-glx", restarted the pc, then tried enabling the driver and I get the following:
```
sudo nvidia-glx-config enable
Password:
Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

```Is this a bug? I have never had this problem on this pc. My card is a 7800GS AGP.

Thanks

UPDATE: One thing I did notice: if I didn't have "linux-restricted-modules-generic" installed first, when trying to install "nvidia-glx", it would add "linux-restriced-modules-386" to the dependancies. Maybe this is a clue that something isn't right?

---

### Post by tronica on 2006-11-04
try doing configuring xorg yourself. if your in gnome open up the terminal and type

> sudo gedit /etc/X11/xorg.conf

go down to the "device" section and change driver "nv" to "nvidia" then save and restart.

---

### Post by tommcd on 2006-11-05
Also, if that doesn't work, then comment out (put a # infront of) 'load dri' and 'GLcore' under modules section of /etc/X11/xorg.conf.

---

### Post by kcy29581 on 2006-11-05
I know how to manually enable the nvidia module; I'll try that when I get home.

I was reluctant to try that myself first, as the error clearly states that it cannot locate a kernel module (unless I'm reading it wrong?). Does anyone think this is a bug?

---

### Post by pietro_spina on 2006-11-05
I have a similar/same? problem... the package that is supposed to contain the  nvidia module
```
linux-restricted-modules-2.6.15-27-686
```
is installed as is the matching kernel
```
$ uname -r
2.6.15-27-686
```

yet the nividia driver cannot be found...
it is neither an option during a "dpkg-reconfigure xserver-xorg" nor loaded after a manual edit of "/etc/X11/xorg.conf"

any thoughts? I think we might be using a different kernel, but I'm hoping we might share the same solution?

-p

never mind... I re-installed the "restricted modules" and "nvidia-glx" and there it is...

---

### Post by kcy29581 on 2006-11-06
ok, this is definately a bug...

I came to work this morning, (nvidia card here as well) saw there were updates for "linux-restricted-modules-generic"; after the update I restarted the pc, and.... bam! the blue screen of xorg errors.

I have "nvidia" in the drivers section, glx is loaded, dri is not.

All I need to do now is work out how to use launchpad, and try and submit a bug.

pietro_spina, how exactly did you get it working? I reinstalled "nvidia-glx" and I still get the error. I use the "generic" kernel by the way.

---

### Post by bmt on 2006-11-06
> **kcy29581 said:**
> ... how exactly did you get it working? I reinstalled "nvidia-glx" and I still get the error. I use the "generic" kernel by the way.
Same initial problem for me.  I got back into the desktop by editing xorg.conf from a console (changed 'nvidia' to 'nv'), but I don't think I needed to, in hindsight.

Eventually, I ran 'dpkg-reconfigure xserver-xorg' (selected 'nvidia', then accepted all defaults to finish) and the updated nvidia worked straight away.

Someone, somewhere (I have read a lot of nvidia posts these past couple of days!) suggested that X should have a fail-safe fallback available, so that a GUI -- any GUI -- can be displayed, rather than going to a 'meaningless' (I know, I know!) text screen full of terrible-sounding error messages.  I have to agree.

---

### Post by tseliot on 2006-11-06
Try Method 1 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

### Post by kcy29581 on 2006-11-06
> **tseliot said:**
> Try Method 1 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
I'll try that later on, after I finish work on this pc.

Is noone else worried that this is a showstopper bug for people who are useless on the command line? I have 2 pc's with this problem, surely I'm not the only one?

---

### Post by eddgy on 2006-11-06
it *is* a bug:


(**) NVIDIA(0): TwinView enabled
(EE) NVIDIA(0): Version mismatch detected between the NVIDIA X driver and the
(EE) NVIDIA(0):     NVIDIA GLX module.  X driver version: 1.0-8762; GLX module
(EE) NVIDIA(0):     version: 1.0-8776.  Please try reinstalling the NVIDIA
(EE) NVIDIA(0):     driver.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"

---

### Post by tseliot on 2006-11-06
> **eddgy said:**
> it *is* a bug:


(**) NVIDIA(0): TwinView enabled
(EE) NVIDIA(0): Version mismatch detected between the NVIDIA X driver and the
(EE) NVIDIA(0):     NVIDIA GLX module.  X driver version: 1.0-8762; GLX module
(EE) NVIDIA(0):     version: 1.0-8776.  Please try reinstalling the NVIDIA
(EE) NVIDIA(0):     driver.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
Are you sure that it's a bug?

It looks like a common driver mismatch to me.

---

### Post by pietro_spina on 2006-11-06
> **kcy29581 said:**
> 
pietro_spina, how exactly did you get it working? I reinstalled "nvidia-glx" and I still get the error. I use the "generic" kernel by the way.

ok, first off, I was using dapper, I believe you are using edgy... I don't think this was the same issue...
the kernel I had was from the security updates, I can't remeber about the restricted package.. I had not even tried to install the nvidia-glx package but once I did, the nvidia module was properly installed... I don't think that is the way it's supposed to work but... shrug...

On a side note, my edgy install had a kernel/module miss-match due to my use of some non-standard Beryl repos and using the nvidia beta driver...

were I in your situation, I would be tempted to install an older kernel package with it's associated restricted-modules package and nvidia-glx just to see if is specificaly related to that most recent edgy kernel...

best of luck.
-p

---

### Post by kcy29581 on 2006-11-06
I'll try installing "linux-restriced-packages-386" as that's the one the driver tried installing first. I'll post here when I have results.

Thanks for the help guys.

---

### Post by neighborlee on 2006-11-14
> **tseliot said:**
> Are you sure that it's a bug?

It looks like a common driver mismatch to me.

its not a bug as much as a omission LOL

they 'changed' the script to enable this and forgot to correct it in synaptic :) (  release notes ?)

ie: sudo nvidia-xconfig

voila

cheers
neighborlee()

---

### Post by kcy29581 on 2006-11-15
> **neighborlee said:**
> its not a bug as much as a omission LOL

they 'changed' the script to enable this and forgot to correct it in synaptic :) (  release notes ?)

ie: sudo nvidia-xconfig

voila

cheers
neighborlee()
that might be it! so simple...

Anyways, since then I have now reinstalled, and all is working fine. "Bug" was put in Launchpad.

Thanks for the help guys

---

