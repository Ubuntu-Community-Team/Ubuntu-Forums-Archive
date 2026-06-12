---
title: "Native Instruments Audio Kontrol 1 Howto"
date: 2009-05-29
forum: Multimedia Software
---

### Post by Paindistributor on 2009-05-29
Hi musicans and owners of the Native Instruments Audio Kontrol 1 USB-soundcard.

I bought a brand new **Audio Kontrol 1** because i wanted to replace the cheap intel-hda soundcard of my laptop. And best of all - Native Instruments supports Linux with a native driver! I connected the soundcard and... nothing works! But finally i've got this beast running. :popcorn:

This howto will show you, how to get the device running and setup midi and audio with jack. Dont expect a "anything works" howto now, but i'll update this post later to fix remaining issues. All help is welcome.

I'll use the name AK1 instead of "Audio Kontrol 1" (easier to read).


My studio setup currently looks like this:

- Roland Juno-D synth
- Phonic MM1705a 11 channel mixer
- Shure PG81 microphone
- Line6 POD 2.0
- Some guitars
- Ardour for audio recording
- Muse for midi recording
- of course the AK1


What works so far?

- playing and recording audio
- jack audio
- ardour
- midi

This doesn't work:

- audio mixer
- audacity keeps crashing if you're trying to use the soundcard
- the alsa version in ubuntu doesn't work - you'll need the latest one

And this isn't really nice:

- the soundcard hasn't a name description (like "HDA-Intel")
- xruns sometimes, sounds strange but i've had never problems with that so far (no "clicks")


I'm using the standard Ubuntu 9.04 64 bit version. In the first step you have to switch on the realtime features to avoid bad sync problems with midi and almost any issues that keeps jack running mad.


1. Change file /etc/security/limits.conf:

```
@audio		 -	 rtprio		 99
@audio		 -	 memlock	 unlimited
@audio		 -	 nice		 -19
```

Now you're all set to use the realtime feature.

I tried to use the linux-rt kernel (the one which comes in Ubuntu Studio). But jack wont work with that kernel - it just keeps crashing. I've got no idea why.


2. Check your environment:

Connect the AK1 to your computer. Check if everything goes right (bold entries have to appear!):

```
$ lsusb
**Bus 001 Device 011: ID 17cc:0815 Native Instruments Audio Kontrol 1**
Bus 001 Device 010: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 001 Device 009: ID 067b:2305 Prolific Technology, Inc. PL2305 Parallel Port
Bus 001 Device 008: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 006: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 005: ID 0c45:624f Microdia PC Camera (SN9C201)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 056a:0065 Wacom Co., Ltd 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0a5c:2101 Broadcom Corp. A-Link BlueUsbA2 Bluetooth
Bus 002 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC861VD Analog [ALC861VD Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
[B]Karte 1: default [], Gerät 0:  []
  Untergeordnete Geräte: 1/2
  Untergeordnetes Gerät '0: subdevice #0
  Untergeordnetes Gerät '1: subdevice #1
[/B]
```

My device doesn't show up with "Audio Kontrol 1" like i had seen in several forums.
I've found out that an error occurs while the driver tries to read the device descriptor - and fails. Thats why it doesn't show up with the proper description. Maybe a bug.


3. Replace alsa with the latest version.

Yes, you have to do this. The version in ubuntu 9.04 will not work.
Get the sourcecode at [www.alsa-project.org](www.alsa-project.org). I've used **alsa-1.0.20**. Get **alsa-driver**, **alsa-lib** and **alsa-utils**.

If you need OSS-support, you'll have to install the alsa-oss package as well.

Extract the files in a seperate directory and compile them. Begin with **alsa-driver**.
I've used following arguments to configure **alsa-driver**:

```

./configure --with-cards=all --with-sequencer=yes --with-card-options=all

```

And this will compile and install the driver.

```

make
sudo make install

```

Then proceed with **alsa-lib** and then **alsa-utils**. You dont't have to use specific arguments here. Just do the "./configure", "make", "sudo make install" and you are fine.

Maybe something goes WRONG: Just drop a message here and we will try to fix it.

If you ever want to go back to the original alsa packages, a "sudo make uninstall" in every source-directory will do the trick. After that (don't reboot!) you'll need to re-install all alsa-packages AND the linux-kernel (linux-modules too)!

**Be warned:** I hadn't installed the packages after uninstalling and gnome doesn't show up anymore
(because of the missing alsa-kernelmodules).


4. Last step through the technical jungle:

reboot :)

