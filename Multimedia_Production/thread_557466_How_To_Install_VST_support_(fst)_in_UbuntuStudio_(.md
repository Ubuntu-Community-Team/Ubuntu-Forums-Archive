---
title: "How To: Install VST support (fst) in UbuntuStudio (also applicable to other Ubuntus)"
date: 2007-09-22
forum: Multimedia Production
---

### Post by Stochastic on 2007-09-22
Hi, this is one of the first How Tos I've written on here so any assistance in formatting/editing/etc... is greatly appreciated.  This is a walk through of how I installed fst - the linux vst host - on my UbuntuStudio Feisty install.

1.)First, you'll need a few pieces of software installed.
```
sudo apt-get install qjackctl lashd liblash-dev wine wine-dev libgtk2.0-dev
``` ***these packages are the only ones I have proof that are needed, I assume there are others such as gcc that will be used in the make process.

2.)Second, you'll need to download two packages from two different websites.  Ardour's website claims that the Steinberg VST 2.3 SDK is the version that you should install.  Get that here: [http://www.steinberg.de/331+M52087573ab0.html](http://www.steinberg.de/331+M52087573ab0.html) MAKE SURE TO GET 2.3 and yes, you have to agree to Steinberg's terms.
Also you'll need the fst 1.8 file [http://joebutton.co.uk/fst/](http://joebutton.co.uk/fst/) or a direct link to the file [http://galan.sf.net/fst-1.8.tar.gz](http://galan.sf.net/fst-1.8.tar.gz)

3.) Untar the fst file to your desired location.  This should create a directory called fst1.8

4.) Unzip the vst_sdk_2_3.zip file to your desktop.  This will have created three new files on your desktop: vstsdk2.3.zip, a .sit, and a .dmg  we will only be using the .zip file but until the process is finished you should leave all three on the desktop.  It's safe to delete all three once fst is installed.

5.) Unzip the new vstsdk2.3.zip file so that the destination is in the previously created fst1.8 folder.

6.) Now open a terminal and go to the fst1.8 folder ```
cd fst1.8
```

7.) Make a directory here called vst ```
mkdir vst
```

8.) move files as shown here: ```
 mv vstsdk2.3/source/common/* vst/
```

9.) now this next step I must give credit to The Muso in the UbuntuStudio IRC channel as I would have been lost here otherwise.  Here are his words: > <TheMuso> Open the Makefile in an editor, and look for the line starting with LIBRARIES
<TheMuso> Its right under LIBRARY_PATH
<TheMuso> At the end of that line, right after -lX11, add a space, followed by -lpthread
<TheMuso> Save the file

10.) ```
make
```  *** if you get errors at this stage you're probably missing some programs/libraries that I already had installed so I didn't take note of.  Let me know which ones those are and I'll add them to the first step.  Also if you need to make a second time, first go into the fst1.8 folder and delete the vstsdk2.3.zip, .sit, and .dmg files as these are remade each time you 'make' and make doesn't have the brains to ignore that step if they're already there.

That should be all.  You should have created an executable in the fst1.8 folder named fst and now to run your vst plugins make sure lashd is running, jackd (preferably qjackctl) is running, and do ```
./fst <path to your .dll file here>
```

