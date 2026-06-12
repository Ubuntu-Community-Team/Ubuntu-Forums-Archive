---
title: "Attempting install of ProjectM for Amarok in Gnome on x86"
date: 2006-10-31
forum: Multimedia &amp; Video
---

### Post by seaward on 2006-10-31
I'm trying to install ProjectM (Milkdrop visualisations) for Amarok in the Gnome environment on x86 architecture.  Has anyone had any success doing this?  I am hitting a brick wall when trying to compile libprojectM.  I am getting hundreds and hundreds of glx.h errors, ending with this one:

/usr/include/GL/glx.h:533: error: expected ';' before '*' token
make[2]: *** [beat_detect.lo] Error 1
make[2]: Leaving directory `/home/scotty/temp/projectM/libprojectM/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/scotty/temp/projectM/libprojectM'
make: *** [all] Error 2

Ho hum.  Its all very confusing and I've been through quite a few forums and howtos in attempting to get this to work.  I have also tried installing under KDE but it made absolutely no difference.

Libvisual is definitely installed because I have other libvisual plugins working fine in Amarok.

Anyone have a clue as to what I am missing here?  Or does anyone know where I can get some precompiled binaries for x86?  I've seen others built for amd64 but I get the feeling they wouldnt be accepted into my system.

Cheers!

---

### Post by grimdestripador on 2006-12-18
I have a pretty clean install of edgy Ubuntu. 
I'm running AMD64, but don't know if its 64 code or 32.... Probably won't matter since i'm compiling.
This Has been tested with Edgy and Feisty
[SIZE="4"]
The following Installs ProjectM Visualization (Milkdrop for Linux) for XMMS and AMAROK[/SIZE]

goto [http://xmms-projectm.sourceforge.net/]("http://xmms-projectm.sourceforge.net/")
and download the links on the left, or run the following URLs if they still work.

```

wget http://superb-west.dl.sourceforge.net/sourceforge/xmms-projectm/libprojectM-0.99.tar.bz2
wget http://umn.dl.sourceforge.net/sourceforge/xmms-projectm/libvisual-projectM-0.99.tar.bz2
wget http://umn.dl.sourceforge.net/sourceforge/xmms-projectm/xmms-projectM-0.99.tar.bz2
wget http://superb-west.dl.sourceforge.net/sourceforge/xmms-projectm/xmms-projectM-pbuffers-0.99.tar.bz2
```

[LIST=1]
[*]Make A Directory called "InstallProjectM" in your home folder.
[*]Extract Each downloaded file into ~/InstallProjectM
[*]Run the following CODE
[/LIST]

```
 ##Compiler tools##
	sudo apt-get install -y build-essential
	sudo apt-get install -y libglib1.2-dev
	sudo apt-get install -y libgtk1.2-dev
	sudo apt-get install -y libsdl1.2-dev
	sudo apt-get install -y xmms-dev
	
##Get Ubuntu's Libvisual###
	sudo apt-get install -y libvisual-0.4-dev
	sudo apt-get install -y libvisual-0.4-plugins

##Open GL Fonts##
	sudo apt-get install -y ftgl-dev

##Extract libProjectM and build##
	cd ~/InstallProjectM/libprojectM/
	./configure
	make
	sudo make install

##Extract libvisual-projectM and build##
	cd ~/InstallProjectM/libvisual-projectM
	./configure --x-includes=/usr/include/X11 --x-libraries=/usr/lib/X11
	make
	sudo make install

##Extract xmms-projectM and build##
	cd ~/InstallProjectM/xmms-projectM
	./configure
	make
	sudo make install
```

---

### Post by grimdestripador on 2006-12-18
I'm unsure why I had you download the pbuffer file, but it seems to work without installing it.

I then, ./configure && make && sudo make install for the pbuffer. And it seems to work that way too,

---

### Post by x1um1n on 2007-03-22
Hi,
I'm following your howto, but get this error on the first compile..

```
/usr/bin/ld: /usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libftgl.a(FTFont.o): relocation R_X86_64_32S against `vtable for FTFont' can not be used when making a shared object; recompile with -fPIC
/usr/lib/gcc/x86_64-linux-gnu/4.1.2/../../../../lib64/libftgl.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [libprojectM.la] Error 1

```

this is a brand new (installed yday) fully updated edgy eft running on an acer aspire 5630 (IA_64)

any help'd be much appreciated :)

EDIT:

ok, found this thread: [http://www.ubuntuforums.org/showthread.php?t=249818&highlight=projectM]("http://www.ubuntuforums.org/showthread.php?t=249818&highlight=projectM")

installed the modified ftgl-dev package, and this compiles perfectly

---

### Post by m910q on 2007-03-24
I had to do a
```
sudo apt-get install libsdl-dev
```
before configureing

---

### Post by grimdestripador on 2007-04-06
sometimes those dependencies.....
good to know

---

### Post by wonkycyber on 2007-04-09
Yoyo; I'm trying to get ProjectM running in Kubuntu to little or no avail. It seems to be installed correctly, but when it's actually running there's all sorts of weird flickering, bad overlay effects, etc.... bringing it to full screen makes the menubar go to some kind of funky resolution, and the thing goes slow as all hell. I'm running a Dell Inspiron E1705, with the integrated graphics card... anyone have any idea what type of problem I might be having? danke

---

### Post by funpop on 2007-04-18
error when compiling libvisual part of it:

```
configure: WARNING: *** No OpenGL found.
                projectm plugin will not be built.
checking wheter to enable profiling... no
checking whether to enable debug... no
checking wheter to enable extra optimizations... no
checking where to install plugins... /usr/lib/libvisual-0.4
configure: error: conditional "HAVE_LIB_GL" was never defined.
Usually this means the macro was only invoked conditionally.
```

any advice ? i got working openGL here, (glx gears and some 3D games like nexuiz, openarena)

any advice would be much appreciated

---

### Post by funpop on 2007-04-20
```
./configure --x-includes=/usr/include/X11 --x-libraries=/usr/lib/X11 
```

worked when configuring like this :D

---

### Post by Cresho on 2007-05-26
yes this worked out just for me as well.

Here is the updated information.

sudo apt-get install automake1.9 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev

and also install these through synaptic incase you dont have it.

libgl1-mesa-dev
libglu1-mesa-dev
libx11-dev
libfreetype6-dev
ftgl-dev
zlib1g-dev

then we download the files.

wget [http://superb-west.dl.sourceforge.net/sourceforge/xmms-projectm/libprojectM-0.99.tar.bz2](http://superb-west.dl.sourceforge.net/sourceforge/xmms-projectm/libprojectM-0.99.tar.bz2)
wget [http://umn.dl.sourceforge.net/sourceforge/xmms-projectm/libvisual-projectM-0.99.tar.bz2](http://umn.dl.sourceforge.net/sourceforge/xmms-projectm/libvisual-projectM-0.99.tar.bz2)
wget [http://umn.dl.sourceforge.net/sourceforge/xmms-projectm/xmms-projectM-0.99.tar.bz2](http://umn.dl.sourceforge.net/sourceforge/xmms-projectm/xmms-projectM-0.99.tar.bz2)
wget [http://superb-west.dl.sourceforge.net/sourceforge/xmms-projectm/xmms-projectM-pbuffers-0.99.tar.bz2](http://superb-west.dl.sourceforge.net/sourceforge/xmms-projectm/xmms-projectM-pbuffers-0.99.tar.bz2)

then we have to extract in a directory.

   1. Make A Directory called "InstallProjectM" in your home folder.
   2. Extract Each downloaded file into ~/InstallProjectM
   3. Run the following CODE


and last we run the code

##Compiler tools##
	sudo apt-get install -y build-essential
	sudo apt-get install -y libglib1.2-dev
	sudo apt-get install -y libgtk1.2-dev
	sudo apt-get install -y libsdl1.2-dev
	sudo apt-get install -y xmms-dev
	
##Get Ubuntu's Libvisual###
	sudo apt-get install -y libvisual-0.4-dev
	sudo apt-get install -y libvisual-0.4-plugins

##Open GL Fonts##
	sudo apt-get install -y ftgl-dev

##Extract libProjectM and build##
	cd ~/InstallProjectM/libprojectM/
	./configure
	make
	sudo make install

##Extract libvisual-projectM and build##
	cd ~/InstallProjectM/libvisual-projectM
	./configure
	make
	sudo make install

##Extract xmms-projectM and build##
	cd ~/InstallProjectM/xmms-projectM
	./configure
	make
	sudo make install



and in amarok, right click on the visualization and and choose project m at the bottom. so there you have it.  Now you have an awsome milkdrop like winamp on the amarok.  it takes 10 seconds before it starts to show visualization and also, you can configure through /usr/local/share/projectM

---

### Post by runesvend on 2007-06-06
When executing the *./configure* command in the directory "~/InstallProjectM/libvisual-projectM" I get the following error:

configure: WARNING: *** No OpenGL found.
                projectm plugin will not be built.
checking wheter to enable profiling... no
checking whether to enable debug... no
checking wheter to enable extra optimizations... no
checking where to install plugins... /usr/lib/libvisual-0.4
configure: error: conditional "HAVE_LIB_GL" was never defined.
Usually this means the macro was only invoked conditionally.


I have followed all the steps prior to this...

---

### Post by runesvend on 2007-06-06
Apparently I had to run it like so:

./configure --x-includes=/usr/include/X11 --x-libraries=/usr/lib/X11

Now it works :)

---

### Post by k84 on 2007-12-23
Hi, I finally got it to work!!; now i'm running the 1.01 version which doesn't come with a configure file but rather you have to create the make file with "cmake". For the ones that are trying this version you might wanna make a link from freetype2 in the include folder to say just "freetype" otherwise you are gonna get lots of errors when running make. This plugin is awesome!

---

