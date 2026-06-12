---
title: "Sound gone after update"
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by bahdom on 2007-09-01
I use USB headphones and alsa 1.0.13 which were working perfectly a couple of days ago. An auotupdate window appeared and i installed the available packages. Once i restarted my computer i've got no sound and it says that "no volume control gstreamer plugins and/or devices found"  and in the sound preferences window i get no options for mixer.

HELP

---

### Post by p110011 on 2007-09-01
Same thing happened to me. ECS Nforce3-A main board with onboard AC 97 Audio.

I looked in hardware information and the sound card does not show up.

I dual boot and sound works in the other OS. Need help please.

---

### Post by tribunal on 2007-09-01
The same problem.
Sound gone.
"Typical methods" didn't work at all.
Only installation ALSA from sources.
But I have a new problem:
only pcm-oss works, but clean-alsa apps doesn't work :(
After starting  them, I see this error:
ALSA lib confmisc.c:1286:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix.device'
ALSA lib conf.c:3510:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3982:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2144:(snd_pcm_open_noupdate) Unknown PCM default

Found solution!!
This 2 lines are a good solution!
 mv ~/.asoundrc .asoundrc.old
 mv ~/.asoundrc.asoundconf ~/.asoundrc.asoundconf.old

---

### Post by freakzilla on 2007-09-01
Add me to the list, sound gone after update.

---

### Post by bahdom on 2007-09-01
sound works for me in XP too

---

### Post by jfas on 2007-09-01
yeah man i just installed ubuntu today happily wish ti remove the bloddy windows but everything seems perfect except the sound system , hmm whats wrong with this hope any one can help with this , this is dissapointing , i know there is a solution for this pls any one who know how to pls tell us .

---

### Post by eddiemcm on 2007-09-01
sounds out for me too.

---

### Post by MrDexterity on 2007-09-01
Installing Alsa 1.0.14 from source also resolved the problem for me.

```

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2
tar xvf alsa-driver-1.0.14.tar.bz2
./configure --with-oss=yes --with-cards=hda-intel
sudo make
sudo make install
sudo modprobe snd-hda-intel
/etc/init.d/alsasound restart

```

---

### Post by bahdom on 2007-09-01
worked for me too [updating alsa]

---

### Post by ubunteduser on 2007-09-01
I have no sound whereas I had it before. And I don't know if anything has changed, but I am at alsa-1.0.13.

Here are my symptoms. 1) Everything looks normal - sound cards exist. I have all controls unmuted. 2) No sound, but everything works as if does exist. I plugged a usb sound system, and it doesn't work either. 3) probs and dmesg etc show no problem.

M

Does this sound like your problem?

Ed

---

