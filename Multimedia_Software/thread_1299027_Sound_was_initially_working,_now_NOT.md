---
title: "Sound was initially working, now NOT"
date: 2009-10-23
forum: Multimedia Software
---

### Post by pgar23 on 2009-10-23
I am working in Ubuntu Jaunty. I have a Toshiba Satellite M305-s4848 which is a 64bit machine. I have been using Jaunty for about a month or so now, but have been using Ubuntu for about two years. The sound on my laptop had initially been working fine. Then I went to watch a movie last night that I downloaded and the sound is working i think because it gives a low hiss like when you hold your cell phone to a radio, but there are no distinctive audible sounds like voices or music.
This problem suddenly occured, i have not installed any new hardware nor software...especially concerning any audio devices. Any help is appreciated.

Also I am including the outout of lshw:

```
 *-multimedia
             description: Audio device
             product: 82801I (ICH9 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

---

### Post by pgar23 on 2009-10-24
BUMP! Please someone help me fix my sound issue.

---

### Post by pgar23 on 2009-10-25
Following this tutorial:

[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

EDIT: Checking in the /usr/src/alsa/alsa-driver-1.0.21/alsa-kernel folder, it says that the link between the ../alsa-kmirror and alsa-kernel is a broken link. How do i fix this broken link??

I got up to the point of "sudo make" of compile and install alsa-driver until I receive the error:
```
python@home:/usr/src/alsa$ sudo tar xjf alsa-lib*
python@home:/usr/src/alsa$ sudo tar xjf alsa-utils*
python@home:/usr/src/alsa$ cd alsa-driver*
python@home:/usr/src/alsa/alsa-driver-1.0.21$ sudo ./configure
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
configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."
python@home:/usr/src/alsa/alsa-driver-1.0.21$ sudo make
make all-deps
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.21'
ln -sf ../alsa-kmirror alsa-kernel
ln -sf alsa-kernel sound
make[1]: *** No rule to make target `utils/mod-deps.c', needed by `utils/mod-deps'.  Stop.
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.21'
make: *** [dummy1] Error 2
python@home:/usr/src/alsa/alsa-driver-1.0.21$ sudo make install
if [ -L /include/sound ]; then \
		rm -f /include/sound; \
		ln -sf /usr/src/alsa/alsa-driver-1.0.21/include/sound /include/sound; \
	else \
		rm -rf /include/sound; \
		install -d -m 755 -g root -o root /include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /include/sound; \
		done \
	fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1
python@home:/usr/src/alsa/alsa-driver-1.0.21$ cd ../alsa-utils*
python@home:/usr/src/alsa/alsa-utils-1.0.21$ sudo ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for cross-compiler... gcc
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking for ALSA CFLAGS... 
checking for ALSA LDFLAGS...  -lasound -lm -ldl -lpthread
checking for libasound headers version >= 1.0.16... not present.
configure: error: Sufficiently new version of libasound not found.
python@home:/usr/src/alsa/alsa-utils-1.0.21$ sudo make
make: *** No targets specified and no makefile found.  Stop.

