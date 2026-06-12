---
title: "JACK Squat"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by CrashintoDMB on 2007-08-06
I'm not sure if this should go here or in the beginner section (as i am a beginner). I have Ubuntu Studio for recording, but i don't really know how to use any of the programs that US came with. I have no idea what JACK is, how it's used, or what it's for. I only know it has to be "on" (whatever that means) for some recording programs. I've used Audacity before, but not enough to really know what i'm doing. Coming from Windows, i used Adobe Audition. Are there any programs out there that mirror Audition? We'll start with this first and see where i get. :confused:

---

### Post by OoooMatron on 2007-08-06
Jack is the sound system that all the decent applications go through. It provides low-latency recording and drives all the applications sound.

It's quite amazing really because it allows you to drop virtual cables between applications and have infinite possibilities with routing. Kind of like Virtual Audio Cable for windows but much better and more powerful. this allows you to record music from one app to another or even just syncronise it.

Usually you just run JACK and then open something like Ardour. JACK will see that Ardour is there and then you route Ardours outputs in JACK to the stereo OUT of your soundcard.  The more outputs you configure in Ardour the more you can route through jack, but for most basic users taking the stereo bus from ardour to the outputs on your card is enough. 

I'm not sure what Audition is so i can't comment.

What i can say, despite how efficient and great the audio apps for Linux are (notably Jack and Ardour), the choice and ease of use of apps created on windows is immense and not easy to transfer if yuo started out being windows based.

---

### Post by CrashintoDMB on 2007-08-06
could you explain more about what i have to do to make sure i've set JACK up correctly?

---

### Post by djxcon on 2007-08-06
Have you tried installing the front end to JACK called qjackctl?

This should be in the repositories and you can find more information about it here: [http://qjackctl.sourceforge.net/]("http://qjackctl.sourceforge.net/")

Once you have this installed, it's pretty basic. Click Start to start the JACK server.  There are a lot of options to configure but the main thing is to get JACK running.  If you launch qjackctl from a terminal window, you should be able to see any error messages that occur once clicking on Start (hopefully there are none).

---

### Post by CrashintoDMB on 2007-08-06
i havent tried that but i will. thanks. If i still need some assistance/enlightenment, I'll be back.

---

### Post by xandermann on 2007-08-07
I'm having a similar problem. Jack won't start because, I think, alsa isn't installed. When I try to start jack through the control problem it gives me the alsa not known driver. I've tried to install alsa different ways. Here is one:

sudo apt-get install build-essential fakeroot linux-headers-$(uname -r) alsa-source kernel-package

cd /usr/src/ && sudo tar jfx alsa-driver.tar.bz2

sudo dpkg-reconfigure alsa-source

in the configure screen I pick no to PNP yes to debug and ca0106 (my sound card is a Sound Blaster Audigy SE card)

cd modules/alsa-driver && sudo debian/rules binary_modules KSRC=/usr/src/linux-headers-$(uname -r/ KVERS=$(uname -r)

When I run that last command I get errors during build:
make[5]: *** [/usr/src/modules/alsa-driver/drivers/serialmidi.o] Error 1
make[4]: *** [/usr/src/modules/alsa-driver/drivers] Error 2
make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2
make[2]: *** [modules] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: *** [compile] Error 2
make[1]: Leaving directory `/usr/src/modules/alsa-driver'
make: *** [build-stamp] Error 2

any suggestions on how to install alsa?

---

