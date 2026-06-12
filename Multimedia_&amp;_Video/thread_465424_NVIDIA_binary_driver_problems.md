---
title: "NVIDIA binary driver problems"
date: 2007-06-05
forum: Multimedia &amp; Video
---

### Post by Rhapsody on 2007-06-05
My current PC is called Chihiro. Over the last five months, we've had some real problems.

However, the refresh rate problems were solved fairly early on, and today, I finally managed to get her producing sound!

But there's still a problem with installing the NVIDIA binary drivers. lspci lists:

00:0d.0 VGA compatible controller: nVidia Corporation GeForce 6100 nForce 405 (rev a2)

Which I believe falls in the range of nvidia-glx-new, but two attempts to install NVIDIA binary drivers have resulted in the X server going down, and requiring a restore of xorg.conf from a backup to get it back.

So, I must ask, what is the best way for me to get NVIDIA binary drivers on Kubuntu? The instructions on the wiki seem to assume I'm using Ubuntu, and have no fallbacks in case I'm not.

Also, Add/Remove Programs will not let me install MPlayer or Xine extra codecs, both of which I very much want. Is this related?

---

### Post by dfreer on 2007-06-05
There is virtually NO difference between ubuntu and kubuntu, so any instructions to install on ubuntu will work on *ubuntu.

Can you post your /etc/X11/xorg.conf file, the one that crashes on you? Also you said you used nvidia-glx-new, but then you used the nvidia binary drivers? so... which one is it, the nvidia-glx-new from the repos or the nvidia-*****.run file?

EDIT: those are most likely seperate problems, try installing them through the terminal and post the output:
```
sudo apt-get install mplayer
sudo apt-get install libxine-extracodecs
```

---

### Post by Rhapsody on 2007-06-05
> **dfreer said:**
> There is virtually NO difference between ubuntu and kubuntu, so any instructions to install on ubuntu will work on *ubuntu.

The [wiki page](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) specifically refers to "System -> Administration -> Restricted Devices Manager", which is an option that does not exist in my K Menu.

> **dfreer said:**
> Can you post your /etc/X11/xorg.conf file, the one that crashes on you?

No, because I overwrote it to get the X server back. I could try it again and make a copy next time, but I'd rather not if at all possible.

> **dfreer said:**
> Also you said you used nvidia-glx-new, but then you used the nvidia binary drivers? so... which one is it, the nvidia-glx-new from the repos or the nvidia-*****.run file?

nvidia-glx-new, which I believe is referred to as "binary drivers" numerous times.

> **dfreer said:**
> EDIT: those are most likely seperate problems, try installing them through the terminal and post the output:
```
sudo apt-get install mplayer
sudo apt-get install libxine-extracodecs
```

MPlayer:

```
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate
```

Xine extra codecs

```
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxine1-ffmpeg
E: Package libxine-extracodecs has no installation candidate
```

---

### Post by dfreer on 2007-06-05
> **Rhapsody said:**
> The [wiki page](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) specifically refers to "System -> Administration -> Restricted Devices Manager", which is an option that does not exist in my K Menu.

```
sudo apt-get install restricted-manager
```
Of course, you probably don't want to download GTK in order to run it as it is an gnome program, so you might as well download the driver manually.

> **Rhapsody said:**
> No, because I overwrote it to get the X server back. I could try it again and make a copy next time, but I'd rather not if at all possible.

Kinda hard to troubleshoot what went wrong with the install without viewing the xorg.conf at fault (if it is indeed at fault, generally people add a bunch of options without knowing what they do). you could post the /var/log/Xorg.0.log to see if there is any useful information. As long as you haven't messed with your xorg.conf file, I guess we don't really need to see it.

> **Rhapsody said:**
> nvidia-glx-new, which I believe is referred to as "binary drivers" numerous times.

technical wording aside, I wanted to make sure you were using the .debs from the repository instead of the .run from nvidia's site.

So basically the way to install the driver would be to:
```
sudo apt-get install nvidia-glx-new
```
backup your /etc/X11/xorg.conf, then edit your xorg.conf file and only change the driver from "nv" to "nvidia", nothing else.
Reboot or restart X, whichever your preference.
If it crashes, either change the driver back to nv, or restore the backup
Then post your /var/log/Xorg.0.log so we can see what is causing the problem.


> **Rhapsody said:**
> MPlayer:

```
Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate
```

> **Rhapsody said:**
> Xine extra codecs

```
Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxine1-ffmpeg
E: Package libxine-extracodecs has no installation candidate
```

What's your /etc/apt/sources.list look like?

---

### Post by Rhapsody on 2007-06-05
> **dfreer said:**
> ```
sudo apt-get install restricted-manager
```
Of course, you probably don't want to download GTK in order to run it as it is an gnome program, so you might as well download the driver manually.

Actually, that's not a problem at all (I much prefer GIMP to Krita, so I'll have GTK+ on here somewhere), but I had no idea I could actually do that. If it'll make this easier, I'd definitely be up for that.

> **dfreer said:**
> What's your /etc/apt/sources.list look like?

```
# 
# deb cdrom:[Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


# deb cdrom:[Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
```

I notice that multiverse doesn't seem to be listed there (aside from backports, which isn't really going to be enough). That would definitely seem to be a problem, but how would I go about fixing it?

---

### Post by dfreer on 2007-06-05
> **Rhapsody said:**
> Actually, that's not a problem at all (I much prefer GIMP to Krita, so I'll have GTK+ on here somewhere), but I had no idea I could actually do that. If it'll make this easier, I'd definitely be up for that.

Well, try installing it, not sure where it will pop up in your menu as it is an gnome app, you could launch it from the commandline (supposedly, my machine is quite buggy all of a sudden) with sudo restricted-manager. Then, see if it recognizes that your card needs a driver, and if it does install it. I'm not too certain it will detect it...

> **Rhapsody said:**
> 
```
# deb cdrom:[Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted
# deb cdrom:[Kubuntu 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
**deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe**
**deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty universe**

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
```

I notice that multiverse doesn't seem to be listed there (aside from backports, which isn't really going to be enough). That would definitely seem to be a problem, but how would I go about fixing it?

There is also a kmplayer package available evidently, just saw it and thought I'd say something. you should be able to enable multiverse by simply adding it after lines I highlighted in **bold**, and then do a sudo apt-get update. Not too sure, but that's where they are on my /etc/apt/sources.list

---

### Post by Nythain on 2007-06-05
sudo apt-get install nvidia-glx
(the 9755 drivers)
or
sudo apt-get install nvidia-glx-new
(the 9631 for cards not supported by 9755 anymore)
or
sudo apt-get install nvidia-glx-legacy
(for really old cards not supported by newer drivers at all anymore)
depending on your vid card


then
kdesu nvidia-settings
make any changes you might want or need
save and exit

voila, that easy

---

### Post by Rhapsody on 2007-06-06
I've just about managed to get all of these problems fixed now, but I have some new one. I think those will be for a new topic though.

---

