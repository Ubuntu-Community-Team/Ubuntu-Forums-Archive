---
title: "Media keys in XMMS"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by Vord on 2006-12-20
How would I get my media keys working in XMMS? I use a Logitech G15 keyboard with the media keys at the top, and I can get them to work in Amarok by configuring hotkeys, but not in XMMS, any tips?

---

### Post by mlampard on 2007-01-01
The g15daemon_xmms plugin in g15daemon svn will allow xmms to use the multimedia keys.  Currently it's not available as a separate package, PM me if you want help building or installing it.

If you have svn installed, you can retrieve the source:
svn co [https://svn.sourceforge.net/svnroot/g15daemon/trunk/g15daemon-audio-plugins/g15daemon_xmms](https://svn.sourceforge.net/svnroot/g15daemon/trunk/g15daemon-audio-plugins/g15daemon_xmms) g15daemon_xmms

It requires the xmms-devel and libg15render packages to build.

---

### Post by lime4x4 on 2007-01-01
i was looking for this as well.. were can i get the libg15render package?

---

### Post by mlampard on 2007-01-01
libg15render is available at [http://sourceforge.net/projects/g15tools](http://sourceforge.net/projects/g15tools).

The svn version is available via
svn co [https://svn.sourceforge.net/svnroot/g15tools/trunk/libg15render](https://svn.sourceforge.net/svnroot/g15tools/trunk/libg15render) libg15render

---

### Post by lime4x4 on 2007-01-01
here is the error i'm getting

john@john-edgy:~$ svn co [https://svn.sourceforge.net/svnroot/...g15daemon_xmms](https://svn.sourceforge.net/svnroot/...g15daemon_xmms) g15daemon_xmms
svn: PROPFIND request failed on '/svnroot/...g15daemon_xmms'
svn: Could not open the requested SVN filesystem

---

### Post by mlampard on 2007-01-01
sorry, looks like the forum munged the url.  it should be
svn co https://svn.sourceforge.net/svnroot/g15tools/trunk/libg15render libg15render
and 
svn co https://svn.sourceforge.net/svnroot/g15daemon/trunk/g15daemon-audio-plugins/g15daemon_xmms g15daemon_xmms

for libg15render and the xmms plugin respectively.

---

### Post by lime4x4 on 2007-01-02
ok one last question i hope.I downloaded it now how do i configure and make and install it?
thanks

---

### Post by earobinson on 2007-01-02
wasent xmms discontinued? why not use a more uptodate player

---

### Post by mlampard on 2007-01-02
change into the g15daemon_xmms directory, and as root:

./autogen.sh && ./configure && ./make && make install

then enable the g15daemon_xmms plugin in the xmms Visualisation Plugin page.

---

### Post by lime4x4 on 2007-01-02
well it complains it can't find the 

configure: error: "libg15daemon_client (or its devel package) not found. please install it"

i did install it from your previous link.So i downloaded the svn version u posted and i get the following error when trying to compile it. the readme says to use ./configure

john@john-edgy:~/libg15render$ ./configure
bash: ./configure: No such file or directory

---

### Post by mlampard on 2007-01-02
g15daemon_client is from the g15daemon devel package.  if you install that, the plugin should compile fine.

---

### Post by Vord on 2007-01-24
So, I know this is an old thread, and my thread at that, but I've just recent;y formatted, and in going through these steps, I've encountered some problems.


I downloaded the g15daemon_xmms svn version, changed into the directory, but when it comes to 
```
./autogen.sh && ./configure && ./make && make install
```
It outputs 
```
root@arsenic:/home/vord/g15daemon_xmms# ./autogen.sh
+ aclocal -I config
./autogen.sh: 1: aclocal: not found
+ libtoolize --force --copy
./autogen.sh: 1: libtoolize: not found
+ autoheader
./autogen.sh: 1: autoheader: not found
+ automake --add-missing --copy
./autogen.sh: 1: automake: not found
+ autoconf
./autogen.sh: 1: autoconf: not found
```

Am I doing something wrong? Or just missing something here?

---

### Post by lime4x4 on 2007-01-24
did u try installing all those packages??

sudo apt-get install aclocal libtoolize autoheader automake autoconf

---

### Post by Vord on 2007-01-24
E: Couldn't find package aclocal


And yeah, I'd tried before with the same output >_<

---

### Post by Vord on 2007-01-24
Okay, well, sudo apt-get install automake installed all the packages needed, but when I go to do 
```

./autogen.sh && ./configure && ./make && make install
```

this time, it goes through the compile process, outputs
```
bash: ./make: No such file or directory

```

and quits, any ideas?

---

### Post by lime4x4 on 2007-01-24
well make sure u have make installed

sudo apt-get install make

or try running it without the ./  in front of make

---

### Post by Vord on 2007-01-24
make is installed, running it without the ./ yields an error as well.

---

### Post by Vord on 2007-02-01
Bump, still getting the same error, any ideas?

---

