---
title: "KDEnlive"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by inuz on 2007-01-15
i shifted to Ubuntu from XP and had adobe to edit videos.
I want to know how can i get and install KDEnlive or other similar software to edit non-linear videos....i have downloaded a folder KDEnlive0.4 version[it has many files; extracted]  on my desktop but i dont know how to install on my system...plz help me..i am using Gnome...how can i go to KDE?
thanks

---

### Post by Richard Kut on 2007-01-15
Hello. From looking at the KDEnlive web site here [http://www.uchian.pwp.blueyonder.co.uk/kdenlive/documentation/handbook/en/requirements.html](http://www.uchian.pwp.blueyonder.co.uk/kdenlive/documentation/handbook/en/requirements.html) it says that you need a KDE environment to run the software.

 KDE, in case you did not know, is another graphical environment (and used by Kubuntu) for UNIX and Linux, like the GNOME environment which is used for Ubuntu. Anyhow, to get KDE setup on your PC, type the following at a command prompt:

sudo apt-get install kubuntu-desktop

That should provide the KDE files that you need. Good luck!

---

### Post by inuz on 2007-01-15
thnks a lot and i am downloading KDE on my comp....but what should i do in order to load KDEnlive on my comp...plz suggest...Ubuntu inbuilt Kino is not what i need...has any one used KDEnlive and is it better than Adobe Premier 6?
inuz

---

### Post by kuja on 2007-01-15
You'll find a more complete post one post down.

---

### Post by kuja on 2007-01-15
From the looks of the kdenlive installation information page, it looks like you'll indeed have to compile the program. What you downloaded was the programs source code, here is what you'll need to do to install using that. 
Imporant: MLT might not build successfully, at least it failed to build for me on kubuntu edgy x86_64.

Note: Not all lines are copy&pastable, the CVS related lines will break your copy and paste, near the end I also don't know where you're storing the kdenlive source directory.
```

## First, you need these packages installed
sudo aptitude install kde-core kdebase-dev kdelibs4-dev libarts1-dev libkonq4-dev libqt3-mt-dev cvs subversion debhelper debconf fakeroot build-essential unsermake libsamplerate0 libsamplerate0-dev libogg0 libogg-dev libvorbis0a libvorbis-dev libdv4 libdv4-dev ladspa-sdk libjack0.100.0-0 libjack0.100.0-dev sox sox-dev libxml2 libxml2-dev libquicktime0 libquicktime-dev libtheora libtheora-dev libsdl1.2-dev libsdlimage1.2-dev libsdl1.2debian-all libsdl-image1.2 libavformat0d libavformat-dev

## For FFMPEG
cd
svn checkout svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg
./configure --enable-gpl --enable-shared --enable-vorbis --enable-libogg --enable-pp
 && make
 && sudo make install

## For MLT
cd
cvs -d:pserver:anonymous@mlt.cvs.sourceforge.net:/cvsroot/mlt login
cvs -z3 -d :pserver:anonymous@mlt.cvs.sourceforge.net:/cvsroot/mlt co mlt 
cd mlt
export DEB_BUILD_OPTIONS="--enable-gpl --enable-shared --enable-theora --enable-vorbis --enable-libogg --enable-pp --enable-shared-pp --enable-motion-est" 
 && fakeroot debian/rules binary
cd ..
dpkg -i *.deb
rm *.deb


## For MLT++
cd
cvs -d:pserver:anonymous@mlt.cvs.sourceforge.net:/cvsroot/mlt login
cvs -z3 -d :pserver:anonymous@mlt.cvs.sourceforge.net:/cvsroot/mlt co mlt++
cd mlt++
fakeroot debian/rules binary
cd ..
dpkg -i *.deb
rm *.deb


## And finally, the part we've all be waiting for
cd thekdenlivedirectory #this line not copy and pastable
./configure
 && make
 && sudo make install

```

I'm merely assuming this is all you need, if/when you run into problems, post back.

---

### Post by uuwatti on 2007-01-15
[look here.]("http://www.ubuntuforums.org/showthread.php?t=322916") It's not better than Premiere, but it is the best (IMO) open-source NLE. The development is really fast and I can honestly that this probably one of the most promising open-source projects atm. It doesn't have any proper color correction tools and it is missing some essential tools like chroma keying. A titling tool is added to the latest svn.
Also read the first few lines here.-->[http://kdenlive.sourceforge.net/wiki/index.php?title=Faq_Install]("http://kdenlive.sourceforge.net/wiki/index.php?title=Faq_Install")

---

### Post by kuja on 2007-01-15
Actually, no, MLT failed to build for some other reason, errors in assembly code of some sort  I think.

---

### Post by uuwatti on 2007-01-15
yeah I edited my post as I realized you are on 64-bit system. Did you try installing from the .debs? Also jahshakas repositories have mlt and mlt++. [http://repo.jahshaka.org/ubuntu/dapper/binary-i386/]("http://repo.jahshaka.org/ubuntu/dapper/binary-i386/")

---

### Post by kuja on 2007-01-15
Didn't really have a strong enough interest to pursue it, I just clicked on the post because it looked interesting and it was on the front. Figured I'd take 10 minutes out of my day and (try to) answer it as well. It looks like that repo is i386 only, so it wouldn't work for me, thanks anyway though uuwatti. On a side note though, I got mlt to compile, had to play with the configure options to get it to though. I'll give this program a try and see what it's like.

---

