---
title: "AOpen MP965-DR Problems"
date: 2007-10-31
forum: Mythbuntu
---

### Post by freak1 on 2007-10-31
**Hardware**
CPU: Intel Core2 Duo T7300
RAM: 2 Gb Kingston DDR-400
Video Card: Intel GM965
Motherboard: AOpen MP965-DR
Sound Card: Intel 82801H
HD: 80GB SATA
DVD-R: Sony
IR: Fintek
Network: Intel 3945ABG

**Problems:**
1) IR doesn't work. Fix is in CVS for LIRC, works great when I overwrite lirc_mceusb2.ko with the CVS version.
2) Network asks for keyring password on bootup to allow wireless to work
3) Alsa does not detect the SPDIF (tested with mythvantage using OSS and works great)
4) Had to manually install libgl1-mesa-dri to get GL to work for GL based menus and games.
5) TV out doesn't work most of the time with the xserver-xorg-video-intel.

---

### Post by apiper on 2008-02-26
Thanks for pointing out that the LIRC in CVS supports the MP965 - I've been hunting everywhere for how to get IR working!

---

### Post by fdemmer on 2008-03-16
i ran into some beginners problems with the way ubuntu installed the lirc modules and how the cvs lirc does it, details here: [http://ubuntuforums.org/showthread.php?p=4525684](http://ubuntuforums.org/showthread.php?p=4525684)

another problem with xorg:
using the "intel" driver and edid detected mode "1920x1080" and no other special configuration in xorg.conf the picture on my toshiba regza z3030 is not correctly aligned (over all resolution seems to be ok). it is about 30-40 pixels moved to the left and about 10-20 moved up, so that there is a black border on the right and bottom of the screen, while parts of the picture are missing on the left and top. i use a dvi2hdmi cable and the flatscreen is set to use "true scan".

from Xorg.0.log:
```
(II) intel(0): Printing probed modes for output TMDS-1
(II) intel(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz)
(II) intel(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz)
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
```

the flatscreen manual gives the following information:
hactive: 1920
vactive: 1080
progressive
h freq khz: 56.25
v freq hz: 50
pixel clock: 148.5
... so i guess the mode detection works just fine.

is this a problem with the driver or my flatscreen?
is there a way to finetune the timing... maybe on the fly without restarting X all the time?

---

### Post by fdemmer on 2008-03-16
got spdif working!

short: use alsa 1.0.16 or install a hardy beta :)

long(er):

i simply added hardy to my apt.sources temporarily:
```
deb http://at.archive.ubuntu.com/ubuntu hardy main universe
```

and installed alsa-source as described here under "Using alsa-source" and the module-assistent: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

spdif volume can be controlled through alsamixer and the PCM control. be sure to unmute the "IEC958" control!

---

### Post by fdemmer on 2008-03-16
ac3 passthough seems not to be working though. tried it with vlc and a dvb-s program carrying ac3.

it plays only short bursts of sound interrupted silence for a moment.

playing the same ac3 source stream decoded to stereo works fine.

any ideas?

---

### Post by fdemmer on 2008-03-17
another important feature especially with this tiny device is sensor data. we don't want it to burn up while watching 1080p h.264 video :)

unfortunately the ICH8 sensors are still not supported according to [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices).

"(2007-11-26) The ICH8 (82801H) and possibly later Intel south bridges have embedded sensors. These are not yet supported, due to a lack of technical documentation."

---

### Post by fdemmer on 2008-03-17
ha, didn't know that thing included a dvd-r! .. nice :D

```
sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
```

thanks for pointing that out freak1!

---

### Post by fdemmer on 2008-03-19
That's maybe interesting when having graphics issues:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/177492](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/177492)

---

### Post by frosch6669 on 2008-03-24
Hello I also own this box. The only thing that does not work is the tv out. it is very strange: after trying for hours it worked, but without changing anything but the next time it does not work the same way?
is someone able to test the composite tv out (ony the yellow cinch connector) and post the results here, also the s-video out. 
I am interested if i am too stupid or if there is a bug.
all you need to do is connect the TV with s-video or composite cable,
open a terminal and type:
xrandr -q (says if the tv is detected) 
xrandr --output TV --set TV_FORMAT PAL (Pal may be changed to one of the following: NTSC-M       NTSC-443     NTSC-J       PAL-M       
                           PAL-N        PAL          480p@59.94Hz 480p@60Hz   
                           576p         720p@60Hz    720p@59.94Hz 720p@50Hz   
                           1080i@50Hz   1080i@60Hz   1080i@59.94H )

You my get an error, but ignor it.
then type
xrandr --output TV --mode 640x480 (or 800x600)
then your tv should show something. 

please post yor results
greetz

---

### Post by apiper on 2008-05-30
> **fdemmer said:**
> ac3 passthough seems not to be working though. tried it with vlc and a dvb-s program carrying ac3.

it plays only short bursts of sound interrupted silence for a moment.