After reboot, check if your default soundcard (not the AK1!) has sound. If that is fine, we'll proceed with the next step.


5. Connect the AK1 to your computer:

Avoid connecting your device to a non-powered usb-hub! You can expect it to fail if you're planning to use phantom power. I'll never try this - maybe it blows your usbcable or eats your cat :P. Seriously - a device that comsumes a lot of power can influence other devices if connected to a hub that isn't active powered. I hadn't problems with this soundcard but with a mouse which was connected to a keyboard (the mouse just stopped working).


6. Connect your headphone or speakers to the device:

In the front of the AK1 you have an headphone ouput-jack. You'll need an adapter for connecting to standard pc-speakers. Connect your speakers and turn the volume (beyond the headphone-jack) up. You also have an switch that switches between channel 1/2 and 3/4. Use the 1/2 output channels in order to get sound. If you're using gnome, select system/settings/audio in your main menue. Go to the "devices" tab where you can select audio-devices. Select "(serial, usb-0000:00:1d.7-7) (ALSA)" for proper playback. The name of the device can be different on your system. But alway use the "(ALSA)" device. Be certain you have turned up the volume. But be careful with the volume - this testsound can blow your ears (ouch, my ears are ringing even now) Now press the "Test" button. If you hear that beeeeeeep sound, congratulations! If not - re-check your volumes/channel selector/speakers.


7. Jack:

Jack is nice. But getting it right can be a binary question - it works - or it doesn't work. I tested the AK1 with multible tracks and bitrates. I just can't get the xruns away - but as mentioned before they never affected any recording or playback. The AK1 just runs fine.

I'm currently using the following settings in jack:

```


[X] Realtime
[ ] Don't lock memory
[ ] Unlock memory
[ ] Soft Mode
[X] Monitor
[ ] Force 16 bit
[X] H/W Monitor
[X] H/W Meter
[ ] Ignore H/W
[ ] Verbose messages
MIDI-Driver: seq


Priority:       [default]
Frames:         [512]
Rate:           [96000]
Periods/Buffer: [3]
Word length:    [greyed out]
Wait:           [greyed out]
Channels:	[greyed out]
Max Ports:      [128]
Timeout:        [500]


Device:         [hw:1]
Dither:         [none]
Audio:          [duplex]
Inputdevice:    [default]
Outputdevice:   [default]
Inputchannels:  [default]
Outputchannels: [default]
Inputlatence:   [default]
Outputlatence:  [default]

Latence: 16ms

```

I'll test other settings later but this ones are working good.


Update: Added more details.

---

### Post by disketto on 2009-05-31
Great HowTo man !!!! i did get playing out that wonderful beeeeeeeeeeeeeep !!! :) :D
and i didn't figure out it was that simple like just recompiling alsa sources... :p
for the tascam us-224 it didn't go so easy... i had to recompile and use the usxy-loader  and i did expect something hard that way... :p
now i can make my muzik with the blessing of Linuzzz :) :KS
thankzz aLLot ;)

dsk

---

### Post by goo25 on 2009-05-31
Are you able to listen to all 4 channels? 
I use Traktor and it would be great to use AK1 under ubuntu, I can only listen on channel 1-2, but I haven't been able to get 3-4 to work. 
I understand that subdevice #0 should be channel 1-2 and subdevice#1 channels 3-4 ?

 > Karte 1: default [], Gerät 0:  []
  Untergeordnete Geräte: 1/2
  Untergeordnetes Gerät '0: subdevice #0
  Untergeordnetes Gerät '1: subdevice #1


---

