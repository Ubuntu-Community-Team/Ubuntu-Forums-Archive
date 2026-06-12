---
title: "IR Blaster Problem [Solved]"
date: 2007-10-26
forum: Multimedia &amp; Video
---

### Post by teet on 2007-10-26
Dear all,

I recently described a problem I was having with a  RS232 IR Blaster purchased from [http://www.irblaster.info/](http://www.irblaster.info/) .  See the following thread:  [http://ubuntuforums.org/showthread.php?t=575370](http://ubuntuforums.org/showthread.php?t=575370)

Since that thread is in the gutsy development section, I am no longer able to edit it, so here is a follow up thread.

I was able to get my IR blaster working by following the advice of the last poster, hexion.  

> To solve it:

sudo m-a fakesource

This will create a directory in /usr/src/linux-source-`uname -r`
In this case, it will be /usr/src/linux-source-2.6.22-14-generic

Then, follow my guide but instead of symlinking to /usr/src/linux-source-2.6.22, do it to that directory you created with fakesource.

It should compile and work.

[http://ubuntuforums.org/showthread.php?t=288229](http://ubuntuforums.org/showthread.php?t=288229)


I'm not sure if I really needed to do the 'fakesource' thing.  I then installed lirc manually by using his guide.  I had to use a pre-release of lirc 0.8.3 because the lirc_serial module is apparently broken in lirc 0.8.2.    [http://lirc.sourceforge.net/software/snapshots/lirc-0.8.3pre1.tar.bz2](http://lirc.sourceforge.net/software/snapshots/lirc-0.8.3pre1.tar.bz2) Hopefully, this problem with lirc will get fixed soon.  Until then, I'm probably not going to upgrade my kernel out of fear of breaking my lirc again.

-teet

---

### Post by gsanse on 2007-10-30
teet,

I am having a very strange problem with the same IR serial blaster you have. To be more precise, I actually purchase a receiver and a blaster at the irblaster site and combined the two in one device using a single DB9 port. It was working perfectly well with Feisty, but when I upgraded to Gutsy it just stopped working. I have followed the ubuntu wiki tutorial and I have managed to make the receiver work. The lirc_serial module loads fine, lircd daemon starts with no problem, but the blaster just does not work.  Using irsend, I can see the xmiter led blinking with my digital camera, but the controlled device just ignores the flashes. To eliminate the possibility of a hardware failure, I tested the combined receiver/blaster with Winlirc and it works perfectly. Also that eliminates a possible problem with the lircd.conf configuration file, as it does work with winlirc. I just don't know how can I troubleshot this problem, any help appreciated.

---

### Post by teet on 2007-10-30
Here is what I know.

When I tried to use the lirc packages from the ubuntu repos I could never get IR transmitting to work.  I knew that my config files should all be fine (I had things working in feisty just fine) and that mythtv should be all setup to work as well (I did an upgrade).

When I finally broke down and installed the lirc-0.8.3 (the preversion) manually by downloading the tarball from lirc.org the blaster started working.

My conclusion:  the lirc package in the repos is broken and lirc_serial can't transmit.

-teet

---

### Post by gsanse on 2007-10-31
I installed the 0.8.3 package and the same thing happens. Transmitter LED does blink but the cable box ignore the flashes. It looks to me the transmitter is working, as I can see the LED flash, but for some reason, the flashes are not being done in the proper way. And I am sure it is not a lircd.conf problem, as it used to work before and it does work with winlirc on the same machine.

Thanks for the reply,

gsanse

---

### Post by gsanse on 2007-10-31
As a final hardware & configuration files, I installed Feisty on a separate partition in the same box. Everything works fine, receiver and blaster. Something is wrong with lirc in Gutsy and I cannot figure it out.

gsanse

---

### Post by gsanse on 2007-11-02
teet,

Would it be too much ask you to post here the steps you took to make the blaster work? I compiled the 0.8.3 pre-version and it still does not work. lirc_serial loads, receiver works, the blaster led blinks, but I cannot control the cable box. Thank you,

gsanse

---

### Post by gsanse on 2007-11-06
I have managed to make the blaster work. To keep it short, one must remove the pre-compiled lirc modules before installing lirc 0.8.3 pre-release from the source.

---

### Post by sica on 2007-11-13
bump.

I have the same problem. Any word on it getting fixed, or maybe a sticky or in the wiki. Took me a few hours before I thought to look for a gutsy specific problem.

---

### Post by columbo on 2008-01-19
Same problem, 

os: kubuntu gutsy 7.10
I have bought light up ir blaster from irblaster.info

My configuration was working to the point that my blaster was sending red light (I have the light up version) but that do nothing on my set top box.

Conclusion: the lirc_serial kernel module is broken in gutsy 7.10

Solution:
# apt-get build-dep lirc
# cd /usr/src
# wget [http://lirc.sourceforge.net/software/snapshots/lirc-0.8.3pre1.tar.bz2](http://lirc.sourceforge.net/software/snapshots/lirc-0.8.3pre1.tar.bz2)
# tar xjf lirc-0.8.3pre1.tar.bz2
# cd lirc-0.8.3pre1
#./setup.sh
# make
# mv /lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_serial/lirc_serial.ko \
#    /lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_serial/lirc_serial.ko.orig
# cp drivers/lirc_serial/lirc_serial.ko /lib/modules/2.6.22-14-generic/ubuntu/media/lirc/lirc_serial/

Restart your system

Note: With this procedure, no need to remove lirc_0.8.2 (installed via apt-get install lirc) and no make install.
Only the kernel module must be 0.8.3

---

### Post by elp99jcm on 2008-01-31
Great, thanks columbo. I now have my transmitter working again, finally after a lot of frustration. I have written about this on this thread:
 [http://http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4155303#post4155303]("http://http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4155303#post4155303")

which is running parallel to this one.

One question, dmesg now reports:

[   78.610669] lirc_i2c: chip 0x10020 found @ 0x71 (Hauppauge PVR150)
[   78.610735] lirc_dev: lirc_register_plugin: sample_rate: 10
[   78.719624] lirc_serial: no version for "lirc_unregister_plugin" found: kernel tainted.
[   79.219956] lirc_serial: auto-detected active high receiver
[   79.219964] lirc_dev: lirc_register_plugin: sample_rate: 0

What is causing the 'kernel tainted' and should I be concerned?

---

### Post by columbo on 2008-02-03
Hi elp99jcm,

Glad that my post helped you.

Concerning the "kernel tainted" see:

[http://www.tux.org/lkml/#s1-18]("http://www.tux.org/lkml/#s1-18")

From what I understand, there is 2 possibilities:

1) the fact that we put the binary module (the one we compile ourselves) directly (cp) where it is expected, maybe this action has for consequence that the module is considered "binary only" by the kernel.

2) problem with the MODULE_LICENSE tag in lirc-0.8.3pre1

In any cases, I don't think you should be concerned by that.

---

### Post by spiregrain on 2008-03-29
I found I could get it to work by adding the softcarrier argument to /etc/modprobe.conf/lirc-serial, like this:

```
#COM1 equivalent, /dev/ttyS0
options lirc_serial irq=4 io=0x3f8 softcarrier=1
#COM2 equivalent, /dev/ttyS1
#options lirc_serial irq=3 io=0x2f8

```

That's with the current Hardy version of lirc.  I Couldn't get any of the recompilation ideas above to work.

---

### Post by teet on 2008-04-27
Has anybody tried this IR blaster with ubuntu 8.04 (hardy heron)?  Is lirc_serial still busted?

It will be a few weeks until I upgrade my system, but I want to be prepared...

-teet

---

### Post by gsanse on 2008-04-27
I have upgrade to Hardy and the blaster is working normally.

---

### Post by teet on 2008-04-27
Awesome!  One less thing I'll have to worry about.

Thanks!

-teet

---