```

---

### Post by Raff1 on 2009-10-25
I just ran through the guide you are following without any problems not covered by the guide. It solved all my sound issues, so now I get the login-sound, youtube sound, sound in totem and in wine. 

> configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."

I dunno whats wrong, but I guess thats why you cant run the subsequent make and make install. So you must at least sort out the install-sh/install.in thing. A quick google search for the error took me here:
[http://www.linuxquestions.org/questions/debian-26/configure-error-cannot-find-install-sh-or-install.sh-in-.-...-.....-364870/](http://www.linuxquestions.org/questions/debian-26/configure-error-cannot-find-install-sh-or-install.sh-in-.-...-.....-364870/)

I hope that helps.

Raff1

---

### Post by AutoStatic on 2009-10-25
> **pgar23 said:**
> Following this tutorial:

[http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)

EDIT: Checking in the /usr/src/alsa/alsa-driver-1.0.21/alsa-kernel folder, it says that the link between the ../alsa-kmirror and alsa-kernel is a broken link. How do i fix this broken link??Your sound used to work with 9.04? Then don't upgrade Alsa, the problem is not Alsa related. Does your sound work with another account? If you don't have an extra account could you create one and test if your sound works there?

---

### Post by pgar23 on 2009-10-25
@ Autostatic:
I already removed all alsa-related files, so now it is a must that I upgrade and re-install alsa, otherwise absolutely no sound will work on the system. I double checked in the /usr/src/alsa/alsa-driver-1.0.21/ folder and there is a INSTALL file located in there.

---

### Post by Raff1 on 2009-10-25
> **AutoStatic said:**
> Your sound used to work with 9.04? Then don't upgrade Alsa, the problem is not Alsa related. Does your sound work with another account? If you don't have an extra account could you create one and test if your sound works there?

You sure? My sound stopped working at some point and following this guide made things work again. I really cant say what went wrong, but upgrading Alsa certainly fixed it.

Raff1

---

### Post by AutoStatic on 2009-10-26
Yes I'm sure.
Sound doesn't stop working all of a sudden. Then it's either an update that made it stop working or a configuration issue. You should verify that first before doing something thorough like upgrading Alsa.
On the other hand, it worked for you :)

@pgar23, I think it's best to reinstall Alsa with Synaptic or to use a PPA that provides newer Alsa drivers.

---

### Post by Raff1 on 2009-10-27
> **AutoStatic said:**
> Yes I'm sure.
Sound doesn't stop working all of a sudden. Then it's either an update that made it stop working or a configuration issue. You should verify that first before doing something thorough like upgrading Alsa.
On the other hand, it worked for you :)


I guess upgrading Alsa effectively set my configurations right again then. And yes, it worked, so I'm happy!:D

---

### Post by pgar23 on 2009-10-27
I tried installing Alsa from synaptic yesterday and it installed all packages with ease. But when I restarted my computer, the X system was not working (aka I could not see my GUI)..I used my hotkeys to open a terminal, and that worked. But after installing Alsa, it takes me to a blank desktop which is a black screen. Rendering my computer useless for the moment until I learn how to restore a snapshot of my system using back-in-time backup utility. DOES ANYONE HAVE SOLUTION FOR SOUND PROBLEMS>>>??? This is frustrating and no one is offer help.

---

### Post by pgar23 on 2009-10-27
Bump.

---

### Post by AutoStatic on 2009-10-28
> **pgar23 said:**
> I tried installing Alsa from synaptic yesterday and it installed all packages with ease. But when I restarted my computer, the X system was not working (aka I could not see my GUI)..I used my hotkeys to open a terminal, and that worked. But after installing Alsa, it takes me to a blank desktop which is a black screen. Rendering my computer useless for the moment until I learn how to restore a snapshot of my system using back-in-time backup utility. DOES ANYONE HAVE SOLUTION FOR SOUND PROBLEMS>>>??? This is frustrating and no one is offer help.
While I understand your frustration I did offer my help:
> Does your sound work with another account? If you don't have an extra account could you create one and test if your sound works there?
But instead of answering that question you removed Alsa completely!
> @ Autostatic:
I already removed all alsa-related files, so now it is a must that I upgrade and re-install alsa, otherwise absolutely no sound will work on the system. I double checked in the /usr/src/alsa/alsa-driver-1.0.21/ folder and there is a INSTALL file located in there.
Apparently this crippled your system and even a reinstall of all Alsa related packages didn't help. So instead of a simple sound problem, I'd love to help out there, it has become a system wide problem which is beyond my reach. So I fear I can't help you out any further, sorry about that.

---

### Post by pgar23 on 2009-10-28
@Autostatic:
> But instead of answering that question you removed Alsa completely!
First and foremost, thank you for the support and trying to help, although your suggestion was a good suggestion, I had deleted alsa files and tried to follow the tutorial prior to you suggesting anything, secondly..if creating another user account and testing the sound in that proile were to fix the problem, it would probably be temporary but would I still have all files and folders that I had in my previous account? probably not right..?

---

### Post by pgar23 on 2009-11-01
So, after much research...apparently if you remove the alsa files and then try to re-install and reconfigure alsa it will not work anyways. I ended up backing up my files and folders and just re-installing Ubuntu.

---

