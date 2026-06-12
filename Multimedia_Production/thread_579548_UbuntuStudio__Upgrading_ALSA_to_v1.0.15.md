---
title: "UbuntuStudio / Upgrading ALSA to v1.0.15"
date: 2007-10-18
forum: Multimedia Production
---

### Post by raintheory on 2007-10-18
I am currently upgrading my Gutsy Install to UbuntuStudio.  I noticed in ALSA's changelog that it now has some support for my audio interface (E-MU 1616m), so I'd like to upgrade ALSA to v1.0.15.  

Unfortunately I do not know where to start, or how to go about this.  

If anyone could help point me in the right direction, I would greatly appreciate it.  

My audio interface and Hi-MD recorders are the only thing keeping me tied to windows, so if I can get the audio interface working I can probably switch to a Virtual Machine to use the Hi-MD recorders (instead of a dual-boot setup like I have now).

Thanks in advance!

---

### Post by Leff on 2007-10-18
Hi, I have just installed ubuntu 7.10 and would like my e-mu 1616pci card to work too...

How can I do that?

---

### Post by raintheory on 2007-10-18
> **Leff said:**
> Hi, I have just installed ubuntu 7.10 and would like my e-mu 1616pci card to work too...

How can I do that?
According to ALSA's changelog, v1.0.15 supports the E-MU 1616 cards (and others): [http://alsa-project.org/main/index.php/Changes_v1.0.14_v1.0.15](http://alsa-project.org/main/index.php/Changes_v1.0.14_v1.0.15)

I just don't know how to go about updating it...

---

