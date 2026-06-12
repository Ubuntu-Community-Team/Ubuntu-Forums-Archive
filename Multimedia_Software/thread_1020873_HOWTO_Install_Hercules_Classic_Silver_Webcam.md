---
title: "HOWTO: Install Hercules Classic Silver Webcam"
date: 2008-12-24
forum: Multimedia Software
---

### Post by gdselzer on 2008-12-24
This a reasonably cheap webcam I got from Newegg.  It did not install automatically with my install of 8.10.  [_[COLOR="Blue"]Google advised me that it has a Sonix chipset and should be supported by gspca under the sonixj module[/COLOR]_]("http://moinejf.free.fr/webcam.html").  Since gspca comes built-in to the 8.10 kernel but my webcam didn't work, I assumed that the kernel driver must be too old a version to work with this cam.  It took me a couple shots to get this right, so I decided to record it for future referral.  I also figured a few others may get this for a Christmas present and might like a shortcut to getting it working.  It requires a little bit of compiling, but nothing that will blow you away. 
This how-to assumes that you have not previously tried to load the gspca from source.  If you have, you will need to clean up all the drivers that were installed previously.

For starters, you will know you have this webcam if, when you run the command:
```
$lsusb | grep 06f8:3004
```
You get:
> Bus 001 Device 003: ID 06f8:3004 Guillemot Corp.
Anything else, and I can't help you.

Since we will be build from source, we need to make sure we have all the tools:
```
$ sudo aptitude install build-essential
```

First we need to have a place to download and keep the source code.  I like to create a directory /opt/src for this, but you can just as easily use another location (eg in your home directory):

```
$ sudo mkdir /opt/src
$ sudo chmod 777 /opt/src
$ cd /opt/src
```

The gspca source lives in the v4l-dvb project.  This project uses Mercurial to allow for easy updating of source.  So let's install Mercurial
```
$ sudo aptitude install mercurial
```

Using mercurial, download the most recent version of v4l-dvb:
```
$ hg clone http://linuxtv.org/hg/v4l-dvb
```

This will actively pull all the most recent source code for this project into a newly created directory called v4l-dvb. If you ever need to update the source (like to fix a bug?) just go to that directory and type:
```
$ hg pull -u http://linuxtv.org/hg/v4l-dvb

```
Before we compile, we need to clean up any gspca stuff already on the system from the original install of 8.10.  The drivers live in the specific folders for your kernel under /lib/modules.  You can identify your kernel by:
```
$ uname -r
```
and locate the /kernel/drivers/media/video/gspca folder.  Or, you can use the below command to quickly remove them:
```
$ sudo rm -r /lib/modules/`uname -r`/kernel/drivers/media/video/gspca
```

There are some modules we need to make sure are not loaded as well before compiling:
```
$ sudo rmmod videodev
```
Check to see if any gspca modules are currently loaded:
```
$ lsmod | grep gspca
```
If any are found, remove them by name:
```
$ sudo rmmod (name of mod here)
```

Now we are ready to compile.  Go into the v4l-dvb directory
```
$ cd v4l-dvb
```

And compile:
```
$ make
```
This will take about 10 mins or so and will compile all the v4l drivers including TV capture card drivers and other stuff.  I'm sure there's a way to only compile what we need, but I'm not smart enough to figure it out.
Once it's done compiling, install it with:
```
$ sudo make install
```

I had to reboot because videodev threw some errors when I plugged in my webcam. So:
```
$ sudo reboot
```

Once it reboots, your camera should be recognized.  Run:
```
$ dmesg
```
and look for something like:
> gspca: main v2.4.0 registered
gspca: probing 06f8:3004
sonixj: Sonix chip id: 11
spca: probe ok
gspca: probing 06f8:3004
gspca: probing 06f8:3004
usbcore: registered new interface driver sonixj
sonixj: registered

