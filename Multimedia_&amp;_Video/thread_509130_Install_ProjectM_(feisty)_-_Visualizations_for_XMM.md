---
title: "Install ProjectM (feisty) - Visualizations for XMMS and AMAROK"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by grimdestripador on 2007-07-25
Verfied to work with Feisty!!! this is a repost of [http://www.linuxmint.com/forum/viewtopic.php?t=4082]("http://www.linuxmint.com/forum/viewtopic.php?t=4082")
Tried and True instructions to providing the best dynamic sound visualization out there. 
Works with: 
Ubuntu Edgy 6.10      &      Linux Mint 2.2 Bianca
Ubuntu Feisty 7.04     &     Linux Mint 3.0 Cassandra
[http://bayimg.com/CaeEOAaBI/"](http://bayimg.com/CaeEOAaBI/")For ScreenShot
The following Installs ProjectM Visualization (Milkdrop for Linux) for XMMS and AMAROK
goto [http://xmms-projectm.sourceforge.net/](http://xmms-projectm.sourceforge.net/)
and download the links on the left, or run the following URLs if they still work.
```

wget http://superb-west.dl.sourceforge.net/sourceforge/xmms-projectm/libprojectM-0.99.tar.bz2
wget http://umn.dl.sourceforge.net/sourceforge/xmms-projectm/libvisual-projectM-0.99.tar.bz2
wget http://umn.dl.sourceforge.net/sourceforge/xmms-projectm/xmms-projectM-0.99.tar.bz2
wget http://superb-west.dl.sourceforge.net/sourceforge/xmms-projectm/xmms-projectM-pbuffers-0.99.tar.bz2
```
[list=1]
[*]Make A Directory called "InstallProjectM" in your home folder.
[*]Extract Each downloaded file into ~/InstallProjectM
[*]Run the following CODE; one line at a time into your terminal
[/list]

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

Having Problems? See some other threads:
[http://ubuntuforums.org/showthread.php?t=290152](http://ubuntuforums.org/showthread.php?t=290152) about compiling dependencies

[http://ubuntuforums.org/showthread.php?t=249818&highlight=ProjectM](http://ubuntuforums.org/showthread.php?t=249818&highlight=ProjectM) for dapper related info

For Edgy Only from some-kids dev package server! (untested)
```
add this repo if you want it
"deb http://mirror.randumb.org/darkmagez/libprojectm /"

"sudo apt-get install libprojectm libvisual-projectm"

```

---

### Post by jordoex on 2007-10-11
The newest version of projectm uses cmake, so you have to install cmake and then use:
cmake . -DCMAKE_BUILD_TYPE=RELEASE
make
make install

---

### Post by Kitsun on 2007-10-16
Running ```
cmake . -DCMAKE_BUILD_TYPE=RELEASE
``` gives me errors, 

```
nwm@nwm-laptop:~/Desktop/projectM-libvisual-1.0$ cmake . -DCMAKE_BUILD_TYPE=RELEASE
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- broken
CMake Error: The C compiler "/usr/bin/gcc" is not able to compile a simple test program.
It fails with the following output:
 /usr/bin/make -f CMakeFiles/cmTryCompileExec.dir/build.make CMakeFiles/cmTryCompileExec.dir/build
make[1]: Entering directory `/home/nwm/Desktop/projectM-libvisual-1.0/CMakeFiles/CMakeTmp'
/usr/bin/cmake -E cmake_progress_report /home/nwm/Desktop/projectM-libvisual-1.0/CMakeFiles/CMakeTmp/CMakeFiles 1
Building C object CMakeFiles/cmTryCompileExec.dir/testCCompiler.o
/usr/bin/gcc   -o CMakeFiles/cmTryCompileExec.dir/testCCompiler.o   -c /home/nwm/Desktop/projectM-libvisual-1.0/CMakeFiles/CMakeTmp/testCCompiler.c
/home/nwm/Desktop/projectM-libvisual-1.0/CMakeFiles/CMakeTmp/testCCompiler.c:4:19: error: stdio.h: No such file or directory
/home/nwm/Desktop/projectM-libvisual-1.0/CMakeFiles/CMakeTmp/testCCompiler.c: In function ‘main’:
/home/nwm/Desktop/projectM-libvisual-1.0/CMakeFiles/CMakeTmp/testCCompiler.c:12: warning: incompatible implicit declaration of built-in function ‘printf’
make[1]: *** [CMakeFiles/cmTryCompileExec.dir/testCCompiler.o] Error 1
make[1]: Leaving directory `/home/nwm/Desktop/projectM-libvisual-1.0/CMakeFiles/CMakeTmp'
make: *** [cmTryCompileExec/fast] Error 2


CMake will not be able to correctly generate this project.
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Configuring done
nwm@nwm-laptop:~/Desktop/projectM-libvisual-1.0$ 

```

---

### Post by jordoex on 2007-10-16
did you install build-essential, etc, etc, as described in the first post? if you did, i don't knwo what your problem is.  ProjectM isn't even working in amarok tho for me, so i still need help.

---

### Post by nimitch on 2007-10-16
hello folks.
also required is the "libglew1.4-dev" package 


for me on a vanilla gutsy the compilation went smoothly
although the install plonked the "libxmms-projectM.so" in
 
    /usr/local/lib/xmms/Visualization

and the others plugins are in

    /usr/lib/xmms/Visualization

and the plugin is not recognised in the xmms menu :-(  .. naturally i have tried moving it but no joy there either

# edit 

to create the correct install path for the plugin use 

ccmake . 

and change the PREFIX to /usr 

....

this still didn't help xmms recognise the plugin tho ??

---

### Post by Kitsun on 2007-10-17
I'm fairly certain I got it to install correctly, but it doesn't show in Amarok or XMMS.

---

### Post by bucksgt on 2007-10-19
at the terminal, type:

ccmake .
when the little curses gui comes up, press the letter: c
arrow down to: CMAKE_INSTALL_PREFIX 
press: enter
change: /usr/local
to: /usr
press: enter
press the letter: c
press the letter: g

redo the cmake/make process for libprojectm and projectm-xmms (or which ever you are using)

can you dig it?

-qk.

---

### Post by jordoex on 2007-10-19
whoops, i forgot to mention that about libglew...  after i restarted some time after installing it and it shows up on amarok, but it doesn't work; the visualization screen shows up, but disappears instantly.  It does the same thing as when I tried using 3d visualizations on older computers.

I'll try that method sometime, but the wireless is acting buggy right now, so i'm on windows.  on that topic, I think i'll try ndiswrapper to see if that works better.

---

### Post by jordoex on 2007-10-23
I'm pleased to announce that it is now working on amarok as well!(using projectm-libvisual) thanks for the tip!

The only thing i wish was different is that i wish that i had the right click context menu, but oh well.  Maximising the window also causes projectM to stop working.  They still have a bit to work on... I wish ubuntu put this in the repos, i only found it because there is a plugin for projectm for foobar2000.

---

### Post by pumalinuz on 2007-10-23
i got everything installed but its not working correctly, all i get is a white screen in the visualization window and i have no configuration window either, it does display the song name in full opengl when song first starts. any ideas?

---

### Post by oCfuu on 2007-10-27
Hi folks. Finally got libvisual and projectm installed.

My only problem right now: It's standart resolution in amarok sucks. How can I configure projectm's resolution?
Any tools or command line commands etc?!
Cheers

---

### Post by quanumphaze on 2007-11-07
It's not working for me:
I get this error when I make libprojectM-1.01:
```
[  2%] Building CXX object CMakeFiles/projectM.dir/projectM.o
In file included from /home/andrew/tarballs/libprojectM-1.01/Renderer.hpp:4,
                 from /home/andrew/tarballs/libprojectM-1.01/projectM.cpp:59:
/home/andrew/tarballs/libprojectM-1.01/FBO.hpp:32:21: error: GL/glew.h: No such file or directory
make[2]: *** [CMakeFiles/projectM.dir/projectM.o] Error 1
make[1]: *** [CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2

```

I'm using Gutsy. I think it's a dependency issue.
Any help will be appreciated.
I'll keep googleing.

---

### Post by quanumphaze on 2007-11-07
Nevermind: I got libprojectM-1.01 compiled. I forgot to put in  -DCMAKE_BUILD_TYPE=RELEASE

But now projectM-libvisual-1.0 is giving me a hard time
```
CMake Error: This project requires some variables to be set,
and cmake can not find them.
Please set the following variables:
SDL_INCLUDE_DIR

```
I don't know what to set it to. Please help

---

### Post by Java_Spiked_Penguin on 2007-11-09
> **quanumphaze said:**
> Nevermind: I got libprojectM-1.01 compiled. I forgot to put in  -DCMAKE_BUILD_TYPE=RELEASE

But now projectM-libvisual-1.0 is giving me a hard time
```
CMake Error: This project requires some variables to be set,
and cmake can not find them.
Please set the following variables:
SDL_INCLUDE_DIR

```
I don't know what to set it to. Please help
It's probably a dependency error, install libsdl1.2-dev and you should be able to compile it.

---

### Post by quanumphaze on 2007-11-17
Sorry for the late response. I got libvisual to work (I think).
Now a problem with projectM-xmms-1.0
cmake works but I get these compile errors:
```
andrew@andrew-laptop:~/tarballs/projectM-xmms-1.0$ make
Scanning dependencies of target xmms_projectM
[ 33%] Building CXX object CMakeFiles/xmms_projectM.dir/main.o
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:30:25: error: xmms/plugin.h: No such file or directory
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:36:23: error: xmms/util.h: No such file or directory
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:40:27: error: xmms/xmmsctrl.h: No such file or directory
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:59: warning: ‘projectM_render_pcm’ initialised and declared ‘extern’
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:59: error: variable or field ‘projectM_render_pcm’ declared void
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:59: error: ‘gint16’ was not declared in this scope
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:60: warning: ‘projectM_render_freq’ initialised and declared ‘extern’
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:60: error: variable or field ‘projectM_render_freq’ declared void
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:60: error: ‘gint16’ was not declared in this scope
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:62: error: expected constructor, destructor, or type conversion before ‘*’ token
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:70: error: ‘VisPlugin’ does not name a type
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:89: error: expected constructor, destructor, or type conversion before ‘*’ token
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:114: error: ‘gint’ does not name a type
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp: In function ‘Uint32 get_xmms_title(Uint32, void*)’:
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:134: error: ‘projectM_vtable’ was not declared in this scope
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:134: error: ‘xmms_remote_get_playlist_pos’ was not declared in this scope
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:138: error: ‘xmms_remote_get_playlist_title’ was not declared in this scope
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:145: error: ‘g_free’ was not declared in this scope
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:149: error: ‘g_free’ was not declared in this scope
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp: In function ‘int worker_func(void*)’:
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:246: error: ‘disable_projectm’ was not declared in this scope
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:246: error: ‘gtk_idle_add’ was not declared in this scope
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp: At global scope:
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:331: warning: ‘projectM_render_pcm’ initialised and declared ‘extern’
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:331: error: variable or field ‘projectM_render_pcm’ declared void
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:331: error: redefinition of ‘int projectM_render_pcm’
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:59: error: ‘int projectM_render_pcm’ previously defined here
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:331: error: ‘gint16’ was not declared in this scope
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:341: warning: ‘projectM_render_freq’ initialised and declared ‘extern’
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:341: error: variable or field ‘projectM_render_freq’ declared void
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:341: error: redefinition of ‘int projectM_render_freq’
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:60: error: ‘int projectM_render_freq’ previously defined here
/home/andrew/tarballs/projectM-xmms-1.0/main.cpp:341: error: ‘gint16’ was not declared in this scope
make[2]: *** [CMakeFiles/xmms_projectM.dir/main.o] Error 1
make[1]: *** [CMakeFiles/xmms_projectM.dir/all] Error 2
make: *** [all] Error 2

```

It seems to be looking for files that didn't come in the tarball like xmms/plugin.h xmms/util.h xmms/xmmsctrl.h and is a complete mystery to me.
It doesn't like me :(

Any help will be appreciated.

---

### Post by tehschulman on 2007-11-23
Well, the install seemed to go fine for me, but on my Feisty system XMMS crashes each time I try to enable projectM. I'm not quite sure what the problem is, but the console output is as follows:

```


Message: device: default
projectM plugin: Initializing
reading ~/.projectM/config 
texsize:256
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 31 error_code 8 request_code 143 minor_code 5
Xlib: unexpected async reply (sequence 0x42ad)!


```

Did I screw something up when compiling? I really want to get these visualizers working :).

EDIT: Aparently projectM works in amarok for me but I'd rather use it in XMMS.

---

### Post by quanumphaze on 2007-11-25
Well I'm pleased to say that I don't need projectM-xmms-1.0 to be able to use projectM in Amarok.

However when I start it in Amarok it just produces a blank white window. Disabling Compiz does nothing.
And when any visualization (including projectM) is run in fullscreen it only takes up a small 640x480 space.

Is there any way to configure projectM in a similar way like I did with Milkdrop in Winamp?

Why won't this work for me?

---

### Post by bmwman91 on 2007-12-13
I too got it installed fine and it shows up/runs in Amarok.

HOWEVER, where is the config file?  The default resolution is like 320x240 or something, and I want to exercise my FireGl card a little more!

Thanks all!

BTW I did NOT install the XMMS part since I do not use it.  I guess I completely forgot where it installed itself to....poop.

---

### Post by bmwman91 on 2007-12-13
Nevermind.  Using the file browser and sorting by date I found a file that had the app's install path in it.

/usr/share/ProjectM

Derrh.........

---

### Post by bmwman91 on 2007-12-13
In the interest of helping out anyone who wants to run this ONLY on Amarok, here is what I did:

(From OP)
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
```

I also had to run:
```
sudo apt-get install libglew1.4-dev
```
for an essential part.

Okie...

Next, you need to download the latest tarballs with the source code for ProjectM and other associated libraries.  Make a new folder in your home folder called whatever you want that you will remember.  This is for installation files only, and can be deleted when done.  Get these two files from the following link and put them in the new folder.
[http://sourceforge.net/project/showfiles.php?group_id=104201](http://sourceforge.net/project/showfiles.php?group_id=104201)
**libprojectM-X.XX** (latest version)
**projectM-libvisual-X.X** (latest version)

Awesome.  Now, extract the files in these two tarballs into the same folder and 2 new folders should pop in.  In the terminal, navigate to the folder for the libprojectM files (not the libvisual one).
Do the following:
```
cmake .
ccmake .
#Press "c" then go down to the CMAKE_INSTALL_PREFIX line and press "Enter"
#Change the line to "/usr" from what it was before.
#Press "enter" again.  Press "c" then "g" which should plop you back out to the command prompt.
cmake .
make
sudo make install

```

BAM, done with the first half.

Now navigate up one level then into the libvisual folder.

Now enter:
```
cmake . -DCMAKE_BUILD_TYPE=RELEASE
ccmake . -DCMAKE_BUILD_TYPE=RELEASE
#Do the same thing you did above to the same line in here.
cmake . -DCMAKE_BUILD_TYPE=RELEASE
make
sudo make install
```

If you experience compiling errors, then you probably do not have all of the required packages installed.  Re-run the "apt-get install" lines.  If you already are up to date, it will not waste your time reinstalling them.

Why run cmake then ccmake then cmake again?  Well, if I ran ccmake first-off, there would not be anything in the config screen to set.  I had to run cmake first.  I am a n00b still, so bear with me.

Anywho, the config file should be located at /usr/share/projectM/config.inp

Hope someone finds this useful.  Some is from posts above here, some from the installer README's.  I claim no credit for re-posting stuff from others, beyond putting it into the order that got me up and running the first time through!  Cheers!

---

### Post by incogn(egro)ito on 2008-02-24
I seemingly got all my files to install, but I can not actually use the projectM visualization in XMMS. I tried restarting and nothing happened. Is there a way to make sure that the plug-in is installed to XMMS.

---

### Post by scottws on 2008-03-08
> **pumalinuz said:**
> i got everything installed but its not working correctly, all i get is a white screen in the visualization window and i have no configuration window either, it does display the song name in full opengl when song first starts. any ideas?
I'm having the same trouble.  I'm using Kubuntu 7.10 Gutsy Gibbon.  I installed ProjectM via using the libprojectm1, libprojectm1-data, and libvisual-projectm packages through the backports repository.

I'm wondering if it's a 3D acceleration problem.  This laptop has an ATi Radeon Mobility 9000, but the fglrx driver doesn't support it, so I'm using the open source ati driver.

---

### Post by Mika1860 on 2008-03-16
@all folks with the white window bug at amarok

With my ATI Mobility 9000 (crap) I had the same problem. Now I'm not quite sure if I really found a solution, but it's worth a try.
Just try to resize the little window until the projectM logo appears. Strangely this works for me and the vis starts (however, until now very slow - 6 fps)
It's not like in windows-winamp-fittingdriver times but better than nothing \\:D/
Now I try to configure at least the resolution...[-o<

Mika1860

---

### Post by LeFou on 2008-04-12
k, i install ftgl but when i try to cmake libprojectM 

Warning: FTGL font support was not detected. Visit [http://ftgl.wiki.sourceforge.net/](http://ftgl.wiki.sourceforge.net/) for help on installing FTGL.

How do I notify cmake that ftgl is really there

/usr/lib/libftgl.a exists, where do i symlink it?

---

### Post by jordoex on 2008-04-13
ProjectM is in hardy, just wait, it's less than two weeks away.

---

