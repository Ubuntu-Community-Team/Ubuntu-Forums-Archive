---
title: "HOWTO: Make speakers/headphones work on ICH7 rev.2 (Fujitsu T4210)"
date: 2006-11-23
forum: Multimedia &amp; Video
---

### Post by bombadier337 on 2006-11-23
Wow, it took me 3 and half days to work through this but I finally got it.  A little background...

On a Fujitsu T4210(my laptop, but others have this problem as well) and a default Edgy installation, sound does not work on the speakers, and only comes out of the headphone jack.  This is related to the alsa version that ships with Edgy (1.0.12rc3).  I found this issue in several forums, and several said to try compiling the 1.0.13 alsa drivers.  I compiled everything and installed it, and it said "no soundcard found" on everything.  Alsa didn't see my card at all.  I thought I had done something wrong (I've only been an Ubuntu user for 2 months), so I fought with it for a long time, eventually reformatted and tried again.  Same thing.  I then tried compiling older drivers and they saw my soundcard.  
I knew I wasn't compiling it wrong so I looked through the alsa bugtracker and found that the problem had been fixed about a week ago in Mercurial.  This is the first thing I've written like this, but I hope this will help someone who's suffering as much as I have been.  On to the how-to...

1.  Install necessary build tools
sudo apt-get install build-essential linux-headers-generic libncurses5-dev automake autoconf mercurial

2.  Go to [www.alsa-project.org](www.alsa-project.org) and download the 1.0.13 version of the library and utilities to your home directory and untar them.

3.  Download the repositories for the mercurial builds of alsa-driver and alsa-kernel.
 