### Post by eddiemcm on 2007-09-01
[http://ubuntuforums.org/showthread.php?t=457011&highlight=aspire+5050+sound](http://ubuntuforums.org/showthread.php?t=457011&highlight=aspire+5050+sound)
this worked for me. download alsa driver, lib, util. Install lib, then driver, then util. 

Install by:
./configure
make
sudo install

Do this for each file in the order and it worked.

---

### Post by sabthagiri on 2007-09-02
Recompiling ALSA did it for me too. Thanks all.

---

### Post by p110011 on 2007-09-02
> **eddiemcm said:**
> [http://ubuntuforums.org/showthread.php?t=457011&highlight=aspire+5050+sound](http://ubuntuforums.org/showthread.php?t=457011&highlight=aspire+5050+sound)
this worked for me. download alsa driver, lib, util. Install lib, then driver, then util. 

Install by:
./configure
make
sudo install

Do this for each file in the order and it worked.

When I get to sudo install for lib I get "missing file operand"

---

### Post by imbringingsexyback on 2007-09-02
Hi! i'm having the exact same problem actually  except that I've spent the entire afternoon attempting to recompile alsa over and over again and nothing appears to be working.  I'm still getting the same error message, and my soundcard has yet to be detected.  I have no idea if it's actually a hardware problem, because i don't have windows and i can't find my brother's live cd.

i get the following output from alsaconf:

```
shaun@shaun-desktop:~$ sudo alsaconf
Password:
modinfo: could not find module snd-opl3sa2
modinfo: could not find module snd-cs4236
modinfo: could not find module snd-cs4232
modinfo: could not find module snd-cs4231
modinfo: could not find module snd-es18xx
modinfo: could not find module snd-es1688
modinfo: could not find module snd-sb16
modinfo: could not find module snd-sb8
shaun@shaun-desktop:~$ 
```

thanks!

---

### Post by tribunal on 2007-09-02
> **imbringingsexyback said:**
> Hi! i'm having the exact same problem actually  except that I've spent the entire afternoon attempting to recompile alsa over and over again and nothing appears to be working.  I'm still getting the same error message, and my soundcard has yet to be detected.  I have no idea if it's actually a hardware problem, because i don't have windows and i can't find my brother's live cd.

i get the following output from alsaconf:

```
shaun@shaun-desktop:~$ sudo alsaconf
Password:
modinfo: could not find module snd-opl3sa2
modinfo: could not find module snd-cs4236
modinfo: could not find module snd-cs4232
modinfo: could not find module snd-cs4231
modinfo: could not find module snd-es18xx
modinfo: could not find module snd-es1688
modinfo: could not find module snd-sb16
modinfo: could not find module snd-sb8
shaun@shaun-desktop:~$ 
```

thanks!

1.Is your card in ALSA sound-cards list?
2. How did you compile ALSA? (And do not forget about "sudo make install"!)
3. Look if your modules are in /lib/modules/`uname -r`/kernel/sound

---

### Post by imbringingsexyback on 2007-09-02
1.  Actually my sound card's built in haha.  Mobo is an Asus a8v-mx, and if i'm not wrong the "sound card" is VIA southbridge AC97.  like the original poster, my sound was working perfectly until i installed updates and rebooted the system.  after that no more sound card.
2.  yea i did.  in fact i did it about ten times over so I don't think i could have missed out anything... right?
```
./configure
sudo make
sudo make install

```
3.  uhm i have no idea how to check for modules actually i'm an ubuntu n00bie.  trying to learn as much as i can though!  so perhaps you could explain how:)

Thank you very much!
shaun

---

### Post by glope on 2007-09-02
I had the same problem.

Was fixed by recompiling ALSA.

as an FYI, it was after i installed the latest linux headers that the problem occurred for me so anyone tracing the problem that may or may not be useful.

---

### Post by roderikk on 2007-09-02
Exactly the same problem here. I haven't had time to recompile alsa though.

---

### Post by roderikk on 2007-09-02
BTW: When I compile from source will the new version be automatically installed when that comes available?

---

### Post by tribunal on 2007-09-02
> **roderikk said:**
> BTW: When I compile from source will the new version be automatically installed when that comes available?

New version of ALSA? No - it is disadvantage of compiling from sources

> i have no idea how to check for modules actually i'm an ubuntu n00bie. trying to learn as much as i can though! so perhaps you could explain how
ls -l /lib/modules/`uname -r`/kernel/sound
ls -l /lib/modules/`uname -r`/kernel/sound/pci (for pci-devs)
And so on

---

### Post by roderikk on 2007-09-02
> **tribunal said:**
> New version of ALSA? No - it is disadvantage of compiling from sources


ls -l /lib/modules/`uname -r`/kernel/sound
ls -l /lib/modules/`uname -r`/kernel/sound/pci (for pci-devs)
And so on
Yes, but it is quite bothersome to have no sound.

Does anyone know whether there is already a bug reported?

---

### Post by freakzilla on 2007-09-02
Sounds back for me too after recompiling latest ALSA.
Thanks

---

### Post by tribunal on 2007-09-03
> **roderikk said:**
> Yes, but it is quite bothersome to have no sound.

Does anyone know whether there is already a bug reported?

Modules are in their dir and modprobe doesn't work?
It is strange, cause modprobe is recursevly looks in /lib/modules/`uname -r`/
Try 
1. sudo depmod -a
2. if modprobe still fails, run dmesg
3 write here, what is in /etc/modprobe.conf

---

### Post by imbringingsexyback on 2007-09-03
```
shaun@shaun-desktop:~$ ls -l /lib/modules/`uname -r`/kernel/sound
total 68
drwxr-xr-x  4 root root  4096 2007-09-02 15:28 acore
drwxr-xr-x  4 root root  4096 2007-09-02 13:44 core
drwxr-xr-x  6 root root  4096 2007-09-02 13:44 drivers
drwxr-xr-x  3 root root  4096 2007-09-02 13:44 i2c
drwxr-xr-x 10 root root  4096 2007-09-02 13:44 isa
drwxr-xr-x  2 root root  4096 2007-09-02 13:44 misc
drwxr-xr-x  2 root root  4096 2007-09-01 21:15 oss
drwxr-xr-x 23 root root  4096 2007-09-02 13:44 pci
drwxr-xr-x  4 root root  4096 2007-07-29 12:26 pcmcia
drwxr-xr-x  2 root root  4096 2007-09-02 13:44 soc
-rw-r--r--  1 root root 11380 2007-08-31 09:33 soundcore.ko
-rw-r--r--  1 root root  4668 2007-08-31 09:33 sound_firmware.ko
drwxr-xr-x  3 root root  4096 2007-09-02 13:44 synth
drwxr-xr-x  3 root root  4096 2007-09-02 13:44 usb
```

my modprobe.conf is... an empty file apparently.  dmesg outputs many many lines of stuff which... all look like they don't really mean anything hahaha.

help please!
thank you so much:)
shaun

---

### Post by tribunal on 2007-09-03
> **imbringingsexyback said:**
> ```
shaun@shaun-desktop:~$ ls -l /lib/modules/`uname -r`/kernel/sound
total 68
drwxr-xr-x  4 root root  4096 2007-09-02 15:28 acore
drwxr-xr-x  4 root root  4096 2007-09-02 13:44 core
drwxr-xr-x  6 root root  4096 2007-09-02 13:44 drivers
drwxr-xr-x  3 root root  4096 2007-09-02 13:44 i2c
drwxr-xr-x 10 root root  4096 2007-09-02 13:44 isa
drwxr-xr-x  2 root root  4096 2007-09-02 13:44 misc
drwxr-xr-x  2 root root  4096 2007-09-01 21:15 oss
drwxr-xr-x 23 root root  4096 2007-09-02 13:44 pci
drwxr-xr-x  4 root root  4096 2007-07-29 12:26 pcmcia
drwxr-xr-x  2 root root  4096 2007-09-02 13:44 soc
-rw-r--r--  1 root root 11380 2007-08-31 09:33 soundcore.ko
-rw-r--r--  1 root root  4668 2007-08-31 09:33 sound_firmware.ko
drwxr-xr-x  3 root root  4096 2007-09-02 13:44 synth
drwxr-xr-x  3 root root  4096 2007-09-02 13:44 usb
```

my modprobe.conf is... an empty file apparently.  dmesg outputs many many lines of stuff which... all look like they don't really mean anything hahaha.

help please!
thank you so much:)
shaun

