---
title: "installing sound card"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by gganitis on 2007-09-27
I'm sorry but I can't understand! I am going to make this post and still, look at the similar ones which I see but, I want to know something "more general" in order to understand what I should do!

I have just bought a Sound Blaster Audigy SE. It plays normally by the first time I logged in Ubuntu, without installing anything. Also, my microphone didn't work (I fixed that) and the two of the three "line out" of my card.

Looking about how to fix these, I saw so many things, that I confused! I tried to install Ubuntu Studio, I tried to install ALSA driver for my card, I downloaded ALSA driver by the site "alsa-project.org", I read it's install information, I read many things in these forums like the command "alsamixer" in which I didn't know how to change the model of the sound card by "CA0106" to Audigy SE or something... 

My volume control (ALSA or OSS) doesn't have the same choices as the most users as I saw in the forum (that's because I haven't installed right the sound card?). The same in the preferences of sound in System/Preferences/Sound

But I still didn't understand if I have to install a driver (ALSA or something else) in order my Sound Blaster Audigy SE to work normally, or if I have to install an application like Ubuntu Studio.

Can anyone explain to me what to do? What to install?
The last thing I've installed was that:
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

Sorry but I'm a really beginner! Thanks a lot.

---

### Post by gwoodard on 2007-09-28
tell u what try disabling ur onboard sound (usually thourgh BIOS (u have to hit one of the "F" keys) then reinstall ubuntu entirely then update then install programs after update see what happens

---

### Post by gganitis on 2007-09-29
Sorry but I didn't understand exactly what you are saying. :confused:

I have disabled the onboard sound card in the BIOS. Which of the programs do I have to install in order to work properly? ALSA, Jack, Ubuntu Studio? Which one?

What do you mean saying "reinstall ubuntu"? 	](*,)  Why? I can't fix it? 

Thank you very much!

---

### Post by Pablo Pablovski on 2007-10-01
CA0106 is the internal device ID for your Audigy card (I've just installed the same one today) - it worked straight away, using the alsa driver.. 

You might need to un-mute or increase the volume of some of the channels in alsamixer (I did) to get it to play sound.

---

### Post by gganitis on 2007-10-02
Thanks for the answer. :) I tried that you said, but nothing changed.

