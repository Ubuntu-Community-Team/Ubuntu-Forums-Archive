---
title: "Cinelerra on Gusty"
date: 2007-07-29
forum: Multimedia Production
---

### Post by Red Moose on 2007-07-29
Hi, I have installed Cinelerra on Gusty using [these packages]("http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/").  Is there any way to get it to work in gusty?  When I click on the icon, cinelerra shows up in the system monitor for a few seconds, then is gone.  This happens with a few other programs as well.  Is this a problem with Gusty, or with Cinelerra?  Any help would be greatly appreciated!
I have searched the forums, but they all seem to deal with feisty.

---

### Post by pfeels on 2008-01-18
I'm getting the error...

void MWindow::init_shm():Warning:/proc/sys/kernel/shmma x is 0x2000000, which is too low.
Before running Cinelerra do the following as root:
echo "0x7fffffff" > /proc/sys/kernel/shmmax

Now I found two different fixes on the boards ...

sudo gedit /etc/sysctl.conf

and changed added the lines

kernel.shmmax = 2147483647  (at the very end)

that fix did nothing them I removed that line and add

kernel/shmmax=0×7fffffff

that again did nothing, I also get this when I try closing the program in terminal 

kernel.printk = 4 4 1 7
kernel.maps_protect = 1
error: "Invalid argument" setting key "kernel.shmmax"

any help s always appreciated

---

### Post by pfeels on 2008-01-18
Funny, the error code still pops up but I'm running the program, It's my first time trying it but I do see video, it also gives me errors for quicktime movies but they still run in the viewer ...

---

### Post by fsman on 2008-01-19
use these instead see cvs cinelerra (get packages)

