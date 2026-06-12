---
title: "Can anyone recommend me a music player?"
date: 2008-12-11
forum: Multimedia Software
---

### Post by SirSigma on 2008-12-11
I've done a lot of digging for the perfect Linux music player for Intrepid. I'm basically looking for something that plays music smoothly, retrieves podcasts successfully, and, if possible, can sync with my Creative Zen Vision M.

First I tried Rhythmbox. After getting the required synaptic packages, it was able to sync with my Creative Zen, but I wasn't able to find an option to transfer music into it, which made the feature seem pointless. Rhythmbox also had the problem of skipping or stuttering when I scrolled web pages or typed. I searched Google for a possible fix and couldn't really find anything. It was a shame since Rhythmbox had the best-looking interface to me.

I tried out Exaile and was satisfied, and I even had the MTP device plugin for it, but the deal breaker was how it was unable to sync with my Creative Zen. When connecting with the device and "Reading tracks..." was displayed, Exaile would spontaneously close on me before displaying anything on my device. I searched Google for how to get this working, and all I found was documentation from the man who created the MTP plugin for Exaile on how he was "going to fix this" or "going to fix that." I don't remember even bothering with podcasts on it. But it did play music smoothly.

I then gave Banshee a shot. Same problem as Exaile on connecting to my device, but no results from Google on what was wrong.

