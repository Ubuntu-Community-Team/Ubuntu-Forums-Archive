---
title: "Where is the executable of MPlayer located?"
date: 2015-11-02
forum: Multimedia Software
---

### Post by Lew_Wei_Hao on 2015-11-02
Hi,

After installing MPlayer, I am able to run it normally from the command line by supplying it with a input mp3 file.However, I am unable to locate its binary executable. If I am able to run the mplayer, there must be an executable somewhere right? The reason I'm trying to locate the executable is that I am trying to feed the AFL fuzzer with the executable for testing. 

I've tried doing a whereis mplayer but it only returned me a file of shared library type.

How do I find its binary executable?

Thanks.

---

### Post by howefield on 2015-11-02
Try

```
whereis mplayer
```

---

### Post by Lew_Wei_Hao on 2015-11-02
Yep I've tried that but it only gives me shared library file type

---

### Post by Lars Noodén on 2015-11-02
'which' should point you to the executable

```

which player

```

---

### Post by Lew_Wei_Hao on 2015-11-02
Yep I've tried using which as well but it points me to the shared library file type.

---

### Post by Lars Noodén on 2015-11-02
Strange.  That should show that mplayer is in /usr/bin/mplayer

---

### Post by Lew_Wei_Hao on 2015-11-02
Yep it shows that exact location of /usr/bin/mplayer as well but when I go to the directory, that mplayer file is of shared library type rather than executable type.

---

### Post by howefield on 2015-11-02
Search for mplayer in Files, right click the icon and select Open Item Location.

All 3 methods give me /usr/bin/mplayer.

---

### Post by Lew_Wei_Hao on 2015-11-02
[ATTACH=CONFIG]265328[/ATTACH]

I got this search result instead.

Could it be the way I compile and make the file? I used the afl-gcc as the compiler and did a make followed by make install.

---

### Post by SeijiSensei on 2015-11-02
If you compiled mplayer yourself, the binary is likely located in /usr/local/bin/.  Most source releases follow the convention of putting things in /usr/local/ so as not to interfere with the files installed by the basic distribution.