hg clone [http://hg-mirror.alsa-project.org/alsa-driver](http://hg-mirror.alsa-project.org/alsa-driver) alsa-driver
hg clone [http://hg-mirror.alsa-project.org/alsa-kernel](http://hg-mirror.alsa-project.org/alsa-kernel) alsa-kernel

4. Go into the alsa-driver in your home directory and run hgcompile.

cd alsa-driver
sudo ./hgcompile

This will build the newest version of the alsa-driver.  Now install it using:

sudo make install

6. Change directories to the untarred library directory.  In that directory run

./configure
make
sudo make install

to install the 1.0.13 release version of the alsa driver.

7. Change directories to the untarred utilities directory, and in that directory run

./configure
make
sudo make install

8.  Configure alsa

sudo alsaconf

Select your soundcard (in my case it was the first one) and hit the default option on everything else.

9.  Load the new alsa module into the kernel.

sudo /etc/init.d/alsasound reload

10.  At this point you should receive messages about a soundcard being removed, as well as messages about a new soundcard being installed.  At this point, I restarted, to hear the wonderful Ubuntu logoff noise for the first time out of my speakers.

Upon reboot, there should be no problems, and audio should continue to work.

If I typed anything wrong I apoligize, and if you correct me I'll gladly change this.  I truly hope this will help somebody, this took me so long to get to work.

Peace.

---

### Post by rax_m on 2006-11-25
Hi, 

Glad you´ve got your sounds working... 
I´ve been trying to follow your guide, and it was going well for a while..

First issue: I had to run
¨hg clone [http://hg-mirror.alsa-project.org/alsa-kernel](http://hg-mirror.alsa-project.org/alsa-kernel) alsa-kernel¨ twice before it actually downloaded these for some reason :/
However i´m guessing since it worked the second time, it shouldn´t be a problem. 

Second issue: 
When I try to ¨make¨ the utilities packages I get the following error:
...
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.12... found.
checking for snd_ctl_open in -lasound... yes
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library

Which curses library do i install?

I´ve got the same hda-intel ICH7 (rev2) sound card, but it´s on a Toshiba P100-429. 

Any help would be great.. 

PS I´m not a total noob, but I probably don´t understand the what some of these libraries do :D

Thanks 
Rax

---

### Post by diogodpc on 2006-11-25
Hi rax,

I ran into the same message. 
"sudo apt-get install libncurses5-dev" did the trick for me.

Thanks bombadier337 everything worked great! (I've an Asus F3JC)

cheers

---

### Post by bombadier337 on 2006-11-25
Oops, I put the wrong curses library in the guide, its fixed now.  Thanks for pointing that out!

---

### Post by GStubbs43 on 2006-11-25
Hi all!

When I do ```
sudo ./hgcompile
``` I get:
```
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

```

Any ideas?

---

### Post by bombadier337 on 2006-11-25
run

sudo apt-get install linux-headers-generic

if your running a standard edgy install
if for some reason that still doesn't work, try running this

sudo apt-get install linux-headers-386

That oughtta fix it.

Peace.

---

### Post by GStubbs43 on 2006-11-26
Thanks Bombadier, that worked great! I now only have sound coming out of what I *want* it to! Thanks!

---

### Post by rax_m on 2006-11-26
Hi

Thanks for the tip .. I managed to install the libcurses now.. 

however when I then run the reload command i get the following:

```

>>> /etc$ sudo /etc/init.d/alsasound reload
Shutting down sound driver: /usr/sbin/alsactl: save_state:1254: No soundcards found...
ERROR: Module snd_timer is in use
ERROR: Module snd is in use by snd_timer
done
ALSA driver is already running.

```

Any ideas?

I may have removed some essential lines from some of my module files in the past.. unfortunately i can´t remember what they were (oops.. stupid i know, but this was a few weeks ago)

Thanks again
Rax

---

### Post by iorbell on 2006-11-26
Just wanted to say thanks for this guide - it successfully overcame the audio problems I was having with Edgy and a new Intel HD mobo - and worked exactly as indicated above. The community support is a great example of why I choose Ubuntu over any other Linux distro...:)

---

### Post by bombadier337 on 2006-11-26
> **rax_m said:**
> Hi

Thanks for the tip .. I managed to install the libcurses now.. 

however when I then run the reload command i get the following:

```

>>> /etc$ sudo /etc/init.d/alsasound reload
Shutting down sound driver: /usr/sbin/alsactl: save_state:1254: No soundcards found...
ERROR: Module snd_timer is in use
ERROR: Module snd is in use by snd_timer
done
ALSA driver is already running.

```

Any ideas?

I may have removed some essential lines from some of my module files in the past.. unfortunately i can´t remember what they were (oops.. stupid i know, but this was a few weeks ago)

Thanks again
Rax

I'm not too sure about that one, but if you reboot it should reload all the modules and then pick up the new snd-hda-intel module.  You can check the version of the alsa by running

$ cat /proc/asound/version

If it says 1.0.13 and shows the date you compiled the modules, then you do have the new modules in there.  If sound still doesn't work after rebooting, all I can think of is making sure the library is installed correctly.

---

### Post by rax_m on 2006-11-26
Ok... I tried re-installing everything again.. 

Strangely when I run alsaconf it say&#347; it&#347; version 1.0.13
but cat /proc/asound/version says 1.0.11 

And I get the following output once it;s done:
```

:/etc/init.d$ ./alsasound restart
Shutting down sound driver: /usr/sbin/alsactl: save_state:1254: No soundcards found...
ERROR: Module snd_timer is in use
ERROR: Module snd is in use by snd_timer
done
ALSA driver is already running.

```

Thanks for the help.. i guess i should post this as another thread and see what happens.. 

Cheers
Rax

---

### Post by bombadier337 on 2006-11-26
Are you running in dapper or edgy?  Basically, you're not getting the new module loaded in.  If you were running the 1.0.13 module it would say that in the asound version.  It did install some of the 1.0.13 stuff though, as the alsaconf script is 1.0.13.  Does alsamixer -h show 1.0.13 too?

Not trying to be a jerk or anything here, but you did run all the make installs with sudo right?

---

### Post by rax_m on 2006-11-26
> **bombadier337 said:**
> Are you running in dapper or edgy?  Basically, you're not getting the new module loaded in.  If you were running the 1.0.13 module it would say that in the asound version.  It did install some of the 1.0.13 stuff though, as the alsaconf script is 1.0.13.  Does alsamixer -h show 1.0.13 too?

Not trying to be a jerk or anything here, but you did run all the make installs with sudo right?


No worries... all help is appreciated :) 


alsamixer reports it as 1.0.13 .. 

I'm pretty sure that i did install everything as root (using sudo) .. 

One thing that's bugging me.. is that trying to run "sudo modprobe snd-hda-intel" just hangs there.. nothing happens
This never used to be the case before

Also lsmod gives the following:
```

laptop:~$ lsmod | grep snd
snd_timer              27529  1 
snd                    66924  1 snd_timer
soundcore              11232  1 snd
snd_page_alloc         12040  0 

```

Don;t know if I've broken my sound modules somehow.. 

Cheers

---

### Post by bombadier337 on 2006-11-26
It sounds like the modules did not compile correctly.

If you're running Dapper (?) you may not have the correct kernel headers installed in usr/src (Dapper doesn't have the generic kernel they switched to with edgy, so you may have the k7 kernel or something).  Run a uname -r and make sure you have the right kernel headers installed for your kernel.  Also run

modinfo snd-hda-intel

and verify that /lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-intel.ko exists.  When you run 

sudo etc/init.d/alsasound start

it should load a lot of modules in related to alsa, and it should alsa load the snd-hda-intel module.  This is my output.

$ lsmod | grep snd
snd_hda_intel          23320  1 
snd_hda_codec         212736  1 snd_hda_intel
snd_pcm_oss            56320  0 
snd_mixer_oss          20224  1 snd_pcm_oss
snd_pcm                93572  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26628  1 snd_pcm
snd                    70288  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         12168  2 snd_hda_intel,snd_pcm

---

### Post by rax_m on 2006-11-26
Sorry .. forgot to tell you I'm using Edgy

Before I started trying to actually get my sound working, my lsmod used to show me something very similar to yours

Also, the sound card used to be detected correctly (but sound still didn't work).. 
I then tried the "Comprehensive Sound problems guide"... unfortunately that seemed to cause some problems where X wouldn't load

I found that commenting out various sound related settings in my modules, modprobe.d/sound (can't really remember which files :| 
fixed my X windows, but sound seems to have come out worse.

---

### Post by bombadier337 on 2006-11-26
Can you run 

$ modinfo snd-hda-intel

without errors?

---

### Post by rax_m on 2006-11-26
Now let me actually answer some of the questions you did ask ;)

```

>> uname -r 
2.6.17-10-generic

```

```

$ modinfo snd-hda-intel
filename:       /lib/modules/2.6.17-10-generic/updates/alsa/pci/hda/snd-hda-intel.ko
license:        GPL
description:    Intel HDA driver
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        snd-pcm,snd-page-alloc,snd,snd-hda-codec,snd
alias:          pci:v00008086d00002668sv*sd*bc*sc*i*
alias:          pci:v00008086d000027D8sv*sd*bc*sc*i*
alias:          pci:v00008086d0000269Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias:          pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004383sv*sd*bc*sc*i*
alias:          pci:v00001106d00003288sv*sd*bc*sc*i*
alias:          pci:v00001039d00007502sv*sd*bc*sc*i*
alias:          pci:v000010B9d00005461sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Csv*sd*bc*sc*i*
alias:          pci:v000010DEd00000371sv*sd*bc*sc*i*
srcversion:     CFC483BC3D9CEEF6D205B9A
parm:           enable:bool
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (int)
parm:           position_fix:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size). (int)
parm:           model:Use the given board model. (charp)
parm:           id:ID string for Intel HD audio interface. (charp)
parm:           index:Index value for Intel HD audio interface. (int)

```
I checked that the file does exist!

Whoops... could the following be the issue:
```

$ sudo etc/init.d/alsasound start
sudo: etc/init.d/alsasound: command not found

```

---

### Post by rax_m on 2006-11-26
Sorry.. I'm being an idiot!
I did a typo in the previous post 

```

$ sudo /etc/init.d/alsasound start
ALSA driver is already running.

```

---

### Post by rax_m on 2006-11-26
I think the main issue is that /proc/asound/cards I used to have a subdirectory called card0 which had my soundcard in there. 
I'm not sure how that disappeared, or how to get it back there :/

---

### Post by bombadier337 on 2006-11-26
the /proc isn't like a normal directory on the hard drive, it is created in memory by the running processes.  If the module was loaded and was working, it would've created this folder and you would be able to see it in /proc/asound/cards.  However, when you did lsmod | grep snd, snd-hda-intel is not listed, so it is not loading the module.  (Remember how you said modprobe snd-hda-intel didn't work?).
  
     I still think it's not compiled correctly, are there any errors when you run make on the drivers?  Try reloading the repositories using the hg commands, and make sure it copies everything.  I think what might have happened is it partially compiled some of the alsa-driver when you ran make, but ran into an error and never finished.  When you ran make install, it overwrote some of the files pertaining to the driver, but not others, like the actual snd-hda-intel module.  That might explain why /proc/asound/version show 1.0.11, but nothing works or loads.

---

### Post by rax_m on 2006-11-26
Ok.. that makes sense now.. 


I've downloaded the alsa-kernel and alsa-driver again... 

I noticed that when I do a make on the alsa-driver it seems to search for ~/alsa-driver/alsa-kernel (and complains it;s not found) 

I noticed we don;t actually do anything with the alsa-kernel directory .. 
should we be?

---

### Post by bombadier337 on 2006-11-26
No, its just needed to compile the hg version of alsa-driver.  It will complain if you don't have it and won't compile.

---

### Post by rax_m on 2006-11-26
Compiled it again... is says it's successful.. and the install seems ok.
But still no luck!

I'm throwing in the towel for this week (can only do this again on the wkend)..

Thanks again for the help Bomardier :)

---

### Post by wylie348 on 2006-11-26
All I can say is...  FINALLY!  And a BIG THANK YOU Bombadier!  I have been working on this for a month solid - as can be discovered by my several posts on this topic - and you found a working solution!  I was so close to saying forget it and return to windoze - but you saved me!
Now out of curiosity - is there a way to set the PCM so that it changes the sound?  Whenever I use my function keys to adjust the volume the slider changes but it is fixed to pcm and for some reason, pcm does not appear to change the volume anymore - only by opening volume contol and adjusting the front values can I change sound levels.
Regardless - awesome job - and thank you from a fellow T4210 owner who is sticking to Ubuntu!
:)

---

### Post by nugalonious on 2006-11-28
Hello,

I installed the mercurial alsa today with the hda intel driver and I still am unable to make it work. The machine is a Asus A8Js. All info I can dig up is to follow. All I can manage to get it to do is play out of the right channel with an annoying high pitch noise and sound stops if I try to adjust the volume. This happens over and over if I reload with /etc/init.d/alsasound reload and then play something again, adjust volume, no sound. I can't figure out anything else to try except maybe i don't have the correct alsa options. I've ran out of solid ideas and don't want to muck about and really mess something up. 

Basics:

```
ryno@crasus:~$ cat /etc/issue
Ubuntu 6.10 \n \l

ryno@crasus:~$ uname -a
Linux crasus 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

ryno@crasus:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
[COLOR="Red"]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)[/COLOR]
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0397 (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
06:00.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
06:00.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:00.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
06:00.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
06:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


```

Alsa:

```
ryno@crasus:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.13.
Compiled on Nov 27 2006 for kernel 2.6.17-10-generic (SMP).

ryno@crasus:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 74

ryno@crasus:~$ modinfo snd-hda-intel
filename:       /lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-intel.ko
license:        GPL
description:    Intel HDA driver
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        snd-pcm,snd-page-alloc,snd,snd-hda-codec,snd
alias:          pci:v00008086d00002668sv*sd*bc*sc*i*
alias:          pci:v00008086d000027D8sv*sd*bc*sc*i*
alias:          pci:v00008086d0000269Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004383sv*sd*bc*sc*i*
alias:          pci:v00001002d0000793Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00007919sv*sd*bc*sc*i*
alias:          pci:v00001106d00003288sv*sd*bc*sc*i*
alias:          pci:v00001039d00007502sv*sd*bc*sc*i*
alias:          pci:v000010B9d00005461sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Csv*sd*bc*sc*i*
alias:          pci:v000010DEd00000371sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003E4sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003F0sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Asv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Bsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Csv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Dsv*sd*bc*sc*i*
srcversion:     CFC483BC3D9CEEF6D205B9A
parm:           enable:bool
parm:           enable_msi:Enable Message Signaled Interrupt (MSI) (int)
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (int)
parm:           position_fix:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size). (int)
parm:           model:Use the given board model. (charp)
parm:           id:ID string for Intel HD audio interface. (charp)
parm:           index:Index value for Intel HD audio interface. (int)


ryno@crasus:~$ cat /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0

ryno@crasus:~$ amixer scontrols
Simple mixer control 'Headphone',0
Simple mixer control 'PCM',0
Simple mixer control 'Front',0
Simple mixer control 'Surround',0
Simple mixer control 'Center',0
Simple mixer control 'LFE',0
Simple mixer control 'Line',0
Simple mixer control 'CD',0
Simple mixer control 'Mic',0
Simple mixer control 'Phone',0
Simple mixer control 'IEC958',0
Simple mixer control 'PC Speaker',0
Simple mixer control 'Aux',0
Simple mixer control 'Mono',0
Simple mixer control 'Capture',0
Simple mixer control 'Mix',0
Simple mixer control 'Stereo Downmix',0

ryno@crasus:~$ amixer info
Card default 'Intel'/'HDA Intel at 0xfebfc000 irq 74'
  Mixer name    : 'Analog Devices AD1986A'
  Components    : 'HDA:11d41986 HDA:15433155'
  Controls      : 32
  Simple ctrls  : 17

```

---

### Post by Goronok on 2006-12-05
Holy crap, I HAVE SOUND!!!  Thanks everyone,  this thread just saved my ubuntu load.  I have an ICH6 realtek ALC655 sound chipset on my laptop and upgrading to the new 1.0.13 Alsa drivers did the trick.

---

### Post by WiryLattice on 2006-12-06
Hi

I'm rather new to Linux. I have been trying for weeks to make the sound work under linux on my Asus w2jb with the ICH7 rev02 card and I was hoping that this post was finally the solution. I have been trying SuSe, Fedora and now I am on Ubuntu Edgy, which is definitely the dist I like the best so far. 

I have gone through all the steps in this post and everything seems to be successful, but no sound ](*,) . Here are some of the outputs that I see other people have posted, hope anyone can make some sense of this.

