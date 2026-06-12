---
title: "How To: Install Cinelerra in Ubuntu 7.10 Gutsy"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by Sabot on 2007-10-29
Open Synaptic

On the menu bar select Settings>Repositories
Click the Third-Party Software Tab
Click the Add button
Enter the repository below:
```
deb http://giss.tv/~vale/ubuntu32 ./
```

Close the software sources window and reload your repositories by clicking on the reload button.
Search for Cinelerra by using the search button in Synaptic  and install it.

Cinelerra needs a little extra memory to run in the Kernel.  To add this extra memory you need to edit a file.

Open a terminal and enter the commands below:

```
sudo gedit /etc/sysctl.conf
```

and at the bottom of this text file add the line:

```
kernel/shmmax=0x7fffffff
```

Restart your computer for this new Kernel setting to take effect.

You will find Cinelerra under Applications>Sound & video>Cinelerra.

Now you are ready to enjoy Cinelerra!

One quick note on how I use Cinelerra.  I import using kino from my camcorder. Then I open the dv files with Cinelerra.  After I have made my edits, I render to a raw dv file in Cinelerra.  Kino is used to open and put the video back on my camera. If I want to export to an mpeg file, I use the export feature in Kino.

---

### Post by thinktyler on 2007-10-30
Thank you very much. Just in the *nix of time.

---

### Post by DaveQB on 2007-11-01
I think this just broke.

deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./

I just updated and it updated the extra multimedia packages the new release of cinelerra needs, except for libfaac0.  So Cinlerra wont install now and left off the system.

---

### Post by Sabot on 2007-11-01
I am working from a clean install of 7.10 Gutsy and all is still fine here.

---

### Post by DaveQB on 2007-11-01
> **Sabot said:**
> I am working from a clean install of 7.10 Gutsy and all is still fine here.


Yes me too.  I had to go get a debian libfaac0 ver. 1.25 to then get the new versions installed.

:confused:

---

### Post by Sabot on 2007-11-01
Cinelerra 1.2.1.02svn20070221 is the version I have installed and synaptic is up to date.  What version do you guys have? My libfaac0 is version 1.24clean-0ubuntu4

---

### Post by DaveQB on 2007-11-01
```
ii  libfaac                        01.25-0.1
ii  cinelerra                              1:2.1.0-2svn20071028
ii  libquicktimehv                      1:2.1.0-2svn20071028
ii  libguicast                             1:2.1.0-2svn20071028 
ii  libmpeg3hv                          1:2.1.0-2svn20071028   
```  

I am using "deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./" in my souces.list

---

### Post by DaveQB on 2007-11-01
As you can see, these came out a few days ago, but the new libfaac0 didnt come with them and thus borked the whole upgrade.  

So I had to track down a 1.25 version of libfaac0 from a Debian mirror site.

All working great now!

---

### Post by Sabot on 2007-11-01
Ok so it is the 64bit version that is broken and not the 32bit version that I put forth in my post.

---

### Post by SFN on 2007-11-01
> **Sabot said:**
> 
Cinelerra needs a little extra memory to run in the Kernel.  To add this extra memory you need to edit a file.

Open a terminal and enter the commands below:

```
sudo gedit /etc/sysctl.conf
```

and at the bottom of this text file add the line:

```
kernel/shmmax=0x7fffffff
```

Restart your computer for this new Kernel setting to take effect.


Just to make this a touch more streamlined, you can skip the restart by doing 

```
sudo sysctl -p
```

---

### Post by YoshiHNS on 2007-11-01
so the x64 version is not working? I was trying to compile it earlier but ran into some problems and then out of time.

---

### Post by DanielG007 on 2007-11-02
I have a problem:

bcbitmap.h:8:34: error: X11/extensions/Xvlib.h: No such file or directory
bcbitmap.h:144: error: ISO C++ forbids declaration of 'XvImage' with no type
bcbitmap.h:144: error: expected ';' before '*' token
bcbitmap.C: In member function 'int BC_Bitmap::initialize(BC_WindowBase*, int, int, int, int)':
bcbitmap.C:77: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'int BC_Bitmap::allocate_data()':
bcbitmap.C:143: error: 'xv_image' was not declared in this scope
bcbitmap.C:149: error: 'XvShmCreateImage' was not declared in this scope
bcbitmap.C: In member function 'int BC_Bitmap::delete_data()':
bcbitmap.C:317: error: 'XvStopVideo' was not declared in this scope
bcbitmap.C:320: error: 'xv_image' was not declared in this scope
bcbitmap.C:323: error: 'XvUngrabPort' was not declared in this scope
bcbitmap.C: In member function 'int BC_Bitmap::write_drawable(Drawable&, _XGC*&, int, int, int, int, int, int, int, int, int)':
bcbitmap.C:446: error: 'xv_image' was not declared in this scope
bcbitmap.C:455: error: 'XvShmPutImage' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_shm_size()':
bcbitmap.C:632: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_shm_offset()':
bcbitmap.C:640: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_y_shm_offset()':
bcbitmap.C:651: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_u_shm_offset()':
bcbitmap.C:659: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_v_shm_offset()':
bcbitmap.C:667: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_y_offset()':
bcbitmap.C:675: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_u_offset()':
bcbitmap.C:683: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'long int BC_Bitmap::get_v_offset()':
bcbitmap.C:691: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'unsigned char* BC_Bitmap::get_y_plane()':
bcbitmap.C:717: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'unsigned char* BC_Bitmap::get_v_plane()':
bcbitmap.C:726: error: 'xv_image' was not declared in this scope
bcbitmap.C: In member function 'unsigned char* BC_Bitmap::get_u_plane()':
bcbitmap.C:735: error: 'xv_image' was not declared in this scope
make[2]: *** [bcbitmap.lo] Error 1
make[2]: se sale del directorio `/home/dani/x264/hvirtual/guicast'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/dani/x264/hvirtual'
make: *** [all] Error 2

What happend?

---

### Post by Sabot on 2007-11-02
It looks like you are trying to build something from source and you don't have the dependances.

---

### Post by qu9542 on 2007-11-02
Thanks for all previous posting, so I can install Cinelerra in my Ubuntu 7.10 (AMD 64Bit Vesrion) Gutsy successfully. Here is my install log:

<1> Add the following source to Synptic Package Manager (SPM) ->Settings->Repositories->Third-Party Software
[http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./

I use AMD 64Bit CPU, and my Ubuntu 7.10(fresh install) is also AMD 64 Version. If you use 32 bit version, you can use this
[http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./

you can find the original details for package repositories from Cinelerra website ([http://cv.cinelerra.org/getting_cinelerra.php#ubuntu](http://cv.cinelerra.org/getting_cinelerra.php#ubuntu))


<2> Search "cinelerra" in SPM. You will find it. and then mark to install, you will get the following error:
cinelerra:
 Depends: libquicktimehv but it is not going to be installed
 Depends: libquicktimehv but it is not going to be installed

When you install libquicktimehv, you will get the following error:
libquicktimehv:
  Depends: libfaac0 (>=1.25) but 1.24clean-0ubuntu4 is to be installed

<3> You need the libfaac0 version 1.25, while Ubuntu only have version 1.24 (packages.ubuntu.com), that break the install.
	
<4> You need go to debian website (packages.debian.org) to download libfaac (1.25 version) by yourself. But their search is disable at that time.

<5> I have to google libfaac, I found it at ([http://rpm.pbone.net/index.php3/stat/4/idpl/3942641/com/libfaac0-1.25-2.el4.at.x86_64.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/3942641/com/libfaac0-1.25-2.el4.at.x86_64.rpm.html)), and you can download the following package to your machine:
 libfaac0-1.25-2.e14.at.x86_64.rpm
This looks like a version for 64 bit CPU, just what I need.
use alien to convert the rpm to deb, then use dpkg to install.
	sudo apt-get install alien   #install alien, which use to convert rpm to deb
	sudo alien -k xxx.rpm       #This will convert your rpm to deb
	sudo kpkg -i xxx.deb	    # install your deb

<6> Now you may install Cinelerra from SPM without any problems.

<7> When you run Cinelerra the first time, you will get this error message.
	sudo gedit /etc/sysctl.conf
and at the bottom of this text file add the line:
	kernel/shmmax=0x7fffffff
and type the following command to take effect.
	sudo sysctl -p

<8> Enjoy your Cinelerra!!

--------------------------------------------------------------------------
Reference
--------------------------------------------------------------------------
How to: Install Cinelerra in Ubuntu 7.10 Gutsy
[http://ubuntuforums.org/showthread.php?p=3667557](http://ubuntuforums.org/showthread.php?p=3667557)

Cinelerra Website
[http://cv.cinelerra.org/](http://cv.cinelerra.org/)

Ubuntu Package Search
packages.ubuntu.com

Debian package Search
packages.debian.org

---

### Post by Unterseeboot_234 on 2007-11-07
qu9542 your HowTo worked beautifully. I just double-clicked the .deb for libfaac 1.25 deb on my Desktop and that brought up Package Installer ( I don't have dpkg installed and I don't bother). Thanks for the help to mod the kernel config error.

---

### Post by devapea on 2007-11-13
After much trial and error of trying to get the gutsy vers. I also kept getting the illegal core dump.  I have I386. I replaced my gutsy repo apt source with a feisty vers. from this page.
[http://cvs.cinelerra.org/getting_cinelerra.php#gutsy](http://cvs.cinelerra.org/getting_cinelerra.php#gutsy)
using sympatic. tried installing it and their was an unresolved issue with ver of libguicast.
i then did a search on sympatic for that and uninstalled that ver. Then (happy ending) was able to install cinelerra (it found the correct ver of libguicast) and it runs great!

---

### Post by julipanno on 2007-11-17
> **qu9542 said:**
> 	
<4> You need go to debian website (packages.debian.org) to download libfaac (1.25 version) by yourself. But their search is disable at that time.


libfaac is not in the official Debian repositories but can be found in Marillat's debian-multimedia. The deb-file in question can be downloaded directly from this page: [http://www.debian-multimedia.org/dists/stable/main/binary-amd64/package/libfaac0.php](http://www.debian-multimedia.org/dists/stable/main/binary-amd64/package/libfaac0.php)

---

### Post by el escocés on 2007-11-20
qu9542's solution worked perfectly, thanks!

---

### Post by kosson on 2007-11-25
Disabling ATI driver gave back Cinelerra in force...

I only hope it runs stable

Thank you for this trick:
sudo sysctl -p
kernel.printk = 4 4 1 7
kernel.maps_protect = 1
kernel.shmmax = 0x7fffffff

have fun and many, many useful creations

---

### Post by eyemean on 2007-12-06
I installed Cinelerra but when i restarted ubuntu and ran the software nothing happened, so went to terminal typed cine and pressed tab and pressed enter then i got the following error:

cinelerra: symbol lookup error: /usr/lib/libguicast.so.1: undefined symbol: glDeleteShader

Im new to linux world so not really clued up as to how to sort things like this out.  I did try searching google for this error which came up with alot of things tht i didnt understand.

Im using an Athlon xp2000+ with 1G ram + Radeon 9550 card (therefore i got ATI fglrx running for compiz)

Any help would be much appreciated, thanx in advance.

---

### Post by Sabot on 2007-12-06
Seems to be something to do with your video driver.  I am not familiar with that error.

---

### Post by julioboaro on 2007-12-07
After how-to first post, I got this error:
cinelerra: error while loading shared libraries: libGL.so.1.2: cannot open shared object file: No such file or directory

I fix with:
```
sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so.1.2
```

have fun!

---

### Post by budman21901 on 2007-12-09
Thank you for the fix.  I was having the same issue, and found how you fixed it.  This worked perfectly for me, and now my cinelerra works again.

---

### Post by ipatec on 2007-12-21
I've followed the steps. Cinelerra appears at Sound and Video but nothing happens when I'm clicking on it... it just don't start.
Any advice?

---

### Post by ugm6hr on 2007-12-21
> **ipatec said:**
> I've followed the steps. Cinelerra appears at Sound and Video but nothing happens when I'm clicking on it... it just don't start.
Any advice?

I had the same problem.  I couldn't find a satisfactory soultion, so just installed kdenlive instead, which was enough for my home videos.  If you find a solution, I'd love to know about it.

---

### Post by eyemean on 2007-12-21
Im new to the Linux world and enjoy using Ubuntu much more than windows xp.  The reason im telling you that im new to linux is because I doubt i would be able to answer any questions about how this procedure works as my knowledge of linux is lower than basic, lol.  But thanks the help and patience of wildhostile and cehteh in the irc channel (I think it was the Cinelerra channel) they managed to help me get it working in Ubuntu 7.10.  I saved the whole conversation and then reduced it to the basic which is as follows:

> 
svn://svn.skolelinux.org/cinelerra/trunk/hvirtual - in a terminal
Should be about 123meg large

go to the floder
cd hvirtual
./autogen.sh
./configure

There will be missing dependencies, install them all.

try sudo apt-get install libdv4 libdv4-dev libdv-bin

./autogen.sh
mkdir build
cd build
./configure

when configure is finished it will list all missing components, install them too 
configure again, until nothing is missing anymore (opengl when you dont have a nvidia card)

install gettext

In terminal copy and paste each line
touch po/de.gmo
touch po/es.gmo
touch po/sl.gmo
touch po/fr.gmo
touch po/it.gmo
touch po/pt_BR.gmo
touch po/eu.gmo

sudo make install
AFTER VERY LONG TIME IT WILL COMPLETE

(There might be some errors but from what i found out on another page, they are not a problem if you are using only english.)

exit

start Cinerella

I havent messed around with this software much yet, but im starting to get a feel for it. I really hope this can help someone get it installed on gutsy.

By the way my graphics card is a Radeon 9550, i think it makes a slight difference if you have an nvidea card, I think the only difference was something about OpenGL, not sure what that is though.

Good luck.
Merry Christmas to everyone.

---

### Post by konungursvia on 2007-12-28
I used qu9542's instructions and they worked for me. Thanks!

---

### Post by tipdrinker on 2007-12-30
> **julioboaro said:**
> After how-to first post, I got this error:
cinelerra: error while loading shared libraries: libGL.so.1.2: cannot open shared object file: No such file or directory

I fix with:
```
sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so.1.2
```

have fun!

fantastic, I'd the same problem. Thanks for that

---

### Post by Ninefold on 2008-01-01
After following the original instruction Cinellera wouldn't do anything for me when clicked on. Typing Cinelerra In the command line gave this response:

> cinelerra: error while loading shared libraries: libGL.so.1.2: cannot open shared object file: No such file or directory


To solve this problem I followed the instruction here at[ linuxvault]("http://www.thelinuxvault.net/wiki/Cinelerra").

Here's a copy of what's at that link.

> If Cinelerra won't load, and when run in the terminal only displays:

    cinelerra: error while loading shared libraries: libGL.so.1.2: cannot open shared object file: No such file or directory 

Opening a terminal and running this command may solve the problem:

    sudo ln -s /usr/lib/nvidia/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1.2 

---

### Post by esmerine on 2008-01-08
Thank you all, installed and replaced library file and now everything works fine.

---

### Post by Vlastr on 2008-01-18
I have a problem here: after adding shmmax parameter and running sysctl -p, I get the following: error: "Invalid argument" setting key "kernel.shmmax". Where is the problem? Of course Cinelerra shows me this error message on the start too... :(

--------------

I have already sorted it out myself: putting it in DEC format solves the problem. :)

kernel.shmmax = 2147483647

---

### Post by henriquemaia on 2008-01-29
This is a very useful Thread. A big thanks to the OP and thanks to all who have posted nice tips throughout the thread.

---

### Post by Muscar on 2008-01-31
It won't open, and when i try to open in terminal: 
bash: Cinelerra: command not found

help!

---

### Post by julipanno on 2008-01-31
> **Muscar said:**
> It won't open, and when i try to open in terminal: 
bash: Cinelerra: command not found

help!

Try Cinelerra with a non-capital C, as in cinelerra.

;-)

---

### Post by Dragonchase on 2008-04-01
Hello everyone...

I have 'played" with Cinelerra off and on in the past.  The last few days, as I had the time to do so, I have tried installing Cinelerra in Gutsy.  I have tried at least four repositories including the one cvs.cinelerra listed. (repository.akirad.net...) It seems not to matter which repo or which "brew".  Generic, K7, K7GL etc. It always comes back to this.

cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen

My system is using a K7 class AMD with an Nvidia with Open GL.  I'm sure this is nothing new as comments appear about it elsewhere.  But I have never seen it before and am at a loss what to do about it. Fixes either don't work or dead-end.

Thanks for any help!

---

### Post by DaveQB on 2008-04-02
> **Dragonchase said:**
> Hello everyone...

I have 'played" with Cinelerra off and on in the past.  The last few days, as I had the time to do so, I have tried installing Cinelerra in Gutsy.  I have tried at least four repositories including the one cvs.cinelerra listed. (repository.akirad.net...) It seems not to matter which repo or which "brew".  Generic, K7, K7GL etc. It always comes back to this.

cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen

My system is using a K7 class AMD with an Nvidia with Open GL.  I'm sure this is nothing new as comments appear about it elsewhere.  But I have never seen it before and am at a loss what to do about it. Fixes either don't work or dead-end.

Thanks for any help!

Interesting.

Trying find out what package its fromt (dpkg -S /usr/lib/libquicktimehv-1.6.0.so.1)
and then re-install that package (apt-get install --reinstall <package name>

Thats all I can think of.

Next would be running cinelerra with strace :popcorn:

---

### Post by julipanno on 2008-04-02
> **Dragonchase said:**
> Hello everyone...

I have 'played" with Cinelerra off and on in the past.  The last few days, as I had the time to do so, I have tried installing Cinelerra in Gutsy.  I have tried at least four repositories including the one cvs.cinelerra listed. (repository.akirad.net...) It seems not to matter which repo or which "brew".  Generic, K7, K7GL etc. It always comes back to this.

cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen

My system is using a K7 class AMD with an Nvidia with Open GL.  I'm sure this is nothing new as comments appear about it elsewhere.  But I have never seen it before and am at a loss what to do about it. Fixes either don't work or dead-end.

Thanks for any help!

It may be that your version of libquicktime is compiled without faac-support (and possibly without other codecs as well). Ideally, this shouldn't  be required to run Cinelerra, but it has some specific dependencies and  I'd advice you to try another libquicktime or compile it yourself. Usually, any repository that offers Cinelerra would offer a working version of libquicktime as well. See the bug at [https://bugs.launchpad.net/ubuntu/+source/libquicktime/+bug/148994](https://bugs.launchpad.net/ubuntu/+source/libquicktime/+bug/148994) for more on this issue.

---

### Post by pavit_laul on 2008-04-08
I installed cinelerra on Gutsy using 'Sabot' 's How-to. But I get the following error after typing cinelerra in the terminal. (This is after I get no response by clicking on the cinelerra icon in Applications.)

Any help??

---

### Post by Sabot on 2008-04-08
> **pavit_laul said:**
> I installed cinelerra on Gutsy using 'Sabot' 's How-to. But I get the following error after typing cinelerra in the terminal. (This is after I get no response by clicking on the cinelerra icon in Applications.)

Any help??

Make sure your start with a fresh install of Gutsy.

---

### Post by julipanno on 2008-04-08
> **pavit_laul said:**
> I installed cinelerra on Gutsy using 'Sabot' 's How-to. But I get the following error after typing cinelerra in the terminal. (This is after I get no response by clicking on the cinelerra icon in Applications.)

Any help??

Which error message do you get from the terminal?

---

### Post by scooterpd on 2008-04-28
every time i try to open up and play a .mov file, i get the following error:
```
virtual int FileMOV::read_frame(VFrame*): quicktime_read_frame/quicktime_decode_video failed, result:
```

does anyone know what that means?  sorry but i am totally new to this and i really need a linux video editor that will work with .mov quicktime files, or mpeg-4.

thanks.

---

### Post by julipanno on 2008-04-28
> **scooterpd said:**
> every time i try to open up and play a .mov file, i get the following error:
```
virtual int FileMOV::read_frame(VFrame*): quicktime_read_frame/quicktime_decode_video failed, result:
```

does anyone know what that means?  sorry but i am totally new to this and i really need a linux video editor that will work with .mov quicktime files, or mpeg-4.

thanks.

It may be that a you have missing or incompatible quicktime library. Usually, any repository that contains cinelerra will also have a working libquicktime, possibly called libquicktimehv. If you do not have this available you can download the installation-file from Debian Multimedia:
[http://debian-multimedia.org/pool/main/c/cinelerra/libquicktimehv_2.1.0~svn20080425-0.0_i386.deb](http://debian-multimedia.org/pool/main/c/cinelerra/libquicktimehv_2.1.0~svn20080425-0.0_i386.deb)
*(This is the 32-bit version from unstable - a lot of other versions are available at [http://debian-multimedia.org/](http://debian-multimedia.org/) )*

If you are new to video editing, you might not feel too comfortable with Cinelerra, though. I'd probably recommend Kdenlive instead, which is available in Ubuntu's own repositories and a lot easier to use.

---

