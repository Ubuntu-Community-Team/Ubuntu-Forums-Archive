---
title: "X-Meridian, ALSA, OSS and What do I do?"
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by Anaximander Thales on 2007-01-21
So, decided to upgrade to a 64-bit processor, and after reading tons of complaints about Creative not having linux drivers and having issues with popping, hissing and crackling when mated with several NForce 4 mb's (mine was one) -- I decided to go with the Auzentech X-Meridian 7.1 sound card.

Manufacturer site says that the card is linux compatible because ALSA has Cmedia 8338, 8738 and 8768 drivers.  What they don't mention is that ALSA hasn't gotten around to get the cmi8788's drivers set up yet.

So, no sound from ALSA, and the card can't even be seen (I attempted to re-install the necessary alsa packages, as well as compile from the latest ALSA sources -- even verified through there website - the CMI8788 is not supported yet).

In my searches, I came across the fact that OSS supports the card.

So, OSS is installed -- ALSA can't see the card -- sound works.

My problem is -- what the hell do I do now?  Only ever having used ALSA, and being relatively new to this, I have no idea what to expect from this and how to make the best situation out of this.  My biggest concern right now is ensuring that 5.1 is up and running correctly, I'll have to find something that takes advantage of that and test it out (A DVD should do the trick).

I can't even find a decent gui mixer (though I do have the man pages) for OSS right now (certainly not in the repos).

So, suggestions?

---

### Post by Anaximander Thales on 2007-01-21
Any ideas -- can I get ALSA to work with this set-up?

Or do I just wait until ALSA supports it?

---

### Post by pb186 on 2007-02-02
blugears has a linux driver release that supports the cmi8788.  This is not without it's problems.  For one, you have to compile the drivers yourself with the outdated version of alsa they included it with... another problem is that it does not automatically *at least in my experience* upmix to 48000hz so all the sound will be a bit higher pitched then normal... this can be fixed by setting up the mixer to upmix all the sound to 48000... lol basically... you're best off waiting for official alsa support

---

### Post by Anaximander Thales on 2007-02-03
Thanks for the information -- 
At this point, as long as Edgy sound is through Alsa with out breaking, I'll be happy.

---

### Post by Allegheny on 2007-02-03
I've got the same problem.  

I installed the OSS drivers and sound works great through applications & games - however no desktop sounds.

As you stated the system does not see the card, so I assume Gnome or KDE just don't know what to do.

OSS has a mixer which can be lauched from the command prompt.  But, it only affects sounds in programs, like games.

With this setup I simply have no system sounds - which I really miss!!

I am still looking for a way to tell the system to use OSS for everything.

---

### Post by pseudonym on 2007-02-03
> **Anaximander Thales said:**
> In my searches, I came across the fact that OSS supports the card.

So, OSS is installed -- ALSA can't see the card -- sound works.

My problem is -- what the hell do I do now?  Only ever having used ALSA, and being relatively new to this, I have no idea what to expect from this and how to make the best situation out of this.  My biggest concern right now is ensuring that 5.1 is up and running correctly, I'll have to find something that takes advantage of that and test it out (A DVD should do the trick).

I can't even find a decent gui mixer (though I do have the man pages) for OSS right now (certainly not in the repos).