sudo /etc/init.d/alsasound reload
Password:
Shutting down sound driver: done
Starting sound driver: snd-hda-intel done
XXX write TLV...
svein@W2Jb-Edgy:~$ 

~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.13.
Compiled on Dec  6 2006 for kernel 2.6.17-10-generic (SMP).

~$ cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 66

:~$ modinfo snd-hda-intel 
filename:       /lib/modules/2.6.17-10-generic/kernel/sound/pci/hda/snd-hda-intel.ko
license:        GPL
description:    Intel HDA driver
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        snd-pcm,snd-page-alloc,snd,snd-hda-codec,snd
alias:          pci:v00008086d00002668sv*sd*bc*sc*i*
alias:          pci:v00008086d000027D8sv*sd*bc*sc*i*
alias:          pci:v00008086d0000269Asv*sd*bc*sc*i*
alias:          pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Fsv*sd*bc*sc*i*
alias:          pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004383sv*sd*bc*sc*i*
alias:          pci:v00001002d0000793Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00007919sv*sd*bc*sc*i*
alias:          pci:v00001106d00003288sv*sd*bc*sc*i*
alias:          pci:v00001039d00007502sv*sd*bc*sc*i*
alias:          pci:v000010B9d00005461sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Csv*sd*bc*sc*i*
alias:          pci:v000010DEd00000371sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003E4sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003F0sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Asv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Bsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Csv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Dsv*sd*bc*sc*i*
srcversion:     CFC483BC3D9CEEF6D205B9A
parm:           enable:bool
parm:           enable_msi:Enable Message Signaled Interrupt (MSI) (int)
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (int)
parm:           position_fix:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size). (int)
parm:           model:Use the given board model. (charp)
parm:           id:ID string for Intel HD audio interface. (charp)
parm:           index:Index value for Intel HD audio interface. (int)


:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c5
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:02.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
06:03.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
06:03.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
06:03.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
06:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
06:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by wzardd on 2006-12-09
This fixed the problem on my HP DV2007EA. Thank you very much for this guide!

---

### Post by thisllub on 2006-12-10
> **rax_m said:**
> Compiled it again... is says it's successful.. and the install seems ok.
But still no luck!

