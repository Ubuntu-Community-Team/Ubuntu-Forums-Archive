---
title: "HOW TO: Get Line6 Guitar Port to work!"
date: 2009-05-18
forum: Multimedia Software
---

### Post by ntaforge on 2009-05-18
How to install a Line6 Guitar Port (and the toneport

	With a very big thanks to Myhrman from Source Forge for helping me get this thing working and a big thanks to Grabner for providing the drivers for something that seems to be non existant for linux! This is to get the Guitar Port to work as a basic USB sound device so you will get a dry signal in and out that will work under Alsa and Jack.

Note: Myhrman says it should work with most toneports too but neither of us have one to test it out.

	First open your Terminal
Applications> Accessories> Terminal	

	You will need to get Subversion 
[PHP]sudo apt-get install subversion
[/PHP]
	Then you will need to get the source
[PHP]svn co https://line6linux.svn.sourceforge.net/svnroot/line6linux[/PHP]

	Change to the directory
[PHP]cd line6linux/driver/trunk[/PHP]

	Time to build from the source but first make sure you have the latest build and headers

[PHP]sudo apt-get install build-essential[/PHP]
[PHP]sudo apt-get install linux-headers [/PHP] (Note: You will atlest have version 2.6.27.14. To check your version in terminal type uname -r)

	Now that is updated and you are in the trunk directory 
[PHP]make[/PHP]
[PHP]sudo make install[/PHP]

	Now shutdown and restart with the guitar port (or toneport) connected and you should beable to see it in your 
System> Preferences> Sound

---

### Post by JohnsShadow on 2009-07-03
hey trying this on 8.04 with 2.6.24-16 headers (it failed miserably)

update to 9.04 its so much better then 8.o4

---

### Post by JohnsShadow on 2009-07-07
i upgrade to 9.04 so i could get the proper kernal
it compiled perfectly no errors or nothing 
i rebooted with the toy pluged in and bam there it was under sound

now to figure out how to get creox to play it

---

### Post by ICX7620 on 2009-07-14
I got my toneport UX1 to work!! Thank you so much! I used OSS. Had to update from 8.04 to 9.04 but it was worth it.


:guitar:

---

### Post by jedi13 on 2009-07-24
Hi, my toneport UX1 is working with everything, except Flash (youtube). Does anybody had a similar problem?

thank you,

Fabio

---

### Post by Orkin on 2009-07-28
Thanks!

Got it working with my Toneport GX in OSS. ALSA won't work at all.

Can't get it working with Wine at the moment, so still no Spotify, still it's a vast improvement over nothing.

---

### Post by darkeale on 2009-08-04
Hi,

I am trying to get my Guitarport to work.  when i set it as the output device in system>preferences>sound and then click test i get this error:-

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.

can anyone help with this?

Thanks,
Alex

---

### Post by tbluejeans on 2009-08-30
I get the same error message. Installation was no problem. Does anybody know what might be wrong?

---

### Post by tbluejeans on 2009-08-30
I'm using Ubuntu 9.04 and Toneport UX1. Trying to get sound to work over headphones. Is that my problem? Should I use a different channel?

---

### Post by ntaforge on 2009-08-31
After using my Guitar Port for some time now here's the settings that work for me. I don't have any problems with these settings!

Go to System> Preferences> Sound Preferences and make sure everything is on the Line6 (OSS) and on Default Mixer Select the ALSA version. This Config seems to work for me. Make sure your "Monitor Track" is muted due to some feedback when using Jack.

When recording with Jack only use "Capture_1" for your recordings. "Capture_2" is used by the Line6 software as the "DI" for the tuner and for some reason it has alot of noise. 

As for the ALSA support I'm clueless! It works under ALSA in Jack, so I don't know about that!

My only problem is to find a nice amp emulator program for Linux.

Forge

---

### Post by ntaforge on 2009-08-31
After using my Guitar Port for some time now here's the settings that work for me. I don't have any problems with these settings!

Go to System> Preferences> Sound Preferences and make sure everything is on the Line6 (OSS) and on Default Mixer Select the ALSA version. This Config seems to work for me. Make sure your "Monitor Track" is muted due to some feedback when using Jack.

When recording with Jack only use "Capture_1" for your recordings. "Capture_2" is used by the Line6 software as the "DI" for the tuner and for some reason it has alot of noise. 

As for the ALSA support I'm clueless! It works under ALSA in Jack, so I don't know about that!

My only problem is to find a nice amp emulator program for Linux.

Forge

---

### Post by ntaforge on 2009-08-31
> hey trying this on 8.04 with 2.6.24-16 headers (it failed miserably)

update to 9.04 its so much better then 8.o4

I could only get this to work with 2.6.24.17

---

### Post by ntaforge on 2009-08-31
> Hi,

I am trying to get my Guitarport to work. when i set it as the output device in system>preferences>sound and then click test i get this error:-

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.

can anyone help with this?

Thanks,
Alex

Just use the OSS Version and it should work

---

### Post by darkeale on 2009-09-26
ive tried oss and alsa and i get the same error message with both.

any other ideas?

does it matter that i had the guitarport pluged in when doing the installation?

thanks,
alex

edit:-

the oss error ends- internal data flow error 

instead of saying could not open audio device for playback

---

### Post by fabioleitao on 2009-10-21
I am trying to use my UX1 under 9.10

I can get the subversion, compile it propoerly, install it flawlessly but it does not get detected after the boot.

I believe its completely different than before, but I have no clue on how to make it work for me.

---

### Post by abelbrito on 2009-10-25
> **tbluejeans said:**
> I get the same error message. Installation was no problem. Does anybody know what might be wrong?
i have the same problem. aside from that i keep getting this weird hissing sound coming from my speakers when the TonePort is connected...kinda like how heavy wind sounds during a snowstorm. 

any help on this would be awesome

---

### Post by dionisio1983 on 2009-12-23
I am also tearing my hair out with this same problem!

I've tried on two different machines, one running 9.04 (an IBM Thinkpad) and the other 9.10 (a Mac G4 Powerbook), but no joy. Kernel on 9.04 is 2.6.28-17-generic.

My **Line 6 Toneport UX1** appears as both ALSA and OSS devices in Sound Preferences, but using ALSA I can't record using Audacity or Ardour (via Jack) - it's just silence. When I click 'Test' with ALSA Playback selected, I get a load of feedback through the headphones plugged into the Toneport. 

If I choose OSS in Sound Preferences and click 'Test', I get the error:

> "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Internal data flow error."

Audio recording programs don't work in OSS mode either.

Can anybody please advise me what I should be doing in Jack/Ardour/anywhere else to get this working properly? It's driving me nuts.

I would be so, so grateful as I'm hoping to do some recording via Linux over Christmas.

Cheers,
Dionisio1983

PS. The output from arecord -l is:

> card 0: UX1 [TonePort UX1], device 0: TonePort UX1 [TonePort UX1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 1: Intel ICH - MIC ADC [Intel 82801DB-ICH4 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 2: Intel ICH - MIC2 ADC [Intel 82801DB-ICH4 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 3: Intel ICH - ADC2 [Intel 82801DB-ICH4 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And aplay -l gives.

> card 0: UX1 [TonePort UX1], device 0: TonePort UX1 [TonePort UX1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 1: Intel ICH - MIC ADC [Intel 82801DB-ICH4 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 2: Intel ICH - MIC2 ADC [Intel 82801DB-ICH4 - MIC2 ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: I82801DBICH4 [Intel 82801DB-ICH4], device 3: Intel ICH - ADC2 [Intel 82801DB-ICH4 - ADC2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by spoons on 2010-07-11
Hi sorry for the bump, but I've gotten this working on my Line 6 UX1 and Ubuntu 10.04 using the guide provided by the OP. (thanks, by the way) however, I get some popping in playback of sounds. How can I get rid of this popping?

Thanks.

---

### Post by spoons on 2010-07-22
No-one?

---

### Post by spoons on 2010-07-25
Bump, really would like to get this working good and proper.

---

### Post by Symantic11 on 2010-11-26
Hey hows it going, I'm wondering if you ever found a solution to your  problem? I ask because I happen to be in some what of a similar problem,  I'm completely new at this and I'm having the hardest time getting the  Guitar-Port to work in 9.04 (jaunty) 

I've pretty much tried many  different times and ways to get this thing to work yet I have not been  successful, this is my new error msg I'm hopping maybe you can help  me??? 

I was following the last step from the instructions on

[http://www.ubuntugeek.com/how-to-install-a-line6-guitarport-or-toneport-ux1-or-gx.html](http://www.ubuntugeek.com/how-to-install-a-line6-guitarport-or-toneport-ux1-or-gx.html)


 last instructions were 

(Note: You will atlest have version 2.6.27.14. To check your version in terminal type uname -r)
 Now that is updated and you are in the trunk directory
  [LEFT][COLOR=#000000][COLOR=#000000][COLOR=#0000BB]make
[/COLOR][/COLOR][/COLOR][/LEFT]
 
  [COLOR=#000000][COLOR=#0000BB]sudo make install[/COLOR][/COLOR]

*** the error msg I got***


/home/eleven/line6linux/driver/trunk/audio.c:30: error: implicit declaration of function ‘snd_card_create’

make[2]: *** [/home/eleven/line6linux/driver/trunk/audio.o] Error 1
make[1]: *** [_module_/home/eleven/line6linux/driver/trunk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-19-generic'
make: *** [default] Error 2

-------------


Thanks for you time:)

---

### Post by jerry85 on 2011-01-06
Hi there, I'm kind of having the same problems installing the drivers..

something seems to go wrong in the last instruction, sudo make install. 

Before I even tried the software center, this indicated the driver was installed, but my soundcard was not listed in the sound settings menu.

So I uninstalled the driver using the software center and tried the instructions here:


Can anybody help? I'd like to know what's going wrong :)


```

jeroen@jeroen-Ubuntu:~$ uname -r
2.6.35-24-generic
jeroen@jeroen-Ubuntu:~$ sudo apt-get install subversion 
[sudo] password for jeroen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jeroen@jeroen-Ubuntu:~$ svn co https://line6linux.svn.sourceforge.net/svnroot/line6linux
A    line6linux/driver/branches/ux8
A    line6linux/driver/branches/ux8/variax.h
A    line6linux/driver/branches/ux8/control_pod.tex
A    line6linux/driver/branches/ux8/debian
A    line6linux/driver/branches/ux8/debian/control
A    line6linux/driver/branches/ux8/debian/compat
A    line6linux/driver/branches/ux8/debian/watch
A    line6linux/driver/branches/ux8/debian/changelog
A    line6linux/driver/branches/ux8/debian/copyright
A    line6linux/driver/branches/ux8/debian/rules
A    line6linux/driver/branches/ux8/debian/control.modules.in
A    line6linux/driver/branches/ux8/pod_resample.sh
A    line6linux/driver/branches/ux8/read_batch.sh
A    line6linux/driver/branches/ux8/toneport.c
A    line6linux/driver/branches/ux8/dumprequest.c
A    line6linux/driver/branches/ux8/toneport.h
A    line6linux/driver/branches/ux8/midibuf.c
A    line6linux/driver/branches/ux8/control.c
A    line6linux/driver/branches/ux8/sysinfo.sh
A    line6linux/driver/branches/ux8/apps
A    line6linux/driver/branches/ux8/apps/resample.sh
A    line6linux/driver/branches/ux8/apps/mp32pod.cpp
A    line6linux/driver/branches/ux8/apps/resample.cpp
A    line6linux/driver/branches/ux8/apps/Makefile
A    line6linux/driver/branches/ux8/dumprequest.h
A    line6linux/driver/branches/ux8/figures
A    line6linux/driver/branches/ux8/figures/impulse_response.odg
A    line6linux/driver/branches/ux8/figures/line6_linux.jpg
A    line6linux/driver/branches/ux8/figures/line6_linux.xcf
A    line6linux/driver/branches/ux8/figures/routing0.fig
A    line6linux/driver/branches/ux8/figures/routing1.fig
A    line6linux/driver/branches/ux8/figures/Makefile
A    line6linux/driver/branches/ux8/figures/routing2.fig
A    line6linux/driver/branches/ux8/figures/routing3.fig
A    line6linux/driver/branches/ux8/reinsert.sh
A    line6linux/driver/branches/ux8/midibuf.h
A    line6linux/driver/branches/ux8/control.h
A    line6linux/driver/branches/ux8/get_all_data.sh
A    line6linux/driver/branches/ux8/makedist.sh
A    line6linux/driver/branches/ux8/podxtpro.spec.in
A    line6linux/driver/branches/ux8/Makefile
A    line6linux/driver/branches/ux8/create_links.pl
A    line6linux/driver/branches/ux8/downsample_interpolate.patch
A    line6linux/driver/branches/ux8/out.sh
A    line6linux/driver/branches/ux8/line6usb.spec
A    line6linux/driver/branches/ux8/set_revision.sh
A    line6linux/driver/branches/ux8/capture.c
A    line6linux/driver/branches/ux8/store_all_data.sh
A    line6linux/driver/branches/ux8/checkpoint
A    line6linux/driver/branches/ux8/checkpoint/CParser.java
A    line6linux/driver/branches/ux8/checkpoint/PreprocessedFileState.java
A    line6linux/driver/branches/ux8/checkpoint/C.java
A    line6linux/driver/branches/ux8/checkpoint/CLexer.java
A    line6linux/driver/branches/ux8/checkpoint/CToken.java
A    line6linux/driver/branches/ux8/checkpoint/CTokenLexer.java
A    line6linux/driver/branches/ux8/checkpoint/C.tokens
A    line6linux/driver/branches/ux8/checkpoint/cc1
A    line6linux/driver/branches/ux8/checkpoint/manifest_c.txt
A    line6linux/driver/branches/ux8/checkpoint/C.g
A    line6linux/driver/branches/ux8/checkpoint/Checkpoint.java
A    line6linux/driver/branches/ux8/checkpoint/build.sh
A    line6linux/driver/branches/ux8/checkpoint/README.txt
A    line6linux/driver/branches/ux8/checkpoint/CMakeLists.txt
A    line6linux/driver/branches/ux8/GNUmakefile
A    line6linux/driver/branches/ux8/capture.h
A    line6linux/driver/branches/ux8/resample.conf
A    line6linux/driver/branches/ux8/pod.c
A    line6linux/driver/branches/ux8/restart_usb.sh
A    line6linux/driver/branches/ux8/pod.h
A    line6linux/driver/branches/ux8/capture.sh
A    line6linux/driver/branches/ux8/driverdocs.lyx
A    line6linux/driver/branches/ux8/aplay.sh
A    line6linux/driver/branches/ux8/midibuf
A    line6linux/driver/branches/ux8/midibuf/midibuf.c
A    line6linux/driver/branches/ux8/midibuf/main.cpp
A    line6linux/driver/branches/ux8/midibuf/CMakeLists.txt
A    line6linux/driver/branches/ux8/retrieve_all_data.sh
A    line6linux/driver/branches/ux8/Kconfig
A    line6linux/driver/branches/ux8/alsa_modules.txt
A    line6linux/driver/branches/ux8/batch_replace.pl
A    line6linux/driver/branches/ux8/control_variax.tex
A    line6linux/driver/branches/ux8/restart_alsa.sh
A    line6linux/driver/branches/ux8/control.txt
A    line6linux/driver/branches/ux8/update_version.pl
A    line6linux/driver/branches/ux8/testsuite.sh
A    line6linux/driver/branches/ux8/midi.c
A    line6linux/driver/branches/ux8/store_all_patches.sh
A    line6linux/driver/branches/ux8/logs
A    line6linux/driver/branches/ux8/logs/compact.pl
A    line6linux/driver/branches/ux8/logs/hex2raw.cpp
A    line6linux/driver/branches/ux8/logs/extract_packet_sizes.pl
A    line6linux/driver/branches/ux8/logs/Makefile
A    line6linux/driver/branches/ux8/logs/extract_data.pl
A    line6linux/driver/branches/ux8/tuner.sh
A    line6linux/driver/branches/ux8/INSTALL
A    line6linux/driver/branches/ux8/download
A    line6linux/driver/branches/ux8/download/create_symlinks.sh
A    line6linux/driver/branches/ux8/download/downsample_interpolate.patch
A    line6linux/driver/branches/ux8/playback.c
A    line6linux/driver/branches/ux8/midi.h
A    line6linux/driver/branches/ux8/driver.c
A    line6linux/driver/branches/ux8/make_control_tab.sh
A    line6linux/driver/branches/ux8/playback.h
A    line6linux/driver/branches/ux8/.bzrignore
A    line6linux/driver/branches/ux8/usbdefs.h
A    line6linux/driver/branches/ux8/driver.h
A    line6linux/driver/branches/ux8/audio.c
A    line6linux/driver/branches/ux8/record.sh
A    line6linux/driver/branches/ux8/get_all_patches.sh
A    line6linux/driver/branches/ux8/audio.h
A    line6linux/driver/branches/ux8/arecord.sh
A    line6linux/driver/branches/ux8/pcm.c
A    line6linux/driver/branches/ux8/pcm.h
A    line6linux/driver/branches/ux8/line6_find_device.pl
A    line6linux/driver/branches/ux8/variax.c
A    line6linux/driver/branches/ux8/control_intro.c
A    line6linux/driver/branches/ux8/make_control_tab.pl
A    line6linux/driver/branches/ux8/create_control.pl
A    line6linux/driver/branches/ux8/remove_old_podxtpro_driver.sh
A    line6linux/driver/branches/ux8/play.sh
Checked out revision 734.
jeroen@jeroen-Ubuntu:~$ cd line6linux/driver/trunk
jeroen@jeroen-Ubuntu:~/line6linux/driver/trunk$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jeroen@jeroen-Ubuntu:~/line6linux/driver/trunk$ sudo apt-get install linux-headers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers is a virtual package provided by:
  linux-headers-2.6.35-24-virtual 2.6.35-24.42
  linux-headers-2.6.35-24-generic-pae 2.6.35-24.42
  linux-headers-2.6.35-24-generic 2.6.35-24.42
  linux-headers-2.6.35-24 2.6.35-24.42
  linux-headers-2.6.35-23-virtual 2.6.35-23.41
  linux-headers-2.6.35-23-generic-pae 2.6.35-23.41
  linux-headers-2.6.35-23-generic 2.6.35-23.41
  linux-headers-2.6.35-23 2.6.35-23.41
  linux-headers-2.6.35-22-virtual 2.6.35-22.35
  linux-headers-2.6.35-22-generic-pae 2.6.35-22.35
  linux-headers-2.6.35-22-generic 2.6.35-22.35
  linux-headers-2.6.35-22 2.6.35-22.35
You should explicitly select one to install.

E: Package 'linux-headers' has no installation candidate
jeroen@jeroen-Ubuntu:~/line6linux/driver/trunk$ sudo apt-get install linux-headers-2.6.35-24-generic 2.6.35-24.42
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 2.6.35-24.42
E: Couldn't find any package by regex '2.6.35-24.42'
jeroen@jeroen-Ubuntu:~/line6linux/driver/trunk$ sudo apt-get install linux-headers-2.6.35-24-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.35-24-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jeroen@jeroen-Ubuntu:~/line6linux/driver/trunk$ cd line6linux/driver/trunkbash: cd: line6linux/driver/trunk: No such file or directory
jeroen@jeroen-Ubuntu:~/line6linux/driver/trunk$ make
./set_revision.sh
make -C /lib/modules/2.6.35-24-generic/build CONFIG_LINE6_USB=m SUBDIRS=/home/jeroen/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  CC [M]  /home/jeroen/line6linux/driver/trunk/driver.o
  LD [M]  /home/jeroen/line6linux/driver/trunk/line6usb.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/jeroen/line6linux/driver/trunk/line6usb.mod.o
  LD [M]  /home/jeroen/line6linux/driver/trunk/line6usb.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
jeroen@jeroen-Ubuntu:~/line6linux/driver/trunk$ sudo make install
./set_revision.sh
make -C /lib/modules/2.6.35-24-generic/build CONFIG_LINE6_USB=m SUBDIRS=/home/jeroen/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
mkdir -p /lib/modules/2.6.35-24-generic/kernel/drivers/staging/line6 /usr/bin /usr/share/doc/packages/line6usb
find /lib/modules/2.6.35-24-generic -name line6usb.ko -delete
cp line6usb.ko /lib/modules/2.6.35-24-generic/kernel/drivers/staging/line6
cp *.sh *.pl /usr/bin
cp driverdocs.pdf /usr/share/doc/packages/line6usb
cp: cannot stat `driverdocs.pdf': No such file or directory
make: *** [install-only] Error 1
jeroen@jeroen-Ubuntu:~/line6linux/driver/trunk$ 

```

```

jeroen@jeroen-Ubuntu:~/line6linux/driver/trunk$ sudo make install
./set_revision.sh
make -C /lib/modules/2.6.35-24-generic/build CONFIG_LINE6_USB=m SUBDIRS=/home/jeroen/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
mkdir -p /lib/modules/2.6.35-24-generic/kernel/drivers/staging/line6 /usr/bin /usr/share/doc/packages/line6usb
find /lib/modules/2.6.35-24-generic -name line6usb.ko -delete
cp line6usb.ko /lib/modules/2.6.35-24-generic/kernel/drivers/staging/line6
cp *.sh *.pl /usr/bin
cp driverdocs.pdf /usr/share/doc/packages/line6usb
cp: cannot stat `driverdocs.pdf': No such file or directory
make: *** [install-only] Error 1
jeroen@jeroen-Ubuntu:~/line6linux/driver/trunk$ 

```

---

### Post by Tim Satterwhite on 2011-02-02
Hi.  I had the same problem with make install.  It's looking to copy the driverdocs.pdf file from the sources directory, but it's not in that directory.  I found it here: [http://www.tanzband-scream.at/line6/driverdocs.pdf](http://www.tanzband-scream.at/line6/driverdocs.pdf), and copied it to the line6usb directory.  Then, I re-ran make install, and things proceeded.  Good luck!

---

### Post by MentatGhola on 2012-01-24
> **Tim Satterwhite said:**
>  and copied it to the line6usb directory. 
As far as I can tell there is no line6usb directory.  Only a file called line6usb.spec, which is literally the usb line6 device experimental driver for linux.

---

### Post by MentatGhola on 2012-01-24
I got an error 2 similar to Synaptic11's.  

Output:```
make
./set_revision.sh
test: 18: https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk: unexpected operator
make -C /lib/modules/2.6.32-5-amd64/build CONFIG_LINE6_USB=m SUBDIRS=/home/ron/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-5-amd64'
  CC [M]  /home/ron/line6linux/driver/trunk/midi.o
/home/ron/line6linux/driver/trunk/midi.c: In function &#8216;midi_set_midi_mask_transmit&#8217;:
/home/ron/line6linux/driver/trunk/midi.c:314: error: implicit declaration of function &#8216;kstrtou16&#8217;
make[4]: *** [/home/ron/line6linux/driver/trunk/midi.o] Error 1
make[3]: *** [_module_/home/ron/line6linux/driver/trunk] Error 2
make[2]: *** [sub-make] Error 2
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-5-amd64'
make: *** [default] Error 2
 
```

---

### Post by princeofnam on 2012-03-09
has anyone tried this only to get a really distorted sound to come through? i once had a clean sound once but now it's really messed up.

---

### Post by princeofnam on 2012-03-10
i'm also told to use OSS frequently in Sound Preferences but I see no options in Ubuntu 11.10.

---

### Post by 777funk on 2012-08-28
Does anyone have any ideas on how to get this working in Ubuntu 12.04? I'm having the same issue with the errors.

---

### Post by bachmaninoff on 2012-09-01
Hi!  I'd really like to get this to work also, not sure what to do next under 12.04:

make
./set_revision.sh
./set_revision.sh: 9: test: [https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:](https://line6linux.svn.sourceforge.net/svnroot/line6linux/driver/trunk:) unexpected operator
make -C /lib/modules/3.2.0-29-generic/build CONFIG_LINE6_USB=m SUBDIRS=/home/john/line6linux/driver/trunk modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-29-generic'
  CC [M]  /home/john/line6linux/driver/trunk/audio.o
/home/john/line6linux/driver/trunk/audio.c: In function ‘line6_init_audio’:
/home/john/line6linux/driver/trunk/audio.c:30:57: error: ‘THIS_MODULE’ undeclared (first use in this function)
/home/john/line6linux/driver/trunk/audio.c:30:57: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [/home/john/line6linux/driver/trunk/audio.o] Error 1
make[1]: *** [_module_/home/john/line6linux/driver/trunk] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-29-generic'
make: *** [default] Error 2

---

### Post by 777funk on 2012-09-01
I just tried it in Hardy Heron (old version 8.04 from 2008) and it didn't work on that either. Got the same errors.

---

### Post by steeldriver on 2012-09-01
For the record, I think we figured out in your other thread that in order to build the driver you need to do the following

1. temporarily link /bin/sh to bash to make the ./set_revision.sh error go away

```
sudo ln -sf bash /bin/sh
```2. newer kernels need an additional include file to supply the THIS_MODULE definition - see[ http://blog.gmane.org/gmane.comp.audio.line6linux.user/month=20120301]("http://blog.gmane.org/gmane.comp.audio.line6linux.user/month=20120301") for example; so add
```
#include <linux/export.h>
```at the top of the line6linux/driver/trunk/audio.c file (I put it  ahead of the other includes, right above sound/core.h)

However it seems you could not get the device to respond even with the new driver installed

---

### Post by svszombie on 2012-12-19
Did anyone manage to fix this because I consider buying one Line 6 Pod Studio UX1 with Pod Farm 2

---