So, suggestions?
So you installed the drivers from [Opensound]("In my searches, I came across the fact that OSS supports the card."), right? The mixer that comes with those drivers is 'ossxmix' which as mentioned you launch from the commandline (or just create a panel launcher for it). You save the settings with 'savemixer' (which may need sudo, I can't remember).

I think 4 Front have started to develop a virtual mixer system which works like ALSA's dmix plugin - ie. enables more than one app to use the soundcard at the same time. I never got it to work properly with my onboard Realtek HD audio, but I quickly switched back to ALSA anyway when I bought my X-Mystique soundcard.

But you might have better luck. There should be documentation that came with the drivers, or at the Opensound website.

---

### Post by pseudonym on 2007-02-03
> **Allegheny said:**
> With this setup I simply have no system sounds - which I really miss!!

I am still looking for a way to tell the system to use OSS for everything.
btw, If you do try the Opensound virtual mixer you should be able to get GNOME sounds working by using steps 6 & 7 of [this guide]("http://www.ubuntuforums.org/showthread.php?t=253725"). I used to have the sound hardware mentioned in that howto, but I never tried the GNOME sounds tweak. Looks simple enough, though.

---

### Post by pb186 on 2007-06-25
It's worth noting that the cmi8788 code from the alsa driver supplied by blue gears finally made it into the cvs source code for the alsa-project.  So we may see cmi8788  support with the next release.

---

### Post by Anaximander Thales on 2007-06-25
Where did you see this in the Alsa site?  I subscribed to the bugtrack system.  There was an issue that talks about blue gears, and I've posted a reply in a seperate ticket that says I'd be happy to upload the blue gears version (which is Alsa 1.0.11)

---

### Post by pb186 on 2007-06-25
[https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=SourceCodeRepository](https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=SourceCodeRepository)
it was added into the repository about 10 days ago.

here's how you can grab the latest code... it still suffers the same flaws as the bluegears drivers with having to resample the sound...

here's my .asoundrc that I use to solve this problem:



## see next post for better .asoundrc settings

to use this you need to run: aoss *command* to get the sound working properly otherwise it will be rediculously high pitched.  

basically.. the oss driver by opensound is vastly superior atm.  Little work was done to the alsa drivers from then to now.  btw the oss driver is now open source as well so we may see some of the progress they made with that move over to the alsa code base *pure baseless speculation mind you*.

so yeah... if this helps you in anyway... enjoy

---

### Post by pb186 on 2007-06-25
mind you that .asoundrc is not very good... I'm just slapping things together as it is...

pcm.!default {
   type plug
   slave.pcm "dmixer"
}

pcm.dmixer  {
   type dmix
   ipc_key 1024
   slave {
      pcm "hw:0,0"
      format S32_LE
   }
   bindings {
      0 0
      1 1
   }
}

ctl.dmixer {
   type hw
   card 0
   device 0
}
pcm.dsp {
    type plug
    slave.pcm "dmixer"     # use our new PCM here
}
ctl.mixer {
    type hw
    card 0
}


this one's a bit better as it does all sound without the aoss before hand... working on 6 channel atm...

---

### Post by GG_HTPC on 2007-07-04
Can you please post the steps you have taken for installing OSS drivers?

I am absolutely new to Ubuntu and was thrilled to know that OSS works with Meridian 7.1

Thank you in advance.

---

### Post by Anaximander Thales on 2007-07-04
Sure -- 
The nice thing, is 4Front produced a .deb file that makes it easy to install.

You can download the latest here: [http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)

Then, open a terminal.

Type in:
```
sudo gdebi </path/filename for oss driver>
```

or type in:
```
sudo dpkg --install </path/filename for oss driver>
```

I know gdebi worked for me -- and I think that's all you need to do for dpkg.

Make sure that you get the deb packages because there will be rpm and source files available in the list also.  There will be a seperate file for amd64, and you may need to get the older version, depending on your kernel and installed files.

---

### Post by GG_HTPC on 2007-07-06
I tried installing the OSS drivers using the tar files (guess I was impatient and did not wait for your response:)

In OSSCTL, Self Test (and OSSTEST) I get stero sound on one of the devices /dev/cmi87880/pcm1 but no sound under any application. Even if I try ossplay -d with all devices (/dev/dsp, /dev/dsp0 etc) nothing!:(

Any pointers?

Thank you, again. I will try installing the .deb version later this weekend.

---

### Post by Anaximander Thales on 2007-07-06
Eh -- don't worry about being impatient.  The only way to learn to do anything in this world is to do it.  You mess-up, you ask questions, you learn.

Alright -- well, looking at my set-up.  This is what I would do, and I tend to assume to the lesser degree, so forgive me if I put in info you're already aware of.

I have symbolic links under /dev for dsp0 and dsp1 -- those link to /dev/oss/cmi87880/pcm0 & pcm1 respectively.  So, first I would check to make sure that you have symbolic links.  If you see the /dev/dsp0 & /dev/dsp1, they should show where they are linked.

You can check the properties of dsp* through your file manager, or can capture the output from an ls -la
command (in a terminal):
cd /dev
ls -la > ~/capture_dev_long_filenames

The ls -la will give a long listing of your filenames, and we've redirected it's output to a file in your home folder.   Now, you can open the file in your favorite text editor and see ALL the entries.  The entry for my /dev/dsp0 looks like this:
lrwxrwxrwx  1 root root          22 2007-07-02 00:07 dsp0 -> /dev/oss/cmi87880/pcm0

So, on mine I have two -- dsp0 & dsp1.  If you don't see these in your dev, then we should create them.

to create the link (in a terminal):
cd /dev
sudo ln -s /dev/<pathtocmi87880>/pcm0 dsp0  (repeat for pcm1 -> dsp1 -- if needed)

I'm betting (well, hoping actually) that you don't have the dsp* entries -- or if you do, they aren't linked with the device.  If you see dsp0, and check it's properties and it isn't pointing to the 8788 pcm* file, then I would delete dsp* and create the links.  I believe that most programs that use OSS will look for /dev/dsp0 -- so, that could be the cause of your problems.

---

### Post by GG_HTPC on 2007-07-09
I checked for the links as per your instructions. The links are there and they point to the right devices in OSS directry. But for some reason my SPDIF device does not show up under the OSSCTL output device list :confused: 

I have posted the query on 4front-tech website as well. Any pointers?

Thank you

---

### Post by Keith.Anyan on 2007-11-29
> **Anaximander Thales said:**
> Sure -- 
The nice thing, is 4Front produced a .deb file that makes it easy to install.

You can download the latest here: [http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)

Then, open a terminal.

Type in:
```
sudo gdebi </path/filename for oss driver>
```

or type in:
```
sudo dpkg --install </path/filename for oss driver>
```

I know gdebi worked for me -- and I think that's all you need to do for dpkg.

Make sure that you get the deb packages because there will be rpm and source files available in the list also.  There will be a seperate file for amd64, and you may need to get the older version, depending on your kernel and installed files.

tried to install that and got this

Preparing to replace oss-linux v4.0-1008 (using /home/Keith/Desktop/oss-linux_v4.0-1009_i386.deb) ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
sh: Can't open /usr/lib/oss/scripts/restore_drv.sh
dpkg: error processing /home/Keith/Desktop/oss-linux_v4.0-1009_i386.deb (--install):
subprocess new pre-removal script returned error exit status 2
Building OSS Modules for Linux-unknown 2.6.22-14-generic
cd: 3: can't cd to /usr/lib/oss/build
sh: Can't open install.sh
Starting Open Sound System
/usr/sbin/soundon: 27: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
cat: /usr/lib/oss/version.dat: No such file or directory
/usr/sbin/soundon: 28: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 30: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 32: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 38: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
/usr/sbin/soundon: 45: cannot create /usr/lib/oss/logs/soundon.log: Directory nonexistent
No /usr/lib/oss/etc/installed_drivers - cannot continue
Errors were encountered while processing:
/home/Keith/Desktop/oss-linux_v4.0-1009_i386.deb

How do I fix this problem?

---

### Post by Anaximander Thales on 2007-11-29
I had to search 4Front's forums to get this --

[quote="4Front Forum Post one ([Recovering from failed .deb installation]('http://4front-tech.com/forum/viewtopic.php?t=2054'))"]

On Ubuntu or Debian, if you don't have the necessary packages listed in the "Installing on Ubuntu 6.10" notes then OSS will likely fail to install and
you will need to do the following to recover:

1) cd /var/lib/dpkg/info
2) rm oss-linux*
3) edit /var/lib/dpkg/status and look for oss-linux
and delete the entire section that looks like:

Package: oss-linux
Status: install ok installed
Priority: extra
Section: alien
Installed-Size: 8440
Maintainer: root <root@dev-desktop>
Architecture: [your architecture]
Version: [version downloaded]
Depends: libatk1.0-0 (>= 1.12.1), libc6 (>= 2.4-1), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.3.0), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.10.3), libpango1.0-0 (>= 1.14.5), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1
Conffiles:
/etc/oss.conf 055432d38aaf37fc6de3dba4a95accc3
Description: Open Sound System sound drivers for Linux
Open Sound System for Linux (OSS/Linux) is a commercial quality sound driver
distributed by 4Front Technologies ([http://www.opensound.com](http://www.opensound.com)). OSS provides
support for practically all sound cards on the market including PnP and
many PCI ones. Installation and configuration is higly automated and easy to
perform. To obtain technical support and additional features, you will need to
order a license key from [http://www.opensound.com/order.html](http://www.opensound.com/order.html)
.
(Converted from a rpm package by alien version 8.64.)



5) Now you should be able to run dpkg --purge oss-linux and it should
say: dpkg - warning: ignoring request to remove oss-linux which isn't installed.
[/quote]

Near exact -- Your will look similar to that, the Dependencies and Conffiles will probably be slightly different since this was first created for v4.0 rc9 of the OSS package.

Once you have that done, here is a complete list of everything you should make sure to have and do to get OSS working correctly on Ubuntu
[quote="4Front Forum Post two ([Installing OSS on Ubuntu 6.10 (Edgy)]('http://www.4front-tech.com/forum/viewtopic.php?t=1438'))"]

You first need to install the compiling environment and kernel sources
so type these:

a) sudo apt-get install gcc
b) sudo apt-get install make
c) sudo apt-get install binutils
d) sudo apt-get install linux-headers-`uname -r`
e) sudo apt-get install build-essential
f) cd /usr/src/linux-headers-`uname -r`
g) sudo make prepare
h) sudo make prepare scripts