I'm throwing in the towel for this week (can only do this again on the wkend)..

Thanks again for the help Bomardier :)

I have been working on this for nearly 2 weeks myself. The only difference between your situation and mine is that I have a VIA82xx card and a TV Card.

When I first installed Edgy the TV card had sound through the via card but the via card wouldn't work properly with any of the normal sound apps.

I tried to change the order of preference in the alsa-base file. Of course I backed it up first. However since then I can't get it to work at all, even after restoring the original alsa-base file ](*,) 

I have done everything on page one of the comprehensive guide at least three times to no avail.
The modprobe snd-via82xx just sits there.

I have even deleted every file on the system that matched via82 just in case of conflicts.
Strangely the modprobe snd- (tab) does nothing for me although I remember at one point it did.

Oh well I will persevere for a while and then try the other 46 pages in the comprehensive thread.

---

### Post by rod.naph on 2006-12-10
hi, i'm trying to follow this tutorial but fail at the part where i have to configure alsa-utils.  my problem is that it's reporting that my version of libasound is only version 1.0.11, and the 1.0.13 alsa code requires version 1.0.12.  i've checked and edgy seems to come with version 1.0.11 so how did you manage to compile it against 1.0.12?  did i miss a step somewhere?

if anyone can help that'd be great!
thanks, rod.

---

### Post by Cyaegha on 2006-12-12
I have the exact same problem rax_m was having.

modprobe snd-hda-intel just hangs
/etc/init.d/alsasound restart says
```
Shutting down sound driver: /usr/sbin/alsactl: save_state:1253: No soundcards found...
ERROR: Module snd_timer is in use
ERROR: Module snd is in use by snd_timer
done
ALSA driver is already running.

```

I've been trying several guides, modifying this, compiling that, probably compounding the problem.  When I first installed Edgy, analog sound was working (through my laptop's speakers) but I wanted to get the SPDIF working   (through the optical line out), now I have no sound at all.

I'm trying really hard to stay in Ubuntu, but it gets boring pretty quickly without sound.

Update:
I have once again ran your guide from the start, everything seems to run fine

```
$./hgcompile
...
  LD [M]  /home/adam/alsa-driver/usb/usx2y/snd-usb-usx2y.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-386'
utils/link-modules /home/adam/alsa-driver

ALSA modules were successfully compiled.

$ make install
...
make[1]: Leaving directory `/home/adam/alsa-driver/pcmcia'
/sbin/depmod -a 2.6.17-10-386 
cat WARNING

WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume.

$ alsaconf
Building card database..
Running update-modules...
Setting default volumes...
amixer: Mixer attach default error: No such device
Saving the mixer setup used for this in /etc/asound.state.
/usr/sbin/alsactl: save_state:1253: No soundcards found...
===============================================================================

 Now ALSA is ready to use.
 For adjustment of volumes, use your favorite mixer.

 Have a lot of fun!

$ /etc/init.d/alsasound reload
Shutting down sound driver: /usr/sbin/alsactl: save_state:1253: No soundcards found...
ERROR: Module snd_timer is in use
ERROR: Module snd is in use by snd_timer
done
ALSA driver is already running.



```

---

### Post by eggdeng on 2006-12-12
People using snd-hda-intel may find this useful. [http://ubuntuforums.org/showthread.php?t=314383](http://ubuntuforums.org/showthread.php?t=314383)

---

### Post by suoko on 2006-12-14
hi
I followed your intructions but unfortunatly myproblem below is not resolved.
Any ideas?
 
I'm experiencing problems with the audio card of my laptop.
SPecifically the problem is with the oss mixer.
Volume of oss mixer is wither max or mute. Plus, the "line in" controller affects the overall audio volume, i.e. if I set it in the middle the overall audio is very high, while if I move it from the middel position it is very low.
Moreover, the "line in" controller affects the headphone exit. middle position -> it works, else it doesn't

---

### Post by nbayiha on 2006-12-16
**_Cyaegha_** i had the same problem about the libasound
but  i figured out,  that i was doing the step 7 before the 6 and (means that i was trying to configure the utilies before the library) in that case it can't work cause, the libasound that alsa need is actually in the library package that you have from the first step, you don't even need to install it from synaptic(you can't even old version in synaptics 1.0.11) or somewhere else just follow the post step by step and i think everything will be fine for you .

Oh smth else, just in case if someone is interest; i tried this thread with the  **[COLOR="MediumTurquoise"]rc1.10.14[/COLOR]** and it just worked fine for me.

Great thanks to **[COLOR="Cyan"]bombadier337[/COLOR]** it's was a pleasure when i heard ubuntu startup from my headphone.
i'm using a  hp dv6000 and actually i've manage to make almost everything work instead of my camera....anyway thank a lot Bombardier.

---

### Post by flyingmantis on 2006-12-16
I followed the instructions and succesfully installed version 1.0.13.  However, now I have sounds on both headphone and speaker.  I can't mute either one.  I can't adjust the sound levels either.  

Any help are greatly appericated!

Mantis

---

### Post by flyingmantis on 2006-12-16
> **flyingmantis said:**
> I followed the instructions and succesfully installed version 1.0.13.  However, now I have sounds on both headphone and speaker.  I can't mute either one.  I can't adjust the sound levels either.  

Any help are greatly appericated!

Mantis

Yes!!! I finally figured it out.  I have to mute "front speaker" in Alsa Mixer in order to mute my headphones, and mute "surround" to mute my laptop built-in speakers.   It's still a pain, but I can live with this.

Mantis.

---

### Post by LuisC-SM on 2006-12-17
[QUOTE=To the Original Poster].[/QUOTE]

Is this working with ACPI=ON??

I've made your tutorial and I falled when compiling but I know it was a mistake of mine. But I'd like to know if you have ACPI iON on boot  before I try again.

Kind Regards

Luis C. Suárez

---

### Post by LuisC-SM on 2006-12-18
Well, I can answer myself... NO Sound with ACPI=ON

Cheers

Luis

---

### Post by Vilhelmo on 2006-12-23
Hi everybody and thanks for a great guide, seem to have helped a lot of people.  First I had the same problem as Rax_m when i tried to install the new modules. (for a long time). My solution to the problem was to remove the old (probably broken) alsa-drivers with these two commands: 
```
sudo aptitude remove --purge alsa-base
``` and
```
sudo aptitude remove --purge alsa-utils
```
This also removes some important packages called ubuntu-minimal and ubuntu-desktop. So when you have removed the old alsa-packages, reboot and log in to the terminal, without gnome, since we removed it. Reinstall everything with:
```
sudo aptitude install ubuntu-desktop
``` and
```
sudo aptitude install ubuntu-minimal
```. Reboot again with the command:
```
sudo reboot now
``` and log in to gnome again.
From now on I just followed this guide from the beginning, doing exactly as it says, and yey i have sound. 

The only issue is, that I have to run  sudo /etc/init.d/alsasound reload every time i start the computer to get sound. I want it to load automaticly every time I start the computer. Maybe this is easy to fix? Thanks in advance and merry christmas! (Please feel free to comment the short guide to reinstall alsa-base, since I am fairly new to ubuntu this was my way to solve the problem :P, maybe there is a better one?)

---

### Post by Softpedia on 2006-12-27
> **flyingmantis said:**
> Yes!!! I finally figured it out.  I have to mute "front speaker" in Alsa Mixer in order to mute my headphones, and mute "surround" to mute my laptop built-in speakers.   It's still a pain, but I can live with this.

Mantis.

Thank you for this great guide, it's very easy and it works! I have to admit that I was a bit disappointed when I didn't had sound on my speakers after I've done the tutorial, but I kept on reading and I saw **flyingmantis** post, activated my Surround option and...of course it was muted...I've unmuted it and my speakers are working!!!!

My laptop: Acer TravelMate 2480
Sound card: HDA Intel

Thank you so much for this guide again, and I think it's a shame Ubuntu 6.10 doesn't have latest updates to alsa and kernel.... (maybe I don't use the right repo?)

Merry Christmas and a Happy New Year to all!

---

### Post by karmaraver on 2006-12-31
Vilhelmo - you should be able to have it do that command every time you log in by going to
System > Preferences > Sessions > Startup Programs tab and clicking "Add." type in your command and save. Pretty sure that will do the trick.

as for me, idk if i'm just being noob, but I'm getting lost in the directions where it instructs to
"6. Change directories to the untarred library directory"

i did a "locate alsa" and found several directories that might constitute a library directory involving alsa.

```
 locate alsa