1. ls -l /lib/modules/`uname -r`/kernel/sound/pci && ls -l /lib/modules/`uname -r`/kernel/sound/oss
2. run sudo depmod -a
3. if modprobe fails, right after it run dmesg and look at the end of its output

---

### Post by mustali on 2007-09-03
Recompiling the alsa drivers per instructions noted above fixed the broken sound. Thanks MrDexterity!

@ roderikk, give recompiling a shot. it shouldn't take more than 5 mins.

The latest kernel update seems to have crashed the sound for a lot of people. Makes you wish the updates were tested more thoroughly before release.

I am using a Dell Inspiron laptop.

Here are the details: 

After the kernel update,  I could only see 'seq' and 'timer'. Compiling and installing ALSA added the others
```

mustali@mustali-laptop:/tmp/alsa-driver-1.0.14$ ls -l /dev/snd
total 0
crw-rw---- 1 root audio 116,  0 2007-09-03 11:05 controlC0
crw-rw---- 1 root audio 116, 24 2007-09-03 11:05 pcmC0D0c
crw-rw---- 1 root audio 116, 16 2007-09-03 11:05 pcmC0D0p
crw-rw---- 1 root audio 116, 25 2007-09-03 11:05 pcmC0D1c
crw-rw---- 1 root audio 116, 17 2007-09-03 11:05 pcmC0D1p
crw-rw---- 1 root audio 116,  1 2007-09-03 11:05 seq
crw-rw---- 1 root audio 116, 33 2007-09-03 11:05 timer

```