playing the same ac3 source stream decoded to stereo works fine.

any ideas?

After trying to get AC3 passthrough working with VLC I gave up and managed to get ac3 passthrough working with mplayer by using the following settings - save them to [FONT="Courier New"]~/.mplayer/config[/FONT] to use them as the defaults.

I also managed to get mostly-smooth H.264 video playback at 720p resolution, which VLC also had real trouble with :D

```
[default]
# Write your default config options here!
# Use OpenGL2 video driver
vo=gl2
# Optimise H.264 decoding
lavdopts=fast=1:skiploopfilter=all
# Use Alsa sound driver, digital interface
ao=pulse,alsa:device=hw=0.1 
# Try to use AC3-passthrough the DTS-passthrough before falling back to MAD MP3
# support
ac=hwac3,hwdts,mad
```


I've recently fitted the optional wireless network card (I think it's an Atheros AR5007, but I'm not 100% sure), which the following post appears to solve for some people but not for me. Has anyone had any luck getting this working

[http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686)

---

### Post by fdemmer on 2008-06-13
today's xorg-intel driver fixed the alignment problems on my lcd. this is the version that works with no special xorg.conf for me:

```
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 2.2.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 2.0
```

also about HDTV/1080p/720p i can report that when i disable desktop effects mplayer "can" play both HD formats (h.264 codec) pretty well, but unfortunately not perfect. (interestingly playback worked in fullscreen with effects enabled)
there is some tearing in camera pans or with fast movement like with football.
xvmc support IS still missing in the driver, so maybe it is just question of a few more month until that gets better.

ac3 passthrough also works like described above. dts i cannot test due to missing hi-fi equipment ;)

---

### Post by apiper on 2008-06-14
I'm glad my mplayer config was of use to you fdemmer :)

It turns out that the optional wireless card for this box has an Atheros AR5007 chip after all - I managed to get it working by following the instructions in this thread: [http://ubuntuforums.org/showthread.php?t=800686](http://ubuntuforums.org/showthread.php?t=800686) 

No more long network leads trailing down the the corridor to the router for me! \\:D/

---

### Post by StephaneLenclud on 2008-07-24
Would you recommend AOpen MP965-DR to run Ubuntu 8.04 out of the box or is there just too many issues to overcome?

---

### Post by frosch6669 on 2008-07-25
It runs out of the box. maybee you have to do some litte changes if nessasary for you. for me only the remote control was needed, and it works now. hope this helps.
greetings

---

### Post by StephaneLenclud on 2008-07-25
Thanks! That's all I wanted to hear ;)

---

### Post by StephaneLenclud on 2008-07-25
Oups no actually ;) I have a few more questions about this hardware:

   * I noticed it does not have PS2 ports and VGA output but rather uses USB and DVI. Has anyone been successful in using it with VGA to DVI adaptor and PS2 to USB adaptors?

   * Just how silent is it? Is it quieter than the XC-Cube MZ915-M?

   * Is anyone using that box as a server running 24/7?

---

### Post by frosch6669 on 2008-07-29
it has vga-output, because the dvi-like output that you may have noticed on the backside is aopen output, and you will receive a y-shaped cabel with both dvi and vga in the box.
it does not support ps/2, i had the same problem and i bought a usb to ps2 adapter, but this adapters only work if you have non wireless ps2 keyboard and mouse. but i would not recommend it, better buy new usb mouse/keyboard, its not not expensive..and its clean....
it is silent, but not as silent as an ordinary laptop because the fan is always running but it is much quieter than a desktop pc. i think it's ok, if you live at a street, open the window, and you wont hear your pc anymore...
i am not running it as server, but i can tell you two configurations:
as new i used a t7300 intel cpu, temp. was about 30-50 degrees, now i changed the cpu to a t9500 intel and 50-70. the higher temperatures are only possible if your surrounding temperature is about 30degree. 
if you put the cpu under full load 24h long i think it will not live long, because the hd is also getting hot inside..

ps 4gb is supported since newest bios update. but i only see 4gb in vista. maybee someone knows if ubuntu 8.04 32bit has a limit of visible 3,2 gb?
fanspeed adjustment, i did not get it work...
hope this helps
i am owning three of this boxes... :-) one for me the rest for family

---

### Post by rothgar on 2008-11-12
Well, I didn't want to bring this thread back from a shallow grave but I just bought one and loaded it with 8.04 and am having nothing but problems getting lirc to build from cvs.
could someone maybe give me a hand.
I installed build-essential and downloaded the source, but when I try make I keep getting "make: *** No targets specified and no makefile found.  Stop."
I saw somewhere else someone said this was a problem because they didn't have g++ installed but I already have that installed too.

any help would be greatly appreciated.

---

