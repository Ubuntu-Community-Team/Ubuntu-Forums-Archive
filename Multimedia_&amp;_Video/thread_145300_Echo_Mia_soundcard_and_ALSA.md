---
title: "Echo Mia soundcard and ALSA"
date: 2006-03-16
forum: Multimedia &amp; Video
---

### Post by SpectralDesign on 2006-03-16
I've been trying to get my Echo Digital Audio Corporation "Mia" card working under Ubuntu 5.10 for almost a week now.

The other day I found a thread in the 5.04 area that was related, and tried everything I found there as well.  I've been all over the place looking for an answer that solves my problem.... Frankly, it's quite irritating now, and when you see the exact trouble I'm having you might agree (or maybe you see I've done something dumb and it's an easy fix, which is even better.) 

For starters, it's a given that the ALSA driver supports the Echo Mia from version 0.8rc2.  This is proven through ALSA documentation, as well as countless 3rd parties whove gotten it working correctly.  From all the sources I've found you can make the proper kernel module by using this command in the source directory:

/usr/src/modules/alsa-driver seems to be the default for the 0.9 version distributed with Breezy Badger. So from this directory one should (apparently) simply type:

*./configure --with-cards=mia;make;make install*

Well, let's start with the output from configure:

[B]checking for kernel version... The file /usr/src/linux/include/linux/version.h does not exist.
Please, install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).[/B]

okay, so a modification, if I the use:

*./configure --with-cards=mia --with-kernel=/usr*

There's still a problem:

[B]...blah...
...blah...
checking for parallel port support... "no"
checking for parallel port module support... "no"
checking for which soundcards to compile driver for... configure: error: Unsupported soundcard mia[/B]

Now, this is iarritating item number one -- Okay, so I try to do this for *all* modules in ALSA, with:

*./configure --with-kernel=/usr;make*

configure exits okay, but now make is having trouble:

[B]...blah...
...blah...
make[3]: Leaving directory `/usr/src/modules/alsa-driver/synth/emux'
make[2]: Leaving directory `/usr/src/modules/alsa-driver/synth'
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make -C /usr SUBDIRS=/usr/src/modules/alsa-driver  modules
make[1]: Entering directory `/usr'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/usr'
make: *** [compile] Error 2[/B]

And irritating item number two....  What gives here?

H E L P !!!!!

I'm pulling the last of my hair out!  The whole point here was to get my wife's recordings for librivox.org sounding better than with her $40.00 headset mic, and we can use the Echo Mia with a real Mic *if* we're running Windows XP, but that feels so --icky--!

Please, Ubuntu Gods, Hear My Call!  
Help me obliterate our Windows install once and for all!
Ohh-Ahh-Ohh-Ahh-Bawl-Bawl-Bawl!

PS - I've tried several other versions of ALSA too, all with basically the same results :cry:

---

### Post by FarEast on 2006-03-27
Hello SpectralDesign;) ,

You probably need to install the kernel headers(linux-headers).
I could compile the module 'snd-mia' on my Breezy System with no problem.  Below is the content of /usr/src .

(Symbolic link) linux -> linux-headers-2.6.12-10-686
(directory) linux-headers-2.6.12-10
(directory) linux-headers-2.6.12-10-686

And it will be better to add an option -with-oss for applications which use OSS APIs.

Good luck!

Edit: mis-spelling :)

---

### Post by SpectralDesign on 2006-03-27
Hi, yes thanks for that!  I thought by installing the linux-source files it would cover what I needed, but the headers were definately needed :)

For anyone following along, this issue is now resolved, thanks to the
#ubuntu irc network and the most helpful 'crimsun'... here, in summary,
are (to the best of my reconstructive abilities) the steps I took to get
ALSA working with my Echo Mia card:

## again, for the record, this is under Ubuntu 5.10, fully patched (a
Debian variant)

export CC=gcc-3.4
sudo apt-get install linux-headers-$(uname -r)
## I had thought installing the 'build-essentials' package was
sufficient, but adding the header files package resolved some issues
too.)

cd alsa-driver-1.0.11rc3
make clean
make mrproper
./configure --with-cards=intel8x0,mia --with-oss=yes
--with-sequencer=yes

make
sudo make install
depmod -e
sudo invoke-rc.d alsa force-unload
sudo modprobe -r snd-seq-device snd-rawmidi snd-mpu401-uart snd-mpu401
sudo modprobe snd-mia

despite getting errors at this point, I decided to reboot, thinking that
an active "nobody" session was using snd-seq-device, and while booting
the Ubuntu splash screen showed:

alsa setting up card 0
alsa setting up card 1
alsa starting

After some tweaking levels and settings with alsamixer, everything seems
to be in proper working order now!

---

### Post by jxn on 2006-03-29
great; glad to see that it's working.  I'm about to try it in dapper.  Why can't echo mia work out of the box, though, instead of having to compile support in for it?

---

### Post by SpectralDesign on 2006-03-29
Good luck!  Let us all know how it went, and if possible the steps you had to take to get it going...

When I was trying to get mine working I spent a week or two looking around for answers with NO luck!  Finally, I got help on the Ubuntu IRC network (as I mentioned already -- thanks again to crimsun.)

So... if you could post what it took you to get it working in Dapper, I'm sure future Ubuntians will be appreciate of some information they can use to guide their installation.

---

### Post by jxn on 2006-03-31
I haven't finished yet, but here's what I'm in the process of doing: (will edit as necessary)

1. used synaptic to install linux-headers and build-essential

---

### Post by jxn on 2006-03-31
I haven't finished yet, but here's what I'm in the process of doing: (will edit as necessary)

1. used synaptic to install linux-source, linux-headers, and build-essential
2. downloaded the alsa 10.11r4 driver from here: [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.11rc4.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.11rc4.tar.bz2")
3. unzipped and ran "./configure --with-cards=intel8x0,mia --with-oss=yes --with-sequencer=yes" from the newly created directory
4. got nasty error, but got around this by installing every linux-kernel related package in synaptic (not sure which one did the job)

after this, I somehow got snd-mia to modprobe using a conflagration of the above instructions and instructions in another thread, but I've still got no sound....

after a reboot, I get the following output from "sudo lsmod |grep mia"
> 
snd_mia                32612  0
snd_rawmidi            27072  1 snd_mia
snd_pcm                97316  2 snd_mia,snd_pcm_oss
snd                    62848  7 snd_mia,snd_rawmidi,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         11336  2 snd_mia,snd_pcm

...so snd-mia is there and all...but I can't seem to unmute it because I get this error when I run "alsamixer"
> alsamixer: function snd_ctl_open failed for default: No such device

please help; thank you!

---

### Post by teopiz on 2008-04-03
Hello boys.
I've a problem with the "make" command for this driver.
I've an Ubuntustudio 7.10 freshly installed, i've a Echo MIA soundcard, i've downloaded latest alsa drivers and installed latest linux headers.
When i try to do these operations (like explained by SpectralDesign): 

"export CC=gcc-3.4
sudo apt-get install linux-headers-$(uname -r)
## I had thought installing the 'build-essentials' package was
sufficient, but adding the header files package resolved some issues
too.)

cd alsa-driver-1.0.11rc3
make clean"

i received this error: "Unable to find Makefile.conf"

In the alsa driver directory there are 2 files: one's Makefile and one's Makefile.conf.in, but no Makefile.conf!!](*,)
How can i make the requested file?
Can you help me??
Thanks a lot.
Bye
Matthew

---

### Post by ThrashJazzAssassin on 2008-04-03
Your card should work out of the box with ubuntustudio 7.10

If not, install the alsa-firmware package.

Good luck.

My old echoaudio darla20 works without compiling anything.

---