for all x86 (full working on 32 and 64 bits), by Paolo Rampino:
deb [http://repository.akirad.net](http://repository.akirad.net) akirad-gutsy main
Notes:
- Installations from this repository need an authentication key. Add it by typing the following command in your terminal:
wget -q [http://repository.akirad.net/dists/akirad.key](http://repository.akirad.net/dists/akirad.key) -O- | sudo apt-key add -
- Cinelerra package is available in 5 variants:
cinelerra (no opengl) - cinelerra-generic (with opengl) - cinelerra-k8 (with opengl) - cinelerra-k7 (no opengl)
- These packages set shmmax to 0x7fffffff and add non-English language support for Cinelerra.

---

### Post by pfeels on 2008-01-19
Thx fsman

I'm still new to the linux way of doing things but here's what I did ...

System>Administration>Software Sources
    Under Third-Party Software Tab, I clicked on Add, then I input: 
 deb [http://repository.akirad.net](http://repository.akirad.net) akirad-gutsy main

I clicked Add Source and I think I hit the reload or re whatever it asked


Then System>Administration>Synaptic Package Manager
   Scrolled down to Cinelerra I have 5 choices, I picked Cinelerra-k8, right clicked it and hit Mark for Install, then at the top left of page I clicked on APPLY ...

After that I opened TERMINAL (Application> Accessories> Terminal) and input: 
    wget -q [http://repository.akirad.net/dists/akirad.key](http://repository.akirad.net/dists/akirad.key) -O- | sudo apt-key add -


My error messages have gone away except when i try to open a Quicktime Movie, so maybe the software isn't meant for MOV. file extensions ...


MPG work and WMV are changed to RAW, the video runs slow in the Viewer but maybe thats intended ... I need to play around with it further but bottom line is I'm new here and I'm loving this stuff ... Thx again

~Feels~

---

### Post by cotcot on 2008-01-19
Files with .MOV extentions work fine with cinelerra on my box.
If you use a lot of effect or have a slow processor it is normal to see the video played in slow motion in the compositor. That is because the video is rendered while you see it in the compositor.
It helps with OpenGL enabled.

If you do not get it ok with the akirad repos you might consider to compile it yourself. 
[[COLOR="Red"]Here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=666911&page=2") in this thread is a description how to do it.
It is less easy than using repos but it is not a nightmare neither. It takes maybe half an hour.

---

### Post by pfeels on 2008-01-19
I had some trouble with your link because of a space inbetween the 9 and 1

 [http://ubuntuforums.org/showthread.php?t=666911&page=2](http://ubuntuforums.org/showthread.php?t=666911&page=2)

I'll check it out, and thanks ...

---

### Post by cotcot on 2008-01-19
Sorry for that. Seems something wrong with the forum. I tried to edit my post with your error announcement but in the edit there is no space between 9 and 1.

---

### Post by pfeels on 2008-01-19
I did everything I could, it's running but the error codes keep coming up, I went to Cinelerra's bug report forum and did a search, it's bug 452, and even though the error codes come up the program works fine, i did what they suggested ...

Bug 452

whenever I try to load or play a movie, following error messages starts showing
up:

virtual int FileMov::read_frame(VFrame*):
quicktime_read_frame/quicktime_decode_video failed, result:

my "workaround" is to move error window on another virtual screen, so it does
not block my work


Reproducible: Always

Steps to Reproduce:
1. start a new project
2. load video
3. play it

Actual Results:  
a lot of following error messages

virtual int FileMov::read_frame(VFrame*):
quicktime_read_frame/quicktime_decode_video failed, result:

Expected Results:  
no errors, because it works..

---

### Post by pfeels on 2008-01-20
Hey guys, where's the best tutorials for Cinelerra?

---

### Post by cotcot on 2008-01-21
About your error. Have you checked if ./configure is satisfied with all the depencencies ? When ./configure is finished it gives a nice overview about what is ok and what is missing. If you have not compiled cinelerra you could follow the steps in the above compilation procedure up to ./configure to check this. It shiuld look like this (except for ESD that can be disabled):
> Summary of mandatory components:
  libogg                  found
  libvorbis               found
  libvorbisenc            found
  libvorbisfile           found
  libtheora               found
  OpenEXR                 found
  libdv                   found
  libpng                  found
  libjpeg libraries       found
  libjpeg headers         found
  libtiff libraries       found
  libtiff headers         found
  FreeType 2              found
  libx264 libraries       found
  libx264 headers         found
  libuuid libraries       found
  libuuid headers         found
  mjpegtools              found
  libfftw3 libraries      found
  libfftw3 headers        found
  liba52 libraries        found
  liba52 headers          found
  libmp3lame libraries    found
  libmp3lame headers      found
  libsndfile libraries    found
  libsndfile headers      found
  libfaac libraries       found
  libfaac headers         found
  libfaad libraries       found
  libfaad headers         found

Summary of optional components:
  ESD subsystem           found
ESD (Enlightenment Sound Daemon) is enabled
  ALSA subsystem          found
ALSA is enabled
  libraw1394              found
  libiec61883             found
  libavc1394 libraries    found
  libavc1394 headers      found
  librom1394 libraries    found
  librom1394 headers      found
Firewire is enabled
  OpenGL 2.0 libraries    found
Hardware acceleration using OpenGL 2.0 is enabled

Now type
          make


About manuals. I highly recommend to start with the [[COLOR="Red"]cinelerra manual[/COLOR]]("http://cv.cinelerra.org/docs.php"). Other manuals or tutorials mostly are quick guides or tips on using 1 specific feature. If you stick with quick guides and so on you will miss some nice features (keyframe, camera and projector, ...) and then you are better of with apps such as kdenlive.

---

### Post by pfeels on 2008-01-23
Sorry Cotcot
 I had booked marked this thread but I didn't notice there was a second page ...

I ran into a wall with your directions at one point, I'll try a walk through again and find out where I get stuck, thanks for all the help ...

Oh and thanks for pointing me in a direction for learning this stuff ...

---

### Post by pfeels on 2008-01-23
Hmmm, there's a problem ...


Summary of mandatory components:
  libogg                  found
  libvorbis               found
  libvorbisenc            found
  libvorbisfile           found
  libtheora               found
  OpenEXR                 found
  libdv                   found
  libpng                  found
  libjpeg libraries       found
  libjpeg headers         found
  libtiff libraries       found
  libtiff headers         found
  FreeType 2              found
  libx264 libraries       missing
  libx264 headers         missing
  libuuid libraries       found
  libuuid headers         found
  mjpegtools              found
  libfftw3 libraries      found
  libfftw3 headers        found
  liba52 libraries        found
  liba52 headers          found
  libmp3lame libraries    found
  libmp3lame headers      found
  libsndfile libraries    found
  libsndfile headers      found
  libfaac libraries       found
  libfaac headers         found
  libfaad libraries       found
  libfaad headers         found

Summary of optional components:
  ESD subsystem           missing
ESD (Enlightenment Sound Daemon) is disabled
  ALSA subsystem          found
ALSA is enabled
  libraw1394              found
  libiec61883             found
  libavc1394 libraries    found
  libavc1394 headers      found
  librom1394 libraries    found
  librom1394 headers      found
Firewire is enabled
  OpenGL 2.0 libraries    found
Hardware acceleration using OpenGL 2.0 is enabled

WARNING: Mandatory components are missing; compilation may fail!

---

### Post by pfeels on 2008-01-23
I deleted the program and started over following your directions, I'm hung up here ...


./configure
make
sudo make install

I can get over to the hvirtual directory, it should look like this right ...

desktop:~/hvirtual$ 

and next to that I put in ... ./configure (no spaces)

it comes back ...

-desktop:~/hvirtual$ ./configure
bash: ./configure: No such file or directory

any ideas? ... I got it to configure once thats how I got the above stuff.

---

### Post by pfeels on 2008-01-23
I finally got it to configure and it came back the same way, 

Summary of mandatory components:
  libogg                  found
  libvorbis               found
  libvorbisenc            found
  libvorbisfile           found
  libtheora               found
  OpenEXR                 found
  libdv                   found
  libpng                  found
  libjpeg libraries       found
  libjpeg headers         found
  libtiff libraries       found
  libtiff headers         found
  FreeType 2              found
  libx264 libraries       missing
  libx264 headers         missing
  libuuid libraries       found
  libuuid headers         found
  mjpegtools              found
  libfftw3 libraries      found
  libfftw3 headers        found
  liba52 libraries        found
  liba52 headers          found
  libmp3lame libraries    found
  libmp3lame headers      found
  libsndfile libraries    found
  libsndfile headers      found
  libfaac libraries       found
  libfaac headers         found
  libfaad libraries       found
  libfaad headers         found

Summary of optional components:
  ESD subsystem           missing
ESD (Enlightenment Sound Daemon) is disabled
  ALSA subsystem          found
ALSA is enabled
  libraw1394              found
  libiec61883             found
  libavc1394 libraries    found
  libavc1394 headers      found
  librom1394 libraries    found
  librom1394 headers      found
Firewire is enabled
  OpenGL 2.0 libraries    found
Hardware acceleration using OpenGL 2.0 is enabled

WARNING: Mandatory components are missing; compilation may fail!

I got the program from your instructions ... damn, this is confusing

---