### Post by disketto on 2009-06-01
well... i did speak too soon.... i got a problem....
when i use 'totem', to listen mp3 or watch some video, audio kontrol 1 works...
but when i try to use softwares like 'hydrogen' or any kind of software for audio production... it does not works with audio kontrol 1, it's like he recognize only the alsa driver of audigy (snd-ca106) and wants to work with it...
i just don't know how to get it working...
please help..:(
tnx 


dsk

---

### Post by Paindistributor on 2009-06-03
@goo25:

I have not tested this so far. But i think you're right with this. In the audio-settings in gnome i can't select anything but one AK1-device. And this leads to output 1/2. In jack you can select each of the outputs the AK1 offers. Maybe gnome just let us select the first device and no sub-devices.
What application did you use? And what do you intend to do with the additional channels?

@disketto:

Your question is easily answered. Your music/video applications are using gstreamer (and on top of that maybe pulseaudio). The audio-settings of gnome never affect "non-gstreamer" applications. That means Hydrogen is using it's own settings and it neither use gstreamer nor pulseaudio. Your default audio-applications in gnome are working, but hydrogen not - because it doesn't know. If you want serious audio production, you have to use jack audio. Just look in the first post (7). Hydrogen works nice with jack.


I've tested some more with the AK1 and discovered more problems. I can't get the xruns away. It has something to do with the realtime-feature of the kernel. There is a realtime-enabled kernel in the repository of ubuntu, but jack crashes with it. The sound crackles a lot and jack somemtimes become unstable. I'll test that with ubuntu-studio. I hope this fixes the issues. Another thing is monitoring of the mixed signal (for example, sequencer-output and keyboard-input). With the headphone-jack you can only monitor input OR output (1/2 or 3/4). This isn't nice, because if you want to record a guitar, the headphone-jack isn't usable here, because you hear only one of both signals. Maybe we can get the 3/4 channel running to output a mix of input- and output-channels. I have solved this issue with a complex mixer-routing with my Phonic MM1705a. This is the next big thing to solve.

---

### Post by goo25 on 2009-06-03
I'm using Traktor Pro (DJ console from Native Instruments) and Live (Ableton) under wine. In order to use Channels 3-4 as monitor and 1-2 as main output. 
I'm not an expert on Jack, and It's not working for me right now. So you say that Jack let you choose for all 4 channels on your AK1? What about using Jack for wine apps?  Do you have some experience on using Jack with Wine?  
I'll give it a try this weekend anyway.

---

### Post by Nareto on 2009-08-05
Hello, 
I managed to get my Rig Kontrol 2 working, with much help from the developer of the snd_usb_caiaq driver. He can be found on the alsa mailing list and has been with me very kind and helpful. I suggest you try posting there the problems you're having with inputs/outputs as they seem driver related (haven't read carefully all the posts though).

