---
title: "AVerMediaTV Hybrid+FM Volar"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by StratosL on 2006-11-27
Originally posted on the Ubuntu Users list:

Hi there.

The above mentioned tv usb stick is supposed to be compatible with linux.

The customer support people were very helpful and fast in directing me
to the correct driver download for linux.

[http://tinyurl.com/yjflfy](http://tinyurl.com/yjflfy)

That installer works with 6.06 LTS, however even in case it does not
find the kernel it was built against, it builds a new one driver, so
long as the kernel source is installed.

From the help file:

QUOTE
1.3 Tested Distributions

    The following distributions are officially supported:

    1. Open SuSE Linux 10.0
    - kernel 2.6.13-15-smp, 2.6.13-15-default

    2. Mandriva Linux 2006
    - kernel 2.6.12-12mdksmp, 2.6.12-12mdk

    3. Fedora Core Release 3
    - kernel 2.6.9-1.667smp, 2.6.9-1.667

    4. Fedora Core Release 4
    - kernel 2.6.11-1.1369_FC4smp, 2.6.11-1.1369_FC4

    5. Fedora Core Release 5
    - kernel 2.6.17-1.2174_FC5smp, 2.6.17-1.2174_FC5

    6. Debian 3.1
    - kernel 2.6.8-3-686-smp, 2.6.8-3-686

    7. Ubuntu 6.06 LTS
    - kernel 2.6.15-23-686, 2.6.15-23-386
UNQUOTE

I run Edgy, so I installed kernel headers and the kernel source. Then I
extracted the kernel source. However, in the directions is says:

QUOTE
If the installer have to rebuild driver to support updated or customized
kernel, kernel source must be available or installer will not work. If
unsure, check if there are C header files (*.h) under this directory:

# ls /lib/modules/`uname -r`/source/drivers/media/dvb/dvb-core/
UNQUOTE

In that directory, I have only "Kconfig" and "Makefile"

When I run the installer, it fails and I want to rule out the
possibility of something that I do wrong about the kernel source.

The message from the installer is:

> $ sudo sh ./AVERMEDIA-Linux-A828-0.03-beta.sh
> ./AVERMEDIA-Linux-A828-0.03-beta.sh: 24: [[: not found
> Verifying archive integrity...
> ./AVERMEDIA-Linux-A828-0.03-beta.sh: 33: [[: not found
> Extracting archive...
> ./AVERMEDIA-Linux-A828-0.03-beta.sh: 42: [[: not found
> Invoke installer...
> # # # # # # # # # # # # # # # # # # # > > ./installer.sh: 21: [[: not found
> # # > > ./installer.sh: 25: [[: not found
> # # # > > ./installer.sh: 30: [[: not found
> # # > > ./installer.sh: 34: [[: not found
> # # ./installer.sh: 36: let: not found
> # ./installer.sh: 37: let: not found
> # # > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > # # > > > > # # > > > > > > # # > > > > > > > > > > > > > # # > > > > > > > > # # > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > # # > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > > ./installer.sh: 229: Syntax error: Bad for loop variable
> # > ./installer.sh: 230: e: not found
> #
> #

If it's not the kernel, then I can go back to the support desk and ask
for new directions. Any hints would be welcome.

Thanks,

Stratos

---

### Post by Enverex on 2007-01-10
I know this is an old post but it's the only one about this device so I'm posting to it.
The errors you're getting are because of Ubuntu using DASH rather than BASH for the /bin/sh simlink. So you need to change that back and the installer works... sort of. At least it starts now...

It still fails complaining:
> make -C /lib/modules/2.6.17-10-generic/source O=/lib/modules/2.6.17-10-generic/build SUBDIRS=`pwd` 
make: *** /lib/modules/2.6.17-10-generic/source: No such file or directory. Stop.

I have Kernel Headers and Source installed so I don't know what I'm missing :(

---

### Post by StratosL on 2007-01-18
Hey, that was actually helpful!

I switched to bash (temporarily) and then created a symlink 

sudo ln -s /usr/src/linux-headers-2.6.17-10-generic /lib/modules/2.6.17-10-generic/source

For the first time the installer started but it did not produce a driver in the end. I have sent the log to Avermedia.

Stratos

---

### Post by StratosL on 2007-01-18
FYI, these are the first error lines in the log:

tmp/avm-install/installer/src/aver/osdep_dvb.c:88:20: error: dvbdev.h: No such file or directory
/tmp/avm-install/installer/src/aver/osdep_dvb.c:89:19: error: demux.h: No such file or directory
/tmp/avm-install/installer/src/aver/osdep_dvb.c:90:23: error: dvb_demux.h: No such file or directory
/tmp/avm-install/installer/src/aver/osdep_dvb.c:91:20: error: dmxdev.h: No such file or directory
/tmp/avm-install/installer/src/aver/osdep_dvb.c:92:24: error: dvb_filter.h: No such file or directory
/tmp/avm-install/installer/src/aver/osdep_dvb.c:93:21: error: dvb_net.h: No such file or directory
/tmp/avm-install/installer/src/aver/osdep_dvb.c:94:28: error: dvb_ringbuffer.h: No such file or directory
/tmp/avm-install/installer/src/aver/osdep_dvb.c:95:26: error: dvb_frontend.h: No such file or directory

---

### Post by Enverex on 2007-01-18
Yeah, seems Linux .17 changed quite a bit from .15 so much so that the driver isn't compatible even for compiling so it just doesn't work. I contacted Avermedia but they just blew me off with the "Currently we only support the... blah blah blah" BS response so I'm not happy. If someone with some skill looked at the source we may be able to get somewhere, but until that time we seem to be at the mercy of companies with false advertising.

---

### Post by Gladier on 2007-01-25
taken from [HERE]("http://doc.ubuntu-fr.org/materiel/tnt/a808&prev=/search%3Fq%3D07ca:b808%2Bubuntu%26hl%3Den%26lr%3D%26client%3Dfirefox-a%26rls%3Dcom.ubuntu:en-US:official%26hs%3DDOK%26sa%3DG")

and modified to suit.

Im running edgy, latest kernel (.17) and the rest of that banter on custom hardware.

~~~~~~~~~

you were correct Enverex - about the shell issue.

so we need to make the following adjustments to AVERMEDIA-Linux-A808-0.17-beta.sh with vi or with pico - ignore the fact that the last line is incomplete
```

//On line 1  This changes from sh to bash
#!/bin/bash
//On line 32 no idea what it does but it fixes it 
#exit 
//On line 46 once again changing from sh to bash
bash -i ./installer.sh 
```

okidoke - so now the installer runs woohoo! but you will notice that it complains that it cant find the sources.

1) install linux-headers-`uname -r` and linux-source
2) decompress the archive in /usr/src (this might already be done)
3) create a symlink ```
cd /lib/modules/`uname -r` && sudo ln -s /usr/src/linux-source-2.6.17 source
```

now run the installer  and dont forget your sudo

---

### Post by Enverex on 2007-01-26
Well it still doesn't work because the precompiled versions are for non-matching kernels and if it tries to compile the kernel it starts but then fails due to not being able to find some DVB files (must be an ABI change or something in regards to the kernel DVB).

Did you actually try this yourself?

---

### Post by Gladier on 2007-01-26
Actually tried this myself - however i am using 6.10 not 6.06

and after many hours of fiddling i managed to break ubuntu somehow - rebuild time. so ill rebuilt it and on a base edgy ill rerun everything.

enverex has your script panic error changed since modifying the script?

care to post your uname -a? you might be on a different kernel to me.

---

### Post by Enverex on 2007-01-26
I got the script working ages ago by switching sh back to bash rather than dash, but as I said and explained before it still didn't work.

I'm on Feisty now so I think there's virtually no chance of it working (it fails slightly differently when trying to compile against .20 than .17 but it's still a failure due to kernel ABI changes which means unless Aver actually stand up to their "Linux Compatible!" claim then we're still stuck.

---

### Post by Gladier on 2007-02-11
Once again taken from my favorite place
and yes i have run this on edgy and successfully compiled the kernel module


~~~~~~~~~~~~~~~~~~~~ 
Download initially the installer here.

It is about a script which will decompress the modules precompiled for certain distributions or will compile to it your if necessary.

Install the package dialog. ($ sudo apt-get install dialog).

   1.
      Decompress the installer
   2.
      Launch to it with sudo

Then follow the instructions to the screen by choosing the normal installation.

If you miss the kernel-sources:

   1.
      install the package linux-source
   2.
      install the package linux-headers-`uname -r`
   3.
      decompress the file  even if you are running something like 2.6.17-11-386
 ```
cd /usr/src 
 sudo tar -xvf linux-source-2.6.17.tar.bz2
```
   4.
      Create a symbolic link towards the sources```
Cd /lib/modules/ `uname -r`
sudo ln -S /usr/src/linux-source-2.6.17 source
```
   5.
      start again the installation

~~~~~~

and then it just compiled

---

### Post by Enverex on 2007-02-11
Problem is that now I'm on 2.6.20 (Feisty) thus it wont compile due to ABI changes it seems so back to square 1.

```
make -C /lib/modules/2.6.20-6-generic/source O=/lib/modules/2.6.20-6-generic/build SUBDIRS=`pwd` 
make[1]: Entering directory `/usr/src/linux-source-2.6.20'
  CC [M]  /home/enverex/src/A828-install/aver/osdep.o
/home/enverex/src/A828-install/aver/osdep.c:1233:25: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/enverex/src/A828-install/aver/osdep.c: In function &#8216;SysInitWork&#8217;:
/home/enverex/src/A828-install/aver/osdep.c:1233: error: &#8216;INIT_WORK&#8217; undeclared (first use in this function)
/home/enverex/src/A828-install/aver/osdep.c:1233: error: (Each undeclared identifier is reported only once
/home/enverex/src/A828-install/aver/osdep.c:1233: error: for each function it appears in.)
/home/enverex/src/A828-install/aver/osdep.c: In function &#8216;SysRequestIrq&#8217;:
/home/enverex/src/A828-install/aver/osdep.c:1280: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
make[3]: *** [/home/enverex/src/A828-install/aver/osdep.o] Error 1
make[2]: *** [_module_/home/enverex/src/A828-install] Error 2
make[1]: *** [_all] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.20'
make: *** [default] Error 2
```

---

### Post by Gladier on 2007-02-11
well this teaches you for doing the update early :P

so you actually have an a808 or an a828. - im using the a808 drivers with an a808 dongle.

---

### Post by Enverex on 2007-02-11
> **Gladier said:**
> well this teaches you for doing the update early :P

so you actually have an a808 or an a828. - im using the a808 drivers with an a808 dongle.

Nothing to do with doing an update early. If I was on Gentoo or LFS I'd have exactly the same problem. This thread is for the AVerMediaTV Hybrid+FM Volar (A828) NOT the A808 (which isn't the AVerMediaTV Hybrid+FM Volar).

---

### Post by kingmanowar on 2007-03-25
Hello

I had exactly the same problem, however now (in feisty) the a808 is supported directly in the kernel. You do not have to download the drivers.

[http://doc.ubuntu-fr.org/dib0700](http://doc.ubuntu-fr.org/dib0700)

I have an AVerTV DVB-T Volar A808 and it works fine on feisty.

Good luck.

---

### Post by lebabyg on 2007-04-16
Sorry this is late, are you saying that the A808 works out of the box in feisty, because I'm thinking of buying one.

---

### Post by Enverex on 2007-04-16
Sounds like it, but the A828 is still just a brick.

---

### Post by kingmanowar on 2007-04-19
Yes it works really well, using the drivers from the kernel. (I have a a808 from avermedia)

---

### Post by Astrak on 2007-08-18
The 0.07 version of the A828 driver was released about a month ago.
This driver is said to work with ubuntu 7.04, but I cannot confirm it.
I can confirm it works on ubuntu 7.10 (gutsy) with kernel 2.6.22, though.

Here is the download url:
[http://www.avermedia.com/EN/default.aspx?TYPE=test.htm&PT=downloadD1&tv_TCAT_POS=0&CATNO0=D&IDX=2.1&CNT=1&CATNO1=D2&UCN=BAB4C&PID=471071067-1556](http://www.avermedia.com/EN/default.aspx?TYPE=test.htm&PT=downloadD1&tv_TCAT_POS=0&CATNO0=D&IDX=2.1&CNT=1&CATNO1=D2&UCN=BAB4C&PID=471071067-1556)

Enjoy!

---

### Post by stoilis on 2007-08-21
I'm on Feisty amd64.

I was able to compile it and install it. Judging from the dmesg output, it works OK.

However, I was unable to run any TV or radio application with various and different problems but I think those are because of a my computer. For example, a problem error regarding DGA refers to a nVidia incompatibility, but then why doesn't radio work either?

Anyway, I'll figure it out, somewhen. I think it should work for any normal person with a normal computer and a normal feisty installation.

---

### Post by DeadEyes on 2007-09-08
I've just got a828 to work on Feisty.

I downloaded the drivers from Avermedia and the compile/install went ok once I added the dialog program and created the symbolic link to the sources as mentioned earlier in the thread.
With tvtime I was able to get a picture but no sound, took me a while to cop on tvtime is for analogue.

Now for the good bit DVB-T
From the reps get dvb-utils
Then follow the instructions [here]("http://linuxtv.org/wiki/index.php/Testing_your_DVB_device") it's the scan section that's important.

I need to also download and install w_scan. I got as far as the tzap section but I couldn't get tzap to work. But I did have the channels.conf which I had created for me I called this ie-Dublin which wasn't in the dvb-utils list. I copied this file into ~/.xine and ~/.mplayer.

After launching xine and selecting dvb and then opening the playlist I was able to select all the channels I get in windows.

To be honest I didn't really expect to get anywhere with dvb on Linux, now I am now one happy camper.

---

### Post by gdp77 on 2007-10-07
I bought AverTV Hybrid + FM Volar (usb stick). I downloaded latest drivers for linux64. Since I am a noob, I can't install the drivers. As I understand it, I must compile the driver.

Please give me exact information regarding how I do that.

I have a file "A828_LinuxDrv_v0.07_x64Beta.sh".

What must I do with it?

---

### Post by DeadEyes on 2007-10-10
Hi gdp77 lets see if we can get you up and running.
first up try
```
sudo sh A828_LinuxDrv_v0.07_x64Beta.sh
```
and see what message you get, at this point I'm not really expecting it to work.
If the error output mentions anything about "dialog" then goto to synaptic package manager and install the program called dialog once complete try running the previous command again.
At this point it might complain about missing linux source files.
Go back in synaptic and install linux-source. Then install linux-header for the version of the kernal your using.
You now need to create a symbolic link so the installer can find the sources
```

cd /lib/modules/ `uname -r`
sudo ln -S /usr/src/linux-source-2.6.17 source

```
Edit: the version number above may be different for you change as required.
This has been detailed earlier by Gladier.
For the third time try running the installer. Fingers crossed it should work at this point
I think that's enough to be getting started with, and if you get this far it's more of less plain sailing. Follow the link in my previous post and try to work out what you need to do. It more straight forward  than it first appears but it takes a bit of reading to get your head around it.

---

