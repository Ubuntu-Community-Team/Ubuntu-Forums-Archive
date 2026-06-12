---
title: "where to get mplayer with vaapi support?"
date: 2015-05-03
forum: Multimedia Software
---

### Post by spot-draves on 2015-05-03
[COLOR=#333333][FONT=ClearSans-Light]I have been using ubuntu 14.04, intel drivers from 0.1.org, and the vaapi enabled mplayer from ppa:sander-vangrieken/vaapi and been very happy with the performance.[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]Yesterday I went to build a new machine and discovered that the drivers no longer work on 14.04 and so I installed 14.10.  Unfortunately, the above PPA with mplayer that works with these drivers does not support 14.10.  I cannot find a replacement PPA.[/FONT][/COLOR]
[COLOR=#333333][FONT=ClearSans-Light]Can anyone provide instructions for installing mplayer that can access this hardware?  Thanks.

[/FONT][/COLOR]

---

### Post by mc4man on 2015-05-03
My question would be do you think the Intel driver(s) really make any difference. 
Also you can note that there are newer packages available for 14.04 from elsewhere
Here I show/use on a 14.04.1 orig install - 
OpenGL renderer string: Mesa DRI Intel(R) Haswell Mobile 
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.1.3
OpenGL core profile shading language version string: 3.30

As far as newer packages - 
i965-va-driver:
  Installed: 1.5.1~pre1-1~trusty
libva1:
  Installed: 1.5.1~pre1~trusty

---

### Post by monkeybrain20122 on 2015-05-03
I use mpv with vaapi enabled (works with Smplayer as front end too) If you must use mplayer with hardware acceleration on intel get libvdpau-va-gl and use vdpau. [https://github.com/i-rinat/libvdpau-va-gl](https://github.com/i-rinat/libvdpau-va-gl)

libvdpau-va-gl is in the repo but it didn't work in 14.04 from what I remember, you can either get the up to date version from webupd8's ppa [http://www.webupd8.org/2013/09/adobe-flash-player-hardware.html](http://www.webupd8.org/2013/09/adobe-flash-player-hardware.html) or get the source from link above and compile, --it is quite easy.

---

### Post by monkeybrain20122 on 2015-05-03
> **mc4man said:**
> My question would be do you think the Intel driver(s) really make any difference. 


yes it does. Huge difference even with Ubuntu's stock driver. But one can get even better results with [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

### Post by spot-draves on 2015-05-03
thanks.  i might be able to use mpv, the only thing i really need is to play from the command line, reading the video stream from stdin.

however if i apt-get install mpv i get:

$ sudo apt-get install mpv
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 mpv : Depends: libguess1 (>= 1.2.1) but it is not going to be installed
       Recommends: mesa-vdpau-drivers but it is not going to be installed or
                   nvidia-vdpau-driver but it is not installable or
                   nvidia-driver-binary or
                   nvidia-current but it is not going to be installed or
                   vdpau-driver
E: Unable to correct problems, you have held broken packages.

i also tried [COLOR=#555555][FONT=consolas]ppa:mc3man/mpv-tests[/FONT][/COLOR]

---

### Post by mc4man on 2015-05-03
Where are you trying to get mpv from & I can maybe help you out
```
apt-cache policy mpv
```

---

### Post by spot-draves on 2015-05-03
maybe i should add, this is on an intel nuc with hd5000

---

### Post by monkeybrain20122 on 2015-05-03
Not sure what is wrong. Maybe you should install from mc4man's ppa [https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)

I install from source myself [https://github.com/mpv-player/mpv](https://github.com/mpv-player/mpv)

---

### Post by spot-draves on 2015-05-03
$ sudo apt-cache policy mpv
mpv:
  Installed: (none)
  Candidate: 2:0.9.0~utopic2.1
  Version table:
     2:0.9.0~utopic2.1 0
        500 [http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu/](http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu/) utopic/main amd64 Packages
     0.4.2-1ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic/universe amd64 Packages

---

### Post by mc4man on 2015-05-03
> **spot-draves said:**
> $ sudo apt-cache policy mpv
mpv:
  Installed: (none)
  Candidate: 2:0.9.0~utopic2.1
  Version table:
     2:0.9.0~utopic2.1 0
        500 [http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu/](http://ppa.launchpad.net/mc3man/mpv-tests/ubuntu/) utopic/main amd64 Packages
     0.4.2-1ubuntu3 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) utopic/universe amd64 Packages
Damn - Give me a little while to fix
As 14.10 is dead to me I blindly decided to give users of it one last build. I must have used the 14.04 package & didn't adjust some deps. 
(I don't have 14.10 to test.

---

### Post by mc4man on 2015-05-03
Ok - should be fixed, packages are building. Ck in about 15 min or so. Decided to up to the latest point release - 0.9.1

The reason it couldn't install is I used the control file from trusty which specifies a version of libguess that not avail. in utopic or anywhere else.
(was a mistake I made in version for myself a long time ago & inadvertently pushed to general use ppa's in trusty. Nothing I can do about it now unless libguess goes to a higher version
I typo'ed 1.2-1 to 1.2.1
Let me know if there are any further issues as I can't test here

---

### Post by mc4man on 2015-05-03
> **monkeybrain20122 said:**
> yes it does. Huge difference even with Ubuntu's stock driver. But one can get even better results with [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)
Ok - I use 1.5.1 here, just get from a different source than oibaf
(actually I just copy it over to my personal [end of the line]("https://launchpad.net/~mc3man/+archive/ubuntu/ffmpeg-tests5") ppa

---

### Post by spot-draves on 2015-05-03
thanks i was able to install mpv from your ppa :)

---