Is there some reason you need to compile mplayer?  If you're using 14.04, I recommend installing Doug McMahon's PPA and getting mplayer from there: [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

If you're using a different version of Ubuntu, you can find mplayer at [https://launchpad.net/~mc3man/+archive/ubuntu/mplayer-test](https://launchpad.net/~mc3man/+archive/ubuntu/mplayer-test).

I used to install mplayer from source, but I gave that up some time ago and let Doug handle it. I've also generally switched over to mpv; I use his repositories for that as well.

---

### Post by Lew_Wei_Hao on 2015-11-02
Yes, the reason I need to compile it is that I am trying to fuzz the program. Hence, I need to use the AFL-GCC as the compiler to get an instrumented version of the executable that is ready for fuzzing.

---

### Post by shantiq on 2015-11-02
this is what i find on my setup


```
locate mplayer
/etc/mplayer
/home/shantiq/.mplayer
/home/shantiq/.mplayer/config
/usr/bin/mplayer
/usr/lib/mime/packages/mplayer2
/usr/lib/python3/dist-packages/devedeng/mplayer.py
/usr/lib/python3/dist-packages/devedeng/__pycache__/mplayer.cpython-34.pyc
/usr/lib/x86_64-linux-gnu/libvisual-0.4/input/input_mplayer.so
/usr/lib/xmms/Input/libxmmplayer.la
/usr/lib/xmms/Input/libxmmplayer.so
/usr/share/app-install/desktop/gnome-mplayer:gnome-mplayer.desktop
/usr/share/app-install/desktop/kmplayer:kde4__kmplayer.desktop
/usr/share/app-install/desktop/mplayer-gui:mplayer.desktop
/usr/share/app-install/desktop/smplayer:smplayer.desktop
/usr/share/app-install/icons/gnome-mplayer.svg
/usr/share/app-install/icons/kmplayer.svgz
/usr/share/app-install/icons/mplayer.png
/usr/share/app-install/icons/smplayer.svg
/usr/share/bash-completion/completions/gmplayer
/usr/share/bash-completion/completions/gnome-mplayer
/usr/share/bash-completion/completions/mplayer
/usr/share/bash-completion/completions/mplayer2
/usr/share/doc/mplayer2
/usr/share/doc/xmms-xmmplayer
/usr/share/doc/liquidsoap/html/scripts/input_mplayer.html
/usr/share/doc/liquidsoap/html/scripts/input_mplayer.liq
/usr/share/doc/mplayer2/changelog.Debian.gz
/usr/share/doc/mplayer2/copyright
/usr/share/doc/mpv/mplayer-changes.rst.gz
/usr/share/doc/mpv/mplayer-input.conf
/usr/share/doc/xmms-xmmplayer/AUTHORS
/usr/share/doc/xmms-xmmplayer/NEWS.gz
/usr/share/doc/xmms-xmmplayer/README
/usr/share/doc/xmms-xmmplayer/TODO
/usr/share/doc/xmms-xmmplayer/changelog.Debian.gz
/usr/share/doc/xmms-xmmplayer/copyright
/usr/share/icons/oxygen/128x128/apps/kmplayer.png
/usr/share/icons/oxygen/128x128/mimetypes/application-x-mplayer2.png
/usr/share/icons/oxygen/16x16/apps/kmplayer.png
/usr/share/icons/oxygen/16x16/mimetypes/application-x-mplayer2.png
/usr/share/icons/oxygen/22x22/apps/kmplayer.png
/usr/share/icons/oxygen/22x22/mimetypes/application-x-mplayer2.png
/usr/share/icons/oxygen/256x256/mimetypes/application-x-mplayer2.png
/usr/share/icons/oxygen/32x32/apps/kmplayer.png
/usr/share/icons/oxygen/32x32/mimetypes/application-x-mplayer2.png
/usr/share/icons/oxygen/48x48/apps/kmplayer.png
/usr/share/icons/oxygen/48x48/mimetypes/application-x-mplayer2.png
/usr/share/icons/oxygen/64x64/apps/kmplayer.png
/usr/share/icons/oxygen/64x64/mimetypes/application-x-mplayer2.png
/usr/share/man/man1/mplayer.1.gz
/var/lib/dpkg/info/mplayer2.list
/var/lib/dpkg/info/mplayer2.md5sums
/var/lib/dpkg/info/xmms-xmmplayer.list
/var/lib/dpkg/info/xmms-xmmplayer.md5sums
```

---

### Post by SeijiSensei on 2015-11-02
> **Lew_Wei_Hao said:**
> Yes, the reason I need to compile it is that I am trying to fuzz the program. Hence, I need to use the AFL-GCC as the compiler to get an instrumented version of the executable that is ready for fuzzing.

So was there a /usr/local/bin/mplayer as a result?

---

### Post by Lew_Wei_Hao on 2015-11-02
Yes, but the mplayer at that location is of shared library type rather than executable,which is what I am looking for.

---

### Post by Lars Noodén on 2015-11-02
Also, try *./configure --help* to see your options.  One of them (--prefix=) by default points executables to /usr/local/bin as SeijiSensei suggests.

---

### Post by vasa1 on 2015-11-02
> **Lew_Wei_Hao said:**
> Yes, but the mplayer at that location is of shared library type rather than executable,which is what I am looking for.
What command are you using to find that?

Why don't you post the actual output here?

Example:```
09:07 PM ~ $ file /usr/bin/mplayer
/usr/bin/mplayer: ELF 64-bit LSB  **_executable_**, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=be30dd9e6337decdf00f6ec82bfa421aa483bbfa, stripped
09:07 PM ~ $ 
```

---

### Post by Lew_Wei_Hao on 2015-11-02
> **vasa1 said:**
> What command are you using to find that?

Why don't you post the actual output here?

Example:```
09:07 PM ~ $ file /usr/bin/mplayer
/usr/bin/mplayer: ELF 64-bit LSB  **_executable_**, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=be30dd9e6337decdf00f6ec82bfa421aa483bbfa, stripped
09:07 PM ~ $ 
```

```

w31ha0@ubuntu:~$ which mplayer
/usr/local/bin/mplayer
w31ha0@ubuntu:~$ file /usr/local/bin/mplayer
/usr/local/bin/mplayer: ELF 32-bit LSB  shared object, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=322168428c8325ed23de0718a294c1ac83311218, stripped

```

Is there any possibility I can compile this shared library into an executable?

---

### Post by mc4man on 2015-11-03
You already found it, ie. /usr/local/bin/mplayer
Recent history mplayer (and some other binaries) are or  seen as shared objects (executable object files
Why I'm not too sure but nothing new.

---

### Post by andrew.46 on 2015-11-04
Same question a while back:

[https://lists.mplayerhq.hu/pipermail/mplayer-users/2013-June/086326.html](https://lists.mplayerhq.hu/pipermail/mplayer-users/2013-June/086326.html)

---