Now download the .DEB version of OSS v4.0 from our website and type:

sudo dpkg -i oss-linux*.deb

You should now have OSS installed and good to go.

[/quote]

---

### Post by Keith.Anyan on 2007-11-29
Can't remove those files

rm: remove write-protected regular file `oss-linux.conffiles'? y
rm: cannot remove `oss-linux.conffiles': Permission denied
rm: remove write-protected regular file `oss-linux.list'? y
rm: cannot remove `oss-linux.list': Permission denied
rm: remove write-protected regular file `oss-linux.md5sums'? y
rm: cannot remove `oss-linux.md5sums': Permission denied
rm: remove write-protected regular file `oss-linux.postinst'? y
rm: cannot remove `oss-linux.postinst': Permission denied
rm: remove write-protected regular file `oss-linux.postrm'? y
rm: cannot remove `oss-linux.postrm': Permission denied
rm: remove write-protected regular file `oss-linux.prerm'?
rm: remove write-protected regular file `oss-linux.shlibs'? y
rm: cannot remove `oss-linux.shlibs': Permission denied

I'm the admin I have no idea why I can't remove these files.

---

### Post by Anaximander Thales on 2007-11-29
I'm not sure of your acumen in Linux, so no offence if you all ready know this:

Ubuntu upon initial installation has no ability to log in as root, and the user account is just that -- a user.  To install anything as a user, you need to have root permission.  To get root permissions on the command line, you need to use "sudo <command>".   When you go through Synaptic or any of the other package managers, you'll be asked to enter a password -- this is giving you the root permission to install the package.

When you tried to remove the files, it asked if you'd like to remove write-protected files, and then errored with permission denied.  This indicates that you don't have appropriate permissions to do this.

You say that you're the admin -- this indicates to me that you mean you are logged in as root.  If you logged in as root, you have serious permission problems.  By this, I mean for some reason, root has lost the ability to read, write and possibly execute on the system wide folders or just perhaps the /location/of/oss/files.  Either way, you'll need sort out those permission problems first.

However, what I really think you mean is this:  I'm the only user on this computer, or I'm the primary user of this computer and ensure that it's maintained and healthy, which probably means that you log in on the account you created at the initial set-up -- and I believe they label it as administrator, but I can't remember.  Permission problems would occur if you simply attempted to rm the oss files as the user is not giving permission to write or execute on those folders.  This is where the sudo command comes in "sudo rm oss-linux.conffiles" should remove it without problems.

So, with that said, are you logging in as root and running these commands?  Are you prepending sudo in front of the commands?  What are the permissions on the oss folder that you are trying to use (ls -la will give detailed information).

---

### Post by Yellow Pasque on 2007-11-29
Perhaps because they're currently in use? Have you tried booting to a failsafe terminal and issuing the soundoff command?

---

### Post by Keith.Anyan on 2007-12-01
I was able to remove the files
but when i got to the scripting part it failed
f) cd /usr/src/linux-headers-`uname -r`
g) sudo make prepare
h) sudo make prepare scripts

Btw, this is my first time using linux, I would appreciate it if you didn't skip any steps, I'm on the latest kubuntu 7.10.

---

### Post by Merc248 on 2007-12-03
Hey, just to let you guys know, there's beta drivers for the CMI8788 chipset that have been rewritten and are supposedly working great.  Look here:

[http://www.alsa-project.org/main/index.php/User:ClemensLadisch](http://www.alsa-project.org/main/index.php/User:ClemensLadisch)

---

### Post by Anaximander Thales on 2007-12-03
> **Keith.Anyan said:**
> I was able to remove the files
but when i got to the scripting part it failed
f) cd /usr/src/linux-headers-`uname -r`
g) sudo make prepare
h) sudo make prepare scripts

Btw, this is my first time using linux, I would appreciate it if you didn't skip any steps, I'm on the latest kubuntu 7.10.
Can you post what kind of errors you're getting, and which specific command you're running when it errors?

I believe you can capture what is going on by using something like this: sudo command 2> ~/command.txt

so, for step (g), it would look like this:
sudo make prepare 2> ~/make.prepare.txt

Just to let you know what I'm doing with 2> ~/somename.txt portion.  The 2> is a redirection of output and error to some other place.  In this instance, a text file.  The ~/ (~ is a 'tilda') is a short cut to go to your home directory.  So ~/somename.txt will be found at /home/chris/somename.txt on my computer.  BTW, when you run that command, you are not going to see any kind of output on your screen.

---

### Post by Keith.Anyan on 2007-12-04
I used the "sudo make prepare 2> ~/make.prepare.txt" and the txt contained this:

make[1]: *** No rule to make target `arch/i386/kernel/asm-offsets.c', needed by `arch/i386/kernel/asm-offsets.s'.  Stop.
make: *** [prepare0] Error 2

