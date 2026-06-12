---
title: "Can AviSynth work on Linux ?"
date: 2022-03-01
forum: Multimedia Software
---

### Post by satimis on 2022-03-01
Hi all,

Any folk on the forum has tried following tutorial;

AviSynth Install Guide for Linux
[https://www.animemusicvideos.org/forum/viewtopic.php?f=44&t=125120#p1546741](https://www.animemusicvideos.org/forum/viewtopic.php?f=44&t=125120#p1546741)

Does it work?

Any online discussion forum for AviSynth running on Linux other than Doom9's forum;
[https://forum.doom9.org/](https://forum.doom9.org/)

Please advise.  Thanks in advance

Regards.

---

### Post by qyot27 on 2022-03-06
Honestly, don't bother with trying to use AviSynth under Wine **unless** you know for a fact that one of the plugins you need to use hasn't been ported to Linux, because while AviSynth is actually one of the traditional examples of programs that can actually run better under Wine than on Windows, it involves understanding how Wine is set up and used.  It's easier to just set up a native Linux build.

Dependencies:
```
sudo apt-get install build-essential git cmake checkinstall libdevil-dev pkgconf
```

AviSynth+:
```
git clone https://github.com/AviSynth/AviSynthPlus.git && \
mkdir -p AviSynthPlus/build && \
cd AviSynthPlus/build && \
cmake ../ && \
make -j$(nproc) && \
    sudo checkinstall --pkgname=avisynth --pkgversion="$(grep -r \
    Version avs_core/avisynth.pc | cut -f2 -d " ")-$(date --rfc-3339=date | \
    sed 's/-//g')-git" --backup=no --deldoc=yes --delspec=yes --deldesc=yes \
    --strip=yes --stripso=yes --addso=yes --fstrans=no --default
```

avs2yuv:
```
git clone https://github.com/DJATOM/avs2yuv.git && \
mkdir -p avs2yuv/build && \
cd avs2yuv/build && \
cmake ../ && \
make && \
sudo make install
```

Ensure it works by piping into mpv. Script (let's name it test.avs):
```
Version(pixel_type="YUV420P8")
```

Pipe from avs2yuv to mpv:
```
avs2yuv test.avs -o - | mpv -
```

Since the ImageSeq plugin was also installed, you can use ImageSource to open image files.  ConvertToYUV444 is only there so avs2yuv can pipe it in y4m format.
```
ImageSource("test.png")
ConvertToYUV444()
```

Install FFMS2 as a source filter.  This is where it gets slightly lengthy, but you only need to do this part once (apart from periodically wanting to update the plugin, but that's usually not needed too often).

Dependencies (the autotools might have already been pulled in with build-essential):
```
sudo apt-get install libdav1d-dev libbz2-dev zlib1g-dev nasm autoconf automake libtool m4
```

Build and install a minimal, static version of FFmpeg to an alternate location so it won't conflict with the one on the system.
```
git clone https://git.videolan.org/git/ffmpeg.git && \
mkdir -p ffmpeg/ffmpeg-minimal-build && \
cd ffmpeg/ffmpeg-minimal-build && \
    ../configure --prefix=/opt/ffmpeg_build_for_ffms2 --enable-gpl \
    --disable-encoders --disable-muxers --disable-doc --disable-debug --disable-devices \
    --disable-avdevice --enable-libdav1d && \
make -j$(nproc) && \
sudo make install
```

Build FFMS2:
```
git clone https://github.com/FFMS/ffms2.git && \
cd ffms2 && \
    PKG_CONFIG_PATH=/opt/ffmpeg_build_for_ffms2/lib/pkgconfig \
    CPPFLAGS="-I/usr/local/include/avisynth" ./autogen.sh \
    --prefix=$HOME/.local --enable-avisynth --enable-shared \
    --with-pic && \
make -j$(nproc) && \
make install
cd ~/.local/lib/avisynth
ln -s ../libffms2.so libffms2.so
```

Now, you can open real video or audio files the way you typically would using AviSynth and FFMS2 on a Windows machine:
```
FFmpegSource2("test.mkv",atrack=-1)
```

Other plugins that have been ported to Linux are listed in this thread on Doom9:
[https://forum.doom9.org/showthread.php?t=182032](https://forum.doom9.org/showthread.php?t=182032)



While it **is** possible to rebuild the system FFmpeg and mpv to support taking AviSynth scripts directly as input without piping (particularly important for audio support, or comfortably watching the script), doing so as a drop-in replacement for the one provided by the Ubuntu repositories is a more advanced task.  So instead, just use the $HOME/.local trick from earlier:
```
cd ffmpeg/ffmpeg-build && \
mkdir linux && cd linux && \
../../configure --prefix=$HOME/.local --progs-suffix=avs --enable-gpl --disable-doc --enable-avisynth && \
make -j$(nproc) && \
make install
```

Now, you can open scripts directly by using **ffmpeg-avs** as the program name, like so:
```
ffmpeg-avs -i test.avs <options> output
```

If $HOME/.local/bin isn't on the $PATH, you may need to add that in your .bashrc.

---

### Post by satimis on 2022-03-06
Hi,

Lot of thanks for your detail advice.

Performed following steps

> **qyot27 said:**
>  - snip -

Dependencies:
```
sudo apt-get install build-essential git cmake checkinstall libdevil-dev pkgconf
```

AviSynth+:
```
git clone https://github.com/AviSynth/AviSynthPlus.git && \
mkdir -p AviSynthPlus/build && \
cd AviSynthPlus/build && \
cmake ../ && \
make -j$(nproc) && \
    sudo checkinstall --pkgname=avisynth --pkgversion="$(grep -r \
    Version avs_core/avisynth.pc | cut -f2 -d " ")-$(date --rfc-3339=date | \
    sed 's/-//g')-git" --backup=no --deldoc=yes --delspec=yes --deldesc=yes \
    --strip=yes --stripso=yes --addso=yes --fstrans=no --default
```

avs2yuv:
```
git clone https://github.com/DJATOM/avs2yuv.git && \
mkdir -p avs2yuv/build && \
cd avs2yuv/build && \
cmake ../ && \
make && \
sudo make install
```

1)
Dependencies:
~$ sudo apt-get install build-essential git cmake checkinstall libdevil-dev pkgconf

It went throught without complaint

2)
AviSynth+:
$ git clone [https://github.com/AviSynth/AviSynthPlus.git](https://github.com/AviSynth/AviSynthPlus.git) && \
> mkdir -p AviSynthPlus/build && \
> cd AviSynthPlus/build && \
> cmake ../ && \
> make -j$(nproc) && \
> sudo checkinstall --pkgname=avisynth --pkgversion="$(grep -r \
> Version avs_core/avisynth.pc | cut -f2 -d " ")-$(date --rfc-3339=date | \
> sed 's/-//g')-git" --backup=no --deldoc=yes --delspec=yes --deldesc=yes \
> --strip=yes --stripso=yes --addso=yes --fstrans=no --default```

....
....
**********************************************************************

 Done. The new package has been installed and saved to

 /home/satimis/AviSynthPlus/build/avisynth_3.7.1-20220306-git-1_amd64.deb

 You can remove it from your system anytime using: 

      dpkg -r avisynth

**********************************************************************

```

3)
avs2yuv:
$ git clone [https://github.com/DJATOM/avs2yuv.git](https://github.com/DJATOM/avs2yuv.git) && \
> mkdir -p avs2yuv/build && \
> cd avs2yuv/build && \
> cmake ../ && \
> make && \
> sudo make install```

....
[ 50%] Building C object CMakeFiles/avs2yuv.dir/avs2yuv.c.o
[100%] Linking C executable avs2yuv
[100%] Built target avs2yuv
[100%] Built target avs2yuv
Install the project...
-- Install configuration: ""
-- Installing: /usr/local/bin/avs2yuv

```



> 
Ensure it works by piping into mpv. Script (let's name it test.avs):
```
Version(pixel_type="YUV420P8")
```

Pipe from avs2yuv to mpv:
```
avs2yuv test.avs -o - | mpv -
```

Since the ImageSeq plugin was also installed, you can use ImageSource to open image files.  ConvertToYUV444 is only there so avs2yuv can pipe it in y4m format.
```
ImageSource("test.png")
ConvertToYUV444()
```

......
......


I'm stuck here;
Ensure it works by piping into mpv. Script (let's name it test.avs): 

Whether create a script named test.avs with following contents ?```

Version(pixel_type="YUV420P8")
avs2yuv test.avs -o - | mpv -
ImageSource("test.png")
ConvertToYUV444()

```

Where shall I put the script test.avs?  Which folder? 

Please advise.  Thanks

Regards

---

### Post by qyot27 on 2022-03-06
It doesn't matter what folder.  And just the Version line goes in that script.  Once you confirm that a simple script using Version works, you can try a different script like the one shown using ImageSource (replacing *test.png* with the real name of the image you want to open).

---

### Post by satimis on 2022-03-06
> **qyot27 said:**
> It doesn't matter what folder.  And just the Version line goes in that script.  Once you confirm that a simple script using Version works, you can try a different script like the one shown using ImageSource (replacing *test.png* with the real name of the image you want to open).
Thanks.

[B][COLOR="#FF0000"]Continue
========[/COLOR][/B]
$ nano /home/satimis/test.avs
Version(pixel_type="YUV420P8") # put this line on the file

$ ls -al /home/satimis/test.avs ```

-rw-rw-r-- 1 satimis satimis 31 Mar  7 12:14 /home/satimis/test.avs

```

$ avs2yuv test.avs -o - | mpv -```

Error: Import: couldn't open "test.avs".
Command 'mpv' not found, but can be installed with:
sudo apt install mpv
```

$ sudo apt install mpv

$ avs2yuv test.avs -o - | mpv -```

Error: Import: couldn't open "test.avs".
[file] Reading from stdin...
Failed to recognize file format.
Exiting... (Errors when loading file)

```

.avs can't be recognized

$ ImageSource("test.png")```

bash: syntax error near unexpected token `"test.png"'
```

How to fix the problem?  Tks

Regards

---

### Post by qyot27 on 2022-03-07
What happens with
```
avs2yuv test.avs -o /dev/null
```

---

### Post by satimis on 2022-03-07
> **qyot27 said:**
> What happens with
```
avs2yuv test.avs -o /dev/null
```
$ avs2yuv test.avs -o /dev/null```

Avs2YUV 0.30
Script file:    test.avs
Resolution:     480x106
Frames per sec: 24
Total frames:   240
Progress       Frames       FPS   Elapsed    Remain
[ 99.6%]    239/240    14937.50   0:00:00   0:00:00   
Started:        Mon Mar  7 13:21:35 2022
Finished:       Mon Mar  7 13:21:35 2022
Elapsed:        0:00:00

```

Again;
avs2yuv test.avs -o - | mpv -```

Avs2YUV 0.30
Script file:    test.avs
Resolution:     480x106
Frames per sec: 24
Total frames:   240
[file] Reading from stdin...
Progress       Frames       FPS   Elapsed    Remain
 (+) Video --vid=1 (rawvideo 480x106 24.000fps)0:44   
VO: [gpu] 480x106 yuv420p 23.45   0:00:00   0:00:08   
[ 99.6%]    239/240      373.44   0:00:00   0:00:00   
Started:        Mon Mar  7 13:45:23 2022
Finished:       Mon Mar  7 13:45:24 2022
Elapsed:        0:00:01
V: 00:00:09 / 00:00:09 (100%) Cache: 0.0s

```

Now it works

> 
...... using ImageSource (replacing test.png with the real name of the image you want to open). 

I haven't created test.png.  Where is test.png?

---

### Post by qyot27 on 2022-03-07
Like I previously said and you just quoted:
> replacing test.png with the real name of the image you want to open

---

### Post by satimis on 2022-03-07
> **qyot27 said:**
> Like I previously said and you just quoted:
noted

[B][COLOR="#FF0000"]Continue
======[/COLOR][/B]

4)
> Install FFMS2 as a source filter .......
Dependencies (the autotools might have already been pulled in with build-essential):
```

$ sudo apt-get install libdav1d-dev libbz2-dev zlib1g-dev nasm autoconf automake libtool m4
```


$ sudo apt-get install libdav1d-dev libbz2-dev zlib1g-dev nasm autoconf automake libtool m4```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libdav1d-dev
```

$ apt policy libdav1d-dev```

N: Unable to locate package libdav1d-dev

```

libdav1d-dev is not on repo

Regards

---

### Post by qyot27 on 2022-03-07
Oh, it appears that libdav1d-dev was only added to the repos in 21.04.  In that case, just swap it out for libaom-dev (in the repos since 20.04) and change the *--enable-libdav1d* option in the FFmpeg step to *--enable-libaom* (the alternative would be to also build libdav1d, but that might be tricky if it requires a newer version of meson than the repos have).  Or just omit the option entirely, as libdav1d and libaom are there for only one reason: making sure FFMS2 can open AV1 files.  Files distributed as AV1 are still relatively niche, so it's not critical for a functioning source filter, it's just nice to have.

---

### Post by satimis on 2022-03-07
> **qyot27 said:**
> Oh, it appears that libdav1d-dev was only added to the repos in 21.04.  In that case, just swap it out for libaom-dev (in the repos since 20.04) and change the *--enable-libdav1d* option in the FFmpeg step to *--enable-libaom* (the alternative would be to also build libdav1d, but that might be tricky if it requires a newer version of meson than the repos have).  Or just omit the option entirely, as libdav1d and libaom are there for only one reason: making sure FFMS2 can open AV1 files.  Files distributed as AV1 are still relatively niche, so it's not critical for a functioning source filter, it's just nice to have.
[B][COLOR="#FF0000"]Continued
======[/COLOR][/B]

5)
> 
Install FFMS2 as a source filter. This is where it gets slightly lengthy, but you only need to do this part once (apart from periodically wanting to update the plugin, but that's usually not needed too often).

Dependencies (the autotools might have already been pulled in with build-essential):

$ sudo apt-get install libaom-dev libbz2-dev zlib1g-dev nasm autoconf automake libtool m4```

....
Setting up bzip2-doc (1.0.8-2) ...
Setting up m4 (1.4.18-4) ...
Setting up libaom-dev:amd64 (1.0.0.errata1-3build1) ...
Setting up autotools-dev (20180224.1) ...
Setting up nasm (2.14.02-1) ...
Setting up autoconf (2.69-11.1) ...
Setting up libbz2-dev:amd64 (1.0.8-2) ...
Setting up automake (1:1.16.1-4ubuntu6) ...
update-alternatives: using /usr/bin/automake-1.16 to provide /usr/bin/automake (automake) in auto mode
Setting up libtool (2.4.6-14) ...
Setting up libltdl-dev:amd64 (2.4.6-14) ...
Processing triggers for man-db (2.9.1-1) ...
Processing triggers for install-info (6.7.0.dfsg.2-5) ...
```

6)
> 
Build and install a minimal, static version of FFmpeg to an alternate location so it won't conflict with the one on the system.

$ git clone [https://git.videolan.org/git/ffmpeg.git](https://git.videolan.org/git/ffmpeg.git) && \
> mkdir -p ffmpeg/ffmpeg-minimal-build && \
> cd ffmpeg/ffmpeg-minimal-build && \
>     ../configure --prefix=/opt/ffmpeg_build_for_ffms2 --enable-gpl \
>     --disable-encoders --disable-muxers --disable-doc --disable-debug --disable-devices \
> --disable-devices \
>     --disable-avdevice --enable-libaom && \
> make -j$(nproc) && \
> sudo make install```

.....
.....
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/replaygain.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/ripemd.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/samplefmt.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/sha.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/sha512.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/spherical.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/stereo3d.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/threadmessage.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/time.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/timecode.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/timestamp.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/tree.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/twofish.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/version.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/video_enc_params.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/xtea.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/tea.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/tx.h
INSTALL home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/libavutil/film_grain_params.h
INSTALL libavutil/avconfig.h
INSTALL libavutil/ffversion.h
INSTALL libavutil/libavutil.pc

```

7)
> 
Build FFMS2:
$ git clone [https://github.com/FFMS/ffms2.git](https://github.com/FFMS/ffms2.git) && \
cd ffms2 && \
    PKG_CONFIG_PATH=/opt/ffmpeg_build_for_ffms2/lib/pkgconfig \
    CPPFLAGS="-I/usr/local/include/avisynth" ./autogen.sh \
    --prefix=$HOME/.local --enable-avisynth --enable-shared \
    --with-pic && \
make -j$(nproc) && \
make install
```

...
...
See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
 /usr/bin/mkdir -p '/home/satimis/.local/bin'
  /bin/bash ./libtool   --mode=install /usr/bin/install -c src/index/ffmsindex '/home/satimis/.local/bin'
libtool: install: /usr/bin/install -c src/index/.libs/ffmsindex /home/satimis/.local/bin/ffmsindex
 /usr/bin/mkdir -p '/home/satimis/.local/share/doc/ffms2'
 /usr/bin/install -c -m 644 doc/ffms2-api.md doc/ffms2-changelog.md '/home/satimis/.local/share/doc/ffms2'
 /usr/bin/mkdir -p '/home/satimis/.local/include'
 /usr/bin/install -c -m 644 ./include/ffms.h ./include/ffmscompat.h '/home/satimis/.local/include'
 /usr/bin/mkdir -p '/home/satimis/.local/lib/pkgconfig'
 /usr/bin/install -c -m 644 ffms2.pc '/home/satimis/.local/lib/pkgconfig'
make[1]: Leaving directory '/home/satimis/ffmpeg/ffmpeg-minimal-build/ffmpeg/ffmpeg-minimal-build/ffms2'

```

8)
> 
Now, you can open real video or audio files the way you typically would using AviSynth and FFMS2 on a Windows machine:

On Windows 10.
Start VirtualDub2
-> File -> Open Video File

$ FFmpegSource2("test.mkv",atrack=-1)```

bash: syntax error near unexpected token `"test.mkv",atrack=-1'
```

$ FFmpegSource2("C:/home/satimis/Videos/test.mkv",atrack=-1)```

bash: syntax error near unexpected token `"C:/home/satimis/Videos/test.mkv",atrack=-1'
```

C:/home/satimis/Videos/
is path

How to start VirtualDub2 here?  Thanks

Regards

---

### Post by qyot27 on 2022-03-08
Those are not commands to be entered into bash.  Those go into the script file.

You can't open VirtualDub2.

---

### Post by satimis on 2022-03-08
> **qyot27 said:**
> Those are not commands to be entered into bash.  Those go into the script file.

You can't open VirtualDub2.
So the test.avs script file will consist 2 lines ?
```

Version(pixel_type="YUV420P8")
FFmpegSource2("test.mkv",atrack=-1)

```

Do I need adding path to "test.mkv" video file as mentioned on posting #11 above?

I don't have VirtualDub2 installed.  So running the test.avs will open the video file ?

---

