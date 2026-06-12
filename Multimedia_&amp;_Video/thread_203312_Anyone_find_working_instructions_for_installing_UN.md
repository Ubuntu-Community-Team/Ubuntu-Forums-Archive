---
title: "Anyone find working instructions for installing UNICHROME drivers?"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by jeeves on 2006-06-25
I've been searching this forum and Google for several days, but I have yet to find [B]working instructions for installing drivers for my unichrome integratede graphics. 
[/B]

I did find t[hese instructions at openchome.org]("http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling%20the%20source%20code"), but it's unclear if I need to edit my xorg.conf. Also I hit a brick wall about four steps into the instructions:

```
jeeves@NOI:~$mkdir openchrome
jeeves@NOI:~$cd openchrome
jeeves@NOI:~/openchrome$  svn co http://svn.openchrome.org/svn/trunk
**bash: svn: command not found**
```

now what?](*,) 



I'm running Ubuntu 6.06 on a laptop with the S3 Graphics Unichrome Pro IGP integrated graphics.

---

### Post by Ptero-4 on 2006-06-25
You need to install svn. search for it in synaptic to see if it's there.

---

### Post by jeeves on 2006-06-25
Thank you - that tip got me a lot further. But it was brick wall time for me when the terminal spit out the following: 

```
checking for XORG... configure: **error: Package requirements (xorg-server xproto xvmc fontsproto libdrm ) were not met**:

No package 'xorg-server' found
No package 'fontsproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

``` 

Of course I went right to the Snaptic package manager to add these, but the aforementioned packages were not in there. Nuts.

Another strategy would be to use [Pirast's pre-compiled binaries for Dapper.]("http://gamesplace.info/opensource/openchrome/dapper-binaries/") However, the README offers no real instructions for getting started.

---

### Post by jeeves on 2006-06-25
Ok, I was able to get even further into [Openchome.org's "30 Second Install.]("http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling+the+source+code") But now I am getting an error after executing "make" about **not being able to find "GL/gl.h"**.  Weird, when I looked with the file browser this file actually does exist in "/usr/include/GL".   Any idea what could be going on.](*,)  Here is the error message the terminal spits out:

/usr/include/GL/glxint.h:28:19: error: GL/gl.h: No such file or directory
In file included from via_driver.h:73,
                 from via_accel.c:45:
/usr/include/GL/glxint.h:95: error: syntax error before 'GLboolean'
/usr/include/GL/glxint.h:97: error: syntax error before 'doubleBufferMode'
/usr/include/GL/glxint.h:98: error: syntax error before 'stereoMode'
/usr/include/GL/glxint.h:99: error: syntax error before 'haveAccumBuffer'
/usr/include/GL/glxint.h:100: error: syntax error before 'haveDepthBuffer'
/usr/include/GL/glxint.h:101: error: syntax error before 'haveStencilBuffer'
/usr/include/GL/glxint.h:104: error: syntax error before 'accumRedBits'
/usr/include/GL/glxint.h:105: error: syntax error before 'depthBits'
/usr/include/GL/glxint.h:106: error: syntax error before 'stencilBits'
/usr/include/GL/glxint.h:107: error: syntax error before 'indexBits'
/usr/include/GL/glxint.h:108: error: syntax error before 'redBits'
/usr/include/GL/glxint.h:109: error: syntax error before 'redMask'
/usr/include/GL/glxint.h:111: error: syntax error before 'multiSampleSize'
/usr/include/GL/glxint.h:113: error: syntax error before 'nMultiSampleBuffers'
/usr/include/GL/glxint.h:114: error: syntax error before 'maxAuxBuffers'
/usr/include/GL/glxint.h:117: error: syntax error before 'level'
/usr/include/GL/glxint.h:120: error: syntax error before 'extendedRange'
/usr/include/GL/glxint.h:121: error: syntax error before 'minRed'
/usr/include/GL/glxint.h:122: error: syntax error before 'minGreen'
/usr/include/GL/glxint.h:123: error: syntax error before 'minBlue'
/usr/include/GL/glxint.h:124: error: syntax error before 'minAlpha'
/usr/include/GL/glxint.h:125: error: syntax error before '}' token
make[2]: *** [via_accel.lo] Error 1
make[2]: Leaving directory `/home/marco/openchrome/trunk/unichrome'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/marco/openchrome/trunk'
make: *** [all] Error 2

---

### Post by jeeves on 2006-06-25
Solved it. For anyone in stuck on the missing GL/gl.h error, I simply ran the following: 

```
sudo apt-get install --reinstall mesa-common-dev
```

That allowed the install process to finish when I ran "make" again. For the record I used the following instructions:

**For Xorg 7.0 or later**
Modular build:

mkdir openchrome
cd openchrome
svn co [http://svn.openchrome.org/svn/trunk](http://svn.openchrome.org/svn/trunk)
cd trunk
./autogen.sh
configure
make
make install

(these were found at [Openchrome.org]("http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=Compiling%20the%20source%20code"))


So there we have it - presumably working instructions for installing the Unichrome drivers.  Now if I can just figure out why I can't get X to start when I specify **Driver "via"** in my xorg.conf!

---

### Post by Tomy on 2006-06-26
[quote=jeeves]Solved it. For anyone in stuck on the missing GL/gl.h error, I simply ran the following: 

```
sudo apt-get install --reinstall mesa-common-dev
``` 
[/quote] 
Hey, thanks alot. I have not been able to compile the openchrome drivers](*,) until just now.:D It wasn't the mesa stuff I was missing but x11proto-gl-dev. 

I found this list of packages in a message over at openchrome.org. ```
sudo apt-get install  subversion build-essential automake1.9 libtool 
pkg-config xserver-xorg-dev libxvmc-dev x11proto-gl-dev libglu1-mesa-dev
``` 
The new drivers and such installed in /usr/local/lib/ so I'll have to move a few things over to /usr/lib and then hopefully it will work.

Tomy

---

### Post by Peepsalot on 2006-07-01
Hello, I am trying to install this on my computer also.  I was able to run these commands, but I don't understand what else I have to do now.

What is this about moving some files from usr/local/lib?
How do I know what to put in xorg.conf?
How will I know when the drivers are running properly?
Do I need to follow these directions for the "Direct Rendering Manager" as well?

I just want some display drivers that aren't completely bug-ridden.

By the way, i had to alter the commands slightly, "./configure", and "sudo make install"
```

mkdir openchrome
cd openchrome
svn co http://svn.openchrome.org/svn/trunk
cd trunk
./autogen.sh
./configure
make
sudo make install

```

Also, after I ran autogen.sh, xfce went nuts and none of my windows would repaint.  I had to Ctrl-Alt-Backspace

---

