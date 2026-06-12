---
title: "How-To AUREAL VORTEX CONTROL 3D Sound Speaker test etc"
date: 2008-07-31
forum: Multimedia Software
---

### Post by loboc on 2008-07-31
Okay So if you have an old aureal card sitting around or in your computer right now you are sitting pretty because alsa supports it with the [au88X0 drivers]("http://alsa.opensrc.org/index.php/Au88x0").  

If you ever have used it in windows you know it has some extra features software rendering of 3D sound and other tricks.  

This how to will install this [little utility]("http://lists.nongnu.org/archive/html/openvortex-dev/2005-06/pngCc7d96YsiT.png") that was written back when those alsa drivers were written that may help you use some other features of your card.  Mine was only an au8810 so I haven't been able to fully test it. 

First get some build essentials for code compiling

```

sudo apt-get install build-essentials checkinstall 

```

Now we need to get the source from [the old gnu project site]("http://savannah.nongnu.org/support/?func=detailitem&item_id=103017")

Source Link: 

[http://savannah.nongnu.org/file/vortexcontrol-0.1.0.tar.bz2?file_id=3959](http://savannah.nongnu.org/file/vortexcontrol-0.1.0.tar.bz2?file_id=3959)

Extract that to a folder with your archive tool or the terminal:

```

tar -xjf vortexcontrol-0.1.0.tar.bz2 
cd vortexcontrol

```

Now we need to get all the development libraries.  I installed thess in groups by trial and error so I am not sure if they are all needed.

```
 sudo apt-get install  libopenal-dev libalut-dev libopenal0a libesd0-dev libgtk2.0-0 libgtk2.0-dev libasound2-dev

```

I had to install the intrepid versions of the libasound2 and libasound2-dev because of some dependency error in Hardy with Backports. You may not have that problem if you have standard hardy or gutsy or intrepid or whatever. 

Go to packages.ubuntu.org use the search feature for the libasound packages and manually download and install them using gdebi if the apt-get command above fails.   


Now we can follow the steps listed on the original site each one of these should complete without any errors now that you have the dependencies met. Make sure you are in the directory that you extracted. It should look like this:
```
 ls
 
acinclude.m4  configure.in-gtk2  README
configure.in  Makefile.am        vortexcontrol.c

```

These are the compiling commands they link things and assembly the makefile.

```
aclocal
autoconf
autoheader
automake -a
./configure 

```

aclocal is the one that I had the most trouble with it you get a 

" macro `AM_PATH_ALSA' not found in library" error you are missing 
libasound2-dev. And etc for other libraries.

Now we build and install a debian package using the make replacment checkinstall so we can remove it easily if need be. 

```


sudo checkinstall

```

Follow the prompts and now you should have a Aureal Vortex Utility run from the command line with

```
 vortexcontrol& 
```

Post any problems or if you get it to work with au8820 or au8830 cards like those listed at the alsa site:

Known supported cards (please add to this list, if the driver works for you as well):

    * Diamond Monster Sound MX300
    * Aureal SuperQuad Digital
    * Aureal SQ2500
    * Turtle Beach Montego II
    * Turtle Beach Montego 3DXtream
    * Digital Research Vortex 2
    * Diamond Sonic Impact S90
    * Trust Sound Expert 128 PCI
    * AzTech PCI 338-A3D (under 2.4.22 Kernel NOT 2.6.0) 

Supported features:

    * Quad speaker surround
    * Hardware EQ

---

