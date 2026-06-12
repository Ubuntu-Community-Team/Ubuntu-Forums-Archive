---
title: "Messed up audio !!"
date: 2009-06-02
forum: Multimedia Software
---

### Post by So*nix on 2009-06-02
:) Hello Community !!
I switched to linux a few days ago & i am having a hard time doing it .
My system is - Asus P5LD2-VM/S (Intel 945 GZ I guess ), ALC 882 audio, 1 GB RAM , GeForce 8600 GT 256 MB . with Linux Mint 7 & XP Pro SP3 on it (until i learn administrarting Linux )
With a little help from google i was able to install drivers for my Graphics card , but i am unable to install audio drivers .

Steps to Install
_________________________________________________________________________

The source code copy from [www.alsa-project.org]("http://www.alsa-project.org").      ver:3.3-4
Linux Source Code for ALC audio codec
Support Codec list:
====AC97 Codec=====
ALC100,100P
ALC200,200P
ALC650D
ALC650E
ALC650F
ALC650
ALC655
ALC653
ALC658
ALC658D
ALC850
ALC101
ALC202
ALC250
ALC203

====HD Audio codec ====
ALC260
ALC262
ALC267
ALC268
ALC269
ALC272
ALC660
ALC660VD
ALC662
ALC663
ALC861
ALC861VD
ALC880
ALC882
ALC883
ALC885
ALC888
ALC889A

Installation:
This Source Code is from [www.alsa-project.org]("http://www.alsa-project.org").
For OS installation, please remember add the Development tool kit.
For driver installation, please follow below steps. 

Automatic install: (Recommend RedHat distribution)
execute

  ./install

Note: Ubuntu OS, please use manual install.
      Run commands need to add sudo at first words.   

Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support from kernel config 
    (soundcore module, default turn on)

Step 3. Complied source code
    a. cd alsa-driver-1.0.xx
    b. ./configure
    c. make
    d. make install
    e. alsaconf
    f. ./snddevices (Only kernel 2.4 does it)

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
     (Please refer to the attached modules.conf)
     
        snd-xxxx is the card ID.

    -- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
       --- Intel ICH6 ICH7 ---------
               snd-hda-intel

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
           snd-via82xx
           --- ATI Chipset  -------------------------------
           snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
    # ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        *Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer

Note:     1. The most detail information, can refer the alsa-kernel/Documenttation/ALSA-Configuration.txt in the azx-021705.tar.bz2.
    2. Kernel Version must be 2.2.14 or later.
    3. All mixer channels are muted by default. You must use a native
        or OSS mixer program to unmute appropriate channels.
    4. If can not compile the source code, try to rename the /usr/src/linux-2.x -> /usr/src/linux.
    5. The driver added to support the SPDIF functoin.     
    6. a. You can download the alsa-lib-1.0.9 and alsa-utils-1.0.9a form the [www.alsa-project.org]("http://www.alsa-project.org"), then unzip and install them. 
       b. Suggest use "alsamixer" to control mixer function.
       c. Used "alsaconf" can autodetect which drive you need to install (step 4).     
        7. SUSE Distribution must install the ncurses package. 
_________________________________________________________________________

Now my problem is Step 2 -Turn on sound support from kernel config 
    (soundcore module, default turn on)
what is it , how to do it & if it is something none of my concerne
then moving towards Step 3 i find my self helpless again

Step 3
a) changed to alsa dir - Fine 
b) ./configure - Fine
c) Make

Now here is my problem , When i do this i get the following message
_________________________________________________________________________
# make
make dep
make[1]: Entering directory `/home/sam/Projects/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11'
make[2]: Entering directory `/home/sam/Projects/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11/acore'
copying file alsa-kernel/core/info.c
/home/sam/Projects/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/home/sam/Projects/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/sam/Projects/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11'
make: *** [include/sndversions.h] Error 2
_________________________________________________________________________

Even if i ignore this & proceed 
d) Make install

I Get
_________________________________________________________________________
# make install
if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /home/sam/Projects/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11/include/sound /usr/include/sound; \
    else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
            install -m 644 -g root -o root $f /usr/include/sound; \
        done \
    fi
find /lib/modules/2.6.28-11-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.28-11-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.28-11-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.28-11-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/sam/Projects/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11/acore'
mkdir -p /lib/modules/2.6.28-11-generic/kernel/sound/acore
cp snd-hrtimer.ko snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rawmidi.ko snd-timer.ko snd.ko /lib/modules/2.6.28-11-generic/kernel/sound/acore
cp: cannot stat `snd-hrtimer.ko': No such file or directory
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rawmidi.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/sam/Projects/realtek-linux-audiopack-5.11/alsa-driver-1.0.19-5.11/acore'
make: *** [install-modules] Error 1
_________________________________________________________________________

Plz somebody help .....

Doing the provided install with the Linux realtek-linux-audiopack-5.11 has killed my audio .

:(

---

### Post by So*nix on 2009-06-07
[B]:evil:Awh !
Come on guys ... don't keep me waiting ....

:-k I wonder why isn't any one answering ...
Is this the community that i had heard about being so damn big & responsive ..
Awh .. gimme a break ...
 [/B]

---

### Post by tolotos on 2009-06-08
Hello So*nix

As with step 2 I can`t provide any help.
Concerning step 3 and the following:

Are you sure you have installed the necessary packages for compiling:

build-essential
linux-headers-generic
kernel-package
xmlto
linux-source

I`m not exactly sure whether you need all of those, but with installing it, you should get all you need.

Is there a specific reason why you want`t to compile alsa yourself? If it is just general Interest in Linux, I would suggest using the alsa-packages from the package-manager and rather invest time in compiling my own kernel (Way more interesting in my eys ;-)).

---

### Post by Azrael3000 on 2009-06-10
The most convenient way of upgrading alsa is here: [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

---

### Post by So*nix on 2009-06-16
Thanks Tolotos .
Oh ! and you too Azrael3000 .

---

