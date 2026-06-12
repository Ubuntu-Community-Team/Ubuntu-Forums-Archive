---
title: "APE, Monkey's Audio and Ubuntu"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by cybertoast on 2007-03-09
Monkey's audio files (APE and the associated CUE files) are not configured by default to work with Ubuntu's burners (either Gnomebaker or K3B). There are the steps I went through to make it work - just sharing in case anyone else needs to do this:

[LIST=1]
[*] Install k3b: sudo apt-get install k3b
[*] Get the Monkey's Audio codecs from the KDE-Apps plugins repository at [http://kde-apps.org/content/show.php?content=11490](http://kde-apps.org/content/show.php?content=11490)
[*] Install KDE libs: sudo apt-get install kdelibs4-dev
[*] Install Qt libs: sudo apt-get install libqt3-mt-dev. The reason for install qt3 libraries is because it appaers that the APE plugins require it. With just qt4 I get the error:
```
checking for Qt... configure: error: Qt (>= Qt 3.1 (20021021) and < 4.0) (headers and libraries) not found. Please check your installation!

```
[*] You'll need the k3b audio encoders/decoders. So, sudo apt-get install libk3b-dev
[*] And you'll also need to sudo apt-get install libhal-dev. I'm not sure why this is necessary, since this is the hardware abstraction layer, which should be part of the k3b core. Why does the APE codec need this? Guess it doesn't matter why - you just do, dammit :-)
[*] Untar/unzip the monkey's audio plugins from step 2 above. Then run the standard install prcess: ./configure && make && sudo make install
[/LIST]
Now when you start up k3b, and go to Settings->Configure k3b... ->Plugins, you'll see the Monkey's Audio entry in the codec list.

So the stupid thing that I did not understand is that the .cue file does all the "work". [this is where i'm going to start making **** up, so pls correct me anyone]. When burning an APE archive, there's usually a .ape file and a .cue file. The .cue file contains all the split-points for the .ape file. So all you need to add to the burn list is the .cue file. I kept adding both the .ape and the .cue and k3b kept bombing on me.

Enjoy

---

### Post by mauro.barrera on 2008-04-06
Very useful post. It helped me a lot. I just used checkinstall to install the plugin and to get a reusable .deb package.

Thank you very much

---

### Post by fjf on 2008-04-06
This should be a HowTo in the turorials section.  Thanks!

---

### Post by carltonh on 2008-07-19
There has to be a more efficient way to play and transcode .ape files if not wanting to install a bunch of KDE files (nothing against them).  Anyone know a simpler way that doesn't install a bunch of extra files?

---

### Post by carltonh on 2008-07-19
I failed at finding a non-KDE alternative so I tried the K3B method above.  Several problems:

Step 2: #  Get the Monkey's Audio codecs from the KDE-Apps plugins repository at [http://kde-apps.org/content/show.php?content=11490](http://kde-apps.org/content/show.php?content=11490)

That website is no longer good, but I was able to use this:
[http://www.k3b.org/download](http://www.k3b.org/download)

Another problem:  For those of us who don't normally install software from source, the first post is missing these dependency:

sudo apt-get install g++ nasm

It is sadly the case that I couldn't find any other way to convert .ape files in Linux or Windows.  Winamp has a plug-in that plays .ape files, but you have to by the Winamp pro version to be able to burn it to CD to convert it to a more common format.

---