---

### Post by Keith.Anyan on 2007-12-04
> **Merc248 said:**
> Hey, just to let you guys know, there's beta drivers for the CMI8788 chipset that have been rewritten and are supposedly working great.  Look here:

[http://www.alsa-project.org/main/index.php/User:ClemensLadisch](http://www.alsa-project.org/main/index.php/User:ClemensLadisch)

I would try this, but I have no idea on how to install it. :?

---

### Post by Anaximander Thales on 2007-12-04
Okay -- well, I see different possible solutions.  But, let's assume it's a header issue.  What I'm finding is that you possibly have incorrect headers loaded.  How that occurs, I'm not sure.

first run this at a command prompt:
uname -r

Then run this at a command prompt:
cat /usr/src/linux-headers-2.6.22-14-generic/include/linux/utsrelease.h

The two version numbers should be the same.  Here's the information I get on my computer, and yours should look similar to mine

uname -r -> 2.6.22-14-generic
cat <...> -> #define UTS_RELEASE "2.6.22-14-generic"

If the version numbers aren't the same, then this should be the problem.

This next set of instructions try ONLY IF THE VERSION NUMBERS DON'T MATCH
=================================================================
run:
sudo dpkg -P linux-headers-generic
sudo dpkg -P linux-headers-2.6.22-14-generic
sudo apt-get install linux-headers-generic 

the dpkg -P will 'purge' the header files.  This will not only remove the files that were installed, but all configuration files.  So, from above, you'll purge the generic headers, the generic headers set up for 2.6.22-14 (that has incorrect information in it), and then you'll use apt-get to reinstall the generic header files.  I'm assuming that the 2.6.22-14 (or what ever kernel you're using) should be installed in the same process.

However, to test, just re-run the above uname and cat commands and they should match.
=================================================================

I'm hoping that it's a header issue simply because if the version numbers match, I'm not sure where to go with it.  But, let me know what you get and what you do, and we'll see what needs to be done next.

---

### Post by Keith.Anyan on 2007-12-16
I tried the
sudo dpkg -P linux-headers-generic
sudo dpkg -P linux-headers-2.6.22-14-generic
sudo apt-get install linux-headers-generic 

and got this

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfltk1.1 libmikmod2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-2.6.22-14-generic
The following NEW packages will be installed:
  linux-headers-2.6.22-14-generic linux-headers-generic
