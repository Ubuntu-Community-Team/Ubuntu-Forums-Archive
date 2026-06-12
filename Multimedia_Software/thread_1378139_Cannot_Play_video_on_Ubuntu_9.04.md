---
title: "Cannot Play video on Ubuntu 9.04"
date: 2010-01-11
forum: Multimedia Software
---

### Post by vamsiL on 2010-01-11
I am a newbie on linux. Have upgraded from Ubuntu 8.10 to 9.04. Everything was working fine till today.
I suddently find that I am not able to play any video files on the Ubuntu 9.04

I have Movie Player and VLC Media Player installed. In both players, whenever I try to play a video, the player is just closing. Or sometimes in VLC Media player, I can hear the audio but when I click the video screen of the player, it closes.:(

Please help me out on this one...

Thanks in advance

---

### Post by vamsiL on 2010-01-11
BTB, I am using a 82815 Intel Chipset based Gigabyte Motherboard with onboard graphics card.

---

### Post by llawwehttam on 2010-01-11
Have you installed codecs and the ubuntu-restricted-extras package?

---

### Post by barnex on 2010-01-11
Can you start vlc from the command line and look if there is an error message printed there?

There has been a vlc update recently, but in my case it did not break things.

---

### Post by vamsiL on 2010-01-11
> **llawwehttam said:**
> Have you installed codecs and the ubuntu-restricted-extras package?

Yes, I have the Gstreamer Codecs Installed and also the Ubuntu-restricted extras package

> **barnex said:**
> Can you start vlc from the command line and look if there is an error message printed there?

There has been a vlc update recently, but in my case it did not break things.

How do i start from command line? (Sorry, but am a totally new to linux...)

Okay, I typed VLC in the terminal. The VLC Media player opened and when I tried to play a video file by Media->Open File,
 this is the output on the terminal

>  VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  81
  Current serial number in output stream:  82


---

### Post by llawwehttam on 2010-01-11
looks like its due to your graphics drivers.

Could you post the output of ```
lspci -nn | grep VGA
```

and 
```
glxinfo |grep vendor

```

thanks

---

### Post by nhong on 2010-01-11
Everybody help please, I have a similar problem since my video still play but no output at all (time bar still count but screen is black), interesting is when I take a screen shot, it captured fine, really confusing, like it has a black screen on top of the original one :(( .

this is a video on example folder I open in totem (I guess), btw problem occur in the other format as well (I've tried mp4, flv)

adobe flash player plugin on firefox still works fine, I'm able to watch youtube on the web.

[IMG]http://i233.photobucket.com/albums/ee55/namnhong/Screenshot.png[/IMG]

```

root@ubuntu:/home/nhong# lspci -nn | grep VGA
01:06.0 VGA compatible controller [0300]: ATI Technologies Inc ES1000 [1002:515e] (rev 02)
root@ubuntu:/home/nhong# glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project

```

---

### Post by vamsiL on 2010-01-11
> **llawwehttam said:**
> looks like its due to your graphics drivers.

Could you post the output of ```
lspci -nn | grep VGA
```and 
```
glxinfo |grep vendor

```thanks

This is the output

> 
vamsi@vamsi-desktop:~$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82865G Integrated Graphics Controller [8086:2572] (rev 02)

> 
vamsi@vamsi-desktop:~$ glxinfo |grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project


---

### Post by llawwehttam on 2010-01-11
firstly try ```
gstreamer-properties
```

then in vlc go to properties>Video and change the driver to GL.

---

### Post by vamsiL on 2010-01-11
> **llawwehttam said:**
> firstly try ```
gstreamer-properties
```then in vlc go to properties>Video and change the driver to GL.

I used the above command and in video tab-> Default Output->Plugin->Default
and Default Input->Plugin->Video for Linux 2 (v4l2)
and when I click test on the Input section, this is the output
> 
vamsi@vamsi-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
The program 'gstreamer-properties' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 61 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)



When I change the VLC video output to Open GL Video Output the video is playing fine

---

### Post by llawwehttam on 2010-01-11
ERRM just a quick question. How much ram do you have?

---

### Post by vamsiL on 2010-01-11
> **llawwehttam said:**
> ERRM just a quick question. How much ram do you have?

I have 1GB DDR RAM

---

### Post by nhong on 2010-01-11
thanks you guys, I also fixed my problem :) thanks a lot, I've been exhausted with this for nearly a month now.;)

---

### Post by vamsiL on 2010-01-11
> **vamsiL said:**
> I used the above command and in video tab-> Default Output->Plugin->Default
and Default Input->Plugin->Video for Linux 2 (v4l2)
and when I click test on the Input section, this is the output



When I change the VLC video output to Open GL Video Output the video is playing fine


Now the video is playing fine ... Thank you "[llawwehttam]("http://ubuntuforums.org/member.php?u=930300")"

 but can you tell me what the problem was..?
Yesterday X11 video output was working fine but why did this problem come suddenly

---

### Post by rifter on 2010-03-02
For a lot of people, BadAlloc errors are fixed by switching from Video4Linux output to X11 Video Output.

For vlc you can do this either by calling it on the command line

vlc --vout x11

or better yet change the output in the preferences of vlc:

Tools -> Preferences -> Video -> Output -> X11 video output

hit save and try it out.

Now to fix it for Totem Movie Player you have to use the

gstreamer-properties

application to change the output.  You can launch that command from alt-f2 or the terminal, or you can instead go to 

System -> Preferences -> Multimedia Systems Selector

then go to the video tab and change the default output plugin to "X Window System"

One way you know you have this problem is, when you fullscreen the video player it crashes immediately.  The BadAlloc error will only show up if you start the video player from the command line, otherwise it is hidden from you.  BadAlloc can happen for a lot of reasons, but someone with a modern video card getting that for a video is completely bogus.  Turning Video4Linux off by changing output to X11(in the player, it's a per player setting unfortunately) does the trick for those people.  Worked for me.

---

