---
title: "[Lucid] How to install VLC 1.1.7 on Ubuntu 10.04?"
date: 2011-02-03
forum: Multimedia Software
---

### Post by r1ft on 2011-02-03
Hello. I have Ubuntu Lucid Lynx (10.04) x86-64 on my laptop (Core2Duo, Intel 4 Series graphics). I want to upgrade from the default version of VLC (1.0.6) to the latest (1.1.7). I added the n-muench and ferramroberto PPAs to my software sources, but Ubuntu's update manager is not showing any VLC updates available.

I also added the 'official' VLC PPA (lucid-bleed) but it is only showing v1.1.5, not the latest version. I tried it and it is VERY buggy on my machine. Can someone tell me how to update VLC on my x64 Lucid install?

Thanks!

---

### Post by Yellow Pasque on 2011-02-03
If you can't find a pre-built binary, then either wait patiently for the PPA to update or use the source, Luke. That can get messy though if you need to update dependencies and such. Generally, this helps:
```
sudo apt-get build-dep vlc
```
Then get the tarball from VLC's site, unpack it, and use the old ./configure, make, make install sequence (unless VLC readme says otherwise).
Post specific errors that you encounter.

---

### Post by luigi_mb on 2011-02-04
It's possible to build vlc v1.1.7 on Ubuntu 10.04. I did, and it works very well.

There are indeed many, many dependencies. First do what Crazy Horse suggests:

```

sudo apt-get build-dep vlc

```

Make sure you uninstall the installed version of vlc, and then run

```

./configure --prefix=/usr --enable-ncurses
[CODE]

Make notes of the errors, if any, and use Synaptic to get the missing dependencies.  Run ./configure again, until there are no more errors. Then run

[CODE]
make

```

and finally

```

sudo make install

```

Note: I used the --prefix=/usr option to avoid possible library problems if the files are installed in /usr/local .

Note: the --enable-ncurses option is to ensure that nvlc is also created. This is a very useful interactive console interface.

/luigi

---

### Post by bloodshot13 on 2011-02-11
This is what I did to install vlc 1.1.7 for 10.04. I uninstalled golden eye 1.0.6. Then:


[HTML]sudo add-apt-repository ppa:n-muench/vlc2
sudo apt-get update
sudo apt-get install vlc mozilla-plugin-vlc[/HTML]is this correct,as I'm new to this stuff. I've been trying to get video to work from my iphone4 and my ultrahd flip video.

---

### Post by Calgarym25 on 2011-03-10
I am stuck at:

./configure --prefix=/usr --enable-ncurses

I am very new to Ubuntu...my error is:

bash: ./configure: No such file or directory

I am so clueless I am not even sure how to run Synaptic  (synaptic package manager?)!

Please help, I am trying to update 10.10 with VLC 1.1.7. 

Thanks,

Michelle

---

### Post by Yellow Pasque on 2011-03-10
If you're struggling to download and unpack a source tarball, and then cd into the new directory, you probably should follow the easier directions in post#4

---

### Post by wojox on 2011-03-10
> **Calgarym25 said:**
> I am stuck at:

./configure --prefix=/usr --enable-ncurses

I am very new to Ubuntu...my error is:

bash: ./configure: No such file or directory

I am so clueless I am not even sure how to run Synaptic  (synaptic package manager?)!

Please help, I am trying to update 10.10 with VLC 1.1.7. 

Thanks,

Michelle

Are you in the right directory?

---

### Post by andrew.46 on 2011-03-11
vlc can be a bit of a difficult one to compile correctly, and I suspect it is an application not really suited to compiling by those new to such things. I have a guide here:

Howto: Build the development version of vlc under Ubuntu
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

that illustrates one method of accomplishing this, albeit for the *development* version of vlc. I suspect the majority of people would be better served by searching out well made packages from PPAs that do not break systems with altered FFmpeg libraries in particular. As well, IMHO, it is better to use an up to date version of Ubuntu with the latest vlc, things get more complicated as Ubuntu versions age...

---

### Post by beew on 2011-03-11
> **Calgarym25 said:**
> I am stuck at:

./configure --prefix=/usr --enable-ncurses

I am very new to Ubuntu...my error is:

bash: ./configure: No such file or directory

I am so clueless I am not even sure how to run Synaptic  (synaptic package manager?)!

Please help, I am trying to update 10.10 with VLC 1.1.7. 

Thanks,

Michelle

You can get in from this ppa[ https://launchpad.net/~maverick-bleed/+archive/ppa]("https://launchpad.net/%7Emaverick-bleed/+archive/ppa")

P.S. OP's first post was made more than a month ago, vlc 1.17 has been avaliable in the Lucid bleed ppa for quite some times.

---

### Post by Calgarym25 on 2011-03-13
Thanks to all who replied!
I tried what bloodshot13 posted, but it installed 1.1.4 instead of 1.1.7.  
Perhaps the problems lies in golden eye 1.0.6...but I have no clue what that is. 

The launchpad.net site looks like Greek to me I have no idea where to start!

Anything else I could try?

---

### Post by BitSar on 2011-03-16
It seems this is now a supported release via the VLC team and the current repositories in the 10.04 Kernel.

From the VLC site (Maverick Meerkat instructions) 
% sudo apt-get update
% sudo apt-get install vlc vlc-plugin-pulse mozilla-plugin-vlc

I simply run those into a terminal session in 10.04 x64 and 5 minutes later I was listening to tunes in an auto-populated library.

I must say the new library interface is light and nice.....

BitSar

---

