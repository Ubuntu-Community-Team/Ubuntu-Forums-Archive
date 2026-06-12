---
title: "Kaffeine 0.8.8 How To"
date: 2009-03-16
forum: Multimedia Software
---

### Post by Dimitree on 2009-03-16
Kaffeine 0.8.8 Ubuntu how to install guide.

First big bIG BIG thanks to "hftom_" on irc #Kaffeine channel for providing this tutorial.

Start:
First you need to install the drivers for your DVB-S2 card.
In my case i'm using Cinergy S2 HD CI and the installation of the drivers goes as this:
*******************************************************************
cd /usr/src
sudo apt-get install mercurial
sudo hg clone [http://mercurial.intuxication.org/hg/s2-liplianin](http://mercurial.intuxication.org/hg/s2-liplianin)
sudo ln -s s2-liplianin s2
cd s2-liplianin
sudo make
sudo make install
sudo cp /usr/src/s2-liplianin/linux/include/linux/dvb/frontend.h /usr/include/linux/dvb/frontend.h
sudo reboot
*******************************************************************

Make sure that the output of :
grep DTV_TUNE  /usr/include/linux/dvb/frontend.h

Is Positive : #define DTV_TUNE  1

If not, locate frontend.h and copy paste it to 
/usr/include/linux/dvb/frontend.h

*******************************************************************
Now apply these commands:

sudo apt-get build-dep kaffeine
sudo apt-get install libcdio-paranoia-dev
sudo apt-get install libcdio-cdda-dev
sudo apt-get install subversion
svn co svn://anonsvn.kde.org/home/kde/branches/extragear/kde3/multimedia
sudo apt-get install build-essential
sudo apt-get install kdelibs4-dev
sudo apt-get install autoconf
sudo apt-get install libxine-dev
sudo apt-get install libcdparanoia0-dev
sudo apt-get install libxtst-dev

*******************************************************************
Now go to this folder :

cd $HOME/multimedia
And delete all directories Except:
Kaffeine
Doc
Admin

*******************************************************************
Then Run :

make -f Makefile.cvs
./configure
make
sudo make install

Happy watching :)

---

