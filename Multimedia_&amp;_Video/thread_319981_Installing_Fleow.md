---
title: "Installing Fleow"
date: 2006-12-16
forum: Multimedia &amp; Video
---

### Post by jordn on 2006-12-16
hey there,

i am having a few problems installing fleow:

[http://fleow.berlios.de/]("http://fleow.berlios.de/")

i get to the installing the autogen.sh file, but when doing so i get this error:

[B]jordn@workstation:~/fleow$ sudo ./autogen.sh
I am going to run ./configure with no arguments - if you wish 
to pass any to it, please specify them on the ./autogen.sh command line.
Running aclocal -I .  ...
Running automake --gnu  ...
Running autoconf ...
Running ./configure ...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for MONO... configure: error: Package requirements (mono >= 1.1.13) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_CFLAGS
and MONO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.[/B]

i thought it was a problem with mono, so i updated it with sudo apt-get install mono; which updated it to the latest version. but i still get this error.

has anybody experienced this or can anybody help me with it?

thanks in advance, 

jordn

---

### Post by taurus on 2006-12-16
You also need the -devel of mono as well...

```
sudo aptitude install mono-devel
```

---

### Post by ikkefc3 on 2007-05-17
> **taurus said:**
> You also need the -devel of mono as well...

```
sudo aptitude install mono-devel
```

I have installed the mono-devel, but i have still te same problem:
```
I am going to run ./configure with no arguments - if you wish 
to pass any to it, please specify them on the ./autogen.sh command line.
Running aclocal -I .  ...
Running automake --gnu  ...
Running autoconf ...
Running ./configure ...
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for MONO... configure: error: Package requirements (mono >= 1.1.13) were not met:

No package 'mono' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MONO_CFLAGS
and MONO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

---

### Post by lanteltech on 2007-06-16
I having the same issue and have installed mono and mon-devel packages as well, btu with no success..  Did you ever find a resolution?

---

### Post by cubox on 2007-06-28
Use synaptic and install also

 libmono-dev

---

### Post by kshezeppelin1 on 2007-08-19
now what do i do with it ?????
/usr/lib/banshee/Banshee.Plugins

:/usr/lib/banshee/Banshee.Plugins/fleow$ sudo ./autogen.sh 

I am going to run ./configure with no arguments - if you wish 

to pass any to it, please specify them on the ./autogen.sh command line.

Running aclocal -I .  ...

Running automake --gnu  ...

Running autoconf ...

Running ./configure ...

checking build system type... i686-pc-linux-gnu

checking host system type... i686-pc-linux-gnu

checking target system type... i686-pc-linux-gnu

checking for a BSD-compatible install... /usr/bin/install -c

checking whether build environment is sane... yes

checking for a thread-safe mkdir -p... /bin/mkdir -p

checking for gawk... no

checking for mawk... mawk

checking whether make sets $(MAKE)... yes

checking whether to enable maintainer-specific portions of Makefiles... yes

checking for pkg-config... /usr/bin/pkg-config

checking pkg-config is at least version 0.9.0... yes

checking for MONO... yes

checking for TAO... configure: error: Package requirements (tao-opengl >= 1.3.0) were not met:


No package 'tao-opengl' found



Consider adjusting the PKG_CONFIG_PATH environment variable if you

installed software in a non-standard prefix.



Alternatively, you may set the environment variables TAO_CFLAGS

and TAO_LIBS to avoid the need to call pkg-config.

See the pkg-config man page for more details.

---

### Post by DeadSuperHero on 2007-10-08
Yeah, I can't find the tao-opengl package anywhere!
Ah well, might as well just wait a while, someone will put it up eventually.

---

### Post by u01p2109 on 2007-10-21
> **Mr. Psychopath said:**
> Yeah, I can't find the tao-opengl package anywhere!
Ah well, might as well just wait a while, someone will put it up eventually.

svn co svn://anonsvn.mono-project.com/source/trunk/tao

---

### Post by explosive on 2007-10-29
I have tried to compile the package myself and followed the instructions in the README but there is no makefile?? The repo seems to be incomplete.

Any ideas?

---

### Post by Ehtetur on 2007-12-02
The README.autotools file gives you instructions on compiling/installing prebuild, and also how to use prebuild  to create the tao-opengl package.

The bad is it looks like the svn trunk for tao is broken. I made the prebuild packages and got all the way to running make on the tao files when I got this error:
> ./Gl.cs(49430,72): error CS0117: `Tao.OpenGl.Gl' does not contain a definition for `GetDelegateForExtensionMethod'

I only other error like this I found on google was someone who posted it in a [**bsd forum**]("http://archive.netbsd.se/?ml=mono-tao&a=2007-11&m=5670743").

I posted that error in the taoframework.com/forum. Some tao devel somewhere has to have the fix for it, right?
[http://www.taoframework.com/node/471](http://www.taoframework.com/node/471)

That fleow plugin better look all shiny and new after all this wackiness to get it to work.

---

### Post by Ehtetur on 2007-12-03
Was able to compile and INSTALL tao-opengl.

But when I run ./autogen --prefix=/usr   or just ./autogen in the fleow folder, I get this error:
> checking for TAO... configure: error: Package requirements (tao-opengl >= 1.3.0) were not met:
No package 'tao-opengl' found
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
Alternatively, you may set the environment variables TAO_CFLAGS
and TAO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Any ideas?

---

### Post by canceLinux on 2007-12-07
No & Can't success yet..

isn't there a "good man" in all over the internet, who tell us how can i do this? (or have a tao-opengl.deb pack, huh :guitar: )

:confused::confused:

---

### Post by spliffmonkey187 on 2007-12-10
Hi Guys, I too am trying to get this interesting plugin for banshee to work i am right now in the process of following the instructions of this guide from mono-project: [http://anonsvn.mono-project.com/source/trunk/tao/README.autotools]("http://anonsvn.mono-project.com/source/trunk/tao/README.autotools")

Once i have finished getting the subversion of tao i will let you know how far i get. I am very interested in developing for this plugin too that is why i am eager to get it up and running.  Also about the Debian Package, apparently there is one but i could not find it via synaptic like the following site says(its an unstable build according to them): [http://www.taoframework.com/node/473]("http://www.taoframework.com/node/473") 

Well let me get back to getting tao installed i will get back to you and let oyu know how far i get.

---

### Post by spliffmonkey187 on 2007-12-10
Ok guys, so far i have been able to get the Subversion of the Tao Framework downloaded. Now i had a problem trying to get the autotool prebuild to work i kept getting recursive errors during the make process. So i decided to work around using the subversion version of tao framework and i downloaded the tarballs (tar.gz) version off their sourceforge page. 

Now i have gotten that one to compile beautifully (make procedure and make install worked perfectly). Now i went back into Fleow and ran the autogen.sh to check on dependencies that it needs to install. First time i ran it i still got the no tao-opengl error, thne it hit me, its in the wrong syntax so you have to edit the configure.ac in your fleow folder. ( i will write up a guide of what i have done so far once i am done)

Well back to cracking it, be right back.

---

### Post by spliffmonkey187 on 2007-12-10
Alright here is a little status report as to how far i have gotten. After i got the Tao.OpenGl problem resolved i ran into a similar problem for the Tao.DevIl dependency that Fleow seems to need. All i did was make the same corrections to the configure.ac and the autogen ran fine up till gtkglarea-sharp. 

So now i am working on getting gtkglarea-sharp installed but its proving to be a problem since it seems all the links to its repositories are down. 

Here is my configure.ac from Line6 - Line16 with the Tao.DevIl and Tao.OpenGl changes

```
AM_MAINTAINER_MODE

MONO_REQUIRED_VERSION=1.1.13
TAO_REQUIRED_VERSION=2.1.0
TAO_DEVIL_REQUIRED_VERSION=1.6.8
GTKGLAREA_SHARP_REQUIRED_VERSION=0.0.8
PKG_CHECK_MODULES(MONO, mono >= $MONO_REQUIRED_VERSION)
PKG_CHECK_MODULES(TAO, Tao.OpenGl >= $TAO_REQUIRED_VERSION) 
PKG_CHECK_MODULES(TAO_DEVIL, Tao.DevIl >= $TAO_DEVIL_REQUIRED_VERSION)
PKG_CHECK_MODULES(GTKGLAREA_SHARP, gtkglarea-sharp >= $GTKGLAREA_SHARP_REQUIRED_VERSION)
```

Oh and incase you are wandering how to get Tao.DevIl working just follow these instructions (They are the same as the ones from the site i quoted earlier i just made changes to it)

```
cd tao/src/Tao.DevIl &&
prebuild /target autotools &&
cd autotools/Tao.DevIl &&
sh autogen.sh &&
make

You should now have all of the .dll files required to use Tao.DevIl.
To install a given package, cd to its directory and run 'sudo make install':

cd Tao.DevIl && sudo make install
```

Don't Forget to run:

```
$ pkg-config --modversion Tao.DevIl
```

Get the version number and put it in your configure.ac like i did not sure itf its really neccessary though.

---

### Post by spliffmonkey187 on 2007-12-10
Has anyone been able to get gtkglarea-sharp to compile on ubuntu? It seems as if the old links to its downloads no longer work i got one via subversion from

```
svn co http://anonsvn.mono-project.com/source/trunk/gtkglarea-sharp/
```

 But when i follow the install instructions listed here: [http://www.mono-project.com/GtkGlAreaSharp:Installation]("http://www.mono-project.com/GtkGlAreaSharp:Installation")
I get all te way to the 

```
./autogen.sh --prefix=$HOME/opt
```

And then i get this at the end of the run attempt:

```
Running glib-gettextize ...
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.

Running intltoolize ...
Running aclocal  ...
**Error**: automake 1.9+ required.
```

Odd thing is i have automake 1.1-1.10 all installed not sure why it does this and all the stuff before that not making any sense either. Lol-dependencies i suppose :( 

I will call it a day for now, my head is gonig to explode :lolflag:

---

### Post by Ehtetur on 2007-12-11
> **spliffmonkey187 said:**
> I will call it a day for now, my head is gonig to explode :lolflag:

Yer preaching to the choir... I'm glad I aint the only one working on this. :twisted:

I wasn't able to compile tao-opengl using  the trunk listed in the fleow instructions:
 [http://anonsvn.mono-project.com/source/trunk/tao](http://anonsvn.mono-project.com/source/trunk/tao)
So  I asked about it in the tao framework forum and they said to use the latest trunk:
[https://taoframework.svn.sourceforge.net/svnroot/taoframework/trunk](https://taoframework.svn.sourceforge.net/svnroot/taoframework/trunk)

That worked... Compiled tao-opengl version 2. 
I had to compile autotools to compile tao-opengl using instructions from README.autotools.
The bad: fleow still complains of not finding tao-opengl... Maybe it's looking for headers, looking for tao-opengl-dev!??

Anyway.. I asked in the fleow forum if the project is still maintained... that was a week ago and still no response.

I  do recall having to compile some sharp lib, but I don't think it was GtkGLAreaSharp.
Here's the instructions from the mono site for compiling GtkGLAreaSharp:
[http://www.mono-project.com/GtkGLAreaSharp:With_MonoDevelop](http://www.mono-project.com/GtkGLAreaSharp:With_MonoDevelop)

Good luck!
I'll be plugging away too.

---

### Post by spliffmonkey187 on 2007-12-13
Hi Ehtetur , yeh sorry i have not been online been abit busy with some other stuff i am going to get busy with this one again today though. I think the only hurdle we have left is getting the GtkGlareaSharp installed. Its the last dependency that Fleow checks for before it compiles. That build script is no longer available for me for some odd reason if i could get it i could compile and install gtkglarea-sharp. 

The other Gtk you are talking about Ehtetur  is the normal GTK# package , i got those too from the same site got them all compiled and installed no problem, the GtkGlareaSharp is a bunch of opengl dlls that were made to work in a GTK widget (a api that will load your opengl). 

I saw your post on the Fleow and saw that there was no responce. I am really thinkgi of taking this on as a project myself. But in order for me to do so i need to see it running so i can get to grips with how it works and stuff. Hehe kinda like reverse engineering. 

I will let you know how far i get.

---

### Post by Ehtetur on 2008-01-11
> **spliffmonkey187 said:**
> [/CODE]
Running intltoolize ...
Running aclocal  ...
**Error**: automake 1.9+ required.[/CODE]

Odd thing is i have automake 1.1-1.10 all installed not sure why it does this and all the stuff before that not making any sense either. Lol-dependencies i suppose :( 

spliffmonkey187 - If it helps, I was able to compile gtkglarea-sharp with automake1.9 installed...

Besides changing the version to 2.1.0 in configuration.ac, did you do anything else to fix the tao-opengl dependency?
I compiled & installed tao-opengl, but when I run sh autogen.sh --prefix=/usr in the  fleow folder, I get this error: :evil:
> checking for TAO... configure: error: Package requirements (tao-opengl >= 2.1.0) were not met:
No package 'tao-opengl' found

I verified that tao-opengl installed:
dpkg -L tao-opengl
> /usr
/usr/lib
/usr/lib/pkgconfig
/usr/lib/pkgconfig/Tao.OpenGl.pc
/usr/lib/mono
/usr/lib/mono/Tao.OpenGl
/usr/lib/mono/Tao.OpenGl/Tao.OpenGl.dll.config
/usr/lib/mono/gac
/usr/lib/mono/gac/Tao.OpenGl
/usr/lib/mono/gac/Tao.OpenGl/2.1.0.12__1ca010269a4501ef
/usr/lib/mono/gac/Tao.OpenGl/2.1.0.12__1ca010269a4501ef/Tao.OpenGl.dll.config
/usr/lib/mono/gac/Tao.OpenGl/2.1.0.12__1ca010269a4501ef/Tao.OpenGl.dll
/usr/share
/usr/share/doc
/usr/share/doc/tao-opengl
/usr/share/doc/tao-opengl/AUTHORS
/usr/share/doc/tao-opengl/NEWS
/usr/share/doc/tao-opengl/INSTALL
/usr/share/doc/tao-opengl/COPYING
/usr/share/doc/tao-opengl/README
/usr/share/doc/tao-opengl/ChangeLog
/usr/share/doc/tao-opengl/doc
/usr/share/doc/tao-opengl/doc/Tao.OpenGl.xml

---

### Post by tomdevries on 2008-02-05
Damn, what a mess, all these dependencies, problems with pkg-config et cetera...

Been trying to install fleow here today, my god :P

Nice to see you guys made some progress as well, I'm wondering if you got it working already?

I don't understand what's up with this (bug?) in pkg-config. It won't read the Tao.*.pc files from /usr/lib/pkgconfig/ which is defined in the $PKG_CONFIG_PATH, but when installing Tao.*.pc files in /usr/local/lib/pkgconfig/ and adding that to the $PKG_CONFIG_PATH, it does seem to work properly. Weird stuff...

I finally got my fleow to run the autogen.sh without complaining about the Tao.OpenGl and Tao.DevIl. So I've got these to packages installed, as well as the gtkglarea-sharp, which I downloaded from the mono-project svn. Installing this indeed required automake1.9, according to the autogen.sh of gtkglarea. After installing automake1.9 it still failed, complaining that automake1.9 wasn't installed. 
By looking at the sourcecode, the check was done by checking 'automake --version'. 
I aliased automake to be automake-1.9, which when prompted with 'automake --version' indeed returned automake-1.9:
```

tom@werkbak:~$ alias automake=automake-1.9
tom@werkbak:~$ automake --version
automake (GNU automake) 1.9.6
[...]

```
But even that didn't seem to work. So still having this aliased I commented out the automake1.9 check in autogen.sh and perfectly ran the autogen.sh.

Problem I'm experiencing at the moment is while trying to make fleow, that package 'tao-opengl-glu' can't be found. Yet another dependency?! Drives me crazy...

Anyway, it's way to late, time to hit the bed. Hopefully this may help some of you guys, and maybe we can finally get this Fleow to work under Ubuntu!

---

### Post by wellwatch on 2008-02-14
Well I'm at the point of compiling thats for the help spliffmonkey187, and Ehtetur but it is throwing an error when I run make

with package config, it can't find tao-opengl, tao-opengl-glu, and tao-devil.  Not too much of a surprise the names are different then the installed packages.  I think the answer is to go into the code, and modify it as sad as that makes me, and as much work as it will be.  If you guys have any suggestions let me know.  If not I'll post back some results.

---

### Post by wellwatch on 2008-02-14
Did some more work on fleow and it does not look good.  After getting the glarea dependency resolved (forgot to take notes on this part).  I ran make, and it started throwing errors.  Involving the renaming of tao libraries from tao-opengl/tao-devil to Tao.OpenGl, and Tao.DeviL in the first line of Makefile.am.  
change the first line of src/Makefile.am to:

```

MCS_FLAGS = -debug -pkg:Tao.OpenGl,Tao.DevIl,gtkglarea-sharp -r:System.Data

```

Then there was an actual code error, that is really just too in depth for me to detail at this point if you really want to know I can post it.  Essentially it was a type casting error.  I don't know what the code is actually doing, so I can't offer a good fix,  I just changed it to get it to compile. After finally getting it build when ever I launched banshee mono couldn't find the tao/glarea libraries.  So pointing MONO_PATH to where ever the tao and gl area libraries are on your machine.  

for me it was
```

export MONO_PATH=/usr/local/lib/mono/gtkglarea-sharp:/usr/local/lib/mono/Tao.OpenGl/:/usr/local/lib/mono/Tao.DevIl/

```

Now it starts throwing a system error since i didnt have album art in the right places (from looking at the code you need to have a file "cover.jpg" in the same directory as the song you want it assosciated with)  that it was indexing an empty array.  I made some more code changes getting rid of this code to get it to launch.  

At this point i figured out the requirement of the cover.jpg file.  So I added one to one of the directoreis I was using, and now I see yet another dependency error.  So I installed the DeviL linux library, from [http://openil.sourceforge.net/download.php](http://openil.sourceforge.net/download.php).  

Here is the relevent output
```

Initializing Fleow Plugin
/home/joe/Desktop/Juno Reactor/Beyond the Infinite/cover.jpg
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.EntryPointNotFoundException: ilutGLLoadImage
  at (wrapper managed-to-native) Tao.DevIl.Ilut:ilutGLLoadImage (string)
  at Banshee.Plugins.Fleow.GLCover.LoadTexture (System.String filename) [0x00000] 
  at Banshee.Plugins.Fleow.Cover..ctor (System.String image, System.String artist, System.String albumtitle) [0x00000] 
  at Banshee.Plugins.Fleow.CoverList..ctor () [0x00000] 
  at Banshee.Plugins.Fleow.GLCoverList..ctor () [0x00000] 
  at Banshee.Plugins.Fleow.Engine.LoadTextures () [0x00000] 
  at Banshee.Plugins.Fleow.Engine.OnRealized (System.Object o, System.EventArgs e) [0x00000] 

```
So I'm going to keep investigating it, if I can actually see some album art I'll probably be more motivated to actually fix all this stuff.  If you guys have any suggestions let me know.  spliffmonkey lemme know if you want to do this as a project I could be game for helping with development if you want, at the very least I'll gladly be a debugger.

If I can think of a word that describes Fleow, it is Deprecated.

---

### Post by wellwatch on 2008-02-14
I got it working!

Initially when I compiled DeviL I didn't have glut3 (The OpenGL Utility Toolkit) installed.  so I installed that, recompiled DeviL, and then all those GL library functions were built into the shared library.  Initially they hadn't been since they didnt exist, and DeviLs config script just ifdefed the code that wouldnt compile out.  Then it worked.

The arts still a little screwy it looks like the art is upside down.  I'm not a big fan of the interface, underneath the art there are three buttons (left right and play) other than these I cant really see a means of picking music via the interface but I still dont have it really integrated and tested.

---

### Post by bwiklak on 2008-02-16
Hey guys,
I also wanted to get CF in Banshee, managed to compile fleow but it's not developed anymore. Also I don't like dotNet and all M$ stuff.
So I started this [http://ubuntuforums.org/showthread.php?t=695506&highlight=CoverFlow](http://ubuntuforums.org/showthread.php?t=695506&highlight=CoverFlow)

---

### Post by Ehtetur on 2008-02-21
> **wellwatch said:**
> I got it working!

Dude way to go... you rock!! :twisted:
kinda funny and definitely kinda cool that devil was the problem...

Was planning on working on fleow after I finished a project on RHEL...
Now I can't wait 'til it's done so I can get into gutsy and recompile DeviL :twisted:

---