### Post by frosch6669 on 2008-11-12
hello it works, you have to look at a build script, i think.
i dont remerber every step because it was a long time ago i build it on my own.
there must be an install script that does everything for you(compile,install and load the module) its inside the cvs package...
here google is your friend AND enemy:
[http://www.gentoo-wiki.info/AOpen_MP965-DR#IR_reciever](http://www.gentoo-wiki.info/AOpen_MP965-DR#IR_reciever)
good luck...
if you get things to work would you be so nice to give a small instruction for ubuntu 8.04 here?
greets from good old germany

---

### Post by rothgar on 2008-11-12
I tried again and I still get this as a error.

> rothgar@mythtv:~/lirc$ sudo ./configure --prefix=/usr --with-driver=mceusb2
rothgar@mythtv:~/lirc$ make
make: *** No targets specified and no makefile found.  Stop.
rothgar@mythtv:~/lirc$ sudo make
from what I found the reason I get this problem is cause I don't have g++ installed but every time I try to install it it says it is already there. I will see what else I can find to get this working.

---

### Post by frosch6669 on 2008-11-13
ok,
because i am running a new kernel without lirc i have compiled lirc again so here you go:
as superuser("sudo su" your passwort)
apt-get install libtool autoconf automake linux-headers-XXXXX cvs
change the XXXXX with the output of "uname -r"
create a directory: mkdir /home/YOURUSERNAME/lirc
go to the directory: cd /home/YOURUSERNAME/lirc
get the cvs files:
cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login press enter for password
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
go to new directory: cd lirc
now do:
./autogen.sh (takes some time)
output shoud be somthing like: 
configure.ac:9: installing `./install-sh'
configure.ac:9: installing `./missing'
daemons/Makefile.am: installing `./depcomp'
Creating setup-driver.sh ...
then
./setup.sh
and graphical user interface comes up:
in the first menu select the driver, ->usb-> (i am note quite sure if it is the last oder the one before? mce oder or newer, no idea try the last)
then go to there third menu "safe configuration and run configure" enter
a lot of checking.... runs over your screen
in the end it says run : make
and then : make install
do so!
then : modprobe lirc-mceusb or lirc-mceusb2
and the test with: mode2 and press some keys of your remote, you shoud see some numbers running over the screen.
if not! do the following:
repeat everything and do not use the cvs-version but a version known to work..
please post if it works 
and which version you took and which driver (mceusb or mceusb2)
greets  and good luck!

---

### Post by frosch6669 on 2008-11-13
sorry i see that there a smilies in my code for cvs (copy&and paste the two lines from the link in my previous post).
second think i noticed is "oder" is german and means "or" sorry i dont have much time at the moment...

---

### Post by rothgar on 2008-11-15
Ok, I have it working now (thanks to you). Here is exactly what I had to do.

```
sudo su
apt-get install libtool autoconf automake linux-headers-2.6.24-21-generic cvs
```

I did not have all of this before. All I had before was build-essential and automake installed so I think I was probably missing the headers etc.

```
mkdir /home/YOURUSERNAME/lirc
cd /home/YOURUSERNAME/lirc
```

I already had the directory created so I just deleted everything inside to start fresh.

```
cvs -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc login
cvs -z8 -d:pserver:anonymous@lirc.cvs.sourceforge.net:/cvsroot/lirc co lirc
```

```
./autogen.sh
./setup.sh
```

In the graphical interface I selected Driver config -> USB -> mceusb2 (new)

```
make
make install
modprobe lirc-mceusb2
```

When I tried mode2 I got the following error

```
mode2: could not get file information for /dev/lirc
mode2: default_init(): No such file or directory
```

I then remember reading that ubuntu puts things in strange locations sometimes so I followed this guide [http://ubuntuforums.org/showthread.php?t=717753](http://ubuntuforums.org/showthread.php?t=717753)

The steps I actually needed to follow were
(I changed the mv commands to cp just to make sure everything would stay were it was originally placed.)

```
cp /lib/modules/2.6.22-14-generic/misc/lirc_dev.ko /lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_dev
cp /lib/modules/2.6.22-14-generic/misc/lirc_mceusb2.ko /lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_mceusb2
```

Then I kept following the tutorial

```
rmmod lirc_mceusb2
rmmod lirc_dev
lsmod|grep lirc
/etc/init.d/lirc restart
```

I tried mode2 to see if I could test the remote again and it still would not start saying the folders were missing still. instead I tried irw cause that is what the other used and i noticed it was working!!
I fired up boxee and everything is working. I have no idea if it will work with a restart but I am hopeful.

Thanks again for the help.

PS. Thanks also for the language tip. I have always wanted to learn a little German. :)

---

### Post by frosch6669 on 2008-11-18
thanks for the detailed howto, will try it when changing my system back to debian...

---

### Post by fdemmer on 2009-10-27
just for the record... with karmic everything works out of the box as far as i can tell.

---

### Post by frosch6669 on 2009-10-27
Does the remotecontrol work out of the box?
What about blank screen sometimes when starting?
what about suspend to disk/ram?
what about different monitors(digital analog - gui switching?)
greetings

---