Earlier, I was also unable to run alsamixer or aplay:
```

mustali@mustali-laptop:~$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such device

mustali@mustali-laptop:~$ aplay -l
device_list:222: no soundcards found. ...

```

This is my lspci info:
```

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Dell Unknown device 01b5
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

After the installation, this is the ouput:
```

mustali@mustali-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Just remember to Unmute ;)

---

### Post by towanda on 2007-09-03
towanda@mymachine:~$ wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)
*lots of output*
towanda@mymachine:~$ tar xvf alsa-driver-1.0.14.tar.bz2
*lots more output*
towanda@mymachine:~$ ./configure --with-oss=yes --with-cards=hda-intel
**bash: ./configure: No such file or directory**

Also, I'm running an AMD processor, not Intel.  What am I doing wrong?

---

### Post by tribunal on 2007-09-03
> **towanda said:**
> towanda@mymachine:~$ wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)
*lots of output*
towanda@mymachine:~$ tar xvf alsa-driver-1.0.14.tar.bz2
*lots more output*
towanda@mymachine:~$ ./configure --with-oss=yes --with-cards=hda-intel
**bash: ./configure: No such file or directory**

Also, I'm running an AMD processor, not Intel.  What am I doing wrong?

You should cd to a directory, where your ALSA is.

---

### Post by towanda on 2007-09-08
I tried all the directories where I found ALSA and got the same result.

---

### Post by sfgiants16 on 2007-11-07
Hello. I am an extreme newbee to Linux in general. I just bought an HP DV6500t and Visa has been less than impressive. I'm really impressed with Ubuntu but I've not been able to resolve the sound issue, most likely due to my limited experience with Linux. If anyone can help, I'd really appreciate it. Here's what I've done so far:

I've attempted to follow the instructions at: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I downloaded the most recent alsa files: alsa-driver-1.0.9rc4a, alsa-lib-1.0.9rc4, and alsa-utils-1.0.9rc4a. I have copied them into /usr/src/alsa

I started with the driver. I believe that the ./configure command worked successfully. However, I received errors when I used the "make" command:

code:
> root@jeff-laptop:/usr/src/alsa/alsa-driver-1.0.9rc4a# make
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
gcc -D__KERNEL__ -DMODULE=1 -I/usr/src/alsa/alsa-driver-1.0.9rc4a/include  -I/lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/include/asm-i386/mach-default -O2 -mpreferred-stack-boundary=2 -march=i586 -D__SMP__ -DCONFIG_SMP -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include -DMODVERSIONS -include /lib/modules/2.6.22-14-generic/build/include/linux/modversions.h  -DKBUILD_BASENAME=hpetimer   -c -o hpetimer.o hpetimer.c
cc1: error: /lib/modules/2.6.22-14-generic/build/include/linux/modversions.h: No such file or directory
In file included from hpetimer.c:22:
/usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:29:26: error: linux/config.h: No such file or directory
In file included from /lib/modules/2.6.22-14-generic/build/include/asm/processor.h:22,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:9,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/linux/cpumask.h:88: error: ‘CONFIG_NR_CPUS’ undeclared here (not in a function)
In file included from /lib/modules/2.6.22-14-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:9,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:83: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:83: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h: In function ‘cpuid_count’:
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness
/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/gfp.h:4,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/slab.h:14,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/percpu.h:5,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/desc.h:11,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/elf.h:50,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/elf.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:15,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h: At top level:
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h:43: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h:93: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/linux/mmzone.h:305: error: requested alignment is not a constant
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:21,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/adriver.h:45,
                 from /usr/src/alsa/alsa-driver-1.0.9rc4a/include/sound/driver.h:42,
                 from hpetimer.c:22:
/lib/modules/2.6.22-14-generic/build/include/asm/module.h:64:2: error: #error unknown processor family
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/sched.h:51,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/irq.h:13,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/irq.h:23,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/pid.h:4,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/sched.h:72,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/irq.h:13,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/irq.h:23,
                 from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/linux/rcupdate.h:71: error: requested alignment is not a constant
/lib/modules/2.6.22-14-generic/build/include/linux/rcupdate.h:74: error: requested alignment is not a constant
In file included from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/linux/irq.h:176: error: requested alignment is not a constant
In file included from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,
                 from hpetimer.c:26:
/lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:12: error: requested alignment is not a constant
make[1]: *** [hpetimer.o] Error 1
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.9rc4a/acore'
make: *** [compile] Error 1


I really have no idea what I am doing or what these commands are supposed to acomplish. I am simply trying to follow the instructions. Given that, are there any steps that I can take to resolve this?

Here are the results of cat /proc/asound/card0/codec#* | grep Codec
> Codec: Realtek ID 268
Codec: Motorola Si3054


Thanks for any help you can provide.

Jeff

---

### Post by mustali on 2007-11-07
do you have the linux kernel headers installed?

if not, install it using this
```

sudo apt-get install linux-headers-2.6.22-14
```

try recompiling alsa now.

---

### Post by fideaux64 on 2007-11-23
I'm a ubuntu n00b who lost sound yesterday. Can't think of anything that triggered it, except the kids were playing some flash-based www game. 

I thrashed around these forums for a bit looking for a fix, and learned a little about alsamixer. I was about to reinstall it, but found the problem. The "PCM" in alsamixer was set to 0<>0 when it should be at 100<>100. Restoring it to 100<>100 got my sound back. I don't know what PCM is, or how it got changed, but there you go. A possible easy fix.

---

### Post by Yellow Pasque on 2007-11-23
If anyone gets tired of wrestling with ALSA, they can try OSSv4 (see my sig)

---

### Post by Unterseeboot_234 on 2007-11-24
My Gutsy lost sound after the latest system update. Never, ever had any sound issues with my onboard Nvidia graphics card sound chip being auto-detected, except the low volume.  Reinstalling Gutsy was the last thing I wanted to do. I did uninstall everything ALSA and tried to reinstall. For some reason, the repositories have not got the Alsa-Gui-mixer available. All the ALSA-driver / libs stuff was there, not the mixer-Gui.

The advice to:

```
alsamixer
```

brought up an old 8-bit software interface. Un-mute through all of those choices brought my sound back.

**[Forum link]("http://ubuntuforums.org/showthread.php?t=205449")**

I can wait for the Alsa-Gui-mixer, and I need it for later. For some reason the phase-controllers for Surround / Center channel / rear channel boost the volume and the quality.

---

### Post by Unterseeboot_234 on 2007-11-24
wished we could delete a double post. just hitting the back button on the browser duplicates an edit and makes a new post.

---