I tried out Amarok and was satisfied that it was able to actually transfer songs to my Creative Zen Vision M, retrieve podcasts, and play smoothly. Unfortunately, it kind of ran slow sometimes, even nearly freezing up when I have Firefox open. But I was able to get past this until I tried to transfer 86 songs in a setlist into my device at once. After getting 15 songs or so (give or take) in, Amarok would display an error message on how Kmail (which I don't have installed) wouldn't open and then crash after I clicked the "OK" button on the message. I thought it might have possibly been that I was transferring too many songs, so I tried to cut off the live album of the artist I wanted to transfer, which cut off a good 24 songs. After deleting what got into my device (playlist and all, to start fresh) and trying again, Amarok displayed the error message on Kmail again, but only after getting to the second song on the list. I tried uninstalling Amarok and using autoremove, then reinstalling, but the settings seem to be the same when I reinstalled it (Amarok remembered my library and podcasts).

Now I've gotten rid of Amarok. I have no idea what player I should use now. Any suggestions or players I haven't tried yet? Or any possible solutions or work-arounds to the problems I've described above?

---

### Post by zeronothing on 2008-12-11
I too have a creative zen and I use banshee. what i had to do is update libmtp which is used too connect to devices like the zen. after i updated that banshee ran great plus was able to transfer music to the zen. I have had similar problems with exaile closing on me as well. if you need help updating libmtp or if that is even an option you want to get let me know. you might want to make sure you grabbed the most up too date version of banshee which is 1.4.

---

### Post by SirSigma on 2008-12-11
Oh, is there any way I can update libmtp then?

---

### Post by zeronothing on 2008-12-11
you will have to download the source code from the libmtp site and compile it, which isn't too hard. this is how I had to update libmtp by compiling the newest code.

---

### Post by SirSigma on 2008-12-11
Do you know how to compile this? Last time I tried to compile something, I was very unsure of what I was doing and I gave up.

---

### Post by zeronothing on 2008-12-11
also you might want to try installing the newest banshee. if you are using intrepid 8.10 you can install the newest banshee using these steps:

1. open terminal and type - sudo gedit /etc/apt/sources.list

2. go to the bottom of the file

3. add this to the bottom of the file:
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main

4. hit the save button on gedit at the top

5. close the gedit program

6. open up synaptic and hit the reload button

7. search for banshee and  install. this should install the newest 1.4 version

---

### Post by SirSigma on 2008-12-11
> **zeronothing said:**
> also you might want to try installing the newest banshee. if you are using intrepid 8.10 you can install the newest banshee using these steps:

1. open terminal and type - sudo gedit /etc/apt/sources.list

2. go to the bottom of the file

3. add this to the bottom of the file:
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main

4. hit the save button on gedit at the top

5. close the gedit program

6. open up synaptic and hit the reload button

7. search for banshee and  install. this should install the newest 1.4 version

I just tried doing this. I got Banshee installed and everything, but like I said in the first post, when it reads my device, it closes spontaneously like Exaile does.

---

### Post by zeronothing on 2008-12-11
then compiling the newest libmtp will fix that. here is the link to the site [http://libmtp.sourceforge.net/index.php](http://libmtp.sourceforge.net/index.php)

---

### Post by SirSigma on 2008-12-11
> **zeronothing said:**
> then compiling the newest libmtp will fix that. here is the link to the site [http://libmtp.sourceforge.net/index.php](http://libmtp.sourceforge.net/index.php)

I have that downloaded, but I don't know how to compile it.

---

### Post by zeronothing on 2008-12-11
before you get started with compiling code, make sure you install:

build-essentials

you can do this using synaptic

next go to where you downloaded the source and you need to extract it by right clicking it and select extract

next you will want to open up terminal and "cd" into the folder you just extracted

once your inside the folders directory enter this command:
./configure

during this process is where you might run into errors. any errors you run into post back here. if you dont run into any errors execute this command next:
make

if all goes well during the make process next run this command:
sudo make install

if this goes well then you have installed the latest libmtp but their is one more step but let me know when you get to here.

---

### Post by SirSigma on 2008-12-11
When you get back to this, I have this error when I get to "./configure"
```

sigma@Sigma-Laptop:~/libmtp-0.3.3$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking how to recognize dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 1572864
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for doxygen... false
configure: WARNING: *** doxygen not found, docs will not be built
checking if the host operating system is Darwin... no
checking For MinGW32... no
checking for usb_control_msg in -lusb... no
configure: error: I can't find the libusb libraries on your system. You
	may need to set the LDFLAGS environment variable to include the
	search path where you have libusb installed before running
	configure (e.g. setenv LDFLAGS=-L/usr/local/lib)
```

---

### Post by kpkeerthi on 2008-12-11
1. You need to install the source (dev) dependencies to compile libmtp. The easiest way to get all libmtp dev dependencies is to run this command:
```
sudo apt-get build-dep libmtp
```

2. Now run ./configure, make and **[checkinstall]("https://help.ubuntu.com/community/CheckInstall")** as usual

Yes. Use checkinstall instead of make install so the package manager knows it (the new libmtp, that is) exists and can later be removed or downgraded easily.

EDIT: Also see [https://help.ubuntu.com/community/AutoApt](https://help.ubuntu.com/community/AutoApt)

---

### Post by SirSigma on 2008-12-11
Didn't work anyway! I was able to compile and install libmtp, but Banshee still gets to loading "2051 of 2052" songs on my device and then shuts off spontaneously.

I don't get it!

---

### Post by zeronothing on 2008-12-11
how did you install it libmtp? if you did it my way by doing ./configure -> make -> sudo make install, you will have to make a symbolic link to the new libmtp library in order for the new libmtp to take effect.

---

### Post by zeronothing on 2008-12-11
I did notice also if you did the installation using checkinstall you will still need to make the symbolic link to the new libmtp in order for it to work. what happens during the installation of libmtp is it is installed in /usr/local/lib directory instead of /usr/lib/. banshee loads the libmtp from /usr/lib/ instead of where the newly installed libmtp is. what you need to do is this:

open up terminal and "cd" into /usr/lib and do "sudo rm /usr/lib/libmtp.so.8

then do "sudo ln -s /usr/local/lib/libmtp.so.8.1.0 /usr/lib/libmtp.so.8"

now this will link the new libmtp to where banshee can find it. hopefully this helps.

---

### Post by SirSigma on 2008-12-11
I installed it using sudo make install.

Anyway, I typed the commands on Terminal and it doesn't look like anything even happened.

```
sigma@Sigma-Laptop:~$ cd /usr/lib
sigma@Sigma-Laptop:/usr/lib$ sudo rm /usr/lib/libmtp.so.8
[sudo] password for sigma: 
sigma@Sigma-Laptop:/usr/lib$ sudo ln -s /usr/local/lib/libmtp.so.8.1.0 /usr/lib/libmtp.so.8
sigma@Sigma-Laptop:/usr/lib$ 
```

I tried Banshee and connected to my device again, and Banshee shut off spontaneously again.

I really think I should just give up on this. Not only does it still not work, but Banshee takes even longer to pick up my device before shutting down. I have Winamp Pro on Vista, and I guess I'll just have to settle with that.

---

### Post by MCrittenden on 2008-12-11
If all else fails, there's always Gnomad2 for transferring files, but of course you can't stream directly from your Zen using it (apologies if you already knew about this app).

---

### Post by SirSigma on 2008-12-11
> **MCrittenden said:**
> If all else fails, there's always Gnomad2 for transferring files, but of course you can't stream directly from your Zen using it (apologies if you already knew about this app).

I did indeed know about Gnomad2 already, but it doesn't have playlists or a more organized structure of transfer. But I forgive you since I myself forgot to mention I gave it a try about a month ago.

---

### Post by evPaseo on 2009-09-28
I am having similar problems using my Sansa Clip in MTP mode with Jaunty. I have tried both Rythmbox and Banshee as well as updating libmtp and libsub. The specific error I receive when trying to mount my Clip is "error initializing MTP device support". Does anyone have any other suggestions. Any help would be greatly appreciated. Thanks!

---

### Post by Cuba71 on 2009-09-29
The USB settings on my Sansa Clip+ are set to "Auto Detect" and it works great with Jaunty 9.04.  It opens up a Nautilus window and all you have to do is copy your music to the Music folder.

---

### Post by evPaseo on 2009-09-30
I must have goofed something up then, because mine does not work like that. I can load the files from Nautilus. But when I disconnect the Clip it does not see the files. I'll try it fresh when I migrate to Karmic. Out of curiosity, have you tried to use your Clip on a Windows machine and noticed any problems with files you loaded from Jaunty?

---