0 upgraded, 2 newly installed, 0 to remove and 33 not upgraded.
Need to get 605kB of archives.
After unpacking, 6623kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main linux-headers-2.6.22-14-generic 2.6.                         22-14.46
  Could not resolve 'ca.archive.ubuntu.com'
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) gutsy/main linux-headers-generic 2.6.22.14.21
  Could not resolve 'ca.archive.ubuntu.com'
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6)                         .22/linux-headers-2.6.22-14-generic_2.6.22-14.46_i386.deb Could not resolve 'ca.                         archive.ubuntu.com'
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux](http://ca.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux)                         -headers-generic_2.6.22.14.21_i386.deb Could not resolve 'ca.archive.ubuntu.com'
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-mi                         ssing.

---

### Post by Keith.Anyan on 2007-12-16
> **Merc248 said:**
> Hey, just to let you guys know, there's beta drivers for the CMI8788 chipset that have been rewritten and are supposedly working great.  Look here:

[http://www.alsa-project.org/main/index.php/User:ClemensLadisch](http://www.alsa-project.org/main/index.php/User:ClemensLadisch)

BTW can someone tell how to install this? I would like to give it a try since nothing else is working :-k

---

### Post by Anaximander Thales on 2007-12-18
to install -- fairly easy.

1. [Download](http://www.alsa-project.org/main/index.php/User:ClemensLadisch) from here.
2. open a terminal
3. cd into the directory where you saved the alsa drivers
4. extract the the archive [tar xjvf *alsa-driver-filename*]
5. cd into the folder that you just extracted
6. sudo ./configure
7. sudo make
8. sudo make install

Let us know if you get any errors.

---

### Post by proteo on 2007-12-19
Can anyone help me, please?

I have installed the latest version of alsa, and the sound works amazing, but it only works on some apps, i can hear the system sounds, Rythmbox and Totem. But anything else doesn't work, xmms, vlc, mplayer, etc. :confused:

Thanks

Edit: Miro is working too, but VLC still doesn't work, I've been looking at the configuration and no matter what i do, still no sound  :(

---

### Post by Keith.Anyan on 2007-12-27
**After using the "sudo make" command I get this:**

make all-deps
make[1]: Entering directory `/home/Keith/alsa'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/Keith/alsa'

Please, run the configure script as first...


**When I use "sudo make install" command I get this error:**

if [ -L /include/sound ]; then \
                rm -f /include/sound; \
                ln -sf /home/Keith/alsa/include/sound /include/sound; \
        else \
                rm -rf /include/sound; \
                install -d -m 755 -g root -o root /include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /include/sound; \
                done \
        fi
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1

---

### Post by Anaximander Thales on 2007-12-28
Did you get any errors while doing running this command?
sudo ./configure

The error that you are receiving from 'sudo make' says 'plaese run the configure script first.'  So it sounds as if 'sudo ./configure' didn't finish correctly.

---

### Post by Anaximander Thales on 2007-12-28
> **proteo said:**
> Can anyone help me, please?

I have installed the latest version of alsa, and the sound works amazing, but it only works on some apps, i can hear the system sounds, Rythmbox and Totem. But anything else doesn't work, xmms, vlc, mplayer, etc. :confused:

Sorry I didn't catch this before.

I'm not terribly familiar with some of the programs listed (as in, I haven't used them).

So, I guess the first step is going to be -- are you getting any errors when you attempt to run the programs?  If you aren't getting errors from the program itself (i.e. can't find alsa device), then what's the output when you run the program in the terminal?

---

### Post by proteo on 2007-12-28
When I run this programs from the terminal i get this errors.
With XMMS i have this:
** WARNING **: alsa_setup(): Failed to open pcm device (default): Dispositivo ó recurso ocupado.   and a dialog box telling me to check the soundcard, the configuration of the plugins, and the outputs.

With VLC, even when its configured to use alsa as the output plugin, i get this:
[00000317] oss audio output error: cannot open audio device (/dev/snd/)
[00000317] main audio output error: no decoder thread

With Last.FM player, I get a dialog box with the message: The ALSA soundsystem is either busy or not present.

With MPlayer, "Could not open/initialize audio device -> no sound."

Basically, its like the alsa system was busy or nonexistant for some programs and other just work flawlessly.

Thanks

---

### Post by Keith.Anyan on 2008-01-03
This is what I get when I use the sudo ./configure command:

checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/Keith/alsa
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

---

### Post by Yellow Pasque on 2008-01-03
Keith - copy and paster
```
sudo apt-get install linux-headers-`uname -r`
```

---

### Post by Keith.Anyan on 2008-01-03
I finally got the drivers to install but I only get Kubuntu sounds.  I don't have sounds for any other applications like Firefox, games, VLC media player or Kaffeine player.  For Kaffeine player I get "Audio output unavailable, Device is busy. ()" error. :confused:

I also got this message at the end of the installation:
WARNING!!! The mixer channels for the ALSA driver are muted by default!!!
**************************************************************************
You would use some ALSA or OSS mixer to set the appropriate volume

Currently I'm using Kmix which is what Kubuntu came with.

---

