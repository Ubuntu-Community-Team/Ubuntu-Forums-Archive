---
title: "Comskip Core dump; general protection fault"
date: 2023-03-21
forum: Multimedia Software
---

### Post by BarnOwl on 2023-03-21
I recently moved from Xunbuntu 20.04 to 22.04 via a new install not an in place upgrade.  Comskip worked fine in 20.04 but, I'm getting core dumps in 22.04.  Dmesg says it's a general protection fault.

The following is displayed on the terminal:

```
comskip --ini=/etc/comskip.ini "/mnt/DVR_disk/EmbyDVR/XXXXX/Season 1/XXXXX.ts"
Comskip 0.82.009, made using ffmpeg
Donator build
The commandline used was:
comskip --ini=/etc/comskip.ini "/mnt/DVR_disk/EmbyDVR/XXXXXXX/Season 1/XXXXXX.ts"

Setting ini file to /etc/comskip.ini as per commandline
Using /etc/comskip.ini for initiation values.
Segmentation fault (core dumped)ec(378.71 fps), 1.00 sec(342.00 fps), 1%
```

The following message shows up in dmesg:

```
[ 5222.273020] traps: comskip[3636] general protection fault ip:7f1d65a7ecfb sp:7ffc83d52c90 error:0 in libc.so.6[7f1d65a28000+195000]
```

The puzzling thing is that it's not every time I run it.  It is almost every time though.

Any pointers would be appreciated.

---

### Post by TheFu on 2023-03-22
Recompile the package.

---

### Post by BarnOwl on 2023-03-27
> **TheFu said:**
> Recompile the package.

I'm not the most experienced at recompiling but, I did try that.  It took a few tries to get all the dependencies in but, I did finally get by the configure step.  The make is still failing. Here's what I think is the pertinent part of the output:

```
mv -f ccextratorwin/.deps/comskip-myth.Tpo ccextratorwin/.deps/comskip-myth.Po
gcc -g -O2    -o comskip comskip-comskip.o comskip-mpeg2dec.o comskip-platform.o comskip-video_out_dx.o ccextratorwin/comskip-608.o ccextratorwin/comskip-ccextractor.o ccextratorwin/comskip-encoding.o ccextratorwin/comskip-general_loop.o ccextratorwin/comskip-myth.o -largtable2 -lavutil -lavformat -lavcodec  -lpthread -lm 
/usr/bin/ld: comskip-mpeg2dec.o:/home/mickeyrat/Comskip-0.82.009/mpeg2dec.c:164: multiple definition of `height'; comskip-comskip.o:/home/mickeyrat/Comskip-0.82.009/comskip.c:537: first defined here
/usr/bin/ld: comskip-mpeg2dec.o:/home/mickeyrat/Comskip-0.82.009/mpeg2dec.c:164: multiple definition of `width'; comskip-comskip.o:/home/mickeyrat/Comskip-0.82.009/comskip.c:536: first defined here
collect2: error: ld returned 1 exit status
make: *** [Makefile:481: comskip] Error 1
```

That looks like an error in the source code.  I'm not sure where to go from here.

---

### Post by TheFu on 2023-03-27
> **BarnOwl said:**
> I'm not the most experienced at recompiling but, I did try that.  It took a few tries to get all the dependencies in but, I did finally get by the configure step.  The make is still failing. Here's what I think is the pertinent part of the output:

```
mv -f ccextratorwin/.deps/comskip-myth.Tpo ccextratorwin/.deps/comskip-myth.Po
gcc -g -O2    -o comskip comskip-comskip.o comskip-mpeg2dec.o comskip-platform.o comskip-video_out_dx.o ccextratorwin/comskip-608.o ccextratorwin/comskip-ccextractor.o ccextratorwin/comskip-encoding.o ccextratorwin/comskip-general_loop.o ccextratorwin/comskip-myth.o -largtable2 -lavutil -lavformat -lavcodec  -lpthread -lm 
/usr/bin/ld: comskip-mpeg2dec.o:/home/mickeyrat/Comskip-0.82.009/mpeg2dec.c:164: multiple definition of `height'; comskip-comskip.o:/home/mickeyrat/Comskip-0.82.009/comskip.c:537: first defined here
/usr/bin/ld: comskip-mpeg2dec.o:/home/mickeyrat/Comskip-0.82.009/mpeg2dec.c:164: multiple definition of `width'; comskip-comskip.o:/home/mickeyrat/Comskip-0.82.009/comskip.c:536: first defined here
collect2: error: ld returned 1 exit status
make: *** [Makefile:481: comskip] Error 1
```

