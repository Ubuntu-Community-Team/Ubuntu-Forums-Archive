---
title: "Asus Xonar"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by ulukay on 2007-10-31
hi

anyone got this card working with 7.10?

---

### Post by s0uthpaw on 2008-01-14
Hi,

Yes, I've got my Xonar D2 working with 7.10.

It took a bit of work...

I originally tried using ALSA, but after 3 days of frustration still had nothing.

I uninstalled all the ALSA packages, and installed OSS v4.0

That gives me SPDIF output, but strangely no Analog. Not sure why... It's not an ideal situation, but it's better than the on-board sound.

To get Amarok working with it, I made sure Amarok was using the Xine engine (Settings - Configure Amarok - Engine).

Change the output plugin to OSS, and specify the device as /dev/dsp

I then created a symbolic link for the spdif output to /dev/dsp:

ln -s /dev/oss/cmi87880/pcm1 /dev/dsp

The gnome volume control won't work though - I deleted it from the panel, and installed an applet running 'ossxmix -d0' instead.

Hope this helps.

s0uthpaw

---

### Post by s0uthpaw on 2008-01-16
:)
Finally got the Xonar D2 to work with alsa, which is a better option than oss.

Setup was Ubuntu 7.10 32-bit (fresh install) with Asus Xonar D2 sound card

The following is largely based on the following account: [http://www.alsa-project.org/main/index.php/Matrix:Module-virtuoso](http://www.alsa-project.org/main/index.php/Matrix:Module-virtuoso)
with some amendments:

Get the following packages (you can use synaptic package manager):
build-essential
g++
ja-trans
libncurses5-dev

Download latest alsa-driver, alsa-lib, and alsa-utils packages from [http://www.alsa-project.org](http://www.alsa-project.org)

At the moment, the most current Xonar D2 driver can be found at [http://www.alsa-project.org/main/index.php/User:ClemensLadisch](http://www.alsa-project.org/main/index.php/User:ClemensLadisch)

sudo -s (to run the following as root)

To check that you have sound complied as module:
modinfo soundcore

Make a directory to store the alsa source code in:
cd /usr/src
mkdir alsa
cd alsa
cp /downloads/alsa-* . 
(change parameters as needed to copy your downloaded alsa files to /usr/src/alsa)

Now unzip and install the alsa-driver package (replace xxx with driver date in filename):
bunzip2 alsa-driver-xxx.tar.bz2
tar -xf alsa-driver-xxx.tar
cd alsa-driver-xxx
./configure --with-cards=virtuoso --with-sequencer=yes
make 
make install

chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi

Now unzip and install the alsa-lib package:

cd ..
bunzip2 alsa-lib-xxx.tar.bz2
tar -xf alsa-lib-xxx.tar
cd alsa-lib-xxx
./configure
make
make install

Now unzip and install the alsa-utils package:

cd ..
bunzip2 alsa-utils-xxx.tar.bz2
tar -xf alsa-utils-xxx.tar
cd alsa-utils-xxx
./configure 
make
make install

Now insert the modules into the kernel:
modprobe snd-virtuoso ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss

Run alsamixer to set soundcard volume level

Create a file 'alsa' in the /etc/&#8203;modutils/ directory. Place the following text in the file:

# ALSA portion
       alias char-major-116 snd
       alias snd-card-0 snd-virtuoso
       # module options should go here
       
       # OSS/Free portion
       alias char-major-14 soundcore
       alias sound-slot-0 snd-card-0
       
       # card #1
       alias sound-service-0-0 snd-mixer-oss
       alias sound-service-0-1 snd-seq-oss
       alias sound-service-0-3 snd-pcm-oss
       alias sound-service-0-8 snd-seq-oss
       alias sound-service-0-12 snd-pcm-oss

Run;

update-modules


To test sound, play a wav file:

aplay -vv bugsbunny1.wav (choose your own wav file)

and enjoy the feeling of success!

---

### Post by Scout128 on 2008-01-24
When I run
>  modprobe snd-virtuoso
after installing the driver 
> FATAL: Module snd_virtuoso not found.

is returned.

Does anyone know what is wrong? Thanks in advance

---

### Post by bulletxt on 2008-03-28
when you do "make install", you should do it this way:  "sudo make install". then do the modprobe stuff.

---

### Post by mcfang on 2008-04-08
Can you report if Dolby Digital Live encoding works under Ubuntu? Probably not I guess :(

---

### Post by GG_HTPC on 2008-04-09
I have a Azuntech Meridian card;same chip (CMI8788). I get error messages when I try to do "sudo modprobe snd-oxygen;..."

I read on the Ubuntu forum somewhere that the new version of ALSA (1.0.16) does not work with 7.10 and works only with Hardy (8.04). 

Any ideas??

---

### Post by YogiPaolo on 2008-05-28
I'm running Hardy x64 on a core 2 duo 2.4ghz proc. I took a few stabs at this card last night. I went so far as to do a fresh install and that didn't work. I'm a glutton for punishment from my Gentoo days, so I figure I'll try compiling the latest of the late using the instructions above.

As always, I'm grateful to the ubuntu community and to the distro itself and of course, Linux in general. This does not stop me from getting frustrated, though. 

We know at least one person can get the card running. I'll post my results here.

Using the instructions on this post: [http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

I had no success. I'm going to go over it again to make sure I did nothing wrong.

Well, good luck all.

---

