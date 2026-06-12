---
title: "[SOLVED] Problem with Mplayer in Ubuntu"
date: 2008-06-23
forum: Multimedia Software
---

### Post by prabath_fun on 2008-06-23
--------------------------------------------------------------------------------

Hi,
I have got some problem with playing DVD. I have installed mplayer from source code in Ubuntu 8.04 (in wubi) with ./configure, sudo make, sudo make install after package is extracted. Installation went fine witout problem. Then I tried to play an DVD from terminal with
mplayer dvd://3 -dvd-device /dev/hdc
command. It playes, but, I am getting only audio. No video. Worked without any problem in Fedora 8 earlier. But, Now I am using ubuntu, because of huge support and impressed with it.



Also I installed .deb package available in ubuntu packages website. But, while trying to play DVD I am geting the following message.
"Error opening/initializing the selected video_out (-vo)device"

Please update me, what is the wrong I am doing?
Prabath

---

### Post by andrew.46 on 2008-06-24
Hi,

Have a look at:

```
$ mplayer -vo help
```

and this should tell you what video out devices are available to you. On my system for example I have:

```
andrew@ilium~$ mplayer -vo help
MPlayer dev-SVN-rUNKNOWN-4.1.2 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
Available video output drivers:
        xv      X11/Xv
        x11     X11 ( XImage/Shm )
        xover   General X11 driver for overlay capable video output drivers
        gl      X11 (OpenGL)
        gl2     X11 (OpenGL) - multiple textures version
        dga     DGA ( Direct Graphic Access V2.0 )
        sdl     SDL YUV/RGB/BGR renderer (SDL v1.1.7+ only!)
        fbdev   Framebuffer Device
        fbdev2  Framebuffer Device
        svga    SVGAlib
        aa      AAlib
        caca    libcaca
        xvidix  X11 (VIDIX)
        cvidix  console VIDIX
        null    Null video output
        mpegpes Mpeg-PES to DVB card
        yuv4mpeg        yuv4mpeg output for mjpegtools
        png     PNG file
        jpeg    JPEG file
        gif89a  animated GIF output
        tga     Targa output
        pnm     PPM/PGM/PGMYUV file
        md5sum  md5sum of each frame

```

Then try an available video codec in the following fashion:
```

$ mplayer -vo xv etc etc etc
```

You can make your successfull video out device the default by placing it in ~/.mplayer/config in the following manner:

```
vo = xv
```

And hopefully all will be well.

   Andrew

---

### Post by Pjotr123 on 2008-06-24
You probably don't have all the codecs yet. Apply this how-to for 100 % multimedia support:

Step 1:
[http://ubuntutip.googlepages.com/multimediaubuntustep1](http://ubuntutip.googlepages.com/multimediaubuntustep1)

Step 2:
[http://ubuntutip.googlepages.com/multimediaubuntustep2](http://ubuntutip.googlepages.com/multimediaubuntustep2)

That should do the job.  :-)

---

### Post by prabath_fun on 2008-06-24
Thanks. Actually I got it with mplayer .deb package installation. I selected different codec for audio and video and checked. For few codecs mplayer hangs.

Now, I am looking for enabling 5.1 surround with Mplayer. My Mother board got 5.1 support. Help me to enable 5.1.
With Thanks,
Prabath

---

### Post by Pjotr123 on 2008-06-24
See what alsamixergui can do for you:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)
(number 2 )

---

### Post by prabath_fun on 2008-06-25
No improvement. Any other methods?
Prabath

---

### Post by prabath_fun on 2008-12-16
[COLOR="Purple"]Now, I am using VLC player instead of MPlayer. I am getting nice experiance with 5.1 surround enabled through pulse audio driver.[/COLOR]

---

### Post by miros84 on 2008-12-16
Hi. I instaled severals players, but I have some problems with the colors. The green is yellow, and some colors, just changed. I thought I had problems with the codecs. I installed several codesc as divx, avi, ac3, but nothing changed. Only one player seems to be Ok with the movies, but I don´t like it, because I canot put subtitles in bulgarian there. Can you recomend me same good players???

---

### Post by prabath_fun on 2008-12-17
[COLOR="Green"]I have come across only two players, VLC and Mplayer. I like VLC player and faced more problem with MPlayer. So, I recommand VLC player based on my experiance with it.
  Even, In VLC, Iam facing problem that, frames were missing in between few frames while playing with full screen mode. I believe that, it will be solved by proper settings of video codec.[/COLOR]

---

### Post by prabath_fun on 2008-12-18
[COLOR="Sienna"]VLC frame missing problem is solved by disabling visual effects. I came to know that through one of thread in VLC forum.

   To disable visual effects, right click on desktop -> change background -> Visual effects tab and select none.[/COLOR]

---

### Post by miros84 on 2008-12-18
I looked for vlc player in synaptic, but I couldnot find it. How did you install it? Where can I find it? Tell me please how can I put a new post, I mean to open new forum here, because I cannot find this option here.

---

### Post by prabath_fun on 2008-12-18
[COLOR="DarkGreen"]For Ubuntu Intrepid Ibex 8.10, 
Ubuntu Hardy Heron LTS 8.04
Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories, make sure you have a "multiverse" repository activated.

Search for vlc and install it. You should also install vlc-plugin-esd, mozilla-plugin-vlc (and libdvdcss2).

Command line way
You need to check that a "multiverse" mirror is listed in your /etc/apt/sources.list.

% sudo apt-get update
% sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc



To add new post, Go to forum main page, select catagory and you will find new thread button / link. Use it to post new thread.[/COLOR]

---

### Post by miros84 on 2008-12-19
Thank you very much. You are great!

---

