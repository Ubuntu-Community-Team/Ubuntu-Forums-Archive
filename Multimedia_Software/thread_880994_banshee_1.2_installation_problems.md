---
title: "banshee 1.2 installation problems"
date: 2008-08-05
forum: Multimedia Software
---

### Post by aformon on 2008-08-05
hi i downloaded the tarball for banshee 1.2 to try and install it today. After extracting it i changed directory in terminal to where id extracted the files and entered the ./configure command. After several other lines i get this error message:

checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.
checking for GDK_X11... configure: error: Package requirements (gdk-x11-2.0 >= 2.8) were not met:

No package 'gdk-x11-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GDK_X11_CFLAGS
and GDK_X11_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


Does anyone have any idea how to fix this so i can install banshee?? 
thanks in advance for any help, i really want to give this new banshee software a go.

---

### Post by finer recliner on 2008-08-05
for an easy install, i recommend following the instructions posted here:
[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)

pretty much, add banshee's source to your apt list, then you just apt-get it.

---

### Post by aformon on 2008-08-05
ok tried that and it seems to install fine... trouble is that when i open banshee i just get the loading symbol for several seconds then nothing! program doesnt open and system goes back to how it was before.

any idea what this means??

---

### Post by SnakeHips on 2008-08-05
> **aformon said:**
> ok tried that and it seems to install fine... trouble is that when i open banshee i just get the loading symbol for several seconds then nothing! program doesnt open and system goes back to how it was before.

any idea what this means??

+1 

I'm running x86_64 - is that an issue anyone?

---

### Post by breakerr on 2008-08-05
> **aformon said:**
> ok tried that and it seems to install fine... trouble is that when i open banshee i just get the loading symbol for several seconds then nothing! program doesn't open and system goes back to how it was before.

any idea what this means??

PLEASE SOMEBODY ANSWER BECAUSE IM GETTING THE SAME ISSUE APPARENTLY THIS ERROR IS AFFECTING A FEW PEOPLE AND STILL NO RESPONSE OR SUPPORT FROM ANYBODY:confused:

---

### Post by mc4man on 2008-08-05
this is what i did (haven't looked hard if any ill effects yet)
go to edit menus, click sound & video and then right click on banshee-1 -> properties.
I changed the launch command to this
> banshee-1  --play-enqueued %U 
in other words removed the beginning about the redirect log.
Have to run so haven't tested, but it will open now

---

### Post by breakerr on 2008-08-05
> **mc4man said:**
> this is what i did (haven't looked hard if any ill effects yet)
go to edit menus, click sound & video and then right click on banshee-1 -> properties.
I changed the launch command to this
 
in other words removed the beginning about the redirect log.
Have to run so haven't tested, but it will open now

THANKS A BUNCH MAN that solved the issue......before taking your step I checked on all gstreamers and then followed the steps on post #6 at [http://ubuntuforums.org/showthread.php?t=137127](http://ubuntuforums.org/showthread.php?t=137127)  

HUgZ for solving my problem and take care man...if you need anything dont hesitate to drop by at [http://breaker.artician.com/](http://breaker.artician.com/) or my breakerr.deviantart.com THANKSSSSSSSS

---

### Post by mc4man on 2008-08-05
If you set banshee-1 as default to 'autorun' for audio cd's and it freezes then you can pare down the launch command. (or if it freezes with the above comm.)

> banshee-1 --play %U

> banshee-1 %U
note that's 1 space and only 1 space between command and %U

Like most gnome music players in hardy there is only autorun, not autoplay for audio cd's.
The only player I've found will autoplay cd's upon insertion in hardy is Amarok.

---

### Post by ryanchang on 2008-08-06
where are these edit menus you speak of? i have the save problem..."thinking" logo pops up, then nothing.

---

### Post by mc4man on 2008-08-06
> where are these edit menus you speak of? i have the save problem..

In upper panel right click on Applications -> edit menus -> highlight sound & video , then in right side column r. click banshee-1 -> properties

---

### Post by aformon on 2008-08-06
aha worked an absolute treat, cheers mc4man you're a legend :)

---

### Post by SnakeHips on 2008-08-06
> **mc4man said:**
> In upper panel right click on Applications -> edit menus -> highlight sound & video , then in right side column r. click banshee-1 -> properties

Thanks ,that fixed it! and runs a treat on 64bit :guitar:

---

### Post by ScrollMaker on 2008-08-06
How does one do this on Kubuntu? (KDE4)

---

### Post by mc4man on 2008-08-07
> How does one do this on Kubuntu? (KDE4) 
I don't have kubuntu at the moment but if you mean change launch command should be easy.  Right click on kmenu icon -> edit menu -> find banshee-1 and in a pop up change the comm.

If you mean install go here and add the lines to your sources. (adept - manage repositories
[https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive)
change to hardy in drop down

---

### Post by jeyaganesh on 2008-08-07
Thanks. Brilliant idea. It is working perfectly now.

---

