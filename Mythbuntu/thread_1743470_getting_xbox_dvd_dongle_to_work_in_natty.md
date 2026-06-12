---
title: "getting xbox dvd dongle to work in natty"
date: 2011-04-29
forum: Mythbuntu
---

### Post by cctsurf on 2011-04-29
First of all, I'm confused why we continue to need to fight this, there are millions of  these very easily workable remotes available, why can't they be added as  an option to the numerous remotes available under the lirc remote selection menu...
I have been using the lirc_atiusb module with a little hand configuration and have been very happy with these controls.  It seems to me that the ati_remote module has replaced this--though I could be wrong. On the other hand, I note that the ati_remote module has been blacklisted in /etc/modprobe.d/blacklist.lirc (or something like that).  I don't seem to get any confirmation that it has connected with the remote when I modprobe it.
Any thoughts getting this to work?
Thanks beforehand,
cctsurf

---

### Post by cctsurf on 2011-04-29
:(I just found some further info from the lirc mailing list.  Someone asked if xbox support was going to be added to the ati_remote or atilibusb driver and Jarod answered with the following:
Probably not, it likely calls for a new driver. I'm afraid it was only
recently that I figure out the xbox remotes supported by lirc_atiusb
use an entirely different key acquisition routine from the ati remotes,
which means they don't fit very well into either of the ati_remote
drivers. In theory, we could just strip lirc_atiusb down to support
only the xbox remotes and then rename it lirc_xbox or something like
that, but if someone is going to go to that much trouble, I think its
actually a better use of time to copy, say, ati_remote.c to create a
new xbox_remote.c or similar. Patches welcome, as the saying goes,
otherwise, no clue on when I might be able to get around to it myself

I might work on it, but I wouldn't hold my breath. :(  I hope someone with better coding skillz could help out.
Thanks,
cctsurf

---

### Post by jdk82 on 2011-05-09
Hi cctsurf,

I also have an original xbox dongle that I have used for years. After much digging on various forums I found something that worked! Here's a step by step guide:

1) Black list xpad in /etc/modprobe.d/blacklist.conf
2) Install lirc-modules-source
3) edit /usr/src/lirc-0.8.7/drivers/lirc_dev/lirc_dev.h
4) change the line "#define LIRC_HAVE_KFIFO" to "#undef LIRC_HAVE_KFIFO"
5) run ```
sudo dpkg-reconfigure lirc-modules-source
```
6) reboot (the modules don't seem to take without rebooting).

Basically this stops lirc_dev from using kfifo, the API for which has changed causing lirc_atiusb to puke. If I'm reading Jarod's comments correctly, lirc_atiusb is going to be removed completely at some point in the future, and rewriting the driver or adding xbox support to one of the others is a bit above me, but this works for now (I've confirmed it works with mythtv at least).

Edit: You have to edit /etc/lirc/hardware.conf and make sure it is using lirc_dev and lirc_atiusb as the drivers. I assume you know this, but for completeness...

---

### Post by mrplow on 2011-05-09
> **jdk82 said:**
> 4) change the line "#define LIRC_HAVE_KFIFO" to "undef LIRC_HAVE_KFIFO"

I think you meant change it to "#undef LIRC_HAVE_KFIFO"

thanks a lot though, got my xbox receiver working again

---

### Post by jdk82 on 2011-05-10
I sure did, good catch. Hopefully someone integrates xbox support into the userspace drivers before to many changes occur in the kernel to kludge lirc_atiusb together.

---

### Post by cianof on 2011-05-11
I was afraid it was the end of the road for my old dongle and remote. 

Thanks to your solution they live again for another ubuntu release. Much appreciated.

---

### Post by cctsurf on 2011-05-21
I finally got to try your fix, Thank You!  :p that made my xbox remote work...  Interesting, I had installed natty previously on one of my frontends, and couldn't get it to install correctly, so I did a clean install, and all works well.
Thanks again!
cctsurf

---

### Post by overlord73978 on 2011-05-28
I was trying to follow this, but on my 11.04 system, the lirc-modules-source package contains nothing but a changelog in /usr/share/docs.

Am I missing something? Should I download the source from lirc.org?

---

### Post by AthleticTrainer on 2011-05-31
Hi guys (gals?) ...everyone :) 
I am trying to get my xbox remote working with xbmc on natty but can't figure out what is wrong. I followed various tutorials but am thouroghly confused. Which isn't surprising because i'm not good with software. However I did have my remote working with XP but was having other problems with XP so I switched to Ubuntu. I followed this thread and tried to get things working but can't. I have lirc installed, xpad blacklisted, I changed the #defined to #undef, and have switched between editing the lircd.conf and hardware.conf files and back but the remote just wont work with xbmc. Any help would be most welcome. Thank you:guitar:

Never mind I reinstalled then tried again..now it works YAY

---