### Post by creativegb on 2010-08-09
Hi
I followed the steps in this Blog, but the software failed to install (the Error Messages in the Terminal for failed steps are shown in red):
"
cd /usr/src
sudo apt-get install mercurial
sudo hg clone [http://mercurial.intuxication.org/hg/s2-liplianin](http://mercurial.intuxication.org/hg/s2-liplianin)
sudo ln -s s2-liplianin s2
[COLOR="Red"]**cd s2-liplianin**[/COLOR]
[COLOR="Red"]sudo make
make[3]: *** [/usr/src/s2-liplianin/v4l/ir-keytable.o] Error 1 
make[2]: *** [_module_/usr/src/s2-liplianin/v4l] Error 2 
make[2]: Leaving directory `/usr/src/linux-headers-2.6.22-3-486' 
make[1]: *** [default] Error 2 
make[1]: Leaving directory `/usr/src/s2-liplianin/v4l' 
make: *** [all] Error 2[/COLOR]
sudo make install
sudo cp /usr/src/s2-liplianin/linux/include/linux/dvb/frontend.h /usr/include/linux/dvb/frontend.h
sudo reboot

Make sure that the output of :
grep DTV_TUNE /usr/include/linux/dvb/frontend.h

Is Positive : #define DTV_TUNE 1

If not, locate frontend.h and copy paste it to 
/usr/include/linux/dvb/frontend.h

Now apply these commands:

[COLOR="Red"]**sudo apt-get build-dep kaffeine**
root@boss[~]#sudo apt-get build-dep kaffeine

Reading package lists... Done

Building dependency tree       

Reading state information... Done

**[COLOR="Red"]E: Build-dependencies for kaffeine could not be satisfied.[/COLOR]**

sudo apt-get install libcdio-paranoia-dev
sudo apt-get install libcdio-cdda-dev
sudo apt-get install subversion
svn co svn://anonsvn.kde.org/home/kde/branches/extragear/kde3/multimedia  
[Earlier the svn command was not found-- so, I downloaded svn]

sudo apt-get install build-essential

sudo apt-get install kdelibs4-dev
root@boss[~]#sudo apt-get install kdelibs4-dev 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
[B]Some packages could not be installed. This may mean that you have 
requested an impossible situation or if you are using the unstable 
distribution that some required packages have not yet been created 
or been moved out of Incoming. 

Since you only requested a single operation it is extremely likely that 
the package is simply not installable and a bug report against 
that package should be filed. 
The following information may help to resolve the situation: 

The following packages have unmet dependencies: 
  kdelibs4-dev: Depends: libarts1-dev (>= 1.5.0) but it is not going to be installed 
                Depends: libavahi-qt3-dev (>= 0.4) but it is not going to be installed 
                Depends: libcupsys2-dev but it is not going to be installed 
                Depends: libqt3-mt-dev (>= 3:3.3.5) but it is not going to be installed 
E: Broken packages[/B][/COLOR]

sudo apt-get install autoconf

sudo apt-get install libxine-dev

sudo apt-get install libcdparanoia0-dev

sudo apt-get install libxtst-dev

Now go to this folder :

cd $HOME/multimedia
And delete all directories Except:
Kaffeine
Doc
Admin

[Do NOT Delete any file, only the directories -- Makefile.cvs etc files are required]

Then Run :

make -f Makefile.cvs

**[COLOR="Red"]./configure[/COLOR]**
root@boss[multimedia]#./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking whether gcc is blacklisted... no
checking whether g++ supports -Wmissing-format-attribute... yes
checking whether gcc supports -Wmissing-format-attribute... yes
checking whether g++ supports -Wundef... yes
checking whether g++ supports -Wno-long-long... yes
checking whether g++ supports -Wno-non-virtual-dtor... yes
checking whether g++ supports -fno-reorder-blocks... yes
checking whether g++ supports -fno-exceptions... yes
checking whether g++ supports -fno-check-new... yes
checking whether g++ supports -fno-common... yes
checking whether g++ supports -fexceptions... yes
checking whether system headers can cope with -O2 -fno-inline... irrelevant
checking how to run the C++ preprocessor... g++ -E
checking whether g++ supports -O0... yes
checking whether g++ supports -Wl,--no-undefined... yes
checking whether g++ supports -Wl,--allow-shlib-undefined... yes
not using lib directory suffix
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
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
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... no
checking for shl_load in -ldld... no
checking for dlopen... no
checking for dlopen in -ldl... yes
checking whether a program can dlopen itself... yes
checking whether a statically linked program can dlopen itself... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking for shl_load... (cached) no
checking for shl_load in -ldld... (cached) no
checking for dlopen... (cached) no
checking for dlopen in -ldl... (cached) yes
checking whether a program can dlopen itself... (cached) yes
checking whether a statically linked program can dlopen itself... (cached) yes
appending configuration tag "F77" to libtool
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for pkg-config... /usr/bin/pkg-config
checking if C++ programs can be compiled... yes
checking for strlcat... no
checking if strlcat needs custom prototype... yes - in libkdefakes
checking for strlcpy... no
checking if strlcpy needs custom prototype... yes - in libkdefakes
checking for main in -lutil... yes
checking for main in -lcompat... no
checking for crypt in -lcrypt... yes
checking for socklen_t... yes
checking for dnet_ntoa in -ldnet... no
checking for dnet_ntoa in -ldnet_stub... no
checking for inet_ntoa... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for sys/types.h... (cached) yes
checking for stdint.h... (cached) yes
checking sys/bitypes.h usability... yes
checking sys/bitypes.h presence... yes
checking for sys/bitypes.h... yes
checking for poll in -lpoll... no
checking Carbon/Carbon.h usability... no
checking Carbon/Carbon.h presence... no
checking for Carbon/Carbon.h... no
checking CoreAudio/CoreAudio.h usability... no
checking CoreAudio/CoreAudio.h presence... no
checking for CoreAudio/CoreAudio.h... no
checking if res_init needs -lresolv... yes
checking for res_init... yes
checking if res_init needs custom prototype... no
checking for killpg in -lucb... no
checking for int... yes
checking size of int... 4
checking for short... yes
checking size of short... 2
checking for long... yes
checking size of long... 4
checking for char *... yes
checking size of char *... 4
checking for dlopen in -ldl... (cached) yes
checking for shl_unload in -ldld... no
checking for size_t... yes
checking size of size_t... 4
checking for unsigned long... yes
checking size of unsigned long... 4
checking sizeof size_t == sizeof unsigned long... yes
checking for PIE support... yes
checking if enabling -pie/fPIE support... yes
checking crt_externs.h usability... no
checking crt_externs.h presence... no
checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... configure: **[COLOR="Red"]error: Can't find X libraries. Please check your installation and add the correct paths![/COLOR]**
.
[COLOR="Red"]**make**
root@boss[multimedia]#make
make: *** No targets specified and no makefile found.  Stop

**sudo make install**
root@boss[multimedia]#make install
make: *** No rule to make target `install'.  Stop.[/COLOR]
"

KINDLY HELP, asap. I'm using BOSS Linux OS (developed by C-DAC). Please also advise as to how remove all the traces of the above application & processes from my pc, and reinstall -- in case a reinstall is advised, please. 
Thanks in advance.

---