When I tried to use Skype, I got very colorful static instead of a picture of Yours Truly. Starting Skype with:
```
$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
fixed it.

A way to start Skype from the menu instead of command line was found here:  [http://ubuntuforums.org/archive/index.php/t-945803.html]("http://ubuntuforums.org/archive/index.php/t-945803.html")
```
$ sudo gedit /usr/local/bin/skype
```
and paste the following two lines into the new file
> #!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

save, then make it executable
```
$ sudo chmod a+x /usr/local/bin/skype
```

That's it!
The color of the picture is a little off, but I'll work on adjusting that later.

Let me know how it goes for you.

---

### Post by frankie:-) on 2009-01-06
Thank you very very much for this post. Worked perfectly for me, after searching a long time for a solution to that problem...

Greetings,

Frank

---

### Post by pavel989 on 2009-01-14
when i plugged my camera back in, ran dmesg, it recognized that it was unplugged and plugged back in, but it doesnt seem to be loading the right module

to the google!

---

### Post by gdselzer on 2009-01-15
pavel989, how far down the steps did you get?  Did you reboot?  Did you get any errors when compiling?  The more info you provide, the better the odds I can help.

---

### Post by pavel989 on 2009-01-16
compiling went fine, rebooted, unplugged and plugged back in the camerea. dmesg recognized the unplugging and plugging, but didnt load anything. i think i need to figure out how to get the system to load the v4l stuff

---

### Post by gdselzer on 2009-01-16
What are the results for:

```
$ ls -al /lib/modules/`uname -r`/kernel/drivers/media/video/gspca
```

and

```
$ lsusb | grep 06f8:3004
```

---

### Post by krist on 2009-01-16
Thanks for your HOWTO, got the camera now working fine with Skype 2.0.72  on kernel 2.6.27 including built-in microphone (which already worked with stock drivers).

---

### Post by kkady32 on 2009-01-16
I have Z Star Vimicro zc0303 webcam,that use gspca driver,after this tutorial and reboot not found gspca 
one time after 30 days i make to work this webcam in 8.10 64 and now after fresh reinstall that will not work

---

### Post by pavel989 on 2009-01-16
```
pavel@pavel-desktop:~$ ls -al /lib/modules/`uname -r`/kernel/drivers/media/video/gspca
ls: cannot access /lib/modules/2.6.24-23-generic/kernel/drivers/media/video/gspca: No such file or directory
pavel@pavel-desktop:~$ lsusb | grep 06f8:3004
Bus 002 Device 003: ID 06f8:3004 Guillemot Corp. 
pavel@pavel-desktop:~$ 

```

i think this has something to do with me running 2.6.24-23-generic

---

### Post by gdselzer on 2009-01-16
pavel, the fact that you do not have any gspca directory leads me to believe that something went wrong during the compiling, otherwise the drivers should be there, regardless of the kernel.  With that said, I have not tried to install this on Hardy, only 8.10, so I can not duplicate your results.

kkady, your camera uses an entirely different chipset and module than the one this post is about.  Check the link at the top of the post to find out which module you need to research.  It looks like it is the zc3xx module.  Good luck.

---

### Post by pavel989 on 2009-01-17
```
 
Removing obsolete files from /lib/modules/2.6.24-21-generic/kernel/drivers/media/dvb/frontends:


[B]Hmm... distro kernel with a non-standard place for module backports detected.
Please always prefer to use vanilla upstream kernel with V4L/DVB
I'll try to remove old/obsolete LUM files from /lib/modules/2.6.24-21-generic/ubuntu/media:[/B]
Installing kernel modules under /lib/modules/2.6.24-21-generic/kernel/drivers/media/:

```

--could that be a problem?

---

### Post by gdselzer on 2009-01-17
Sure strikes me as a clue to the problem, but I'm in over my head on this one.  I know it's a crummy answer, but maybe you should try upgrading to 8.10 and try again.

---

### Post by pavel989 on 2009-01-19
omg i feel so embarrassed, i had no idea i was running 8.04. i thought i had upgraded already. good idea then!

---

### Post by pavel989 on 2009-01-19
well, while upgrading, i went to play a game, and screwed my system, took me a bit to get it running. tried reinstalling v4l. and i noticed that it was still trying to install to an earlier kernel than im using. So i simply re-downloaded the source. instead of a make, ran a sudo make (just to be sure), sudo make install, dmesg'd and it worked!!

now im just trying to find out if its laggy or not, and if it is guess thats my next goal.

Good guide!!

---

### Post by KDDKDD on 2009-01-23
I have a trouble, i did everything, that was written here, my cam started to work, BUT it work normally about 10 seconds, after that everything become red... What shoud i do with it???
P.S. Can i turn on the light on the cam?
P.P.S. Sorry for my english...

---

### Post by gdselzer on 2009-01-26
The color on mine tends toward red, but certainly is not "all red".  Can't help you there.

I have not been able to figure out how to activate the leds on the camera (although I have not tried real hard).  Maybe someone else will drop through and provide some help with that part.

---

### Post by pavel989 on 2009-01-26
about the LED: I eventually plan to check it out, just to see if id be able to do it, as much as i hate em.

My coloring is also off. Ima start experitmenting and see what settings can be changed where.

---

### Post by highgeere on 2009-02-19
Anyone know if the same method will work with the hercules deluxe? I haven't bought it yet but a commenter on newegg mentioned that it shows up as 06f8:3008 instead of 06f8:3004. I don't know if that number has any relevance to the build of the device, or if it's just a product identifier. I guess if it's the latter then knowing the number doesn't really help.

Thanks

---

### Post by TheThinker on 2009-03-12
gdselzer:

You are my hero! I recently just bought the same Hercules model on the gamble that your instructions would work. You just saved me a good $20 for the more expensive yet compatible Logitec brand. And the camera works like a charm; some blue or red coloring but overall good 800x600 video. Thanks big time!

---

### Post by Diego_Tristan on 2009-04-06
Hi!
I'm a beginer in using ubuntu and I have a problem with my Hercules Classic Link webcam. More specific, I don't know how to install it!
I searched the forums on other Hercules webcams, and I did all that was written there, including what is written here
I even installed some ov51x stuff
Still it does not work!
I still don't now if i need to plug the webcam before installing the drivers, or after.
Thanks and excuse my english mistakes.

---

### Post by TheThinker on 2009-04-06
Diego_Tristan:

Sorry, but I think the instructions were only meant for the Hercules Classic Silver webcam, not your Hercules Classic Link. After installing the V4L drivers, did you try using this command in the terminal when your camera was connected? 

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so <name of video program you want to use>

So, if you're using Ekiga then it would be:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so ekiga

Let us know if this works. If it doesn't, substitute v4l2compat.so for v4l1compat.so and try again. Cross your fingers.

---

### Post by Diego_Tristan on 2009-04-07
First of all, how do I install vl4 drivers?

---

### Post by TheThinker on 2009-04-07
> **Diego_Tristan said:**
> First of all, how do I install vl4 drivers?

The answer to your question is at the beginning of this thread, provided by gdselzer. You said before that, "I searched the forums on other Hercules webcams, and I did all that was written there, including what is written here"

When you said "here" I assumed you actually read this thread. It seems you didn't.

---

### Post by Diego_Tristan on 2009-04-07
Sorry, my mistake; I did all that was written at the begining of this thread, only i didn't know that doing that it will install those drivers. So i gues I installed them.
Next in terminal i wrote the line you sad to me:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so ekiga

 and I've got this message:

ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

Another fact about my web cam is that when I plugged into usb the blue light always stays on. 
I hope in the end i will be able to install it, with your help, of course

PS: on another forum it says that the web cam is not suported 

[http://forum.ubuntu-fr.org/viewtopic.php?pid=2545777#p2545777](http://forum.ubuntu-fr.org/viewtopic.php?pid=2545777#p2545777)

In that case, is there anything to do? (Exept, of course, crossing my fingers :))

---

### Post by TheThinker on 2009-04-08
Diego_Tristan:

Sorry man, I don't know what else to say. Sadly, not all webcam chipset manufacturers provide linux drivers, so you might be out of luck. However, have you ever considered either of the following:

1) Dual-booting your hard-drive with linux and windows, with windows strictly for your webcam's video conferencing, therefore taking up little hard-drive space.
2) Exchanging/replacing your camera for a logitec brand, or a brand that supports UVC? See here: [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
3) Keep searching and tweaking your drivers to find out what works.

Should you choose option two, you should be able to find a good deal on a webcam online somewhere. Logitec is the a top choice for linux compatibility, but newer models might be too pricey for your tastes. I wouldn't be surprised if you find one on e-bay that you like for cheap.

Good luck. ;)

---

### Post by godsucker on 2009-06-08
I refer myself to the post of Diego_Tristan, since I have a similar problem. The error message that shows when starting skype by executing
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 
is also:
ERROR: ld.so: object '/lib/modules/2.6.25.20-0.1-default/kernel/drivers/media/video/v4l1-compat.ko' from LD_PRELOAD cannot be preloaded: ignored

I am aware, that it is v4l1-compat.ko and not the v4l1compat.so file. But searching for the *so file was not succesfull (ran "find . -name v4l1compat* from root dir) and *ko was the closest match. Skype actually detects the cam but only a green, fuzzy image is showing up, which is already better than before.

Obviously, v4l1compat.so was not installed and i don't know why. Any comments on that? Followed the instructions from the first post. Additional info: I am using Opensuse 11.0, but this should not be an issue, since compilation will be the same.

---

### Post by godsucker on 2009-06-08
sorry for bugging the forum with opensuse stuff. for any opensuse guys stumbling over this thread, i just found the answer to my problem:

[http://forums.opensuse.org/hardware/414813-msi-starcam-clip-driver-not-installing.html](http://forums.opensuse.org/hardware/414813-msi-starcam-clip-driver-not-installing.html)

---

### Post by portilhe on 2009-06-24
Hi, Thanks for this fix! I have Ubuntu 9.04 installed and I ran all the steps on your post. Everything worked fine untill the last bit. When I run

```
portilhe@gavdos:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