### Post by cianof on 2011-10-19
Not meaning to be digging up old threads, just an addendum to this one.

For those with newer versions of Ubuntu.
 
As of Ubuntu 11.10: Oneiric Ocelot, the  lirc-modules-source are no longer available in the repositories, so this solution won't work with laters versions of ubuntu.

---

### Post by SneakerElph on 2011-10-21
Is there a way to install older versions of LIRC to make this remote work? It's the only remote I have and I'd hate to have to roll back to Natty just because I can't get my remote to work.

---

### Post by usergood on 2011-10-23
Does anyone have any idea on howto get this to work in 11.10 ?

I was reading this thread, and tried to use some of their solutions, but out of luck :(

[http://ubuntuforums.org/showthread.php?p=11323540](http://ubuntuforums.org/showthread.php?p=11323540)


I really want to get my old dongle to work again :o

---

### Post by ArmondoGates on 2011-10-24
I am also having trouble configuring lirc to work with the XboxDVDDongle.

I am using the same hardware.conf and lircd.conf files as previously used in Ubuntu 10.04

Has anyone gotten lirc and XBOX dongle to work in 11.10 yet?

[PHP]
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES="lirc_atiusb lirc_dev"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF=""
REMOTE_LIRCD_ARGS="-r"

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF="lircd.conf"

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""
[/PHP][PHP]
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

# brand: Microsoft Xbox DVD Receiever (also works with generic)
# remote control: Xbox remote or any remote using RCA DVD player codes

begin remote

name XboxDVDDongle
bits 8
eps 30
aeps 100

one 0 0
zero 0 0
gap 163983
toggle_bit_mask 0x0

begin codes
LEFT 0xA9
UP 0xA6
RIGHT 0xA8
DOWN 0xA7
SELECT 0x0B
1 0xCE
2 0xCD
3 0xCC
4 0xCB
5 0xCA
6 0xC9
7 0xC8
8 0xC7
9 0xC6
0 0xCF
MENU 0xF7
DISPLAY 0xD5
REVERSE 0xE2
FORWARD 0xE3
PLAY 0xEA
PAUSE 0xE6
STOP 0xE0
SKIP- 0xDD
SKIP+ 0xDF
TITLE 0xE5
INFO 0xC3
BACK 0xD8
end codes

end remote
[/PHP]

[PHP]
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:0809 Logitech, Inc. Webcam Pro 9000
Bus 002 Device 004: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 004 Device 002: ID 1241:f767 Belkin
Bus 004 Device 003: ID 045e:0284 Microsoft Corp. Xbox DVD Playback Kit
Bus 004 Device 004: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
[/PHP]

[PHP]
blacklist xpad
[/PHP]

irw shows no activity at all :(

---

### Post by olabri on 2011-11-01
atiusb is referenced but not in the kernel. Wonder if someone is on to this...

---

### Post by mrplow on 2011-11-02
[https://bbs.archlinux.org/viewtopic.php?id=122502](https://bbs.archlinux.org/viewtopic.php?id=122502)
this may work, I'm not home to test it until tonight though

---

### Post by cianof on 2011-11-03
Got to this point:

modprobe lirc_xbox
FATAL: Error inserting lirc_xbox (/lib/modules/3.0.0-12-generic/misc/lirc_xbox.ko): Operation not permitted


I had to the following to get to that point:

1) sudo aptitude install libtool

the ./autogen.sh failed before I did this.

2) mv /etc/modprobe.d/lirc-blacklist /etc/modprobe.d/lirc-blacklist.conf
(ubuntu requires that they file ends in .conf)

I tried uninstall the ubuntu lirc to see if that would work. No luck.

---

### Post by olabri on 2011-11-03
dmesg tells you why. 

if you had same as me; it was something along the lies of different kernel version symbols or something.

---

### Post by cianof on 2011-11-03
[COLOR=#000000][COLOR=#FF8000][COLOR=Black]
This is what I have from my dmesg:

lirc_dev: IR Remote Control driver registered, major 250 
lirc_xbox: disagrees about version of symbol lirc_register_driver
lirc_xbox: Unknown symbol lirc_register_driver (err -22)
lirc_xbox: disagrees about version of symbol lirc_register_driver
lirc_xbox: Unknown symbol lirc_register_driver (err -22)

My kernel version is Ubuntu 3.0.0-12.20-generic 3.0.4[/COLOR]
[/COLOR][/COLOR]

---

### Post by mrplow on 2011-11-03
got it going, I just compiled the xbox driver rather than all of lirc

```
sudo nano /etc/modprobe.d/blacklist.conf
```add 'blacklist xpad' without the quotes to the bottom of the file


```
sudo update-initramfs -u
sudo apt-get build-dep lirc
sudo apt-get install git dialog automake autoconf libtool
git clone git://lirc.git.sourceforge.net/gitroot/lirc/lirc
wget http://old.nabble.com/attachment/31787507/0/lirc_0.9.1_lirc_xbox_driver.patch
cd lirc/
patch -p1 <../lirc_0.9.1_lirc_xbox_driver.patch
nano drivers/lirc_xbox/lirc_xbox.c
```remove the line #include <linux/smp_lock.h>


```
./autogen.sh
./configure -with-driver=userspace
cd drivers/lirc_xbox/
make
sudo make install
sudo apt-get install lirc
```edit hardware.conf to use lirc_xbox as the remote module.


I might be missing something but I'm pretty sure thats all I did with my fresh 11.10 xubuntu install, seems to be working well. Oh ya and setting up lircd.conf but that shouldn't be any different than before.

---

### Post by cianof on 2011-11-04
Trips up for me here.

make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.

/usr/src/linux-headers-3.0.0-12-generic/kernel/bounds.c is missing from kernel source folder.

What kernel version are you using?

---

### Post by mrplow on 2011-11-04
> **cianof said:**
> What kernel version are you using?
3.0.0-12-generic
sorry, I'm not of much help but I might try on a fresh install this weekend to see if there was anything else I did.

---

### Post by mrplow on 2011-11-07
just did a fresh install of mythbuntu 11.10 and my steps in post 19 worked just as they are, did you forget to to into the drivers/lirc_xbox folder before you ran make?

---

### Post by VoltaGe23 on 2011-11-09
FYI everyone I upgraded from an 11.04 install and needed the following dependencies:

git automake libtool

Now I'm stuck on compiling:

```
cp ./../lirc_dev/Module*.symvers .
cp: cannot stat `./../lirc_dev/Module*.symvers': No such file or directory
make: [lirc_xbox.o] Error 1 (ignored)
mv Makefile Makefile.automake
cp ./../Makefile.kernel Makefile
CPPFLAGS="" CFLAGS="" LDFLAGS="" \
        make -C /lib/modules/3.0.0-12-generic/build/ SUBDIRS=/home/mediabox/lirc/drivers/lirc_xbox modules \
                KBUILD_VERBOSE=1
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-12-generic'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (                \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /home/mediabox/lirc/drivers/lirc_xbox/.tmp_versions ; rm -f /home/mediabox/lirc/drivers/lirc_xbox/.tmp_versions/*
make -f scripts/Makefile.build obj=/home/mediabox/lirc/drivers/lirc_xbox
  gcc -Wp,-MD,/home/mediabox/lirc/drivers/lirc_xbox/.lirc_xbox.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.6.1/include  -I/usr/src/linux-headers-3.0.0-12-generic/arch/x86/include -Iarch/x86/include/generated -Iinclude  -include include/generated/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -DCONFIG_AS_CFI_SECTIONS=1 -DCONFIG_AS_FXSAVEQ=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -Wno-unused-but-set-variable -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fconserve-stack -DCC_HAVE_ASM_GOTO -DEXPORT_SYMTAB -DHAVE_CONFIG_H -I. -I../.. -I/home/mediabox/lirc/drivers/lirc_xbox/. -I/home/mediabox/lirc/drivers/lirc_xbox/. -I/home/mediabox/lirc/drivers/lirc_xbox/../.. -I/home/mediabox/lirc/drivers/lirc_xbox/../.. -I/lib/modules/3.0.0-12-generic/build//include/ -I/lib/modules/3.0.0-12-generic/build//drivers/media/video/  -DMODULE  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(lirc_xbox)"  -D"KBUILD_MODNAME=KBUILD_STR(lirc_xbox)" -c -o /home/mediabox/lirc/drivers/lirc_xbox/.tmp_lirc_xbox.o /home/mediabox/lirc/drivers/lirc_xbox/lirc_xbox.c
/home/mediabox/lirc/drivers/lirc_xbox/lirc_xbox.c:51:1: error: stray â##â in program
/home/mediabox/lirc/drivers/lirc_xbox/lirc_xbox.c:51:11: error: expected â=â, â,â, â;â, âasmâ or â__attribute__â before â<â token
In file included from /usr/src/linux-headers-3.0.0-12-generic/arch/x86/include/asm/hw_irq.h:26:0,
                 from include/linux/irq.h:351,
                 from /usr/src/linux-headers-3.0.0-12-generic/arch/x86/include/asm/hardirq.h:5,
                 from include/linux/hardirq.h:7,
                 from include/linux/interrupt.h:12,
                 from include/linux/usb.h:15,
                 from /home/mediabox/lirc/drivers/lirc_xbox/lirc_xbox.c:54:
/usr/src/linux-headers-3.0.0-12-generic/arch/x86/include/asm/sections.h:8:37: error: array type has incomplete element type
make[2]: *** [/home/mediabox/lirc/drivers/lirc_xbox/lirc_xbox.o] Error 1
make[1]: *** [_module_/home/mediabox/lirc/drivers/lirc_xbox] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-12-generic'
make: *** [lirc_xbox.o] Error 2
```make oldconfig && make prepare in the kernel headers folder threw another error.  If anyone has solved this one please let me know, I'm presently googling for a solution and will post back if I figure it out.

---

### Post by olabri on 2011-11-09
> **VoltaGe23 said:**
> make oldconfig && make prepare in the kernel headers folder threw another error.  If anyone has solved this one please let me know, I'm presently googling for a solution and will post back if I figure it out.


did you do as mrplow said? That worked for me :)

---

### Post by VoltaGe23 on 2011-11-09
No, even simpler than that.

I made a stupid mistake, where the instruction said remove the line #include <linux/smp_lock.h> I foolishly added another # thinking that will comment it out.

It doesn't.

Delete the line!

---

### Post by cianof on 2011-11-24
Installed 3.0.0-13-generic

Followed mrplow's instructions and it worked!

Not sure what I wasn't doing correctly before.

I think it might have been applying the patch
"patch -p1 <../lirc_0.9.1_lirc_xbox_driver.patch"

Thanks.

---

### Post by olabri on 2011-11-25
can you please post the various conf files that you use. i got it to work, but I cannot get xbmc to recognise the keypresses.

in mode2 i get input from the remote, but not with irw.

---

### Post by jruaux on 2011-12-24
got lirc working on Xubuntu 11.10. Thanks mrplow!

---

### Post by dmm_au on 2011-12-25
Well done Mr Plough.

I followed your instructions and now have my old xbox remote working with Ubuntu 11.10

I'm new to ubuntu, but have been a long time debian user.
Something went wrong with my xbmc installation, resulting in no sound over HDMI, and the difficulties of reinstalling debian 'unstable' led me to try ubuntu.

I must say I had found the ubuntu forums coming up increasingly in my google searchs for debian related problems. 

Again, well done on documenting this simple fix in a way that most linux users could follow.

---

### Post by pumkinut on 2012-01-06
I followed mrplow's example and everything seemed to work fine.  I've modified /etc/lirc/hardware.conf and /etc/lirc/lircd.conf, but I'm not getting any response from irw and mode2 reports that no such file or directory exists for /dev/lirc.  Under /dev, I only have lircd.  I've tried rebooting multiple times, and restarting lirc.

If I perform an lsmod, lirc_xbox and lirc_dev show up.  I'm using an original MS XBox Dongle, but that doesn't show up via lsusb as it used to, I don't know if it should or not. When I look at dmesg, everything seems fine there as well.

I'm not sure what's going wrong, or where else I should look to troubleshoot further.

Edit:
Okay, I feel like a complete moron.  My receiver dongle had come a bit loose from the USB cable.  Reseating it and the cable fixed the problem....duh.

---

### Post by cctsurf on 2012-04-28
Mr. Plow's directions Work great in Precise Penguin as well!  Thanks for your continued help!
James

---

### Post by cctsurf on 2012-04-28
A further question, this method works, but for kernel updates it seems somewhat of a pain.  Don't we have to rebuild this module every time the kernel is updated?
I'm wondering if there would be a way to do this from dkms (even if it might be a bit of a hack, lacking the lirc-modules-source package.
Just a thought,
Again, thanks for this, at least I can use my remotes.
James

---

### Post by www.rzr.online.fr on 2012-05-13
Can you share your /etc/lirc/hardware.conf

there is no 

DRIVER='lirc_atiusb'

in

lircd --driver=help


Regards

-- 
[http://rzr.online.fr/q/ir](http://rzr.online.fr/q/ir)

---

### Post by wisenuts on 2012-05-17
followed this and I am stuck here

When I try to enable the module I get this

#modprobe lirc_xbox
FATAL: Error inserting lirc_xbox (/lib/modules/3.0.0-19-generic/misc/lirc_xbox.ko): Invalid argument

A quick grep of dmesg reveals this.  

dmesg | grep lirc

[   10.094366] lirc_dev: IR Remote Control driver registered, major 251
[   10.109255] lirc_xbox: disagrees about version of symbol lirc_register_driver
[   10.109260] lirc_xbox: Unknown symbol lirc_register_driver (err -22)
[   10.112312] lirc_xbox: disagrees about version of symbol lirc_register_driver
[   10.112317] lirc_xbox: Unknown symbol lirc_register_driver (err -22)
[   17.308531] lirc_xbox: disagrees about version of symbol lirc_register_driver
[   17.308537] lirc_xbox: Unknown symbol lirc_register_driver (err -22)


uname -a gives me this. 
3.0.0-19-generic #33-Ubuntu SMP Thu Apr 19 19:05:57 UTC 2012 i686 i686 i386 GNU/Linux

Where do I go from here? This is the first I've seen these types of errors

---

### Post by cctsurf on 2012-05-20
@wisenuts, I'm not sure what the problem is, I had no troubles both time I built it for my 2 mythfrontends...  I wish I could help you more...

I don't want to be a jerk, but are you certain you did everything Mr. Plow directed?  I remember this one time when I was bugging the kernel developers about a bug, and it ended up being a badly connected cable on my end (oh the shame!).

Based on my observations while I was doing this, I noticed that Mr. Plow's directions pull off of the LIRC git head (not always a consistent thing), it may be that they have adjusted something to do with this so that the head will no longer work with the version of lirc in Ubuntu 12.04...(I don't know if this is true, but it seemed a possibility)  Just a thought

@www.rzr.online.fr
Here's my hardware.conf:

[INDENT]```
:/etc/lirc$ more hardware.conf 
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES="lirc_xbox"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="xbox/lircd.conf.xbox"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"                                                                                                                       
                                                                                                                                            
#Try to load appropriate kernel modules                                                                                                     
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""

```[/INDENT]

Hope that helps!
James

---

### Post by cctsurf on 2012-05-20
I just followed these directions on an older install of 11.10, and had no problems with it.  So my statement above is obviously wrong, it does not have anything to do with the version of lirc.
James

---

### Post by wisenuts on 2012-05-21
I'm not sure if this matter but i'm using xbmcubuntu which is based on 11.10. 

I followed his steps. I've done all the stupid human tricks I can think of. Including trying a different receiver, replugging it in, using a different usb port. Seem straight forward so I guess that's where I am stuck. 

I'll try doing a fresh install(seems excessive....) but I guess for what it's worth maybe I screwed the pooch....

---

### Post by ant2ne on 2012-05-24
I'm using XMBCubuntu and this worked for me, thanks!

---

### Post by wisenuts on 2012-06-06
well, did a fresh install and followed mr plows instructions and the stars have aligned. Long live xbox dvd dongle and remote!

---

### Post by bob90 on 2012-08-04
Mr Plow's guide worked perfectly on Asus EB1501 running  XMBCubuntu.  My xbox dvd remote is alive and kicking again after upgrade to XBMC Eden ! Thanks a lot Mr Plow. Long live XBMC !

---

### Post by divingmule on 2012-09-12
Hi, I put a bash script together here -> [http://pastebin.com/ivu3XeZw](http://pastebin.com/ivu3XeZw) that when run will update/fix lirc_xbox module after kernal update.

This script assumes that you have followed mrplow's guide from post #19

Please share any code improvements :)

---

### Post by divingmule on 2012-09-12
-duplicate-

---

### Post by Pouts73 on 2012-10-25
Just followed MrPlow's instructions #19, works great on 12.04,

Thanks a bunch.:)

---

### Post by hmistry on 2013-02-14
Has anyone got this working in 12.10 (Quantal Quetzal)?

I am installing xbmcbuntu (Frodo) which is based on 12.10 and don't seem to be getting anywhere, no errors or anything useful yet.

I am going to try again from scratch just to make sure but would be good to know if someone has already done this?
Thanks

---

### Post by ReMiA on 2013-03-03
> **hmistry said:**
> Has anyone got this working in 12.10 (Quantal Quetzal)?
I am installing xbmcbuntu (Frodo) which is based on 12.10 and don't seem to be getting anywhere, 
no errors or anything useful yet.
I am going to try again from scratch just to make sure but would be good to know if someone has already done this?
Thanks

I got the same setup, followed the instructions in this topic. And all works fine :P

```
sudo nano /etc/modprobe.d/blacklist.conf
=> add line to bottem: 
*blacklist xpad*


sudo update-initramfs -u
sudo apt-get build-dep lirc
sudo apt-get install git dialog automake autoconf libtool
git clone git://lirc.git.sourceforge.net/gitroot/lirc/lirc
wget http://old.nabble.com/attachment/31787507/0/lirc_0.9.1_lirc_xbox_driver.patch
cd lirc/
patch -p1 <../lirc_0.9.1_lirc_xbox_driver.patch
nano drivers/lirc_xbox/lirc_xbox.c
=> remove the line *#include <linux/smp_lock.h>*


./autogen.sh
./configure -with-driver=userspace
cd drivers/lirc_xbox/
make
sudo make install
not needed, already installed (apt-get install lirc)


edit hardware.conf to use lirc_xbox as the remote module.
nano /etc/lirc/hardware.conf
[I]#Chosen Remote Control
REMOTE="None"
REMOTE_MODULES="lirc_xbox lirc_dev"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="xbox/lircd.conf.xbox"[/I]
*REMOTE_LIRCD_ARGS="-r"*

[I]#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""[/I]

[I]#Enable lircd
START_LIRCD="true"[/I]

[I]#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"[/I]

[I]#Try to load appropriate kernel modules
LOAD_MODULES="true"[/I]

[I]# Default configuration files for your hardware if any
LIRCMD_CONF="lircd.conf"[/I]

[I]#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="true"
START_LIRCMD=""
[/I]



```

---

### Post by jsalin on 2013-04-23
Thanks, the post #19 helped me too and the patch still worked with only slightly changed offsets. Ubuntu 11.10, which has been dist-upgraded from many years back from an initial ubuntu-server installation on a different computer. :D 
The trick still is to blacklist xpad and to have correct lircd.conf and hardware.conf, but it seems Ubuntu's lirc package doesn't come with xbox remote dongle support anymore. It seems to have been removed when the module changed from lirc_atiusb to ati_remote? But the development (GIT) version of lirc has new support in a new module lirc_xbox, so compiling just that from the sources with the guide in #19 makes it work again, lirc otherwise being from ubuntu's original binary package. I guess lirc_xbox will eventually make its way back to Ubuntu's lirc package officially, at least I hope so.

---

### Post by V-Turn on 2013-05-03
> **mrplow said:**
> got it going, I just compiled the xbox driver rather than all of lirc

[...]

I might be missing something but I'm pretty sure thats all I did with my fresh 11.10 xubuntu install, seems to be working well. Oh ya and setting up lircd.conf but that shouldn't be any different than before.
Great stuff! Worked like a charm on xubuntu 12.04. (reboot was necessay)

V.

---

### Post by bob90 on 2013-08-19
> **divingmule said:**
> Hi, I put a bash script together here -> [http://pastebin.com/ivu3XeZw](http://pastebin.com/ivu3XeZw) that when run will update/fix lirc_xbox module after kernal update.

This script assumes that you have followed mrplow's guide from post #19

Please share any code improvements :)


=> this worked for me after upgrading from v11 Eden to V12.2 of XBMC ( Frodo ).  

I ran the individual commands, not the script though the script would have worked.  Mr Plow's guide did'nt work this time on its own for some reason though it worked in V11.

I am using an Asus EB1501 with Xbox DVD Remote and IR receiver.  

Thanks to everyone who works on this ! May the force be with you all

---

### Post by jsalin on 2013-08-26
Thanks for the script, it's a really handy way to do it when kernel changes and made it swift after a dist-upgrade and remote not working. I wonder why the driver still isn't part of standard ubuntu kernel/lirc package?

---

### Post by mrplow on 2013-09-06
Wow I haven't visited this thread in a while, still pretty active. The latest 12.04.3 kernel, 3.2.0-53-generic-pae #81, broke the driver. Git pulled in the latest lirc source and its good to go again.
Divingmule, thanks for the updater script, its a bit better than the one I use but didn't share because mine was pretty ugly.
btw, sourceforge's git server has moved, git://git.code.sf.net/p/lirc/git

---

### Post by redstain on 2014-04-19
Confirmed still working for Ubuntu 14.04 
Great to have the original Xbox dvd remote working for XBMC use.

---

### Post by mrplow on 2014-05-29
Hmmmm, the newest lirc seems to have broken xbox support, even after I fixed the patch for the new offsets the module work

sudo modprobe lirc_xbox
FATAL: Error inserting lirc_xbox (/lib/modules/3.2.0-64-generic-pae/misc/lirc_xbox.ko): Invalid module format

updated patch
[http://pastebin.com/eVDkeL1M](http://pastebin.com/eVDkeL1M)


busy at work, can't look into it now

---

### Post by mrplow on 2014-05-29
sticking with the 0.9.0 branch seems to fix the issue, haven't tested beyond ubuntu 12.04 though
git clone -b "lirc-0.9.0-branch" git://git.code.sf.net/p/lirc/git lirc

---

### Post by V-Turn on 2014-06-15
> **mrplow said:**
> sticking with the 0.9.0 branch seems to fix the issue, haven't tested beyond ubuntu 12.04 though
git clone -b "lirc-0.9.0-branch" git://git.code.sf.net/p/lirc/git lirc
MrPlow, it seems we need your help again... Same thing on my side, lirc stopped working with the XBOX remote (Ubuntu 12.04)
I've tried to stick to the 0.9.0 branch as you say, but I'm not sure what you mean exactly. Should a patch be applied? Should the whole lirc be built, or only the XBOX driver? I've tried various things, but without success so far.

Thank you in advance.

V.

---

### Post by mrplow on 2014-07-04
> **V-Turn said:**
> MrPlow, it seems we need your help again... Same thing on my side, lirc stopped working with the XBOX remote (Ubuntu 12.04)
I've tried to stick to the 0.9.0 branch as you say, but I'm not sure what you mean exactly. Should a patch be applied? Should the whole lirc be built, or only the XBOX driver? I've tried various things, but without success so far.

Thank you in advance.

V.

Just follow the steps from post #19 in this thread except change the line
```
git clone git://lirc.git.sourceforge.net/gitroot/lirc/lirc
```
to
```
git clone -b "lirc-0.9.0-branch" git://git.code.sf.net/p/lirc/git lirc
```

Cheers!

---

### Post by V-Turn on 2014-07-06
> **mrplow said:**
> Just follow the steps from post #19 in this thread except change the line
```
git clone git://lirc.git.sourceforge.net/gitroot/lirc/lirc
```
to
```
git clone -b "lirc-0.9.0-branch" git://git.code.sf.net/p/lirc/git lirc
```

Cheers!
Thanks Mr Plow.
No luck :( I think that my good old xbox remote died. I went for a MCE remote and it works now.

V.

---

### Post by praest762 on 2014-07-24
I'm trying to set this up again on a new machine,but it looks like old.nabble.com is down. Is the patch available elsewhere? Or does someone have a backup of it they can post?

---

### Post by V-Turn on 2014-07-25
> **praest762 said:**
> I'm trying to set this up again on a new machine,but it looks like old.nabble.com is down. Is the patch available elsewhere? Or does someone have a backup of it they can post?
Just google the patch name (lirc_0.9.1_lirc_xbox_driver.patch), you can find it : 

**[http://svn.stmlabs.com/filedetails.php?repname=raspbmc&path=%2Fpatches%2Flirc%2Flirc_0.9.1_lirc_xbox_driver.patch&rev=1677&peg=1677](http://svn.stmlabs.com/filedetails.php?repname=raspbmc&path=%2Fpatches%2Flirc%2Flirc_0.9.1_lirc_xbox_driver.patch&rev=1677&peg=1677)** for example

V.

---

### Post by praest762 on 2014-08-09
> **V-Turn said:**
> Just google the patch name (lirc_0.9.1_lirc_xbox_driver.patch), you can find it : 

**[http://svn.stmlabs.com/filedetails.php?repname=raspbmc&path=%2Fpatches%2Flirc%2Flirc_0.9.1_lirc_xbox_driver.patch&rev=1677&peg=1677](http://svn.stmlabs.com/filedetails.php?repname=raspbmc&path=%2Fpatches%2Flirc%2Flirc_0.9.1_lirc_xbox_driver.patch&rev=1677&peg=1677)** for example

V.

Something's not right. This is what I'm getting.

```
patching file configure.ac
Hunk #1 FAILED at 172.
Hunk #2 FAILED at 446.
Hunk #3 FAILED at 611.
Hunk #4 succeeded at 493 with fuzz 2 (offset -915 lines).
Hunk #5 FAILED at 1518.
Hunk #6 FAILED at 1783.
5 out of 6 hunks FAILED -- saving rejects to file configure.ac.rej
patching file drivers/lirc_xbox/Makefile.am
patching file drivers/lirc_xbox/lirc_xbox.c
patching file remotes/xbox/lircd.conf.xbox
can't find file to patch at input line 1148
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/setup.data b/setup.data
|index 407d6b2..e9e9ee0 100644
|--- a/setup.data
|+++ b/setup.data
--------------------------
File to patch: 

```

---

### Post by redstain on 2014-08-21
> **mrplow said:**
> sticking with the 0.9.0 branch seems to fix the issue, haven't tested beyond ubuntu 12.04 though
git clone -b "lirc-0.9.0-branch" git://git.code.sf.net/p/lirc/git lirc

Tried this on 14.04 with kernel 3.16.0-031600-generic

```
Aug 22 11:38:26 xbmc kernel: [278070.892311] lirc_xbox: disagrees about version of symbol lirc_register_driver
Aug 22 11:38:26 xbmc kernel: [278070.892315] lirc_xbox: Unknown symbol lirc_register_driver (err -22)
```


Looks like the good run is over for now. I miss my xbox remote.

---

### Post by redstain on 2014-11-13
several weeks ago i managed to include the lirc_xbox patch into the V4L media driver bundle following the instructions in README.patches section 7.1 for simple drivers.


```
dmesg | grep lir
[ 8.644259] lirc_dev: IR Remote Control driver registered, major 249
[ 8.644682] lirc_xbox: XBOX DVD Dongle USB remote driver for LIRC $Revision: 0.01 $
[ 8.644684] lirc_xbox: Jason Martin <austinspartan@users.sourceforge.net>
[ 8.645806] lirc_xbox 3-2:1.0: lirc_dev: driver lirc_xbox registered at minor = 0
[ 8.645808] lirc_xbox[2]: on usb3:2
[ 8.645831] usbcore: registered new interface driver lirc_xbox
[ 11.547882] rc rc0: lirc_dev: driver ir-lirc-codec (cx23885) registered at minor = 1

```


So the lirc_xbox driver now loads without complaining about symbol mismatch.


copied
lirx_xbox.c
kcompat.h
lirc.h


to media_build-bst-14/linux/drivers/media/rc

Source code
[http://www.dvbsky.net/download/linux/media_build-bst-14-141106.tar.gz](http://www.dvbsky.net/download/linux/media_build-bst-14-141106.tar.gz)


edit lirc_xbox.c


```

-#include "drivers/kcompat.h"
+#include "kcompat.h"

```




edit Kconfig


```

config LIRC_XBOX
        tristate "LIRC interface driver"
        depends on RC_CORE
        depends on LIRC


        ---help---
           Xbox DVD Dongle

```




edit Makefile


```

obj-$(CONFIG_LIRC_XBOX) += lirc_xbox.o

```


The driver compiles but some warnings are generated. This will need to be cleaned up before submitting to v4l.
```

  CC [M]  /home/xbmc/zzz/media_build-bst-14/v4l/lirc_xbox.o
In file included from include/linux/module.h:17:0,
                 from /home/xbmc/zzz/media_build-bst-14/v4l/lirc_xbox.c:49:
/home/xbmc/zzz/media_build-bst-14/v4l/lirc_xbox.c: In function '__check_debug':
include/linux/moduleparam.h:347:61: warning: return from incompatible pointer type [enabled by default]
  static inline type __always_unused *__check_##name(void) { return(p); }
                                                             ^
include/linux/moduleparam.h:393:35: note: in expansion of macro '__param_check'
 #define param_check_bool(name, p) __param_check(name, p, bool)
                                   ^
include/linux/moduleparam.h:127:2: note: in expansion of macro 'param_check_bool'
  param_check_##type(name, &(value));       \
  ^
include/linux/moduleparam.h:113:2: note: in expansion of macro 'module_param_named'
  module_param_named(name, name, type, perm)
  ^
/home/xbmc/zzz/media_build-bst-14/v4l/lirc_xbox.c:982:1: note: in expansion of macro 'module_param'
 module_param(debug, bool, S_IRUGO | S_IWUSR);
 ^
/home/xbmc/zzz/media_build-bst-14/v4l/lirc_xbox.c: In function '__check_unique':
include/linux/moduleparam.h:347:61: warning: return from incompatible pointer type [enabled by default]
  static inline type __always_unused *__check_##name(void) { return(p); }
                                                             ^
include/linux/moduleparam.h:393:35: note: in expansion of macro '__param_check'
 #define param_check_bool(name, p) __param_check(name, p, bool)
                                   ^
include/linux/moduleparam.h:127:2: note: in expansion of macro 'param_check_bool'
  param_check_##type(name, &(value));       \
  ^
include/linux/moduleparam.h:113:2: note: in expansion of macro 'module_param_named'
  module_param_named(name, name, type, perm)
  ^
/home/xbmc/zzz/media_build-bst-14/v4l/lirc_xbox.c:988:1: note: in expansion of macro 'module_param'
 module_param(unique, bool, S_IRUGO | S_IWUSR);
 ^

```

when i remove the module and insert it with debug=1 more info is displayed.

```
[48132.191630] usbcore: deregistering interface driver lirc_xbox
[48132.191813] lirc_xbox[2]: usb remote disconnected
[48155.797663]
[48155.797663] lirc_xbox: XBOX DVD Dongle USB remote driver for LIRC $Revision: 0.01 $
[48155.797666] lirc_xbox: Jason Martin <austinspartan@users.sourceforge.net>
[48155.797667] lirc_xbox: debug mode enabled: $Id: lirc_xbox.c,v 1.88 2011/06/05 11:11:11 jmartin Exp $
[48155.797682] lirc_xbox[2]: usb_remote_probe: dev:ffff88020da41800, intf:ffff8800c63f6400, id:ffffffffc0703120)
[48155.797683] lirc_xbox[2]: scanning remote_list...
[48155.797684] lirc_xbox[2]: remote type = XBOX DVD Dongle
[48155.797684] lirc_xbox[2]: adding remote to list
[48155.797685] lirc_xbox[2]: processing endpoint 0
[48155.797686] lirc_xbox[2]: acceptable inbound endpoint (0x81) found (maxp=8 len=6)
[48155.797688] lirc_xbox[2]: adding ep=0x81 to list
[48155.797734] lirc_xbox 3-2:1.0: lirc_dev: driver lirc_xbox  registered at minor = 0
[48155.797736] lirc_xbox[2]:  on usb3:2
[48155.797754] lirc_xbox[2]: usb_remote_probe: dev:ffff88020da41800, intf:ffff8800c63f6800, id:ffffffffc0703120)
[48155.797755] lirc_xbox[2]: scanning remote_list...
[48155.797756] lirc_xbox[2]: prior instance found.
[48155.797782] usbcore: registered new interface driver lirc_xbox

```

a new lirc device is created in /dev
/dev/lirc0

I have not been able to get any data from the remote, It looks like i am missing something...

lsmod
```
lirc_xbox              17827  0
lirc_dev               19980  2 ir_lirc_codec,lirc_xbox


```
If i can get this working ill submit a patch to v4l and get the dongle included in their driver bundle so it may live on for those of us that like the remote.

---