### Post by TorchlightJay on 2007-10-18
This is an interesting task. Go to [www.alsa-project.org](www.alsa-project.org) (I think that's the site) and download all the tarballs. Then just untar them and then in konsole/terminal navigate to the directory you untar to.

From there just compile (navigate into the untarred folders, ./configure, make, sudo make install) 

After that is done, do sudo /etc/init.d/alsasound stop (assuming alsasound is running or installed). Then do sudo alsaconf and go through the motions. Then you'll be good.

---

### Post by raintheory on 2007-10-18
Thanks TorchlightJay,
 
This will be my first time compiling anything, never done it before...  

Do I need to download/install anything first in order to be able to compile, or are the compile utilities all preinstalled in Gutsy?

I'll give this a whirl tomorrow.

---

### Post by raintheory on 2007-10-19
Update:

Here's what I've done so far today (stuck at the moment)

Installed build-essentail & linux-headers:
```
sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
```

Downloaded tarballs from ALSA & followed instructions for E-MU 1616m as described here: [http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga)

As follows...

Make a directory to store the alsa source code in:
```
cd /usr/src
mkdir alsa
cd alsa
cp /downloads/alsa-* .
```
(where "/downloads" is the folder where tarballs were originally downloaded)

Unzip and install the alsa-driver package:
```
bunzip2 alsa-driver-1.0.15.tar.bz2
tar -xf alsa-driver-1.0.15.tar
cd alsa-driver-1.0.15
./configure --with-cards=emu10k1 --with-sequencer=yes ; make ; make install
```
...Worked fine.

Set permissions for the devices:
```
chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi
```
(/dev/midi complained here, directory doesn't exist)

Unzip and install the alsa-lib package:
```
cd ..
bunzip2 alsa-lib-1.0.15.tar.bz2
tar -xf alsa-lib-1.0.15.tar
cd alsa-lib-1.0.15
./configure ; make ; make install
```
Worked fine...

Unzip and install the alsa-utils package:
```
cd ..
bunzip2 alsa-utils-1.0.15.tar.bz2
tar -xf alsa-utils-1.0.15.tar
cd alsa-utils-1.0.15
./configure ; make ; make install
```
Does NOT complete...   

"configure: error: this package requires a curses library"
"make: *** No targets specified and no makefile found. Stop"
"make: *** No rule to make target `install'. Stop"

There are plenty more steps to install this...   but I am stuck here.  Any idea what package(s) I need, or what I can do?

---

### Post by TorchlightJay on 2007-10-19
install the curses package. When you see that error message, it means that there is something missing before configure can make the "makefile". Basically, the ./configure portion checks to see that you have all the dependencies and tools to compile the program. So download curses from synaptic and the corresponding dev files.

---

### Post by raintheory on 2007-10-19
alright, i've installed *libncurses5-dev* and it seems to be going along now...

---

### Post by raintheory on 2007-10-19
Well, at the next step:

Insert the modules into the kernel:
```
modprobe snd-emu10k1 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss
```

This happens:

```
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.22-14-rt/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.22-14-rt/kernel/sound/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_emu10k1 (/lib/modules/2.6.22-14-rt/kernel/sound/acore/snd-emu10k1.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

Stuck again!

dmesg shows a bunch of errors about "unknown symbol" and "disagrees about version of symbol"


Thanks torch...  I really appreciate the help!  :)

---

### Post by raintheory on 2007-10-19
I'm pointing now to this thread: [http://ubuntuforums.org/showthread.php?p=3563848](http://ubuntuforums.org/showthread.php?p=3563848)

seems to be the same issues..

---

### Post by TorchlightJay on 2007-10-19
You can also try depmod -a. That can work.

---

### Post by raintheory on 2007-10-19
I had to move some files from /lib/modules/2.6.22-14-rt/kernel/sound/pci/hda/ to /lib/modules/2.6.22-14-rt/ubuntu/media/

and 

put the modules/* in alsa's compile directory into /lib/modules/2.6.22-14-rt/kernel/sound

then depmod -a 

seems to have worked...   I followed the rest of the instructions and rebooted with the card in and got an error about the firmware .   

quite a project here!  wondering if ALSA v1.0.15 will be implemented in any kernel updates for ubuntustudio or just plain old gutsy...   or will it not be until the next official release?

---

### Post by TorchlightJay on 2007-10-20
I don't think alsa-1.0.15 is on gutsy. I have Gutsy and see no sign of it. I have installed ALSA a few times on my system from source. Did you do the alsaconf portion? Try doing it again, that should do the trick. Also, what kind of sound card/chipset do you hav?

---

### Post by raintheory on 2007-10-20
I'm already using UbuntuStudio 7.10..  I actually started with a plain old Gutsy install and upgraded it to UbuntuStudio via the repos..  

I was just wondering if there would be a chance that 1.0.15 would be implemented in any kernel updates for Gutsy/UbuntuStudio, or if it would be held off until the next major release..

My audio interface is an [E-MU 1616m]("http://www.emu.com/products/product.asp?category=505&subcategory=491&product=13552").  It's a PCMCIA card with a breakout box.  I'm actually trying to test it out on a desktop computer via a PCI>PCMCIA adapter.  I want to see if I can at least get it working on that before I bother installing UbuntuStudio 7.10 & going through the ALSA updates on my laptop, whick I normally use for music production.

I reinstalled Gutsy/UbuntuStudio 7.10 on the desktop so I can start over from the beginning and see if I can get it working this time.

---

### Post by TorchlightJay on 2007-10-21
I see,

well as far as 7.10 is concerned, to date, there is no alsa 1.0.15 out in those repositories. Not to say that there will never be on 7.10 but I wouldn't hold your breath. You may be able to find some deb files of alsa online somewhere. Since ubuntu is built on a deb database.

---

### Post by gladstone on 2007-10-22
Here's my attempt with an EMU-1616m (PCMCIA):

```

cd ~\Downloads
mkdir alsa

Download all Alsa releases from: http://www.alsa-project.org/main/index.php/Download
noting that plugins is: ftp://ftp.alsa-project.org/pub/plugins/alsa-plugins-1.0.15.tar.bz2

cd ~\Downloads\alsa

bunzip2 alsa-driver-1.0.15.tar.bz2
tar -xf alsa-driver-1.0.15.tar
cd alsa-driver-1.0.15
./configure --with-cards=emu10k1 --with-sequencer=yes ; make ; make install

Compiled fine, but gave me this: install: "cannot create regular file `/usr/include/sound': Permission denied"

So tried sudo ./configure --with-cards=emu10k1 --with-sequencer=yes ; make ; make install. Didn't make any difference, so checked in synaptic just to make sure it installed, could only find 1.0.14, but carried on anyway

sudo chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi
chmod: cannot access `/dev/midi': No such file or directory

cd ..
bunzip2 alsa-utils-1.0.15.tar.bz2
tar -xf alsa-utils-1.0.15.tar
cd alsa-utils-1.0.15
sudo ./configure ; make ; make install

configure: error: Sufficiently new version of libasound not found.

sudo apt-get install libasound2-dev
sudo ./configure ; make ; make install
configure: error: this packages requires a curses library

sudo apt-get install libncurses5-dev
sudo ./configure ; make ; make install

alsactl.c:125: fatal error: opening dependency file .deps/alsactl.Tpo: Permission denied
compilation terminated.
make[1]: *** [alsactl.o] Error 1
make[1]: Leaving directory `/home/tom/Downloads/alsa/alsa-utils-1.0.15/alsactl'
make: *** [install-recursive] Error 1
```

Then I'm stuck after that. I don't think even the driver has installed yet, but I don't want to wait until April before this is included in Gutsy!

---

### Post by gladstone on 2007-10-22
Started again and deleted all the extracted source files.

**sudo /etc/init.d/alsa-utils stop**

Apparently, this command is **important** for a good install. It seems to have helped me with the permission error I was having (I suppose the file was in use before this)

```

tar -xf alsa-driver-1.0.15.tar
cd alsa-driver-1.0.15
sudo ./configure --with-cards=emu10k1 --with-sequencer=yes
sudo make
sudo make install

This time no permission error occurred! Also separating the make commands seems to have worked better
 for me (NB, dont you tie commands together with "&" rather than ";" ?)

(Files were already .tar from previous .bz2 extraction)

cd ..
tar -xf alsa-lib-1.0.15.tar
cd alsa-lib-1.0.15
sudo ./configure
sudo make
sudo make install

cd ..
tar -xf alsa-utils-1.0.15.tar
cd alsa-utils-1.0.15
sudo ./configure
sudo make
sudo make install

sudo modprobe snd-emu10k1 ; modprobe snd-pcm-oss ; modprobe snd-mixer-oss ; modprobe snd-seq-oss

Reboot and check if Alsa has upgraded using:

cat /proc/asound/version
```

This time I completed the compiling, but when I issue the last command, it gives me an error and when I try to un-mute the mixer, it says "alsamixer: function snd_ctl_open failed for default: No such device" So still no luck yet. I also checked in synaptic and its reporting 1.0.14 still

I have inserted the 1616m and it doesn't crash ubuntu!! First step forward at least! I checked in Device Manager and its being identified as: "SB0400 Audigy2 Value" under my cardbus controller

---

### Post by TorchlightJay on 2007-10-22
doesn't look like you did alsaconf

after you stop alsa-utils, before alsa is going to work, you need to do "sudo alsaconf" and go through the motions there. Then try to restart alsa-utils, you may have a new option out there. "sudo /etc/init.d/alsasound restart" as well. Sometimes a reboot of the computer might work just because it restarts all services but not always.  alsaconf is very important though in this whole process. also, make sure you device is plugged in while you are doing this.

---

### Post by gladstone on 2007-10-23
Okay, when I run sudo /etc/init.d/alsa-utils stop now, it gives me this error:

>  * Shutting down ALSA...                                                         * warning: 'alsactl store' failed with error message 'alsactl: save_state:1251: No soundcards found...'...                                              [fail] 


and when I run sudo alsaconf, it gives:

> Running update-modules...
Setting default volumes...
amixer: Mixer attach default error: No such device


Also when I reboot with the card left in, boot hangs with this error message:

> modprobe: FATAL: error running install command for snd_emu10K1

Oh dear...

---

### Post by raintheory on 2007-10-23
gladstone, do you have the 1616's microdock attached and powered on while rebooting?

not sure if it would make a difference, but worth a shot.

also are you using the PCMCIA card or the PCI version of the 1616?

---

### Post by gladstone on 2007-10-23
Raintheory, tried it with the dock powered on and it made no difference and I have the PCMCIA version (for a laptop).

BTW, I'm h2oz7v from the production forums. Have you had any success with this yet?

---

### Post by AnBylsoma on 2007-11-04
In case you have problems compiling ALSA yourself: the 1616m works flawlessly under Gutsy with the 1.0.15rc3 drivers included in the linux-backports-modules package. To make it work, just install the package:

```

sudo aptitude install linux-backports-modules

```

Unfortunately, this does not install the firmware required by the 1616m, so you'll still need to compile and install that part:

```

wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.15.tar.bz2
tar -xvjf alsa-firmware-1.0.15.tar.bz2
cd alsa-firmware-1.0.15/
./configure
make
sudo make install

```

(Or do it the Ubuntu way, and use dh_make to create an alsa-firmware_1.0.15-1_i386.deb package)

That's it!

> **raintheory said:**
> I am currently upgrading my Gutsy Install to UbuntuStudio.  I noticed in ALSA's changelog that it now has some support for my audio interface (E-MU 1616m), so I'd like to upgrade ALSA to v1.0.15.  

Unfortunately I do not know where to start, or how to go about this.  

If anyone could help point me in the right direction, I would greatly appreciate it.  

My audio interface and Hi-MD recorders are the only thing keeping me tied to windows, so if I can get the audio interface working I can probably switch to a Virtual Machine to use the Hi-MD recorders (instead of a dual-boot setup like I have now).

Thanks in advance!

---

### Post by gladstone on 2007-11-04
AnBylsoma: I followed your steps and seem to have the new drivers installed correctly!

I have an onboard soundcard in my laptop aswell as the 1616m (PCMCIA). After doing the above, the default soundcard was still the onboard one.

I think I've managed to change the default soundcard by doing:

```
 cat /proc/asound/modules
 0 snd_intel8x0 
1 snd_emu10k1

```

and then appending /etc/modprobe.d/alsa-base with:

```

options snd_emu10k1 index=0
options snd_intel8x0 index=1

```

Rebooted and checked cat /proc/asound/modules:

```

0 snd_emu10k1
 1 snd_intel8x0 

```

Now when I try to play a music file, there is no sound at all! I'm using Xubuntu and have set xfce4-mixer to #0: E-mu 1010 Notebook [MAEM8950] and raised all the volume sliders, but still nothing!

---

### Post by mightysween on 2007-11-20
gladstone,  I had a similar wasn't able to use that method.

Instead, I blacklisted my onboard soundcard in /etc/modprobe.d/alsa-base-blacklist by adding this code to the end of the file:

blacklist snd_intel8x0
blacklist snd_ac97_codec
blacklist snd_ac97_bus

My onboard showed up as both a Cirrus and an Intel ICH...but at any rate it is gone now and the E-mu 1010 boots as the primary sound card.

BUT, I have no sound coming out, either.  :(


AnyBylosoma, by "works flawlessly" do you mean that you have the cardbus and the audio dock working?   If so, how did you get software in Linux to initialize the dock?   Mine is just frozen with the same random lights that come on in Windows before Patchmix is started.  That seems to be the final step for me to make this work.

Another great thing I noticed is that the result of aplay -l  which shows 8 active capture (input) channels being detected.  Here's what it looks like:  

---
card 0: EMU1010 [E-mu 1010 Notebook [MAEM8950]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
---

That MUST mean that the driver is properly functioning.   Though, I would expect there to be more than 8...

So, lets work on getting the dock recognized and we'll be multitracking in  no time. :)

Thanks to everyone who is working on this.   We are closer than ever to getting it running.

---

### Post by mightysween on 2007-11-20
For the record, here is the error I receive when I try to run a test sound through System/Preferences/Sound:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Internal GStreamer error: state change failed. 

Anyone have a clue on this one?

---

### Post by mightysween on 2007-11-21
Uh...what is this?

[http://disk.ersca.com/pub/Linux/linux-2.6.22.5/sound/pci/emu10k1/](http://disk.ersca.com/pub/Linux/linux-2.6.22.5/sound/pci/emu10k1/)

Sure looks like code to control the audio dock when connected to the cardbus.

If I knew where to begin, I would. :)

---

### Post by gladstone on 2007-12-02
Has anyone managed to get any further with this??

---

### Post by mightysween on 2007-12-02
Not really, gladstone...my E-MU 1616 now is recognized and properly loaded, and I can see all the inputs and outputs in alsamixer. 

However, there is no known way to route those inputs/outputs to anything useful.   I can't get Jack working even though it recognizes the hardware it only shows 2 inputs and 2 outputs.

So right now it would appear that we're stuck waiting  for a "Patchmix" alternative to come along.

-J

---

### Post by cbreeze34 on 2007-12-04
It looks like the driver presents the i/o on different subdevices, i.e. hw:0,0 through hw:0,7 (or something like that).  One thing to try would be to create an .asoundrc to aggregate all the i/o together.  It's already recognizing the hardware, so I would think Jack would see all the i/o if it was joined together in a virtual device.  This is how I got Jack to see all 16 ins simultaneously on my Echo Layla3G.  There's a useful page on creating an .asoundrc here:

[http://alsa-project.org/main/index.php/Asoundrc]("http://alsa-project.org/main/index.php/Asoundrc")

i'd recommend reading the whole document, it's good stuff to know, but especially the section on "virtual multi-channel devices".

A friend of mine has a 1212m I'm going to try to get running under UbuntuStudio for him... If successful I'll post a "how I did it" here.

---

### Post by mightysween on 2007-12-04
cbreeze, I think you are exactly right.   I believe that hw:0,2 represents 8 channels of inputs on the 1616, but I'm not seeing them in Jack.

I'm going to tinker with .asoundrc and see what happens.

---

### Post by mightysween on 2007-12-04
HOLY CRAP!  IT...FINALLY....WORKS!   :guitar:

I just recorded a test with 6 analog and 8 ADAT inputs running SIMULTANEOUSLY in Ardour.  I can hardly contain my excitement at seeing this work after months and months of trying.

I didn't actually end up editing asoundrc.   I reconfigured Jack working on the assumption that hw:0,2 was indeed the input (capture) ports.  That did turn out to be the case.

So, in Jack I set the input as hw:0,2 and the output as hw:0,0.  I left the "input channels" set at 0, yet it found 16.   I only seem to have two playback channels (left and right) at this point, but that is OK.  That's all I really need right now.

In alsamixer, I assigned each of the "DSP" capture channels numbered 0 to 5 to an analog dock input, and DSP 6 through 13 to an ADAT input.   You could also do this in the converse through the playback mixer...though it is much more confusing.   Man, it's confusing enough as it is!!

It would be nice to write a customized mixer GUI for the Emu system...maybe that is a project I can tackle.

Now before anyone gets too excited, I am having serious "Xrun" issues in Jack, I'm experiencing pretty high latency, and there is some snap/crackle/pop on playback (maybe not in the recording judging by the waveforms).

I might bring the laptop with me to a show tonight and record some real-world test audio and try to put this thing through its paces.

I will update my progress here.

---

### Post by gladstone on 2007-12-05
Great news!!

After reading this, I went and installed Jack Control (never used all this stuff before, it just gets more and more confusing!) and set the output to hw:0,0 and input to hw:0,2.

Started the Jack server and fired up Mplayer and set it to Jack output (also tried alsa) but still no sound :(

---

### Post by mightysween on 2007-12-06
Yes, it is confusing for sure.  That is really the major stumbling block with Linux in general, IMHO.  

Yes, I have this system working after hundreds of hours of trying.   But no, it isn't working enough to record professionally as I do.   I would love to not have to rely on microsoft's expensive and bloated products.  

But you know what...when I boot into my Windows XP partition the computer and audio hardware are up-and-running in about 45 seconds.   Other than putting a CD in the drive and installing it, I did NOTHING else to set it up and I have never had so much as a glitch in 2 years and hundreds of hours of recording.

I doubt Linux will ever get to this point.

That being said, the "geek" in me still thrives on the challenge of Linux.  So I'll continue to try to figure out how to make this work well.   And if it does end up being a solid platform, all the better.   

But, I digress...

I did try to record 10 tracks live with it Tuesday night -- no go.  Too much latency and too many Xruns in Jack.   I'll play around with it and try again.   If I figure something out I'll post my results here.

---

### Post by gladstone on 2007-12-06
I know exactly what you mean and it sounds like we have a very similar setup (Laptop, EMU1616m, Dual booting Linux and XP). I made the switch to Ubuntu a few months ago and while I've learnt loads, it's still very very daunting. I can't wait for the time when I know my way around linux as well as I know Windows!

Could you explain the steps for me to *just* have stereo playback from the 1616? It's funny how my shoddy onboard sound is still dwarfing my £xxx hundred pound soundcard! At least it works! but for now if I can get some output from my 1616 I'd be happy (recording is for another day :P)

---

### Post by sd82 on 2007-12-18
gladstone, I tried it this way, but when I tried to do ./configure I get this error message:

sd@morgenthau:~/alsa-firmware-1.0.15$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
sd@morgenthau:~/alsa-firmware-1.0.15$       
 

what is this all about?!

sd

> **AnBylsoma said:**
> In case you have problems compiling ALSA yourself: the 1616m works flawlessly under Gutsy with the 1.0.15rc3 drivers included in the linux-backports-modules package. To make it work, just install the package:

```

sudo aptitude install linux-backports-modules

```

Unfortunately, this does not install the firmware required by the 1616m, so you'll still need to compile and install that part:

```

wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.15.tar.bz2
tar -xvjf alsa-firmware-1.0.15.tar.bz2
cd alsa-firmware-1.0.15/
./configure
make
sudo make install

```

(Or do it the Ubuntu way, and use dh_make to create an alsa-firmware_1.0.15-1_i386.deb package)

That's it!

---

### Post by sd82 on 2007-12-18
Ok, now the driver works (I had to install some packages, I found in another forum)

...but I don't hear anything!

(Jack connections are up)

---

### Post by gladstone on 2007-12-19
sd82: Yeah, it looks like you probably had to install the build-essential package before it would compile, good to hear you got the drivers working!

But that's as far as I can help unfortunately, I'm in the same position as you (no sound) and it looks like most people are the same, although from mightysween's post, it looks like there could be some hope yet.

Hopefully (s)he'll get back to us when it's figured out!

---

### Post by gladstone on 2008-04-28
To anyone who follows this thread, I've managed to get my 1616m working!!

Upgrade to Alsa 1.0.16 and follow the steps from here:

[http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1-fpga)

I installed the:

```
alsa-driver
alsa-lib
alsa-firmware
```

in that order.

Woooooo!

---

