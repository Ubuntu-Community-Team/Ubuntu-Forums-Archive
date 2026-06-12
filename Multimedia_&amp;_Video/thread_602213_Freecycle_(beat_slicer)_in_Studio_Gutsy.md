---
title: "Freecycle (beat slicer) in Studio Gutsy"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by Kumeelyun on 2007-11-04
So far the graphic-designer/Linux-newbie (GD/LN) has been very happy with the audio tools in Ubuntu Studio, but one thing that is sorely missed is some type of beat slicer like Recycle. The GD/LN was happy to find one being developed called [Freecycle]("http://freecycle.redsteamrecords.com/"), but has so far had trouble getting it to install at all. With this thread, the GD/LN expresses hope in documenting the install processes in the hopes that:
[LIST]
[*]others might gain insight
[*]offer advice
[*]not go through the crap the GD/LN had to go through to try and get this working
[/LIST]
The GD/LN also hopes that those in charge of Ubuntu Studio might see fit to start including it in their repositories [as some might wish it]("https://wiki.ubuntu.com/UbuntuStudio/Wishlist"). Hope also thrives for the developer to realize the demand for this program on Ubuntu.

**Method One: Running the binary.**
Downloaded the binary from the site. Double-clicked on it. Nothing happened.

**Method Two: Installing from source**
Downloaded and unpacked into my home bin folder. The GD/LN has had some practice with the terminal, but commands like "qmake" confuse the GD/LN. Yet it seems simple according to the README, so:

```
****@****-main:~/bin/freecycle$ qmake freecycle.pro
****@****-main:~/bin/freecycle$ make
cd src/ && /usr/bin/qmake src.pro -unix -o Makefile
Project MESSAGE: Jack includes not found!
Project MESSAGE: ALSA includes found!
Project MESSAGE: libinstpatch includes not found!
Project MESSAGE: aubio includes not found!
Project MESSAGE: SoundTouch includes not found!
Project MESSAGE: Building Freecycle with midi support
uic: File generated with too old version of Qt Designer
uic: File generated with too old version of Qt Designer
uic: File generated with too old version of Qt Designer
uic: File generated with too old version of Qt Designer
uic: File generated with too old version of Qt Designer
cd src/ && make -f Makefile 
make[1]: Entering directory `/home/****/bin/freecycle/src'
/usr/bin/uic-qt4 FFTDialogBase.ui -o ui_FFTDialogBase.h
uic: File generated with too old version of Qt Designer
File 'FFTDialogBase.ui' is not valid
make[1]: *** [ui_FFTDialogBase.h] Error 1
make[1]: Leaving directory `/home/****/bin/freecycle/src'
make: *** [sub-src-make_default] Error 2
****@****-main:~/bin/freecycle$
```

Hmmm. A search in Synaptic under "qt designer" finds I have the packages *libqt4-gui* and *qt4-dev-tools* but not *qt3-designer* or *qt4-designer*. This puzzles the GD/LN. Taking a chance, qt4-designer is installed, giving this output:

```
****@****-main:~/bin/freecycle$ qmake freecycle.pro
****@****-main:~/bin/freecycle$ make
cd src/ && make -f Makefile 
make[1]: Entering directory `/home/****/bin/freecycle/src'
/usr/bin/uic-qt4 FFTDialogBase.ui -o ui_FFTDialogBase.h
uic: File generated with too old version of Qt Designer
File 'FFTDialogBase.ui' is not valid
make[1]: *** [ui_FFTDialogBase.h] Error 1
make[1]: Leaving directory `/home/****/bin/freecycle/src'
make: *** [sub-src-make_default] Error 2
```

The error still remains, just not as prevalent. The GD/LN holds little confidence in the success of the third method.

**Method Three: Is a deb still a deb?**
There is mention on the Freecycle site of debs available from a couple of sources,
[One from the official Debian repositories, but it is version .60-alpha1]("http://packages.debian.org/lenny/freecycle/i386/download")
[Another from a place the GD/LN has never heard of, yet it holds version .60-alpha3]("http://piem.org/debian/unstable/i386/")
The GD/LN likes debs. So simple to install. However, all the ones the GD/LN has dealt with so far were made specifically for Ubuntu. So the question is pondered upon: if Linux is meant to be modular and Ubuntu is based on Debian, would a Debian deb work just as well as an Ubuntu deb? Possibilities of a tounge twister created from that last sentence aside, the GD/LN realizes he is a bit out of his depth here but downloads the testing (lenny) version from the official Debian site because even the GD/LN feels uncomfortable in attempting an install of something clearly marked *unstable*. And so, he cautiosly double-clicks on the deb...

...and it installs.

Wow.

It automatically installed the *libaubio2* package as well, but it seems to have installed with no problems. Starting up the program and loading a wave into it presents no problem. Click on play...no sound.. Ah. The GD/LN remembers that the Flash plugin for Firefox is a jealous mistress who demans attention and cannot abide by any other audio to be played while she is active. The GD/LN shuts down Firefox and stars up Jack and Freecycle.

Heavy sigh. No amount of coaxing from Jack will provoke any sound from Freecycle. Yea, no amount of fiddling even gets Freecycle to *show up* in Jack. Already tasting gunpowder from biting the bullet so far, the GD/LN removes freecycle using Synaptic (a program the GD/LN enjoys as an occasional respite from the terminal) and downloads the alpha-3 deb. Alas, the alpha-3 deb asks for a dependency of *libinstpatch0* which does not seem to be available in Synaptic.

So the path ends here for now. The Freecycle website does warn that Freecycle won't work with the latest Alsa drivers. Conversely, the claim that Freecycle plays well with Jack has been repudiated. 

The GD/LN thusly goes off to lick his wounds, lament the state of audio management in Linux, and read up on the up-and-coming PulseAudio system.

---