/var/lib/alsa
/var/lib/alsa/asound.state
/var/lib/dpkg/info/alsa-base.conffiles
/var/lib/dpkg/info/alsa-base.list
/var/lib/dpkg/info/alsa-base.md5sums
/var/lib/dpkg/info/alsa-base.postinst
/var/lib/dpkg/info/alsa-base.postrm
/var/lib/dpkg/info/alsa-base.preinst
/var/lib/dpkg/info/alsa-utils.conffiles
/var/lib/dpkg/info/alsa-utils.list
/var/lib/dpkg/info/alsa-utils.md5sums
/var/lib/dpkg/info/alsa-utils.postinst
/var/lib/dpkg/info/alsa-utils.postrm
/var/lib/dpkg/info/alsa-utils.preinst
/var/lib/dpkg/info/gstreamer0.10-alsa.list
/var/lib/dpkg/info/gstreamer0.10-alsa.md5sums
/var/lib/dpkg/info/libesd-alsa0.list
/var/lib/dpkg/info/libesd-alsa0.md5sums
/var/lib/dpkg/info/libesd-alsa0.postinst
/var/lib/dpkg/info/libesd-alsa0.postrm
/var/lib/dpkg/info/libesd-alsa0.shlibs
/var/lib/dpkg/info/libpt-plugins-alsa.list
/var/lib/dpkg/info/libpt-plugins-alsa.md5sums
/var/lib/dpkg/info/libsdl1.2debian-alsa.list
/var/lib/dpkg/info/libsdl1.2debian-alsa.md5sums
/var/lib/dpkg/info/libsdl1.2debian-alsa.postinst
/var/lib/dpkg/info/libsdl1.2debian-alsa.postrm
/var/lib/dpkg/info/libsdl1.2debian-alsa.shlibs
/etc/acpi/suspend.d/85-alsa-state.sh
/etc/apm/resume.d/20alsa
/etc/apm/scripts.d/alsa
/etc/apm/suspend.d/80alsa
/etc/default/alsa
/etc/init.d/alsa-utils
/etc/modprobe.d/alsa-base
/etc/rc0.d/K50alsa-utils
/etc/rc6.d/K50alsa-utils
/etc/udev/rules.d/85-alsa.rules
/lib/modules/2.6.17-10-generic/kernel/drivers/media/video/cx88/cx88-alsa.ko
/lib/modules/2.6.17-10-generic/kernel/drivers/media/video/saa7134/saa7134-alsa.ko
/sbin/alsactl
/usr/bin/alsamixer
/usr/lib/ao/plugins-2/libalsa09.so
/usr/lib/gcj-4.1/libgjsmalsa.so
/usr/lib/gstreamer-0.10/libgstalsa.so
/usr/lib/pwlib/device/sound/alsa_pwplugin.so
/usr/share/alsa
/usr/share/alsa/cards
/usr/share/alsa/cards/SI7018
/usr/share/alsa/cards/SI7018/sndoc-mixer.alisp
/usr/share/alsa/cards/SI7018/sndop-mixer.alisp
/usr/share/alsa/cards/AACI.conf
/usr/share/alsa/cards/ATIIXP-MODEM.conf
/usr/share/alsa/cards/ATIIXP-SPDMA.conf
/usr/share/alsa/cards/ATIIXP.conf
/usr/share/alsa/cards/AU8810.conf
/usr/share/alsa/cards/AU8820.conf
/usr/share/alsa/cards/AU8830.conf
/usr/share/alsa/cards/Audigy.conf
/usr/share/alsa/cards/Audigy2.conf
/usr/share/alsa/cards/Aureon51.conf
/usr/share/alsa/cards/Aureon71.conf
/usr/share/alsa/cards/CA0106.conf
/usr/share/alsa/cards/CMI8338-SWIEC.conf
/usr/share/alsa/cards/CMI8338.conf
/usr/share/alsa/cards/CMI8738-MC6.conf
/usr/share/alsa/cards/CMI8738-MC8.conf
/usr/share/alsa/cards/CS46xx.conf
/usr/share/alsa/cards/EMU10K1.conf
/usr/share/alsa/cards/EMU10K1X.conf
/usr/share/alsa/cards/ENS1370.conf
/usr/share/alsa/cards/ENS1371.conf
/usr/share/alsa/cards/ES1968.conf
/usr/share/alsa/cards/FM801.conf
/usr/share/alsa/cards/GUS.conf
/usr/share/alsa/cards/HDA-Intel.conf
/usr/share/alsa/cards/ICE1712.conf
/usr/share/alsa/cards/ICE1724.conf
/usr/share/alsa/cards/ICH-MODEM.conf
/usr/share/alsa/cards/ICH.conf
/usr/share/alsa/cards/ICH4.conf
/usr/share/alsa/cards/Maestro3.conf
/usr/share/alsa/cards/NFORCE.conf
/usr/share/alsa/cards/PC-Speaker.conf
/usr/share/alsa/cards/PMac.conf
/usr/share/alsa/cards/PMacToonie.conf
/usr/share/alsa/cards/RME9636.conf
/usr/share/alsa/cards/RME9652.conf
/usr/share/alsa/cards/SI7018.conf
/usr/share/alsa/cards/TRID4DWAVENX.conf
/usr/share/alsa/cards/VIA686A.conf
/usr/share/alsa/cards/VIA8233.conf
/usr/share/alsa/cards/VIA8233A.conf
/usr/share/alsa/cards/VIA8237.conf
/usr/share/alsa/cards/VX222.conf
/usr/share/alsa/cards/VXPocket.conf
/usr/share/alsa/cards/VXPocket440.conf
/usr/share/alsa/cards/YMF744.conf
/usr/share/alsa/cards/aliases.alisp
/usr/share/alsa/cards/aliases.conf
/usr/share/alsa/pcm
/usr/share/alsa/pcm/center_lfe.conf
/usr/share/alsa/pcm/default.conf
/usr/share/alsa/pcm/dmix.conf
/usr/share/alsa/pcm/dpl.conf
/usr/share/alsa/pcm/dsnoop.conf
/usr/share/alsa/pcm/front.conf
/usr/share/alsa/pcm/iec958.conf
/usr/share/alsa/pcm/modem.conf
/usr/share/alsa/pcm/rear.conf
/usr/share/alsa/pcm/side.conf
/usr/share/alsa/pcm/surround40.conf
/usr/share/alsa/pcm/surround41.conf
/usr/share/alsa/pcm/surround50.conf
/usr/share/alsa/pcm/surround51.conf
/usr/share/alsa/pcm/surround71.conf
/usr/share/alsa/speaker-test
/usr/share/alsa/speaker-test/sample_map.csv
/usr/share/alsa/alsa.conf
/usr/share/alsa/sndo-mixer.alisp
/usr/share/alsa-base
/usr/share/alsa-base/alsa.default
/usr/share/app-install/desktop/alsamixergui.desktop
/usr/share/app-install/desktop/balsa.desktop
/usr/share/app-install/desktop/gnome-alsamixer.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_alsamixergui.xpm
/usr/share/app-install/icons/_usr_share_pixmaps_gnome-alsamixer_gnome-alsamixer-icon.png
/usr/share/app-install/icons/gnome-balsa2.png
/usr/share/bug/alsa-base
/usr/share/bug/alsa-base/control
/usr/share/bug/alsa-base/presubj
/usr/share/bug/alsa-base/script
/usr/share/doc/alsa-base
/usr/share/doc/alsa-base/driver
/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
/usr/share/doc/alsa-base/driver/Audigy-mixer.txt.gz
/usr/share/doc/alsa-base/driver/Audiophile-Usb.txt.gz
/usr/share/doc/alsa-base/driver/Bt87x.txt
/usr/share/doc/alsa-base/driver/CMIPCI.txt.gz
/usr/share/doc/alsa-base/driver/ControlNames.txt
/usr/share/doc/alsa-base/driver/Joystick.txt
/usr/share/doc/alsa-base/driver/MIXART.txt
/usr/share/doc/alsa-base/driver/OSS-Emulation.txt.gz
/usr/share/doc/alsa-base/driver/Procfile.txt.gz
/usr/share/doc/alsa-base/driver/SB-Live-mixer.txt.gz
/usr/share/doc/alsa-base/driver/VIA82xx-mixer.txt
/usr/share/doc/alsa-base/driver/emu10k1-jack.txt
/usr/share/doc/alsa-base/driver/hda_codec.txt.gz
/usr/share/doc/alsa-base/driver/hdspm.txt.gz
/usr/share/doc/alsa-base/driver/seq_oss.html
/usr/share/doc/alsa-base/driver/serial-u16550.txt
/usr/share/doc/alsa-base/FAQ
/usr/share/doc/alsa-base/NEWS.Debian.gz
/usr/share/doc/alsa-base/README
/usr/share/doc/alsa-base/README.Debian
/usr/share/doc/alsa-base/SOUNDCARDS.gz
/usr/share/doc/alsa-base/changelog-old.Debian.gz
/usr/share/doc/alsa-base/changelog.Debian.gz
/usr/share/doc/alsa-base/changelog.gz
/usr/share/doc/alsa-base/copyright
/usr/share/doc/alsa-utils
/usr/share/doc/alsa-utils/PATCHES.Debian
/usr/share/doc/alsa-utils/README
/usr/share/doc/alsa-utils/README.Debian
/usr/share/doc/alsa-utils/README.aconnect
/usr/share/doc/alsa-utils/README.alsamixer
/usr/share/doc/alsa-utils/README.aseqnet
/usr/share/doc/alsa-utils/TODO
/usr/share/doc/alsa-utils/changelog.Debian.gz
/usr/share/doc/alsa-utils/changelog.gz
/usr/share/doc/alsa-utils/copyright
/usr/share/doc/gstreamer0.10-alsa
/usr/share/doc/gstreamer0.10-alsa/AUTHORS
/usr/share/doc/gstreamer0.10-alsa/NEWS.gz
/usr/share/doc/gstreamer0.10-alsa/README.Debian
/usr/share/doc/gstreamer0.10-alsa/README.gz
/usr/share/doc/gstreamer0.10-alsa/changelog.Debian.gz
/usr/share/doc/gstreamer0.10-alsa/copyright
/usr/share/doc/libesd-alsa0
/usr/share/doc/libpt-plugins-alsa
/usr/share/doc/libpt-plugins-alsa/copyright
/usr/share/doc/libsdl1.2debian-alsa
/usr/share/doc/libsdl1.2debian-alsa/BUGS.gz
/usr/share/doc/libsdl1.2debian-alsa/CREDITS
/usr/share/doc/libsdl1.2debian-alsa/README
/usr/share/doc/libsdl1.2debian-alsa/README-SDL.txt
/usr/share/doc/libsdl1.2debian-alsa/changelog.Debian.gz
/usr/share/doc/libsdl1.2debian-alsa/copyright
/usr/share/evolution-data-server-1.8/zoneinfo/Asia/Choibalsan.ics
/usr/share/lintian/overrides/alsa-base
/usr/share/locale-langpack/en_AU/LC_MESSAGES/alsa-utils.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/alsa-utils.mo
/usr/share/man/man1/alsactl.1.gz
/usr/share/man/man1/alsamixer.1.gz
/usr/share/menu/alsa-utils
/usr/share/sounds/alsa
/usr/share/sounds/alsa/Front_Center.wav
/usr/share/sounds/alsa/Front_Left.wav
/usr/share/sounds/alsa/Front_Right.wav
/usr/share/sounds/alsa/Noise.wav
/usr/share/sounds/alsa/Rear_Center.wav
/usr/share/sounds/alsa/Rear_Left.wav
/usr/share/sounds/alsa/Rear_Right.wav
/usr/share/sounds/alsa/Side_Left.wav
/usr/share/sounds/alsa/Side_Right.wav
/usr/share/zoneinfo/Asia/Choibalsan
/usr/share/zoneinfo/posix/Asia/Choibalsan
/usr/share/zoneinfo/right/Asia/Choibalsan
/usr/src/linux-headers-2.6.17-10/include/asm-arm/arch-omap/omap-alsa.h
/usr/src/linux-headers-2.6.17-10/include/config/video/saa7134/alsa.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/bt/alsa
/usr/src/linux-headers-2.6.17-10-generic/include/config/bt/alsa/module.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/video/cx88/alsa
/usr/src/linux-headers-2.6.17-10-generic/include/config/video/cx88/alsa/module.h
/usr/src/linux-headers-2.6.17-10-generic/include/config/video/saa7134/alsa
/usr/src/linux-headers-2.6.17-10-generic/include/config/video/saa7134/alsa/module.h