I get

```
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
```.

I have no idea what that means. Any help?

---

### Post by pebe on 2009-07-23
Works on Hercules Dualpix HD Webcam also. Tested with amsn messenger, abit slow though, maybe the camera is slow I don't know.. Picture perfect. Thanks for the guide.

---

### Post by chute on 2009-07-23
Great HowTo, gdselzer, it worked perfectly. Very clear instructions, thanks a lot.

Setup here is Jaunty 9.04 with kernel 2.6.28-13 generic. Cheese recognized the Classic Silver straight ahead and Skype, with the help of the LD_PRELOAD... bit, works fine too.

I hope you will dig deeper into the led and color issues very soon, gdselzer ;)

---

### Post by kswenson on 2010-01-05
FYI, you don't need to do any compiling anymore, you just need to open skype with:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

---

### Post by puppett on 2010-01-08
> luca@puppet:/opt/src/v4l-dvb$ uname -r
2.6.31-9-rt
luca@puppet:/opt/src/v4l-dvb$ lsusb 
Bus 001 Device 002: ID 04b8:082b Seiko Epson Corp. Stylus DX5050
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 06f8:3004 Guillemot Corp. 
Bus 002 Device 002: ID 07d1:f101 D-Link System DBT-122 Bluetooth
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


sorry but it didn't work for me ;-( and for my Ubuntu 9.10 (rt-kernel).
I think it didn't cause of the error in the compiling... btw now no softwares are recognizing my webcam. Before doing this process I cpould only see strange distorted colors and not my clear image.


> luca@puppet:/opt/src/v4l-dvb$ make
make -C /opt/src/v4l-dvb/v4l 
make[1]: ingresso nella directory «/opt/src/v4l-dvb/v4l»
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/opt/src/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/opt/src/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/opt/src/v4l-dvb/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/opt/src/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/2.6.31-9-rt/build
make -C /lib/modules/2.6.31-9-rt/build SUBDIRS=/opt/src/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.31-9-rt'
  CC [M]  /opt/src/v4l-dvb/v4l/dvb_frontend.o