To get vst/fst support into ardour follow these instructions: [http://ardour.org/building_vst_support](http://ardour.org/building_vst_support)

Happy jammin.

---

### Post by orange2k on 2007-09-24
Great how-to...:guitar:
Gonna try it later today to see if it works for me...

---

### Post by darklincomp on 2007-09-24
First thanks for the tutorial but hmm... I might just really be noobing this one (apparently this post precedes mine by just a day), but is seems like this is already out of date. 

When I downloaded the sdk 2.3 files, and I tried from both the direct link and the other link supplied, I received a similarly named file (preceded by a "d") which neither produced the three files mentioned in the tutorial nor created a directory structure anything like what is mentioned in succeeding steps.

as I said, hmm. Looks like the tutorial or the file links need to be updated. Going looking for another way.

---

### Post by darklincomp on 2007-09-24
Ok, apparently the vst sdk file that I downloaded was for Delphi *?...:( anyway, I found the file that adour wants (for my system) here:

[http://www.steinberg.de/331+M52087573ab0.html](http://www.steinberg.de/331+M52087573ab0.html)

(and selected 2.3)

Looks like Steinberg is moving these files around alot.

---

### Post by Stochastic on 2007-09-24
yeah Steinberg does move the files quite a bit. Upon further review I realized that your link is the right one and I was mistaken.  It's fixed now.  Are you still having troubles or is it sorted out now?

---

### Post by Anbech on 2007-10-16
ey mates

i just registrered in here, because im a total noob at linux.. 
and im used to Fruityloops, so the vst support is really needed for me to use..  so ive tried the guide here at the topic, but i get some errors, wich i dont know why i do.. 

but, here is a copy+paste of the errors in the terminal.. 

anbech@anbech-desktop:~/Desktop/fst-1.8$ make
cp -a `find . | grep 'vstsdk[^/]*\$'`/source/common ./vst
sed -i '/struct VstFileType\|struct VstFileSelect/,/};/d' vst/aeffectx.h
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o audiomaster.o audiomaster.c
Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
No package 'jack' found
Package jack was not found in the pkg-config search path.
Perhaps you should add the directory containing `jack.pc'
to the PKG_CONFIG_PATH environment variable
Package 'jack', required by 'LASH', not found
In file included from audiomaster.c:23:
jackvst.h:6:23: error: jack/jack.h: No such file or directory
jackvst.h:7:29: error: jack/ringbuffer.h: No such file or directory
jackvst.h:9:28: error: alsa/asoundlib.h: No such file or directory
In file included from audiomaster.c:23:
jackvst.h:14: fejl: expected specifier-qualifier-list before ‘jack_client_t’
audiomaster.c: In function ‘jack_host_callback’:
audiomaster.c:49: fejl: ‘jack_position_t’ undeclared (first use in this function)
audiomaster.c:49: fejl: (Each undeclared identifier is reported only once
audiomaster.c:49: fejl: for each function it appears in.)
audiomaster.c:49: fejl: expected ‘;’ before ‘jack_pos’
audiomaster.c:50: fejl: ‘jack_transport_state_t’ undeclared (first use in this function)
audiomaster.c:50: fejl: expected ‘;’ before ‘tstate’
audiomaster.c:106: fejl: ‘tstate’ undeclared (first use in this function)
audiomaster.c:106: fejl: ‘JackVST’ has no member named ‘client’
audiomaster.c:106: fejl: ‘jack_pos’ undeclared (first use in this function)
audiomaster.c:114: fejl: ‘JackPositionBBT’ undeclared (first use in this function)
audiomaster.c:119: advarsel: incompatible implicit declaration of built-in function ‘floor’
audiomaster.c:124: fejl: ‘JackTransportRolling’ undeclared (first use in this function)
winegcc: i486-linux-gnu-gcc failed.
make: *** [audiomaster.o] Fejl 2
anbech@anbech-desktop:~/Desktop/fst-1.8$ ./fst /media/C/Programmer/VstPlugins/Pro-53.dll
bash: ./fst: No such file or directory
anbech@anbech-desktop:~/Desktop/fst-1.8$ .fst /media/C/Programmer/VstPlugins/Pro-53.dll
bash: .fst: command not found
anbech@anbech-desktop:~/Desktop/fst-1.8$ fst /media/C/Programmer/VstPlugins/Pro-53.dll
bash: fst: command not found
anbech@anbech-desktop:~/Desktop/fst-1.8$ /fst /media/C/Programmer/VstPlugins/Pro-53.dll
bash: /fst: No such file or directory
anbech@anbech-desktop:~/Desktop/fst-1.8$ 

btw, "Fejl" means Error in danish.. :)

hope some of u guys in here is able to help me out.. thx in advance..

-Anbech

---

### Post by Tom Mann on 2007-10-16
I would suggest overkill on dev libraries which (going by Ardour's site) should work out as follows:

```

sudo aptitude -y install build-essential scons libtool gettext

sudo aptitude -y install libjack0.100.0-dev libxml2-dev libxslt-dev libart-dev libsamplerate-dev libraptor-dev liblrdf-dev libart-2.0-dev libglib2.0-dev libgtk2.0-dev libgnomecanvas2-dev liblo-dev libboost-dev libasound-dev

```

And try the instructions again. Switch aptitude for apt-get if you use that method to install.

---

### Post by glangollor on 2007-11-03
Mhh I always have some linker errors when I try 'make'
(Running Gutsy on amd64)
Has anybody a solution for this?
```

/usr/bin/ld: skipping incompatible /usr/lib64/libgtk-x11-2.0.so when searching for -lgtk-x11-2.0
/usr/bin/ld: skipping incompatible /usr/lib64/libgtk-x11-2.0.a when searching for -lgtk-x11-2.0
/usr/bin/ld: skipping incompatible /usr/lib64/libgtk-x11-2.0.so when searching for -lgtk-x11-2.0
/usr/bin/ld: skipping incompatible /usr/lib64/libgtk-x11-2.0.a when searching for -lgtk-x11-2.0
/usr/bin/ld: skipping incompatible /usr/lib/libgtk-x11-2.0.so when searching for -lgtk-x11-2.0
/usr/bin/ld: skipping incompatible /usr/lib/libgtk-x11-2.0.a when searching for -lgtk-x11-2.0
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libgtk-x11-2.0.so when searching for -lgtk-x11-2.0
/usr/bin/ld: skipping incompatible /usr/bin/../lib/libgtk-x11-2.0.a when searching for -lgtk-x11-2.0
/usr/bin/ld: skipping incompatible /usr/lib/libgtk-x11-2.0.so when searching for -lgtk-x11-2.0
/usr/bin/ld: skipping incompatible /usr/lib/libgtk-x11-2.0.a when searching for -lgtk-x11-2.0
/usr/bin/ld: cannot find -lgtk-x11-2.0
collect2: ld gab 1 als Ende-Status zurück
winegcc: gcc failed.
make: *** [fst.exe] Fehler 2


```
Thank you for your help

---

### Post by hogiewan on 2008-01-03
is this possible in 64 Bit US?

---

### Post by abalone on 2008-03-24
Fantastic How-To, but I have to third the above comments... no luck anymore on 64 bit. Lots of warnings about "incompatible pointer types" and incopatible "implicit declarations of built-in function" (floor, malloc) ...then the ld errors posted before (sorry, warnings translated from German)

---

### Post by robeast on 2008-03-24
Hey Stochastic, this rules! I've seen lots of questions concerning VST plugins so I'm psyched you took the time to write up this HOWTO. I'll be trying this out later.

---

### Post by drumanart on 2008-05-19
As root "make" and I get the errors:


root@martin-desktop:/home/martin/downloads/fst-1.8# make
cp -a `find . | grep 'vstsdk[^/]*\$'`/source/common ./vst
sed -i '/struct VstFileType\|struct VstFileSelect/,/};/d' vst/aeffectx.h
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o audiomaster.o audiomaster.c
winegcc: gcc-3.4 failed
make: *** [audiomaster.o] Error 2
root@martin-desktop:/home/martin/downloads/fst-1.8# 

Any idea Thks

---

### Post by ezramorris on 2008-06-03
> **drumanart said:**
> As root "make" and I get the errors:


root@martin-desktop:/home/martin/downloads/fst-1.8# make
cp -a `find . | grep 'vstsdk[^/]*\$'`/source/common ./vst
sed -i '/struct VstFileType\|struct VstFileSelect/,/};/d' vst/aeffectx.h
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o audiomaster.o audiomaster.c
winegcc: gcc-3.4 failed
make: *** [audiomaster.o] Error 2
root@martin-desktop:/home/martin/downloads/fst-1.8# 

Any idea Thks

Did you try installing the packages in post 7?

---

### Post by oystercake on 2008-06-06
Thank you very much for the tutorial, helping to ease the transition onto ubuntu from windows, except - 


```

cp -a `find . | grep 'vstsdk[^/]*\$'`/source/common ./vst
sed -i '/struct VstFileType\|struct VstFileSelect/,/};/d' vst/aeffectx.h
winegcc -c  `pkg-config --cflags gtk+-2.0` `pkg-config --cflags jack` `pkg-config --cflags jack` `pkg-config --cflags lash-1.0` -DHAVE_LASH -I.   -o audiomaster.o audiomaster.c
Package alsa was not found in the pkg-config search path.
Perhaps you should add the directory containing `alsa.pc'
to the PKG_CONFIG_PATH environment variable
Package 'alsa', required by 'LASH', not found
In file included from audiomaster.c:23:
jackvst.h:9:28: error: alsa/asoundlib.h: No such file or directory
In file included from audiomaster.c:23:
jackvst.h:29: error: expected specifier-qualifier-list before ‘snd_seq_t’
audiomaster.c: In function ‘jack_host_callback’:
audiomaster.c:119: warning: incompatible implicit declaration of built-in function ‘floor’
winegcc: i486-linux-gnu-gcc failed
make: *** [audiomaster.o] Error 2

```


I've installed all the packages advised in post 7 (since i was sharing the previous users troubles), but now i'm left with that.

I'm a linux newbie so sorry if i've missed anything obvious!


Thanks

---

### Post by Stochastic on 2008-06-06
Oystercake, it looks like you're missing some alsa libs.  Try installing libasound2-dev

---

### Post by russo.mic on 2008-06-20
> **ezramorris said:**
> Did you try installing the packages in post 7?


So, Same problem and I've got the packages installed...seems like a simple path error, but I can't seem to figure it out.

Russo

---