That looks like an error in the source code.  I'm not sure where to go from here.

That when you ask for help from the project team.  It has been a few months since the last time I recompiled comskip and I don't clearly recall, but are you certain the ccextratorwin/ directory isn't for MS-Windows?  There should be a README or INSTALL file that explains which code to use.  You'll need to be using the latest version.  Devs won't bother looking at old versions.  When I use comskip (about 10x a day), there's no GUI. I'm on ...
```
$ comskip -v
Comskip 0.82.011, made using ffmpeg
```
which is newer than the version you are trying to compile.

---

### Post by BarnOwl on 2023-03-28
> **TheFu said:**
> That when you ask for help from the project team.  It has been a few months since the last time I recompiled comskip and I don't clearly recall, but are you certain the ccextratorwin/ directory isn't for MS-Windows?  There should be a README or INSTALL file that explains which code to use.  You'll need to be using the latest version.  Devs won't bother looking at old versions.  When I use comskip (about 10x a day), there's no GUI. I'm on ...
```
$ comskip -v
Comskip 0.82.011, made using ffmpeg
```
which is newer than the version you are trying to compile.

That's odd.  I downloaded the tarball at the [Comskip GitHub page]("https://github.com/erikkaashoek/Comskip") by hitting the latest release link.  The only README has instructions for both Linux and Windows.  I'm not getting any GUI and I don't want one.  

If you've got a better place to get it, please share.

---

### Post by TheFu on 2023-03-28
Comskip has been very stable for years.  Making a "release" is a big deal that requires more effort than just saying to git-clone the master branch.  The dev will be working in just off the master branch on a stable software project like this.

Ensure your setup meets the dependencies, then use:
```
$ git clone git://github.com/erikkaashoek/Comskip
$ cd Comskip
$ ./autogen.sh
$ ./configure
$ make
```

I know this works on 20.04. I don't have a 22.04 system, but I do have an Mint 21.1 system (based on Ubuntu 22.04) and was able to get it compiled there.
```
$ sudo apt-get install -y autoconf libtool git build-essential libargtable2-dev libavformat-dev libsdl1.2-dev **libswscale5-dev libswscale-dev**
$ git clone **https**://github.com/erikkaashoek/Comskip
$ cd Comskip
$ ./autogen.sh
$ ./configure
$ make
```

Yep, it worked. Just tested it.

Hopefully, you can get it working too.

---

### Post by BarnOwl on 2023-03-29
[QUOTE=I know this works on 20.04. I don't have a 22.04 system, but I do have an Mint 21.1 system (based on Ubuntu 22.04) and was able to get it compiled there.
```
$ sudo apt-get install -y autoconf libtool git build-essential libargtable2-dev libavformat-dev libsdl1.2-dev **libswscale5-dev libswscale-dev**
$ git clone **https**://github.com/erikkaashoek/Comskip
$ cd Comskip
$ ./autogen.sh
$ ./configure
$ make
```

Yep, it worked. Just tested it.
libswscale5-dev
Hopefully, you can get it working too.[/QUOTE]

I need to thank you for sticking with this.  Unfortunately, there's still an issue.  I installed libswscale-dev but, I could not find libswscale5-dev at all.  It's supposed to be in the universe repository and I added that but, still didn't get Ilibswscale5-dev.  It did complie without it but, I'm now getting a segmentation fault.  So, I'm guessing there's a package or repository I need.

---

### Post by TheFu on 2023-03-29
I don't have any special repos added.  1 from Mint and 4 from Ubuntu jammy (main, updates, backports, security). That's it.

---

### Post by BarnOwl on 2023-03-29
> **TheFu said:**
> I don't have any special repos added.  1 from Mint and 4 from Ubuntu jammy (main, updates, backports, security). That's it.

Tell you the truth, I'm beginning to think there's something wrong with my installation.  Tomorrow I may try firing up another box and just try to get comskip working and nothing else.

---

### Post by ranger122 on 2023-05-11
Did you ever come up with a solution for this?  Comskip is giving segmentation faults 'sometimes'.  Other times it runs.  Also running Mint 21 and also unable to install libswscale5-dev.  "Unable to locate package libswscale5-dev"

---

