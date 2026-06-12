---
title: "VLC, DVB-T and GPU decoding"
date: 2011-01-18
forum: Multimedia Software
---

### Post by Al Grant on 2011-01-18
Hi All

I have a DVB-T card that I want to use with VLC to watch TV.

At the moment it is horribly slow on 10.10 even though I have a GTX470 card. I think I need to get the VLC to use the GPU.

I am in NZ on Ubuntu 10.10.

I dont know what logs would be helpful so if someone can tell me what to type I will paste!

Cheers

-AL

---

### Post by BicyclerBoy on 2011-01-18
1.  Do you have the latest nvidia driver installed ?

You can do this the easy way by adding this ppa
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

You need to install libvdpau from std *buntu repos.
Check function with 
vdpauinfo

2. VLC from *buntu repos does not support vdpau.
You need to get a version from source or 3rd party ppa. 
IMO for best PQ (no vdpau) enable yadifx2 de-interlace filter & lancros or bicubic scaling for SD & DVD playback.
Vdpau can do the same stuff & better if configured.

3. Other useful stuff
[http://www.ubuntuupdates.org/ppa/medibuntu_non_free](http://www.ubuntuupdates.org/ppa/medibuntu_non_free)

4. seriously consider MythTV/mythbuntu. &/or XBMC frontend.

---

### Post by Al Grant on 2011-01-18
Hey thanks for the reply.I am at work at the moment so I can only ssh in but:

vdpauinfo
command not found

sudo apt-get install vdpau <tab><tab>
has only one option and that is : vdpau-va-driver

Is this what I want?

Cheers

-Al

---

### Post by BicyclerBoy on 2011-01-18
No that is a wrapper for VA-API.

libvdpau1  is in maverick/main...

What about question 1 ?
Can easily find it in /var/log/Xorg.0.log ..

---

### Post by Al Grant on 2011-01-18
I am no expoert but

grep vdpau /var/log/Xorg.0.log 

should have brought something up? It was blank

-Al

---

### Post by Al Grant on 2011-01-18
Also prety sure using nvidia driver 156 cause I am using CUDA for some other apps.

---

### Post by BicyclerBoy on 2011-01-18
You could use CUDA with MatLAB & Octave...but probably not for video decode & presentation.

cat /var/log/Xorg.0.log | grep nvidia

VDPAU & VA-API has nothing to do with CUDA.
VDPAU is an library & API for purevideo in Linux.

I believe that CUDA is included in the later nvidia drivers.

It was a separate installation up to 195 ? as I remember have trouble compiling the examples.

---

### Post by gradinaruvasile on 2011-01-18
Just install the full nvidia driver bundle from the nvidia site and you will have vdpau decoding.That cannot be used by vlc directly, you have to install libva1 and vainfo then go to the preferences, input and codecs and tick the "use gpu acceleration" checkbox. You will gain some 20-30 cpu% s this way.
VDPAU, the native nvidia gpu decoding is used by smplayer/mplayer, xine and others. I use smplayer and it works very well, better than vlc. Libva uses a subset of VDPAU so naturally VDPAU is way better (~5% CPU with 1080p movies).

---

### Post by Al Grant on 2011-01-22
sudo apt-get install libvdpau1 says already installed newest version.

cat /var/log/Xorg.0.log | grep nvidia 

returns nothing?

Cheers

-Al

---

### Post by Al Grant on 2011-01-24
Also I get:

al@al-ubuntu:~$ vainfo
libva: libva version 0.31.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns -1
vaInitialize failed with error code -1 (unknown libva error),exit
al@al-ubuntu:~$

---

### Post by BicyclerBoy on 2011-01-25
Forget VA-API for now..
libva in not required.

I think you do NOT have any nvidia driver installed..

cat /var/log/Xorg.0.log | grep nouveau
maybe just post the whole file as attachment Xorg.0.log.txt

You need 
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

nvidia-260-modaliases
nvidia-260-glx
libvdpau
vdpauinfo

---

### Post by cascade9 on 2011-01-25
> **BicyclerBoy said:**
> You need 
[https://launchpad.net/~nvidia-vdpau/+archive/ppa]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa")


I dont think that Al Grant needs an nVidia PPA. The 260.xx drivers in 10.10 shoudl support the GTX470 and VDPAU just fine. 

Adding nvidia drivers from a PPA is great way to break 'x' if there is ever a kernel update.

---

### Post by BicyclerBoy on 2011-01-25
Okay 10.10 could ship with nvidia driver that work.

nvidia ppa or [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")
Because these are package managed with install scripts I think will have a build dependency on the correct kernel headers.
They use the same install process as the Ubuntu std packages.

I have used a 3rd party ppa for nvidia driver with >3 kernel updates no problems
(granted it is not this ppa)
I have the kernel headers package installed.

So may fail to install but not break with kernel updates.
The nvidia installer method breaks with kernel updates.

---

### Post by cascade9 on 2011-01-25
I always forget that the PPA shouldn't break 'x' with an update. :lolflag: 

I just dont see the point of adding PPAs to get minor revisions to the driver in the repos if the repo driver will work with the card. It just makes things messier for no real gain.

---

### Post by Yellow Pasque on 2011-01-25
VLC does not support VDPAU directly, but it will through VA-API.
Here's what you need:
- VLC and libva from this PPA: [https://launchpad.net/~dtl131/+archive/catalysthacks](https://launchpad.net/~dtl131/+archive/catalysthacks)
- The latest vdpau-video package from here: [http://www.splitted-desktop.com/~gbeauchesne/vdpau-video/pkgs/](http://www.splitted-desktop.com/~gbeauchesne/vdpau-video/pkgs/)

EDIT: make sure you don' have Ubuntu's vdpau-va-video package installed, as this is an old version.

---

### Post by BicyclerBoy on 2011-01-25
The OP does not yet know if:
video driver is installed.
video driver is loaded.  (logs)
if vdpau is possible.  (vpdauinfo)
if tuner card dvb is working.  (dvb scan or VLC)

IMO getting those items ticked off/understood is better than more media player software.

If Ubuntu X team (& nvidia ppa) can not make package dependencies work then there is little hope of anything else working..

---

### Post by cascade9 on 2011-01-25
> **BicyclerBoy said:**
> The OP does not yet know if:
video driver is installed.
video driver is loaded.  (logs)
if vdpau is possible.  (vpdauinfo)
if tuner card dvb is working.  (dvb scan or VLC)

IMO getting those items ticked off/understood is better than more media player software.

Point, but VLC isnt anywhere near as easy as some of the other players to get VDPAU going on (Temüjin is right as far as I know). 

> **BicyclerBoy said:**
> If Ubuntu X team (& nvidia ppa) can not make package dependencies work then there is little hope of anything else working..

Why the PPA? Its not going to help, and is just adding complexity.

---

### Post by Al Grant on 2011-01-25
By the way I had to reinstall the Nvidia driver and now I get:


al@al-ubuntu:~$ vainfo
libva: libva version 0.31.0
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
libva: va_getDriverName() returns 0
libva: Trying to open /usr/lib/dri/nvidia_drv_video.so
libva: va_openDriver() returns 0
vainfo: VA API version: 0.31
vainfo: Driver version: Splitted-Desktop Systems VDPAU backend for VA API - 0.6.3
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
al@al-ubuntu:~$ 


Am I getting any closer?

---

### Post by Al Grant on 2011-01-26
al@al-ubuntu:~$ cat /var/log/Xorg.0.log | grep nouveau
al@al-ubuntu:~$ cat /var/log/Xorg.0.log | grep nvidia
[    26.866] (II) LoadModule: "nvidia"
[    26.866] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    27.090] (II) Module nvidia: vendor="NVIDIA Corporation"
[    28.725] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    28.725] (II) NVIDIA(0):     "nvidia-auto-select"
[    28.756] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
al@al-ubuntu:~$

---

### Post by beew on 2011-01-26
> **gradinaruvasile said:**
> Just install the full nvidia driver bundle from the nvidia site and you will have vdpau decoding.That cannot be used by vlc directly, you have to install libva1 and vainfo then go to the preferences, input and codecs and tick the "use gpu acceleration" checkbox. You will gain some 20-30 cpu% s this way.
VDPAU, the native nvidia gpu decoding is used by smplayer/mplayer, xine and others. I use smplayer and it works very well, better than vlc. Libva uses a subset of VDPAU so naturally VDPAU is way better (~5% CPU with 1080p movies).


I am interested in how you do it. I have installed libva and vainfo and change the settings of vlc as you said but I notice little change in cpu usage in my Maverick box. I know vdpau is enabled because it works dramatically with mplayer and smplayer.

---

### Post by Yellow Pasque on 2011-01-26
> **beew said:**
> I am interested in how you do it. I have installed libva and vainfo and change the settings of vlc as you said but I notice little change in cpu usage in my Maverick box. I know vdpau is enabled because it works dramatically with mplayer and smplayer.
There's an option in VLC for accelerated video output (varies by version). Make sure you have that checked and start vlc from the terminal to see if it's working.

---

### Post by beew on 2011-01-26
I did check the box.

---

### Post by Yellow Pasque on 2011-01-29
> **beew said:**
> I did check the box.
And your terminal output from vlc is where..?

---

