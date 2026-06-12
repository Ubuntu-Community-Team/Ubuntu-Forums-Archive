---
title: "Need assistance in installing Echo Mona Sound Device"
date: 2008-08-08
forum: Multimedia Software
---

### Post by jukingeo on 2008-08-08
Hello All,

I have installed Ubuntu Studio on my Dell Dimension computer (on a properly set up triple boot:  Win XP, Puppy Linux, & Ubuntu Studio).

I recently removed my Sound Blaster Live for the more capable Echo Mona sound device.  I have done my research and discovered that the Echo24 line of products (of which the Mona is a part of) is in fact supported.

However, setting this device up is proving to be very difficult.   For one it isn't "automagically" detected and step via Ubuntu Studio. 

So I searched for information here in the Ubuntu forums and found this very outdated guide:

[https://help.ubuntu.com/community/EchoMia](https://help.ubuntu.com/community/EchoMia)

While this guide is aimed at the Mia, I was told that it SHOULD have worked for any card in the Echo24 line.  Anyway, I started by downloading the latest files I needed from the ALSA site.  (alsa-drivers-1.0.17 (version denoted via *) , alsa-lib-*, alsa-firmare-*, alsa-plugins-*, alsa-tools-*, & alsa-utils-*

I removed the old drivers on my machine via Synaptic.

I got up to the ./configure (etc) line and then I started to get error messages.  I figured I would abandon this guide because it is old.

So then I decided to go for more updated approach and follow the specific guide for the Mona install on the ALSA website.

This isn't working either.  Loads and Loads of error messages.   Anyway, this below is a posting of my progress in the terminal.

Do forgive the constant mistypings.  I am still very new to Linux.

Here is the results of my Terminal:

geo@home:~$ uname -r
2.6.24-19-rt
geo@home:~$ lsmod |more
Module                  Size  Used by
rfcomm                 43280  2 
l2cap                  25984  13 rfcomm
bluetooth              62564  4 rfcomm,l2cap
ppdev                  10372  0 
speedstep_lib           6532  0 
cpufreq_userspace       5284  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9740  0 
cpufreq_conservative     8840  0 
cpufreq_stats           7360  0 
freq_table              5536  2 cpufreq_ondemand,cpufreq_stats
container               5760  0 
dock                   11564  0 
video                  19984  0 
output                  4736  1 video
sbs                    15368  0 
sbshc                   7808  1 sbs
battery                14596  0 
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16644  1 ip_tables
ipv6                  275236  8 
ac                      7044  0 
sbp2                   24456  0 
lp                     13252  0 
loop                   19460  0 
snd_mona               30756  0 
snd_pcm_oss            42400  0 
af_packet              24196  2 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                78724  2 snd_mona,snd_pcm_oss
parport_pc             36516  1 
dcdbas                  9504  0 
parport                38600  3 ppdev,lp,parport_pc
evdev                  13312  3 
snd_seq_dummy           4868  0 
serio_raw               7940  0 
psmouse                41104  0 
snd_seq_oss            35968  0 
snd_seq_midi            9376  0 
snd_rawmidi            25632  1 snd_seq_midi
pcspkr                  4224  0 
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54992  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_m
idi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmi
di,snd_seq
snd                    57636  10 snd_mona,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_
seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nvidia               7826784  24 
soundcore               9312  1 snd
snd_page_alloc         11400  2 snd_mona,snd_pcm
i2c_core               25344  1 nvidia
button                  9232  0 
iTCO_wdt               13524  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34708  0 
intel_agp              25492  1 
pci_hotplug            31776  1 shpchp
agpgart                34900  2 nvidia,intel_agp
ext3                  137480  3 
jbd                    49044  1 ext3
mbcache                 9856  1 ext3
sg                     36624  0 
sd_mod                 31232  5 
sr_mod                 18084  0 
cdrom                  37152  1 sr_mod
ata_generic             8452  0 
pata_acpi               8320  0 
floppy                 62660  0 
ata_piix               19716  4 
e100                   37772  0 
ohci1394               34096  0 
libata                160112  3 ata_generic,pata_acpi,ata_piix
mii                     6400  1 e100
ieee1394               95544  2 sbp2,ohci1394
scsi_mod              153196  5 sbp2,sg,sd_mod,sr_mod,libata
ehci_hcd               37644  0 
uhci_hcd               26896  0 
usbcore               146924  3 ehci_hcd,uhci_hcd
thermal                16924  0 
processor              37384  1 thermal
fan                     5636  0 
fuse                   51604  1 
geo@home:~$ cd /geo/alsatemp/alsa-driver-1.0.17
bash: cd: /geo/alsatemp/alsa-driver-1.0.17: No such file or directory
geo@home:~$ cd /home/geo/alsatemp/alsa-driver-1.0.17
bash: cd: /home/geo/alsatemp/alsa-driver-1.0.17: No such file or directory
geo@home:~$ cd /home/geo/alsatmp/alsa-driver-1.0.17
geo@home:~/alsatmp/alsa-driver-1.0.17$ make clean
rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
make[1]: Entering directory `/home/geo/alsatmp/alsa-driver-1.0.17/acore'
Makefile:6: /home/geo/alsatmp/alsa-driver-1.0.17/Makefile.conf: No such file or directory
/home/geo/alsatmp/alsa-driver-1.0.17/Rules.make:75: /Rules.make1: No such file or directory
make[1]: *** No rule to make target `/Rules.make1'.  Stop.
make[1]: Leaving directory `/home/geo/alsatmp/alsa-driver-1.0.17/acore'
make: *** [clean] Error 1
geo@home:~/alsatmp/alsa-driver-1.0.17$ make mrproper
rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
make[1]: Entering directory `/home/geo/alsatmp/alsa-driver-1.0.17/acore'
Makefile:6: /home/geo/alsatmp/alsa-driver-1.0.17/Makefile.conf: No such file or directory
/home/geo/alsatmp/alsa-driver-1.0.17/Rules.make:75: /Rules.make1: No such file or directory
make[1]: *** No rule to make target `/Rules.make1'.  Stop.
make[1]: Leaving directory `/home/geo/alsatmp/alsa-driver-1.0.17/acore'
make: *** [mrproper] Error 1
geo@home:~/alsatmp/alsa-driver-1.0.17$ ./configure --with-cards=mona --with-oss=yes --with-sequencer=yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
geo@home:~/alsatmp/alsa-driver-1.0.17$ modinfo soundcore
filename:       /lib/modules/2.6.24-19-rt/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.24-19-rt SMP preempt mod_unload 586 
geo@home:~/alsatmp/alsa-driver-1.0.17$ cd /
geo@home:/$ cd usr/src
geo@home:/usr/src$ mkdir alsa
mkdir: cannot create directory `alsa': Permission denied
geo@home:/usr/src$ sudo mkdir alsa
[sudo] password for geo: 
geo@home:/usr/src$ cd alsa
geo@home:/usr/src/alsa$ cp /downloads/alsa-*
cp: missing destination file operand after `/downloads/alsa-*'
Try `cp --help' for more information.
geo@home:/usr/src/alsa$ cp downloads/alsa-*
cp: missing destination file operand after `downloads/alsa-*'
Try `cp --help' for more information.
geo@home:/usr/src/alsa$ cp --help
Usage: cp [OPTION]... [-T] SOURCE DEST
  or:  cp [OPTION]... SOURCE... DIRECTORY
  or:  cp [OPTION]... -t DIRECTORY SOURCE...
Copy SOURCE to DEST, or multiple SOURCE(s) to DIRECTORY.

Mandatory arguments to long options are mandatory for short options too.
  -a, --archive                same as -dpR
      --backup[=CONTROL]       make a backup of each existing destination file
  -b                           like --backup but does not accept an argument
      --copy-contents          copy contents of special files when recursive
  -d                           same as --no-dereference --preserve=links
  -f, --force                  if an existing destination file cannot be
                                 opened, remove it and try again
  -i, --interactive            prompt before overwrite
  -H                           follow command-line symbolic links in SOURCE
  -l, --link                   link files instead of copying
  -L, --dereference            always follow symbolic links in SOURCE
  -P, --no-dereference         never follow symbolic links in SOURCE
  -p                           same as --preserve=mode,ownership,timestamps
      --preserve[=ATTR_LIST]   preserve the specified attributes (default:
                                 mode,ownership,timestamps), if possible
                                 additional attributes: context, links, all
      --no-preserve=ATTR_LIST  don't preserve the specified attributes
      --parents                use full source file name under DIRECTORY
  -R, -r, --recursive          copy directories recursively
      --remove-destination     remove each existing destination file before
                                 attempting to open it (contrast with --force)
      --sparse=WHEN            control creation of sparse files
      --strip-trailing-slashes  remove any trailing slashes from each SOURCE
                                 argument
  -s, --symbolic-link          make symbolic links instead of copying
  -S, --suffix=SUFFIX          override the usual backup suffix
  -t, --target-directory=DIRECTORY  copy all SOURCE arguments into DIRECTORY
  -T, --no-target-directory    treat DEST as a normal file
  -u, --update                 copy only when the SOURCE file is newer
                                 than the destination file or when the
                                 destination file is missing
  -v, --verbose                explain what is being done
  -x, --one-file-system        stay on this file system
      --help     display this help and exit
      --version  output version information and exit

By default, sparse SOURCE files are detected by a crude heuristic and the
corresponding DEST file is made sparse as well.  That is the behavior
selected by --sparse=auto.  Specify --sparse=always to create a sparse DEST
file whenever the SOURCE file contains a long enough sequence of zero bytes.
Use --sparse=never to inhibit creation of sparse files.

The backup suffix is `~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

As a special case, cp makes a backup of SOURCE when the force and backup
options are given and SOURCE and DEST are the same name for an existing,
regular file.

Report bugs to <bug-coreutils@gnu.org>.
geo@home:/usr/src/alsa$ cp /home/geo/alsatmp/alsa-drivers-1.0.17
cp: missing destination file operand after `/home/geo/alsatmp/alsa-drivers-1.0.17'
Try `cp --help' for more information.
geo@home:/usr/src/alsa$ cp /home/geo/alsatmp/alsa-drivers-1.0.17
cp: missing destination file operand after `/home/geo/alsatmp/alsa-drivers-1.0.17'
Try `cp --help' for more information.
geo@home:/usr/src/alsa$ cp /home/geo/alsatemp/alsa-drivers-1.0.17*
cp: missing destination file operand after `/home/geo/alsatemp/alsa-drivers-1.0.17*'
Try `cp --help' for more information.
geo@home:/usr/src/alsa$ cd /home/geo/alsatemp/alsa-drivers-1.0.17
bash: cd: /home/geo/alsatemp/alsa-drivers-1.0.17: No such file or directory
geo@home:/usr/src/alsa$ cd /home/geo/alsatmp/alsa-drivers-1.0.17
bash: cd: /home/geo/alsatmp/alsa-drivers-1.0.17: No such file or directory
geo@home:/usr/src/alsa$ cd/
bash: cd/: No such file or directory
geo@home:/usr/src/alsa$ cd ~
geo@home:~$ cd /home/geo/alsatmp/1.0,17
bash: cd: /home/geo/alsatmp/1.0,17: No such file or directory
geo@home:~$ ls-l
bash: ls-l: command not found
geo@home:~$ ls -l
total 24
drwxr-xr-x 8 geo geo 4096 2008-08-08 12:05 alsatmp
drwxr-xr-x 4 geo geo 4096 2008-08-07 00:40 Audio
drwxr-xr-x 2 geo geo 4096 2008-08-07 00:29 Desktop
drwxr-xr-x 3 geo geo 4096 2008-08-08 11:58 Downloads
drwx------ 7 geo geo 4096 2008-08-05 21:38 Games
drwxr-xr-x 2 geo geo 4096 2008-08-07 01:00 Music
geo@home:~$ cd alsatmp
geo@home:~/alsatmp$ cd alsatmp/alsa-driver-1.0.17
bash: cd: alsatmp/alsa-driver-1.0.17: No such file or directory
geo@home:~/alsatmp$ ls -l
total 24
drwxr-xr-x 27 geo geo 4096 2008-08-08 12:15 alsa-driver-1.0.17
drwxr-xr-x 18 geo geo 4096 2008-07-14 05:19 alsa-firmware-1.0.17
drwxr-xr-x 10 geo geo 4096 2008-07-14 05:14 alsa-lib-1.0.17
drwxr-xr-x 12 geo geo 4096 2008-07-14 05:15 alsa-plugins-1.0.17
drwxr-xr-x 20 geo geo 4096 2008-07-14 05:19 alsa-tools-1.0.17
drwxr-xr-x 15 geo geo 4096 2008-07-14 05:16 alsa-utils-1.0.17
geo@home:~/alsatmp$ cd alsa-driver-1.0.17
geo@home:~/alsatmp/alsa-driver-1.0.17$ .configure --with-cards=mona --with-sequencer=yes ; make ; make install
bash: .configure: command not found
make all-deps
make[1]: Entering directory `/home/geo/alsatmp/alsa-driver-1.0.17'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/geo/alsatmp/alsa-driver-1.0.17'

Please, run the configure script as first...

if [ -L /include/sound ]; then \
		rm -f /include/sound; \
		ln -sf /home/geo/alsatmp/alsa-driver-1.0.17/include/sound /include/sound; \
	else \
		rm -rf /include/sound; \
		install -d -m 755 -g root -o root /include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /include/sound; \
		done \
	fi
install: cannot create directory `/include': Permission denied
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1
geo@home:~/alsatmp/alsa-driver-1.0.17$ sudo ./configure --with-cards=mona --with-sequencer=yes ; make ; make install
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
make all-deps
make[1]: Entering directory `/home/geo/alsatmp/alsa-driver-1.0.17'
make[1]: Nothing to be done for `all-deps'.
make[1]: Leaving directory `/home/geo/alsatmp/alsa-driver-1.0.17'

Please, run the configure script as first...

if [ -L /include/sound ]; then \
		rm -f /include/sound; \
		ln -sf /home/geo/alsatmp/alsa-driver-1.0.17/include/sound /include/sound; \
	else \
		rm -rf /include/sound; \
		install -d -m 755 -g root -o root /include/sound; \
		for f in include/sound/*.h; do \
			install -m 644 -g root -o root $f /include/sound; \
		done \
	fi
install: cannot create directory `/include': Permission denied
install: cannot stat `include/sound/*.h': No such file or directory
make: *** [install-headers] Error 1
geo@home:~/alsatmp/alsa-driver-1.0.17$ 



Now I would like to have a step by step procedure to properly install this sound device on my machine. 

This is the exact path to my alsa downloads as per my terminal:

geo@home:~$ cd /home/geo/alsatmp
geo@home:~/alsatmp$ ls -l
total 24
drwxr-xr-x 27 geo geo 4096 2008-08-08 12:33 alsa-driver-1.0.17
drwxr-xr-x 18 geo geo 4096 2008-07-14 05:19 alsa-firmware-1.0.17
drwxr-xr-x 10 geo geo 4096 2008-07-14 05:14 alsa-lib-1.0.17
drwxr-xr-x 12 geo geo 4096 2008-07-14 05:15 alsa-plugins-1.0.17
drwxr-xr-x 20 geo geo 4096 2008-07-14 05:19 alsa-tools-1.0.17
drwxr-xr-x 15 geo geo 4096 2008-07-14 05:16 alsa-utils-1.0.17
geo@home:~/alsatmp$ 


So any suggestions as to what I should do in my terminal I would like in easy cut & paste fashion with as little guesswork as possible (which is why I am providing so much detail to begin with).

Speak to me as if I just started Linux yesterday.  While I have been on Linux for close to 3 months now, I have been plagued with many many many problems with trying to get sound to properly work.  The Mona is my third (and probably my last) attempt at getting sound to properly work with Linux.

Any thoughts, suggestions, and advice would be appreciated.

Thank You,

Geo

---

### Post by NullHead on 2008-08-08
Is there a configure script like the make output suggests? ls -la should show you. Generally for building from source, you have to do a ./configure before you can issue the make command. 

Just try running ./configure before you run make. Re-make and see if that works.

---

### Post by mountain_goat on 2008-08-08
Hey Geo,

OK, from your message a few quick things I notice. There may be more as I read more, but just now,[INDENT][INDENT] snd_mona               30756  0 
snd_pcm_oss            42400  0 
af_packet              24196  2 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_pcm                78724  2 snd_mona,snd_pcm_oss
[/INDENT][/INDENT]This is telling me that the kernel hasn't got the alsa modules installed, or that oss is being used as default.
Maybe we need to look at removing the oss things, or somehow re-configuring.
Check Preferences|Sound that you have alsa used.
I think from reading about the Mona that there is a pci card installed which connects to the mona main unit.
So check Administration|Hardware just in case you see there is a driver there that needs to be enabled.

Also, I notice that your commands for cd /#### may be incorrect. I get caught doing the same.
Try doing cd ##### without the initial forward slash. That should work. Your mind is still working DOS and windows ;)

OK, I shall have coffee and look further.
mountain goat ~ enjoying the sun

---

### Post by mountain_goat on 2008-08-08
Geo,

[INDENT][INDENT]geo@home:~/alsatmp/alsa-driver-1.0.17$ make clean
rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
make[1]: Entering directory `/home/geo/alsatmp/alsa-driver-1.0.17/acore'
Makefile:6: /home/geo/alsatmp/alsa-driver-1.0.17/Makefile.conf: No such file or directory
/home/geo/alsatmp/alsa-driver-1.0.17/Rules.make:75: /Rules.make1: No such file or directory
make[1]: *** No rule to make target `/Rules.make1'.  Stop.
make[1]: Leaving directory `/home/geo/alsatmp/alsa-driver-1.0.17/acore'
make: *** [clean] Error 1
[/INDENT][/INDENT]
Maybe you need to do a 'sudo make clean'
Then the error message on line 6 above;
[INDENT][INDENT] Makefile:6: /home/geo/alsatmp/alsa-driver-1.0.17/Makefile.conf: No such file or directory
[/INDENT][/INDENT]seems to be looking for a config file. Remember how we needed to make a config file in Amtam's HowTo guide for the X-fi by using 'make menuconfig'?
I wonder if something the same is required here, where you need to create such a config file?

Oh, then I see further down you have tried the following
[INDENT][INDENT] geo@home:~/alsatmp$ cd alsa-driver-1.0.17
geo@home:~/alsatmp/alsa-driver-1.0.17$ .configure --with-cards=mona --with-sequencer=yes ; make ; make install
bash: .configure: command not found
[/INDENT][/INDENT]
OK, try putting a forward slash before the command configure thus
[INDENT][INDENT] geo@home:~/alsatmp/alsa-driver-1.0.17$ ./configure --with-cards=mona --with-sequencer=yes ; make ; make install
[/INDENT][/INDENT]I read that the period '.' tells the system to run the following command, shell command. The slash is needed as well I think.
'configure' is the shell script you need to get running.

I would make sure you issue a sudo bash to set as root so that you wont get 'permission denied' error messages

See how this goes Geo

mountain goat ~ more coffee needed

---

### Post by veggiebenz on 2008-08-09
Geo,

Try this:

[https://lists.ubuntu.com/archives/ubuntu-studio-users/2007-October/000638.html](https://lists.ubuntu.com/archives/ubuntu-studio-users/2007-October/000638.html)

I do remember having to make these edits to the config file.

I did not have to rebuild ALSA tho, I used what was in the repository.  Only exception is that (at the time -- 2 yrs ago?) alsa-firmware was not found in ubuntu repository.  So I had to grab an RPM and rebuild it with "alien". 

But i would think you could just use alsa packages from ubuntu repositories and then make some edits to the config file as shown in the post above.

good luck!

---

### Post by jukingeo on 2008-08-13
Hello all, 

I been away from my machine the past few days to take a Linux break.  Tonight I booted up Ubuntu Studio for the first time since my mishap above, now there is a new problem.

When I boot into Ubuntu, I don't get to the log on screen.  I get this instead:

Kinit: name_to_dev_t (/dev/sda8) = sda8 (8,8)
Kinit: trying to resume from /dev/sda8
Kinit: no resume image, doing normal boot

Ubuntu 8.04.01 Home ttyl

Home Login:


I have tried all of the options in recovery mode and nothing gets me back to the main login screen.  I get bounced back to this.

I am not sure if what I did above with my initial attempt to get the Echo Mona card working did this, but it is too coincidental that now I have the problem as a result of that.

At any rate, how do I fix this?

Geo

---

### Post by jukingeo on 2008-08-27
Hello all,

I took a few weeks off from Linux to clear my head.  Anyway, I am back now and I would like to get my Echo Mona to work with Linux.

However, instead of doing "guesswork" I would like to get some advice from anyone that has set up an Echo24 series device on their machine.

As stated above, the procedure for the Mia is too old and it didn't work anyway.  I was going to give the ALSA site information a shot again, but that is what caused my Ubuntu installation to completely fail the last time.

So I just would like to know the RIGHT way to do this.

Thanx,

Geo

---

### Post by jukingeo on 2008-09-03
Hello All, 

I STILL cannot get my Echo Mona installed.

The ALSA guide makes it sound SO easy and it seems straightforward, but what do you do when this happens?

(The first part shows the contents of my Downloads directory and I show navigating in my terminal to the directory and performing the sudo make clean and then the ./configure command.

The ALSA guide also mentions compiling a Kernal with the Echo Mona sound device.  If that method is more straightforward (and/or easier) can someone show me how to do it that way?  (The ALSA site doesn't explain that method.

geo@home:~/Downloads$ ls -l
total 15756
drwxr-xr-x 27 geo geo     4096 2008-09-03 22:15 alsa-driver-1.0.17
drwxr-xr-x 18 geo geo     4096 2008-07-14 05:19 alsa-firmware-1.0.17
drwxr-xr-x 10 geo geo     4096 2008-07-14 05:14 alsa-lib-1.0.17
-rw-r--r--  1 geo geo   308119 2008-08-08 11:58 alsa-plugins-1.0.17.tar.bz2
-rw-r--r--  1 geo geo  1546105 2008-08-08 11:58 alsa-tools-1.0.17.tar.bz2
drwxr-xr-x 15 geo geo     4096 2008-07-14 05:16 alsa-utils-1.0.17
-rw-r--r--  1 geo geo   508352 2008-08-07 00:47 gens_2.15.2_i386.deb
drwxr-xr-x  2 geo geo     4096 2008-03-24 22:02 install_flash_player_9_linux
-rw-r--r--  1 geo geo  1140670 2008-08-07 00:42 stella_2.6.1-1_i386.deb
-rw-r--r--  1 geo geo 12562724 2008-08-21 01:50 WMER1284137192.exe
geo@home:~/Downloads$ cd alsa-driver-1.0.17
geo@home:~/Downloads/alsa-driver-1.0.17$ sudo make clean
rm -f .depend *.o snd.map*
rm -f /*.ver
rm -f modules/*.o modules/*.ko
make[1]: Entering directory `/home/geo/Downloads/alsa-driver-1.0.17/acore'
Makefile:6: /home/geo/Downloads/alsa-driver-1.0.17/Makefile.conf: No such file or directory
/home/geo/Downloads/alsa-driver-1.0.17/Rules.make:75: /Rules.make1: No such file or directory
make[1]: *** No rule to make target `/Rules.make1'.  Stop.
make[1]: Leaving directory `/home/geo/Downloads/alsa-driver-1.0.17/acore'
make: *** [clean] Error 1
geo@home:~/Downloads/alsa-driver-1.0.17$ sudo ./configure --with-card=mona
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
geo@home:~/Downloads/alsa-driver-1.0.17$ 

Thanx,

Geo

---

### Post by djhash on 2008-09-11
Hey,

   Just to let you know. You will need to install build-essential (sudo apt-get install build-essential); agree to the addittional packages to be installed with it.

   Then run ./configure 

   If you get any errors during configure or make, then you are missing files, you then either need to install them from repos (using apt-get) or you'll need to compile it separately from source.

   Let me know how this works for you. If you still have problems, come to #ubuntu on irc.ubuntu.com:8001 and ask there.

   (BTW: for linux to execute a file, it needs to have a path to the file. If the file is not in a path already setup an the PATH environment, then it will not execute it, even though it is in the same directory you are in, because current working directory is not in the path. So telling linux ./file is saying, use the current working directory for the path of the command, windows automatically looks for files it can run in the current directory)

---

### Post by jukingeo on 2008-09-17
> **djhash said:**
> Hey,

   Just to let you know. You will need to install build-essential (sudo apt-get install build-essential); agree to the addittional packages to be installed with it.

   Then run ./configure 

   If you get any errors during configure or make, then you are missing files, you then either need to install them from repos (using apt-get) or you'll need to compile it separately from source.

   Let me know how this works for you. If you still have problems, come to #ubuntu on irc.ubuntu.com:8001 and ask there.

Hello,

I tried the first part of what you said to do and that seemed to work and from the look of it, it doesn't seem like I get any error messages.  Then I tried run ./configure and that didn't do anything.  It said it couldn't find the command.

See my Terminal below...(more to follow that).


geo@home:~$ sudo apt-get install build-essential
[sudo] password for geo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev libtimedate-perl
  linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.2-multilib gcc-4.2-doc libstdc++6-4.2-dbg
  glibc-doc manpages-dev libstdc++6-4.2-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.2 libc6-dev libstdc++6-4.2-dev
  libtimedate-perl linux-libc-dev patch
0 upgraded, 9 newly installed, 0 to remove and 20 not upgraded.
Need to get 8704kB of archives.
After this operation, 34.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-19.41 [696kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libc6-dev 2.7-10ubuntu3 [3344kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libstdc++6-4.2-dev 4.2.3-2ubuntu7 [1187kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main g++-4.2 4.2.3-2ubuntu7 [2784kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main g++ 4:4.2.3-1ubuntu6 [1440B]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libtimedate-perl 1.1600-9 [30.1kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main patch 2.5.9-4 [95.6kB]           
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main dpkg-dev 1.14.16.6ubuntu4 [559kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main build-essential 11.3ubuntu1 [7066B]
Fetched 8704kB in 15s (545kB/s)                                                
Selecting previously deselected package linux-libc-dev.
(Reading database ... 112735 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-19.41_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_i386.deb) ...
Selecting previously deselected package libstdc++6-4.2-dev.
Unpacking libstdc++6-4.2-dev (from .../libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package g++-4.2.
Unpacking g++-4.2 (from .../g++-4.2_4.2.3-2ubuntu7_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.2.3-1ubuntu6_i386.deb) ...
Selecting previously deselected package libtimedate-perl.
Unpacking libtimedate-perl (from .../libtimedate-perl_1.1600-9_all.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-4_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.14.16.6ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.3ubuntu1_i386.deb) ...
Setting up linux-libc-dev (2.6.24-19.41) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
Setting up libtimedate-perl (1.1600-9) ...
Setting up patch (2.5.9-4) ...
Setting up dpkg-dev (1.14.16.6ubuntu4) ...
Setting up libstdc++6-4.2-dev (4.2.3-2ubuntu7) ...
Setting up g++-4.2 (4.2.3-2ubuntu7) ...
Setting up g++ (4:4.2.3-1ubuntu6) ...

Setting up build-essential (11.3ubuntu1) ...
geo@home:~$ run ./configure
bash: run: command not found
geo@home:~$ sudo run ./configure
sudo: run: command not found
geo@home:~$ run./configure
bash: run./configure: No such file or directory
geo@home:~$ run ./configure
bash: run: command not found
geo@home:~$ 

 >   (BTW: for linux to execute a file, it needs to have a path to the file. If the file is not in a path already setup an the PATH environment, then it will not execute it, even though it is in the same directory you are in, because current working directory is not in the path. So telling linux ./file is saying, use the current working directory for the path of the command, windows automatically looks for files it can run in the current directory)

These are the kind of problems I always get when attempting to install something that is not automagically recognized, or not within the repositories.  Most programs that are zipped packages also unpack and work fine.  But anything that requires a reconfiguring of the kernel or module builds almost never works.  And this is the big complaint I have with Linux.  It isn't clear cut.  I consider my self an above average user in Windows XP, but Linux makes me look like I just started computing yesterday.

Also another thing I find very weird is that I have uncovered four _different_ procedures to get the Echo Mona to work and the best part is that all four procedures do not work.

Mostly with anything else, I CAN get it to work in Linux.  I had video issues and some other problems that were just isolated to Ubuntu itself and I managed to get those problems fixed.  However, sound support is horrible at best.

So I don't know why there isn't a clear cut procedure to get sound to work on every system, every time.  Sure Linux isn't Windows, but if it is to get more followers, something simpler has to be done.

---

