---
title: "Amarok 1 KDE 4?"
date: 2009-05-23
forum: Multimedia Software
---

### Post by henky on 2009-05-23
Hey guys
I absolutely hate Amarok 2 which comes with kde4, sorry for saying it but I'd really like to switch to the amarok supplied with kde 3.X

is there any way of achieving this?

Thanks!

---

### Post by I_Like_Pie on 2009-05-23
Same here...I am not sure how they managed to, in one version change, to turn the best music player to the worst music player...but they seemed to have done it.

It WAS the reason I abandoned Windows years ago.  Glad they didn't switch to 2.0 earlier

---

### Post by poloking on 2009-06-14
If you havent already found a solution, here goes.

Open up your sources file
```
sudo nano /etc/apt/sources.list
```

Go right to the bottom and input the sources which have the old amarok, on seperate lines:
```
deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
```

ctrl-o to save ctrl-x to exit

then to add the key:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \
0x1d7e9dd033e89ba781e32a24b9f1c432ae74ae63
```

Update your sources:
```
sudo apt-get update
```

Remove amarok2 and install amarok1.4:
```
sudo apt-get remove amarok
sudo apt-get install amarok14
```

Hope that helps

---

### Post by henky on 2009-06-25
thank you that worked like a charm!
Gotta say I really, REALLY missed the old amarok:P

thanks!

---

### Post by PeonDevelopments on 2009-10-24
I'm not too fond of adding repositories that are not officially maintained. Can someone direct this thread to the amarok 1.4.x source tarball?

EDIT:

You can find the tarball for amarok 1.4.10 here:
[http://openports.se/audio/amarok](http://openports.se/audio/amarok)

It's an OpenBSD port supposedly, but I've gotten it past the configure stage as of this edit.
It's not as easy as ./configure make and make install.
If you just installed 9.10 like I have, you'll need your typical -dev packages for everything. (kdelibs, qt3/4, xorg, ruby) (also build-essentials, kde-devel, etc.)

You'll need ruby1.8 or higher (amarok will complain about header files frequently) plus the ruby / ruby-full packages and taglibs.

If compiling with gcc-4.4 and up, some .cpp files will create errors when [make]ing the binaries, so you have to add '#include <stdio.h>' to those classes OR '#include <cstdio>' if that fails (should give an  error: 'rename' is not a member of 'std'). 
According to the link below, gcc 4.3 is the way to go. It should not have the issues that gcc 4.4 has.
(see: [http://aur.archlinux.org/packages.php?ID=25712](http://aur.archlinux.org/packages.php?ID=25712)). I, however, used gcc 4.4, and it does in fact, work.

If you want mtp (and it will fail if you do), make SURE you have the 0.2.6.1 version.

[https://launchpad.net/ubuntu/hardy/+source/libmtp/0.2.6.1-2ubuntu1](https://launchpad.net/ubuntu/hardy/+source/libmtp/0.2.6.1-2ubuntu1)

Get the source, configure / make / make install (as root).

I added the --program-suffix=-1.4 to the configure so I could have both on my system. To launch, you must run amarokapp-1.4 (in my case), not amarok-1.4.

It would not play the Matthias .ogg file that is default with 1.4.x, but it plays mp3s just fine! (Installed libraries from amarok 2.x that would play them, so it's good)

The solution is a bit of a mess and I'll see about blogging it so it's more understandable.

I really hope this helps you guys. Be sure to read up on forums whenever you get an error. It took me 4+ hours, and all I wanted was playlist functionality that amarok 2.x does not have. Now that I have both, I'm satisfied for now.

---