(I must explain that the one of the three "line out" of the card is working, but the second set of my speakers which is in the second "line out", don't work.)

And something else that I saw just today. The volume control which is in the top bar of my desktop, doesn't work. Works just the "Analog Front" in the "Playback" of the "Volume Control (Alsa mixer)"...  :confused:

Thanks again....

---

### Post by HilliBilly on 2007-10-03
try this
([http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106](http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106))
([http://www.overclockers.at/linux_bsd_and_others/solved_x-fi_xtreme_audio_6kanal_184928/page_1](http://www.overclockers.at/linux_bsd_and_others/solved_x-fi_xtreme_audio_6kanal_184928/page_1)) ...it's german, i know.

-------------------------------------

asound.conf

    code:
    pcm.ca0106 {
              type hw
              card 0
           }

           ctl.ca0106 {
              type hw
              card 0
    }

    pcm.snd_card {
            type hw
            card 0
            device 0
    }

    ctl.snd_card {
            type hw
            card 0
            device 0
    }



    pcm.dmixer {
        type dmix
        ipc_key 1024
        ipc_perm 0666
        slave.pcm "snd_card"
        slave {
            period_time 0
            period_size 1024
            buffer_size 4096
            rate 44100
            channels 6
        }
        bindings {
            0 0
            1 1
            2 2
            3 3
            4 4
            5 5
        }
    }

    pcm.dsnooper {
        type dsnoop
        ipc_key 2048
        ipc_perm 0666 
        slave.pcm "snd_card"
        slave 
        {
            period_time 0
            period_size 1024
            buffer_size 4096
            rate 44100
        }
        bindings {
            0 0
            1 1
        }
    }

    pcm.duplex {
        type asym
        playback.pcm "dmixer"
        capture.pcm "dsnooper"
    }

    pcm.!default {
        type plug
        slave.pcm "duplex"
    }


--------------------------------------

.asoundrc

    code:
    pcm.dmix51 {
        type dmix
        ipc_key 1024
        slave {
            pcm "hw:0,0"
            rate 44100
            channels 6
            period_time 0
            period_size 1024
            buffer_time 0
            buffer_size 4096
        }
    }

    pcm.20to51 {
         type route
         slave.pcm surround51
         slave.channels 6
         ttable.0.0 1
         ttable.1.1 1
         ttable.0.2 1
         ttable.1.3 1
         ttable.0.4 0.5
         ttable.1.4 0.5
         ttable.0.5 0.5
         ttable.1.5 0.5
    }

    pcm.duplex {
        type asym
        playback.pcm "20to51" #muss als pcm.20to51 definiert sein
        capture.pcm "dsnooper"
    }

---

### Post by gganitis on 2007-10-09
:(
I made those files and I added the code you told me, but nothing changed. :(

What should happen using those?

Thanks again.........

---

### Post by gganitis on 2007-10-09
Does it help you????

giannis@giannis:~$ cat /proc/asound/cards
 0 [CA0106         ]: CA0106 - CA0106
                      Audigy SE [SB0570] at 0xdc00 irq 20
giannis@giannis:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).
giannis@giannis:~$ cat /proc/asound/oss/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.14rc1 emulation code)
Kernel: Linux giannis 2.6.20-16-lowlatency #2 SMP PREEMPT Sun Sep 23 19:54:02 UTC 2007 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
Audigy SE [SB0570] at 0xdc00 irq 20

Audio devices:
0: CA0106 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: CA0106 MPU-401 (UART)

Timers:
31: system timer

Mixers:
0: mixer00

---

### Post by HilliBilly on 2007-10-09
have a look here, this is more up-to-date:
[http://ubuntuforums.org/showthread.php?t=524506&page=2](http://ubuntuforums.org/showthread.php?t=524506&page=2)

---

### Post by gganitis on 2007-10-10
Hillibilly, thanks again... I read this threat you told me and I started installing the things are writen. Writing "lspci -vvn" it shows:

00:03.2 0c03: 1039:7001 (rev 0f) (prog-if 10 [OHCI])
        Subsystem: 1039:7001
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (20000ns max), Cache Line Size: 32 bytes
        Interrupt: pin C routed to IRQ 18
        Region 0: Memory at ef003000 (32-bit, non-prefetchable) [size=4K]

00:03.3 0c03: 1039:7002 (prog-if 20 [EHCI])
        Subsystem: 1458:5004
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (20000ns max)
        Interrupt: pin D routed to IRQ 19
        Region 0: Memory at ef004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:0b.0 0401: 1102:0007
        Subsystem: 1102:100a
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 20
        Region 0: I/O ports at dc00 [size=32]
        Capabilities: <access denied>

00:0d.0 0c03: 1106:3038 (rev 62) (prog-if 00 [UHCI])
        Subsystem: 1106:3038
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 21
        Region 4: I/O ports at e000 [size=32]
        Capabilities: <access denied>

00:0d.1 0c03: 1106:3038 (rev 62) (prog-if 00 [UHCI])
        Subsystem: 1106:3038
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin B routed to IRQ 22
        Region 4: I/O ports at e400 [size=32]
        Capabilities: <access denied>

00:0d.2 0c03: 1106:3104 (rev 65) (prog-if 20 [EHCI])
        Subsystem: 1106:3104
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 128 bytes
        Interrupt: pin C routed to IRQ 20
        Region 0: Memory at ef006000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:0f.0 0200: 10ec:8139 (rev 10)
        Subsystem: 1458:e000
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (8000ns min, 16000ns max)
        Interrupt: pin A routed to IRQ 20
        Region 0: I/O ports at e800 [size=256]
        Region 1: Memory at ef007000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 0300: 10de:0110 (rev b2) (prog-if 00 [VGA])
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 248 (1250ns min, 250ns max)
        Interrupt: pin A routed to IRQ 23
        Region 0: Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at e0000000 (32-bit, prefetchable) [size=128M]
        [virtual] Expansion ROM at ed000000 [disabled] [size=64K]
        Capabilities: <access denied>


What does it mean? Can I continue? I continued but installing **gcc-4.1-multilib, gcc-4.2, gcc-4.2-base**, it answered "E: Couldn't find package"

And something else, after that, I continued installing the alsa driver. I made the directory and I wrote "sudo bunzip2 alsa-driver-1.0.14.tar.bz2" but I took back "**bunzip2: Can't open input file alsa-driver-1.0.14.tar.bz2: No such file or directory**"

I didn't use 
[ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/drive...1.0.14.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/a....0.14a.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/a....0.14a.tar.bz2)
because I didn't know how... :confused:

Thanks again

---

### Post by HilliBilly on 2007-10-10
> 00:0b.0 0401: 1102:0007
Subsystem: 1102:[COLOR="Red"]100a[/COLOR]
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
Latency: 32 (500ns min, 5000ns max)
Interrupt: pin A routed to IRQ 20
Region 0: I/O ports at dc00 [size=32]
Capabilities: <access denied>


that shows your model (100a). this model is already included in alsa driver version 1.0.14 what you could see here /usr/src/alsa/alsa-driver-1.0.14/alsa-kernel/pci/ca0106/ca0106_main.c, if you would have downloaded this two files which you haven't downloaded :)

/* New Audigy SE. Has a different DAC. */
         /* SB0570:
          * CTRL:CA0106-DAT
          * ADC: WM8775EDS
          * DAC: WM8768GEDS
          */
         { .serial = 0x100a1102,
           .name   = "Audigy SE [SB0570]",
           .gpio_type = 1,
           .i2c_adc = 1,
           .spi_dac = 1 } ,

just klick on the two links and save to disk (to your home directory)
[ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15rc3.tar.bz2)
[ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc3.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15rc3.tar.bz2)

you have to make a new directory:
sudo mkdir /usr/src/alsa

you have to copy the two files from your home directory to this new directory
sudo cp ~/alsa-* /usr/src/alsa/
 
> I continued but installing gcc-4.1-multilib, gcc-4.2, gcc-4.2-base, it answered "E: Couldn't find package"

try to install via synaptic. search for gcc-4 this should show up this 3 packages (among others) and mark for installation.

because you'v downloaded newer versions of the alsa stuff you have to use this modified commands:
cd /usr/src/alsa/
sudo bunzip2 alsa-driver-1.0.15rc3.tar.bz2
sudo tar -xf alsa-driver-1.0.15rc3.tar
sudo bunzip2 alsa-lib-1.0.15rc3.tar.bz2
sudo tar -xf alsa-lib-1.0.15rc3.tar
cd /usr/src/alsa/alsa-driver-1.0.15rc3/
sudo ./configure --with-cards=ca0106 --with-sequencer=yes
sudo make
sudo make install
cd /usr/src/alsa/alsa-lib-1.0.15rc3/
sudo ./configure
sudo make
sudo make install

and continue as described in the other thread.


ps.:
> "bunzip2: Can't open input file alsa-driver-1.0.14.tar.bz2: No such file or directory"

if you don't download the files, well, then there is "no such file". ;-)

---

### Post by gganitis on 2007-10-13
Sorry but I am not stupid... I' m just a really new ubuntu user...

First of all, I have to extract those 2 files, or just copy them?
Which is "via synaptic"? Where from do I have to install it? I know Synaptic Manager, Automatix 2, and the instructions of the "ubuntuguide.org". I didn't find these files on them.

I copied the two files about alsa, I tried to extract them but I couldn't in this directory, so I continued...
But...
giannis@giannis:/usr/src/alsa$ sudo bunzip2 alsa-driver-1.0.15rc3.tar.bz2
bunzip2: Can't open input file alsa-driver-1.0.15rc3.tar.bz2: No such file or directory.

Thanks for your patient Hillibilly! :)

---

### Post by HilliBilly on 2007-10-13
i am not sure if i understood all your questions. but let's start :)

> Which is "via synaptic"? Where from do I have to install it? 

(normaly) on the left top end of your screen you could cklick on "system", then "administration", then "synaptic package manager". enter your password. cklick on search. search for whatever you want. when you found it, right-click on it, mark for installation and click an "apply".

> 
First of all, I have to extract those 2 files, or just copy them?

**First** you have to copy (or move) them to the newly created directory /usr/src/alsa. if the two files are in your home directory, that's the right command:

sudo cp ~/alsa-* /usr/src/alsa/

if the two files are somwhere else, then go to the directory where the two files are and do a:

sudo cp alsa-* /usr/src/alsa/

if you can't find the two files, do a

sudo updatedb
locate alsa-driver-1.0.15rc3.tar.bz2

**After copying** you have to extract them. go the newly created directory with this command

cd /usr/src/alsa/

then do the gunzip commands. if you still get this error message, please post the output of this command:

ls -ltr  /usr/src/alsa/

mine looks like this:
~$ ls -ltr  /usr/src/alsa/
total 40740
-rw-r--r--  1 root src    785668 2007-10-03 22:41 alsa-lib-1.0.14a.tar.bz2
-rw-r--r--  1 root src  17387520 2007-10-03 22:41 alsa-driver-1.0.14.tar
drwxr-xr-x 28 root root     4096 2007-10-03 22:47 alsa-driver-1.0.14
drwxr-xr-x 10 root root     4096 2007-10-03 22:47 alsa-lib-1.0.14a
-rw-r--r--  1 me  me  17797120 2007-10-09 23:58 alsa-driver-1.0.15rc3.tar
-rw-r--r--  1 me  me   5662720 2007-10-09 23:58 alsa-lib-1.0.15rc3.tar
drwxr-xr-x 28 root root     4096 2007-10-10 00:03 alsa-driver-1.0.15rc3
drwxr-xr-x 10 root root     4096 2007-10-10 00:03 alsa-lib-1.0.15rc3

---

### Post by gganitis on 2007-10-13
Well................

**I copied the tar.bz2 files on the alsa directory and I extracted them. So in this dir now I have:**
    alsa-driver-1.0.14      
    alsa-lib-1.0.14a
    alsa-driver-1.0.14.tar  
    alsa-lib-1.0.14a.tar

I tried to find the three packages I couldn't find, but I realise that these are only for Gutsy! **I am on Feisty!** (I am talking about **gcc-4.1-multilib, gcc-4.2, gcc-4.2-base**. (as I read in [http://packages.ubuntu.com/feisty/allpackages](http://packages.ubuntu.com/feisty/allpackages))
[B]
I continued with the others but when I wrote [/B]
sudo ./configure --with-cards=ca0106 --with-sequencer=yes

**I took back:**
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
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
checking for current directory... /usr/src/alsa/alsa-driver-1.0.14
checking cross compile... 
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build... 
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

**I tried to install the full kernel sources and now in the src directory I have those files/dirs:**
alsa                             
linux-headers-2.6.20-16
linux-headers-2.6.17-10          
linux-headers-2.6.20-16-generic
linux-headers-2.6.17-10-generic  
linux-source-2.6.20
linux-headers-2.6.17-11          
linux-source-2.6.20.tar
linux-headers-2.6.17-11-generic

(I guess it's ok?)
[B]
Being in the "giannis@giannis:/usr/src/alsa/alsa-driver-1.0.14" directory I wrote again: [/B]
sudo ./configure --with-cards=ca0106 --with-sequencer=yes

**... and I took back again the same message:**
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

(I know that there is no directory named "linux" in the "src" directory)
[B]
The other you asked me:[/B]
giannis@giannis:/$ ls -ltr /usr/src/alsa/
total 22476
drwxr-xr-x 10 root root     4096 2007-06-11 11:53 alsa-lib-1.0.14a
-rw-r--r--  1 root src  17387520 2007-10-13 07:11 alsa-driver-1.0.14.tar
-rw-r--r--  1 root src   5580800 2007-10-13 07:12 alsa-lib-1.0.14a.tar
drwxr-xr-x 27 root root     4096 2007-10-13 18:56 alsa-driver-1.0.14

Thanks again.............................

---

### Post by HilliBilly on 2007-10-13
have a look here:

[http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106](http://www.alsa-project.org/main/index.php/Matrix:Module-ca0106)
(read inside the first black frame)

[http://64.233.183.104/search?q=cache:Ak_yVLXTq8IJ:ubuntuforums.org/archive/index.php/t-34692.html+The+file+/usr/src/linux/include/linux/version.h+does+not+exist.&hl=en&ct=clnk&cd=2&client=firefox-a](http://64.233.183.104/search?q=cache:Ak_yVLXTq8IJ:ubuntuforums.org/archive/index.php/t-34692.html+The+file+/usr/src/linux/include/linux/version.h+does+not+exist.&hl=en&ct=clnk&cd=2&client=firefox-a)

you're right, i'm on gutsy. 

unfortunately my linux skills are limited, therefore -if the two links don't solve your problem- you have to wait that someone else is coming along and can give you better support than i could.

good luck! :)

> giannis@giannis:/$ ls -ltr /usr/src/alsa/
total 22476
drwxr-xr-x 10 root root 4096 2007-06-11 11:53 alsa-lib-1.0.14a
-rw-r--r-- 1 root src 17387520 2007-10-13 07:11 alsa-driver-1.0.14.tar
-rw-r--r-- 1 root src 5580800 2007-10-13 07:12 alsa-lib-1.0.14a.tar
drwxr-xr-x 27 root root 4096 2007-10-13 18:56 alsa-driver-1.0.14


that looks perfect for me.

---

### Post by gganitis on 2007-10-15
Hillibilly, thanks a lot for your really useful help! I just read that on Thursday will be up to date the new version Gutsy... I hope installing that, my problems will be fixed after the download.

Anyway, thanks for everything. I learnt many things!
Keep helping!

Giannis Ganitis

---

### Post by gganitis on 2007-10-24
Nothing changed after upgrading to Gutsy. 

The same problems still exist!

:confused:  :confused:  :confused:  :confused:

---

### Post by gganitis on 2007-11-06
Is there any help? Hillibilly?

I think the driver is installed now in the right way. I tried it a lot, but I still have some problems.

I have some questions in order to fix that, if you can help me:

Which mixer is that we have to be sure all controls are on?
I've installed all the ALSA drivers (drivers, utils, libs). I saw they were right. I made the file .asound, I did everything you had in the link of the German forum (if I understood right)!! :)
In gutsy I could installed the three lib packages I couldn't before, but nothing happened.

May I have everything installed right and I am looking for the wrong direction???

Does all of your card "Line out" work? Should I have a utility to enable them?

Does anyone know? Can anyone help pleaeaeaeaeaease???

---

### Post by gganitis on 2007-11-18
It is solved!

I tried the same things from the beginning and everything worked fine!

Hillibilly thanks a lot for the advice.

---