/opt/src/v4l-dvb/v4l/dvb_frontend.c: In function 'dvb_frontend_stop':
/opt/src/v4l-dvb/v4l/dvb_frontend.c:710: error: implicit declaration of function 'init_MUTEX'
make[3]: *** [/opt/src/v4l-dvb/v4l/dvb_frontend.o] Error 1
make[2]: *** [_module_/opt/src/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-9-rt'
make[1]: *** [default] Errore 2
make[1]: uscita dalla directory «/opt/src/v4l-dvb/v4l»
make: *** [all] Errore 2
luca@puppet:/opt/src/v4l-dvb$ 

> luca@puppet:/opt/src/v4l-dvb$ sudo make install
make -C /opt/src/v4l-dvb/v4l install
make[1]: ingresso nella directory «/opt/src/v4l-dvb/v4l»
-e 
Removing obsolete files from /lib/modules/2.6.31-9-rt/kernel/drivers/media/video:

-e 
Removing obsolete files from /lib/modules/2.6.31-9-rt/kernel/drivers/media/dvb/cinergyT2:

-e 
Removing obsolete files from /lib/modules/2.6.31-9-rt/kernel/drivers/media/common:

-e 
Removing obsolete files from /lib/modules/2.6.31-9-rt/kernel/drivers/media/dvb/frontends:

Installing kernel modules under /lib/modules/2.6.31-9-rt/kernel/drivers/media/:
/sbin/depmod -a 2.6.31-9-rt 
make -C firmware install
make[2]: Entering directory `/opt/src/v4l-dvb/v4l/firmware'
Installing firmwares at /lib/firmware: vicam/firmware.fw dabusb/firmware.fw dabusb/bitstream.bin ttusb-budget/dspbootcode.bin cpia2/stv0672_vp4.bin av7110/bootcode.bin 
make[2]: Leaving directory `/opt/src/v4l-dvb/v4l/firmware'
make[1]: uscita dalla directory «/opt/src/v4l-dvb/v4l»

Now I'm thinking about giving this webcam to my father, and tacke (and try) his logitech... but how can I go back to the status quo? Can you help me please?:frown:

---

### Post by teacosy on 2010-03-17
hi... im having some problems getting the camera to work...
im using kubuntu 9.10
on make, towards the end, i do get a couple of errors:

```

make[3]: *** [/opt/src/v4l-dvb/v4l/firedtv-1394.o] Error 1                               
make[2]: *** [_module_/opt/src/v4l-dvb/v4l] Error 2                                      
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'                    
make[1]: *** [default] Error 2                                                           
make[1]: Leaving directory `/opt/src/v4l-dvb/v4l'                                        
make: *** [all] Error 2 

```sudo make install seems to go ok [although i didnt notice a /lib/modules/2.6.31-20-generic/kernel/drivers/media/video/gspca directory or file after install]

after reboot i dont get any entries for: 

dmesg | grep gspca

or for:

lsmod | grep gspca 
or
lsmod | grep videodev

since i removed the modules with:

sudo rmmod videodev...

am i missing something here?

anyone had this issue before?

thanks

t

---

### Post by SawmSawn on 2010-03-29
Hey guys! I got the same problem like my beforeposter, does anyone maybe have some suggestions what to do if compiling fales? Thank you. And now neither my sound nor my microphone works. grr

---

### Post by kenshir on 2010-04-20
Hello, I give my feedback :)
Thank you very much gdselzer for your great job, it made me able to install Hercules Classic Silver under Ubuntu 8.04 with 2.6.27 kernel.

Like pavel989 I encountered this message during the make install process:

> **pavel989 said:**
>  
[B]Hmm... distro kernel with a non-standard place for module backports detected.
Please always prefer to use vanilla upstream kernel with V4L/DVB
I'll try to remove old/obsolete LUM files from /lib/modules/2.6.24-21-generic/ubuntu/media:[/B]


Anyway, my cam is now working perfectly with ekiga. So I guess this message doesn't mean that it's necessary to upgrade to 8.10.
I'm still experiencing some troubles with skype video input, but I hope to fix that soon.

Last thing: before that, I plugged the cam into another computer with Ubuntu 9.04. I didn't need any compilation, camera was recognized and it worked out of the box. I just had to use the specified LD_PRELOAD command launching skype, and video input was already all right.

---