Also, please have a look at the alsa wiki's page on Native Instruments device's [http://alsa.opensrc.org/index.php/NativeInstruments]("http://alsa.opensrc.org/index.php/NativeInstruments"). I've put everything I needed to make the Rig Kontrol 2 work properly. Feel free to add info, especially specific to the Ak1; infact, as said in the wiki, the info there has been tested only by me and only with the rk2, so it definitely needs some addons by others.

Does the Audio Kontrol 1 have buttons/switches etc? The Rk2 has and I was able to make them trigger midi events using supercollider, as explained in the wiki.

---

### Post by Vigh on 2009-11-03
hi im following your guide and everything has worked successfully but when i go to configure alsa-utils i get an error-

configure: error: required curses helper header not found

how can I fix this? are alsa utils are requirement to get the AK1 working

AK1 is working now thanks for the guide

---

### Post by Drumitar on 2010-05-17
can someone make a video for this im kinda new to ubuntu and would love to get audio to work with my rigkontrol 3.

---

### Post by Nareto on 2010-05-23
I'm sorry but I'm not practical with making videos... but setting your RK3 shouldn't be at all difficult.

What is not working for you? 

If you install JACK (I reccomend you also use 'qjackctl', a nice gui), from the setup window you should be able to select your RK3 (once it's plugged obviously)

Then from the "Connections" window you should be able to route the input signal where you want (for guitar effects I reccomend Rakarrack, possibly git version)

let us know what you manage to do

---

### Post by triss on 2010-10-05
Hey all, I've just noticed my Audio Kontrol card is only showing as having two outputs in jack.

When I try and up the amount of outputs to four Qjackctl just refuses to launch jack for me.

I'm on ubuntu 10.04.

Can anyone suggest how I can make outputs 3/4 turn up?

NB: I haven't upgraded alsa as the device showed up when i did lsusb.

---

### Post by triss on 2010-10-15
sorry to bump this chaps but i'd really like to get access to outputs 3/4 on my AK1.

My Kaoss Pad is feeling alittle unloved.

---

### Post by d3rR on 2012-04-22
You can access the outputs 3/4 with putting the following code in your .asoundrc file:

```
# Makes the subdevices aka channel 1&2 and 3&4 available for alsa applications pcm_slave.sl12 {     pcm "hw:AudioKontrol1,0,0"     format S24_3BE     channels 2     rate 192000 }  pcm.channel12 {     type plug     slave sl12     }  pcm_slave.sl34 {     pcm "hw:AudioKontrol1,0,1"     format S24_3BE     channels 2     rate 192000 }  pcm.channel34 {     type plug     slave sl34 }
```I've written a tutorial with some additional information about the sound card on Linux on this page:

[http://www.ralf-oechsner.de/opensource/page/audio_kontrol1](http://www.ralf-oechsner.de/opensource/page/audio_kontrol1)

You can make pretty much everything work as it is expected to. You can also make the buttons and the wheel send MIDI signals to control audio software with it. I've written a small program to make do this which also takes care of turning on and off the LEDs the same way the Windows software does. You can find that program here:

[http://www.ralf-oechsner.de/opensource/page/nicontrol](http://www.ralf-oechsner.de/opensource/page/nicontrol)

---

### Post by jimkaragian on 2012-12-15
Hello there, first of all thanks for the guide.
I have the following problem, i tried the steps exactly as you say, but firstly i had the error 
"configure: error: required curses helper header not found"
when i run "./configure" at utilities..
and i do the next steps and now i have no sound at all and aplay -l gives "aplay: device_list:252: no soundcards found..."

Can you give me some help?

Thanks in advance..

---

### Post by jimkaragian on 2012-12-16
I solved my problem and finally i have "real" sound at my ubuntu..
I tried many many things i found on forums etc..and i am too new to Ubuntu, so i dont know what exactly caused this..but i think it is because the old alsa-drivers i downloaded..
i give > find /lib/modules/`uname -r` | grep snd
 i found here [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") and after new drivers install i took the "large list of items" answer.

Anyway, at last i couldnt install alsa-utils because of "configure: error: required curses helper header not found"...but i dont mind.;)
To change the internal laptop sound card and the AK1 i use pavucontrol 

I hope i will help someone:p

(3.5.0-19-generic kernel Ubuntu)

---

### Post by kPRnmnm on 2013-10-12
Hello

I try to record myself using my microphone in Audio Kontrol 1 under Ubuntu 13.04
Audio Kontrol 1 works for playing sounds : if I play sounds in Audacity, I can hear them in the headphones connected to Audio Kontrol 1
But when I try to record my voice in Audacity using the microphone connected to Audio Kontrol 1, no sound is recorded !

When I visualize "Sound settings" I can see Audio Kontrol 1 in "Output" panel but not in "Input" panel !

Here are some info about my environment (which is in French language so I hope you can guess what it says) :

```
# modinfo soundcore
filename:       /lib/modules/3.8.0-30-generic/kernel/sound/soundcore.ko
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     8ABC5ACBDA218CE05EAE01E
depends:        
intree:         Y
vermagic:       3.8.0-30-generic SMP mod_unload modversions

# cat /proc/asound/cards
 0 [MID            ]: HDA-Intel - HDA Intel MID
                      HDA Intel MID at 0xf1000000 irq 47
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xcfeec000 irq 48
 2 [AudioKontrol1  ]: snd-usb-caiaq - Audio Kontrol 1
                      Native Instruments Audio Kontrol 1 (usb-0000:00:1d.0-1.2)

cat /proc/asound/modules 
 0 snd_hda_intel
 1 snd_hda_intel
 2 snd_usb_caiaq

# lsusb | grep "Audio Kontrol"
Bus 002 Device 003: ID 17cc:0815 Native Instruments Audio Kontrol 1

# aplay -l
...
carte 1: AudioKontrol1 [Audio Kontrol 1], périphérique 0: Audio Kontrol 1 [Audio Kontrol 1]
  Sous-périphériques: 2/2
  Sous-périphérique #0: subdevice #0
  Sous-périphérique #1: subdevice #1
...
```


Audio Kontrol 1 used to work well when I installed the latest Alsa drivers under Ubuntu 12.04
But now, I am using Ubuntu 13.04. And when I try to install the latest Alsa drivers as I did before, it does not work


```
$ sudo apt-get install linux-headers-$(uname -r)
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
linux-headers-3.8.0-31-generic est déjà la plus récente version disponible.
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.

$ sudo apt-get install build-essential
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
build-essential est déjà la plus récente version disponible.
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.

$ sudo apt-get install kernel-package
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Paquets suggérés :
  linux-source kernel-source docbook-utils xmlto grub grub2 jfsutils mcelog oprofile reiserfsprogs squashfs-tools xfsprogs quota btrfs-tools
Les NOUVEAUX paquets suivants seront installés :
  kernel-package
0 mis à jour, 1 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 427 ko dans les archives.
Après cette opération, 1 890 ko d'espace disque supplémentaires seront utilisés.
Réception de : 1 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring/universe kernel-package all 12.036+nmu3 [427 kB]
427 ko réceptionnés en 0s (737 ko/s)
Sélection du paquet kernel-package précédemment désélectionné.
(Lecture de la base de données... 329028 fichiers et répertoires déjà installés.)
Dépaquetage de kernel-package (à partir de .../kernel-package_12.036+nmu3_all.deb) ...
Traitement des actions différées (« triggers ») pour « man-db »...
Paramétrage de kernel-package (12.036+nmu3) ...

$ sudo apt-get install linux-kernel-headers
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Note : sélection de « linux-libc-dev » au lieu de « linux-kernel-headers »
linux-libc-dev est déjà la plus récente version disponible.
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.

/usr/src/alsa/alsa-driver-1.0.25# sudo apt-get install kernel-devel
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet kernel-devel
root@Studio-XPS-1645:/usr/src/alsa/alsa-driver-1.0.25# sudo apt-get build-dep linux
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Choix de « linux-meta » comme paquet source à la place de « linux »
Les NOUVEAUX paquets suivants seront installés :
  gawk libsigsegv2
0 mis à jour, 2 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de prendre 793 ko dans les archives.
Après cette opération, 1 989 ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n] ? O
Réception de : 1 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring/main libsigsegv2 amd64 2.9-4ubuntu3 [14,7 kB]
Réception de : 2 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) raring/main gawk amd64 1:4.0.1+dfsg-2ubuntu1 [778 kB]
793 ko réceptionnés en 1s (655 ko/s)
Sélection du paquet libsigsegv2 précédemment désélectionné.
(Lecture de la base de données... 329556 fichiers et répertoires déjà installés.)
Dépaquetage de libsigsegv2 (à partir de .../libsigsegv2_2.9-4ubuntu3_amd64.deb) ...
Sélection du paquet gawk précédemment désélectionné.
Dépaquetage de gawk (à partir de .../gawk_1%3a4.0.1+dfsg-2ubuntu1_amd64.deb) ...
Traitement des actions différées (« triggers ») pour « man-db »...
Paramétrage de libsigsegv2 (2.9-4ubuntu3) ...
Paramétrage de gawk (1:4.0.1+dfsg-2ubuntu1) ...
Traitement des actions différées (« triggers ») pour « libc-bin »...
ldconfig deferred processing now taking place

$ uname -r
3.8.0-31-generic


/usr/src/alsa/alsa-driver-1.0.25# ln -s /usr/src/linux-headers-3.8.0-31-generic /usr/src/linux

ls -l /usr/src
lrwxrwxrwx  1 0 0      39 oct.   9 21:59 linux -> /usr/src/linux-headers-3.8.0-31-generic

# if not already done, do the following
ln -s /usr/src/linux-headers-3.8.0-31-generic /lib/modules/3.8.0-31-generic/build

ls -l /lib/modules/3.8.0-31-generic
lrwxrwxrwx  1 root root     39 sept. 10 22:37 build -> /usr/src/linux-headers-3.8.0-31-generic


/usr/src/alsa# tar xvf alsa-lib-1.0.27.2.tar.bz2
/usr/src/alsa# cd alsa-lib-1.0.27.2
/usr/src/alsa/alsa-lib-1.0.27.2# ./configure; make; make install

/usr/src/alsa# tar xvf alsa-driver-1.0.25.tar
/usr/src/alsa# cd alsa-driver-1.0.25
/usr/src/alsa/alsa-driver-1.0.25# ./configure --with-cards=usb-caiaq,hda-intel --with-sequencer=yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.25
checking cross compile... 
checking for directory with ALSA kernel sources... /usr/src/alsa/alsa-driver-1.0.25/alsa-kernel
checking for directory with kernel source... /lib/modules/3.8.0-31-generic/build
checking for directory with kernel build... /lib/modules/3.8.0-31-generic/build
checking for kernel linux/version.h ... no
The file /lib/modules/3.8.0-31-generic/build/include/INCLUDE_VERSION_H does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /lib/modules/3.8.0-31-generic/build).

```

I am stuck to this point. I am pretty sure that my Audio Kontrol 1 could work better if I could succeed installing Alsa drivers.
Anyone could help at this stage ?


Here is the ~/.asoundrc I created according to what I've found on the net:

```
pcm_slave.sl12 {     
 pcm "hw:AudioKontrol1,2,0"     
 format S24_3BE     
 channels 2     
 rate 192000 
}  

pcm.channel12 {     
 type plug     
 slave sl12     
}  

pcm_slave.sl34 {     
 pcm "hw:AudioKontrol1,2,1"     
 format S24_3BE     
 channels 2     
 rate 192000 
}  

pcm.channel34 {     
 type plug     
 slave sl34 
}
```

---