```

---

### Post by DrKatz on 2007-01-03
Hi! It was the first time I tried to turn on the sound with the headsets and I followed this tutorial and worked on the first time!!! I'm so happy that I registered an account here just to say THANK YOU and GREAT JOB!

My distribution is Ubuntu 6.10 Edgy and my Notebook is an HP Pavilion dv6175ea

The only problem is the mute light is on the orange it should be on the blue... but I can live with that hehehehe

Thanks again!

---

### Post by ozPATT on 2007-01-11
Hi all, 

I think i am so close here to getting this working,... 

in the terminal, when i type 

```
sudo /etc/init.d/alsasound start
```

it just says that the command isnt found... 

anyone know why this is or how i can fix it? 

thanks

Patrick

---

### Post by carpy on 2007-01-22
Has anyone tried the Feisty packages of alsa?  It is supposed to have 1.0.13.  
I'm running Edgy on my new HP Pavilion dv6000t, and was shocked when this morning I plugged in my headphones and nothing happened.  The speakers continued to play and my headphones continued to be silent.

I'm frankly shocked that something so basic is part of the driver, and not hard-coded.  Intriguing.  My tape players have done this behavior since I was a young child.  I'm not sure how I feel about the potentially buggy driver having control over something that fundamental.  Oh well.  I suppose I trust it with the sound being sent to the card.  I just don't ever want to have a time where I plug in the headphones to protect information or stop annoying sound and *not* have it work.  However, since it's a multimedia machine, I can see the benefits of flexibility (perhaps not shut off speakers while using externals as well).

Thanks all,
Matt

---

### Post by LosD on 2007-02-08
> **carpy said:**
> I just don't ever want to have a time where I plug in the headphones to protect information or stop annoying sound and *not* have it work.  


Funny you should mention it, I have the exacy problem you're afraid of. Usually it turns off the external speaker when I plug in my headphones (Edgy on Dell D620, by the way), but once in a while, I plug in the headphones, listen to my wonderful music (:guitar:), and start working... That is, until one of my bosses comes and taps me on the shoulder, and says: "Do you think you could turn it down/off/throw out that piece of junk music/noisemaker?". Quite annoying, I'm starting to go paranoid, taking my headphones off and listening constantly, just to be sure! ](*,)

Dennis

---

### Post by m0sand on 2007-02-11
Oh man that was such a nice howto! I followed it step-by-step and as you said it was amazing to hear the ubuntu log off sound again! :D

---

### Post by ozPATT on 2007-02-11
> **m0sand said:**
> Oh man that was such a nice howto! I followed it step-by-step and as you said it was amazing to hear the ubuntu log off sound again! :D

what how to? I'd be happy if my laptop played music through the headphones as well as the main speakers :D at least then it would be doing something! Oh to have speakers and headphones working... Do you think that Feisty will fix this issue? Or will I still be left with trying to find answers?

---

### Post by vishwak on 2007-03-14
Hello,
I am an Ubuntu newbie (3 weeks old). I have been trying unsuccessfully to get my headphones to work. 

I have Edgy installed on a HP dv6000t with Intel HDA soundcard (ICH 7 rev 2). My speakers work fine and I can mute, unmute and change volume on the speakers , but I have no sound coming out of my headphones and no headphone jack available under Volume Control

I followed the guide here and I get the following error when running the hg clone commands

hg clone [http://hg-mirror.alsa-project.org/alsa-driver](http://hg-mirror.alsa-project.org/alsa-driver) alsa-driver
HTTP 403 Error : Forbidden 

Has anybody else experienced similar errors ?

---

### Post by ozPATT on 2007-03-14
Hi vishwak, welcome to ubuntu! :D Its great to hear of new people turning to it... 

I have had the same issue as you, I discovered that the newest alsa-driver supports the headphones. I went to alsa-project.org, and downloaded the driver, library and utilities files for 1.0.14

Then I extracted each, then ./configure, make, make install and restarted and all was well... not sure if that helps, but thats what I did and it worked. I couldnt get the guide in this thread to work properly.

Thanks

Patrick

---

### Post by vishwak on 2007-03-15
hi patrick,
Thanks, your reply gave me a some options to try. I just have a few more questions on this.  I saw on one of your posts about including the following line under /etc/modprobe.d/alsa-base

options snd-hda-intel model=14f1

I also have the same codec. Generic 14f1 ID 5045. 

- Should I also be include the same line under alsa-base besides building alsa 1.0.14

- Also , when building alsa with the new versions I read in the ubuntu docs about doing a 
 ./configure -with-cards=hda-intel (as opposed to just ./configure). Is that neccessary ?

I am gonna go ahead and give it a try tommorow, hopefully everything will work!!

---

### Post by vishwak on 2007-03-15
An Update:

I downloaded the latest versions of alsa-driver(1.0.14rc3), alsa-lib(1.0.14rc3) and alsa-util(1.0.14rc2). I did a sudo ./configure followed by sudo make and sudo install for each of them in that order. 

When I restarted Edgy and opened the Gnome Volume Control I found controls for Int Mic and Ext Mic. Under the "Switches" tab I see Line-in, IntMic and IEC958.

Also rebuilding alsa changed my codec. Initially when I did a
 
cat /proc/asound/card0/codec#0 | grep -i codec

I got "Generic 14f1 ID 5045. " Now the same command lists my codec as 

"Conexant CX20549 (Venice)"

Right now I am getting audio out of my speakers but  I still don't have a headphone jack control and when I plug in my headphones I get audio out of both my headphones and the built in speakers. The weird thing is when I remove the headphones from the jack , I am unable to get any audio from the built-in speakers too.

I am wary of making any more changes , lest I totally loose sound from my system.

I am at my wits end, not sure what is happening!!

Any suggestions on how to solve this will be very invaluable.

---

### Post by vishwak on 2007-03-15
sorry I made a typo earlier it should be sudo make install instead of sudo install

---

### Post by vishwak on 2007-03-15
Anyone, any ideas on how to solve this issue. I am in dire need of having my headphones work!!

---

### Post by vishwak on 2007-03-15
Anyone, any ideas on how to solve this issue. I am in dire need of having my headphones work!!
Till then, I might just have to stick with windows:(

---

### Post by bongo on 2007-04-12
Same problem here too.
Seems Ubuntu doesn't handle more "advanced" audiocards. Its a pain when trying to play music through headphones to have the whole neighborhood hear it as well.

I will try Sabayon since I think that handled the card correct and ill get back to you.

Edit: I get it working now, Front is my headphones and surround is my speakers. Very logical indeed :)

---

### Post by Rospo Zoppo on 2007-04-13
Can you tell me more precisely how did you get it work bongo?

---

### Post by lamho on 2007-04-28
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/lamho/Desktop/downloads/alsa-driver-1.0.13  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/lamho/Desktop/downloads/alsa-driver-1.0.13/acore/memalloc.o
In file included from /home/lamho/Desktop/downloads/alsa-driver-1.0.13/acore/memalloc.c:1:
/home/lamho/Desktop/downloads/alsa-driver-1.0.13/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /home/lamho/Desktop/downloads/alsa-driver-1.0.13/acore/memalloc.inc:13,
                 from /home/lamho/Desktop/downloads/alsa-driver-1.0.13/acore/memalloc.c:1:
/home/lamho/Desktop/downloads/alsa-driver-1.0.13/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/home/lamho/Desktop/downloads/alsa-driver-1.0.13/include/adriver.h:1099: error: too many arguments to function ‘pci_save_state’
/home/lamho/Desktop/downloads/alsa-driver-1.0.13/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/home/lamho/Desktop/downloads/alsa-driver-1.0.13/include/adriver.h:1103: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/home/lamho/Desktop/downloads/alsa-driver-1.0.13/acore/memalloc.o] Error 1
make[2]: *** [/home/lamho/Desktop/downloads/alsa-driver-1.0.13/acore] Error 2
make[1]: *** [_module_/home/lamho/Desktop/downloads/alsa-driver-1.0.13] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] Error 2

---

### Post by WiryLattice on 2007-05-17
Hi everyone

Just wanted to announce that I have finally managed to make my ICH7 rev02 soundcard work on my asus w2jc laptop. I installed ubuntu feisty and then installed the latest drivers from alsa (1.0.14.rc4) according to this guide:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I just compiled the drivers, libs and utils, rebooted and the sound worked. I didn't have to add a line in the alsa-base file or anything. 

I've been struggling with this for a year. If there is anyone else out there who is still struggling I hope this can help you.

---

### Post by hanout on 2007-11-14
Ok Im running Ubuntu 7.10on a fujitsu Amilo 1451G and am having the same sound problem
I got the same message as Rax_m did about the Alsa driver already running and still no sound...

I dont really know how to check the libraries as suggested by Bombadier...hey Im new to Ubunto and Linux ...3 weeks ago I didn't know a driver from a diver and now Im updating compilers etc and it's all rather ....fantastic...except that I cant blast my favorite tunes like a normal geek while I learn about linux! so when I did:
lsmod | grep snd

I got:
snd_pcm_oss            43008  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                80644  1 snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35456  0 
snd_seq_midi            9728  0 
snd_rawmidi            26112  1 snd_seq_midi
snd_seq_midi_event      8704  2 snd_seq_oss,snd_seq_midi
snd_seq                54256  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24580  2 snd_pcm,snd_seq
snd_seq_device          9740  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56708  9 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11656  1 snd_pcm
 
and when I did: modinfo snd-hda-intel

filename:       /lib/modules/2.6.22-14-generic/ubuntu/media/snd-hda-intel/snd-hda-intel.ko
description:    Intel HDA driver
license:        GPL
srcversion:     CE1E01126593A3DE5624AE8
alias:          pci:v000010DEd0000055Dsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000055Csv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Bsv*sd*bc*sc*i*
alias:          pci:v000010DEd0000044Asv*sd*bc*sc*i*
alias:          pci:v000010DEd000003F0sv*sd*bc*sc*i*
alias:          pci:v000010DEd000003E4sv*sd*bc*sc*i*
alias:          pci:v000010DEd00000371sv*sd*bc*sc*i*
alias:          pci:v000010DEd0000026Csv*sd*bc*sc*i*
alias:          pci:v000010B9d00005461sv*sd*bc*sc*i*
alias:          pci:v00001039d00007502sv*sd*bc*sc*i*
alias:          pci:v00001106d00003288sv*sd*bc*sc*i*
alias:          pci:v00001002d0000AA00sv*sd*bc*sc*i*
alias:          pci:v00001002d0000960Csv*sd*bc*sc*i*
alias:          pci:v00001002d00007919sv*sd*bc*sc*i*
alias:          pci:v00001002d0000793Bsv*sd*bc*sc*i*
alias:          pci:v00001002d00004383sv*sd*bc*sc*i*
alias:          pci:v00001002d0000437Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000811Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000293Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000284Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000269Asv*sd*bc*sc*i*
alias:          pci:v00008086d000027D8sv*sd*bc*sc*i*
alias:          pci:v00008086d00002668sv*sd*bc*sc*i*
depends:        snd-pcm,snd-page-alloc,snd
vermagic:       2.6.22-14-generic SMP mod_unload 586 
parm:           index:Index value for Intel HD audio interface. (int)
parm:           id:ID string for Intel HD audio interface. (charp)
parm:           model:Use the given board model. (charp)
parm:           position_fix:Fix DMA pointer (0 = auto, 1 = none, 2 = POSBUF, 3 = FIFO size). (int)
parm:           probe_mask:Bitmask to probe codecs (default = -1). (int)
parm:           single_cmd:Use single command to communicate with codecs (for debugging only). (bool)
parm:           enable_msi:Enable Message Signaled Interrupt (MSI) (int)
parm:           enable:bool


that could just as well be Ancient Babylonian to me! What do I do now???
 I won't give up! No way! I'll do Anything to get windows out of my life!
Can someone help me, Please?

Thanks in advance

---

### Post by Intro5pection on 2007-12-18
I've tried many of the suggestions in this thread, including the main one, to no avail.

I think I might be on to something but need some help:

Another post suggested using :
sudo apt-get install linux-backports-modules-generic

But I receive the following every time.

E: Couldn't find package linux-backports-modules-generic


I do have everything added/enabled right in sources.list as far as I can see.

I also want to note I received the same when trying to get the libncurses5

Help?

---

### Post by LuisC-SM on 2007-12-22
> **Intro5pection said:**
> I've tried many of the suggestions in this thread, including the main one, to no avail.

I think I might be on to something but need some help:

Another post suggested using :
sudo apt-get install linux-backports-modules-generic

But I receive the following every time.

E: Couldn't find package linux-backports-modules-generic


I do have everything added/enabled right in sources.list as far as I can see.

I also want to note I received the same when trying to get the libncurses5

Help?

I believe everyone is willing to help you, BUT, you must provide some more info...
AFAIC, the linux-backports-modules-generic are not in the repos anymore (at least not in mine), so..
What are you doing?, what are the responses you get from the command line, etc...
some basic things so anyone can help u
Regards
Luis

---

