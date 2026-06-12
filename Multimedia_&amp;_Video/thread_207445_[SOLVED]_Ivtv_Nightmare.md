---
title: "[SOLVED] Ivtv Nightmare"
date: 2006-07-01
forum: Multimedia &amp; Video
---

### Post by SPW06 on 2006-07-01
Hi,

I'm running Kubuntu 6.06 and have a WinPVR 150.

I know (maybe I'm wrong...)  I need ivtv...I've looked everywhere and cant find instructions that work. There are numerous sites out there and they all are different and lead to dead ends...has anyone got this to work?

Also, once I get my card to work, how do i set up IR?

I'm also in need of a TV app that  has a "one-touch record" so I can record from my VCR.

---

### Post by MonkeyNet on 2006-07-02
Hey there,

I am using a PVR150 and had little problems setting it up. I used Hyam's MythTV guide, however there are a couple of changes that need to be made. Have pasted the IVTV part of the guide here with changes already made for Dapper (I am assuming that you are using Dapper)

+++++++++++++++++START PASTE+++++++++++++++++
5. Install IVTV (10 minutes)
5.1 Prepare the build environment

To me, this is the hardest part of getting the entire MythTV solution to work -- creating the build environment to be able to compile ivtv properly. It's not really ivtv's fault; it's just that pretty much all distributions nowadays require a certain amount of work out of you, if you are going to do plucky things like compile the kernel and/or kernel modules. Luckily, I've gone through some pain so that you don't have to.

First, type the following, and remember the output.

    uname -r

For my system, the output is

    2.6.12-10-686

It is important to remember both parts. The 2.6.12 is the kernel version (henceforth referred to as <kver>), and the -10-686 part is the extra tag. This will be important later. Now, to ins
+++++++++++++++++START PASTE+++++++++++++++++tall the proper kernel source, execute the following command:

    apt-get install linux-source-<kver> linux-headers-`uname -r`

where <kver> is replaced with your current kernel version that you found out from the uname -r command above. Recall that mine was 2.6.12.  And notice the backticks in the above command!  The tick used here is the one next to your 1 key, not the quote next to your Enter key.

Now that we have the source, we need to unpack it and configure its pseudo-location:

    tar xvjf /usr/src/linux-source-*.tar.bz2 -C /usr/src/
    ln -s /usr/src/linux-source-<kver> /usr/src/linux
    ln -s /usr/src/linux /lib/modules/`uname -r`/build

Now switch to the /usr/src/linux directory:

    cd /usr/src/linux

We need to make sure to remember our extra "tag" in the kernel source Makefile. Edit /usr/src/linux/Makefile with your favorite editor, and set the variable EXTRAVERSION (about the fourth line of the Makefile) to your "tag" that we found out from the uname -r command above. My tag was -10-686, for example. Therefore, the line in the Makefile should read something similar to:

    EXTRAVERSION = -10-686

Now lets configure the source tree to get it ready for compiling, without actually compiling it:

    cp /boot/config-`uname -r` /usr/src/linux/.config
    make oldconfig
    make prepare0
    make scripts

Lastly, do the following:
+++++++++++++++++START PASTE+++++++++++++++++

    cd /lib/modules/`uname -r`/
    ls -l build

If this symbolic link points to /usr/src/linux, we don't have to do anything.  However, if it does not, manually delete it and make the link yourself:

    rm build
    ln -s /usr/src/linux build

Yay! We finally have our build environment ready. Now on to the compilation and installation of the ivtv drivers. 
5.2 Compile and install ivtv drivers - 0.4.1 drivers and later

IMPORTANT: If you want to use the 0.4.0 drivers, please do not follow the remainder of section 5 here!  Go to the 0.4.0 ivtv driver HOWTO and follow those instructions. 

Let's go the the ivtvdriver.orgsite and download the latest stable 0.4.x version of the ivtv drivers, and extract them (as of now, this is version 0.4.5).  NOTE that for Ubuntu Breezy, you cannot use the 0.6.x series of the driver; this is for kernels 2.6.16 and later. 

    cd /usr/src
    wget [http://dl.ivtvdriver.org/ivtv/archive/0.4.x/ivtv-0.4.5.tar.gz](http://dl.ivtvdriver.org/ivtv/archive/0.4.x/ivtv-0.4.5.tar.gz)
    tar xvfz ivtv-0.4.5.tar.gz

64-bit users need to look here for further instructions.  Now, compile your ivtv drivers and utilities:

    cd ivtv-0.4.5
    make
    make install

During your make install, it could be that the installer reports that there are conflicts for the files that it is trying to install. IMPORTANT: do not ignore these conflicts! After each conflict, it will tell you exactly the command to issue to "hide" the offending file. Execu
+++++++++++++++++START PASTE+++++++++++++++++te each command it tells you, and rerun "make install" until there are no more conflicts.

In some rare cases (I don't believe that this will happen to you, but I am leaving this bit here just in case) the drivers end up installed in the wrong place; they land in /lib/modules/<kver>/ivtv rather than /lib/modules/`uname -r`/ivtv. So, check on this. If they are installed incorrectly, you can fix this just by copying

    cp -r /lib/modules/<kver>/ivtv /lib/modules/`uname -r`/

The Hauppauge cards require firmware files, as the firmware is not stored in the ROMs on the card.  We must download and install these properly now.  To do this,

    cd utils
    wget [ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip](ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip)
    wget [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip)
    unzip pvr_2.0.24.23035.zip 
    ./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
    cp HcwMakoA.ROM /lib/firmware/v4l-cx25840.fw
    cp HcwFalcn.rom /lib/firmware/v4l-cx2341x-enc.fw
    mv /lib/modules/ivtv-fw-dec.bin /lib/firmware/
    mv /lib/modules/ivtv-fw-enc.bin /lib/firmware/
    cp ../v4l-cx2341x-init.mpg /lib/firmware
    ln -s /lib/firmware/ivtv-fw-dec.bin /lib/firmware/v4l-cx2341x-dec.fw 

After this set of commands, if you execute

    ls -ltra /lib/firmware/

You should see

    drwxr-xr-x 3 root root 4096 2005-12-18 10:04 ..
    -rw-r--r-- 1 root root 262144 2005-12-23 20:05 ivtv-fw-enc.bin
    -rw-r--r-- 1 root root 262144 2005-12-23 20:05 ivtv-fw-dec.bin
    -r--r--r-- 1 root root 14264 2005-12-23 20:08 v4l-cx25840.fw
    -r--r--r-- 1 root root 376836 2005-12-23 20:08 v4l-cx2341x-enc.fw
    -rw-r--r-- 1 root root 155648 2005-12-24 13:33 v4l-cx2341x-init.mpg
    lrwxrwxrwx 1 root root 41 2006-01-03 00:40 v4l-cx2341x-dec.fw -> /lib/firmware/ivtv-fw-dec.bin
    drwxr-xr-x 2 root root 4096 2006-01-03 00:40 .

Now lets tell Ubuntu that we have ivtv modules. Edit /etc/modules, and just stick "ivtv" at the end of the file. Also edit /etc/modprobe.d/aliases, and put the following line in where it fits:

    alias char-major-81-0 ivtv

If you have a PVR-500, you also need to add the following line as well:

    alias char-major-81-1 ivtv

Then, do the following:

    depmod
    modprobe ivtv
    dmesg
+++++++++++++++++START PASTE+++++++++++++++++

If, at the end of the output of dmesg, you see a section starting with ==START INIT IVTV== and ending with ==END INIT IVTV==, you are in good shape, as long as the text in between these markers is not filled with errors. Mine wasn't, so it was time to write this up and take a break.
5.3 Verification of IVTV drivers

This section is not meant to be exhaustive, but to cover a couple of steps that you can do to make sure that your ivtv drivers are working properly.  First, capture a raw MPG stream to a file:

    cat /dev/video0 > /tmp/test.mpg
     (hit Ctrl+C to stop the capturing)

and play the file using mplayer:

    mplayer -vo xv /tmp/test.mpg
+++++++++++++++++START PASTE+++++++++++++++++

If you get a picture, that's great; time to move on to the MythTV install.  If not, it could be that the tuner is just not tuned to a viewable channel.  Shut down mplayer, and while that is running, let's use the command line utility ivtv-tune to change channels:

    mplayer -vo xv /dev/video0
    ivtv-tune -c # -d /dev/video0 (in a separate terminal/konsole)

Where "#" is replaced by the channel that you want to tune to.  If you have a PVR-500, you might want to try the same steps above, but with /dev/video0 replaced with /dev/video1.  If you are able to watch TV in this way, great!  Ivtv is working just fine.

+++++++++++++++++END PASTE+++++++++++++++++

Hope this helps.

---

### Post by SPW06 on 2006-07-02
Almost there,

All went well until:
./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip

I  ran perl ./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip

The file ivtvfwextract.pl doesn't exist.

What am I doing wrong?

---

### Post by MonkeyNet on 2006-07-02
Ok. Are you sure you are in the utils directory?

Try this:
```
pwd
```

you should be in the following directory:
```
/usr/src/ivtv-0.4.5/utils
```

If you are in that directory, make sure that the file exists.

Let me know how you go

---

### Post by SPW06 on 2006-07-02
So close,

depmod
 modprobe ivtv
 dmesg
FATAL: Module ivtv not found.

I edited the right files, I don't understand

ls -ltra /lib/firmware/
total 1084
drwxr-xr-x  3 root root   4096 2006-05-30 21:19 2.6.15-23-386
drwxr-xr-x  3 root root   4096 2006-06-30 12:47 2.6.15-25-386
lrwxrwxrwx  1 root root     28 2006-07-01 21:13 v4l-cx2341x-dec.fw -> lib/firmware/ivtv-fw-dec.bin
drwxr-xr-x  4 root root   4096 2006-07-01 21:22 .
drwxr-xr-x 19 root root   4096 2006-07-02 21:02 ..
-rw-r--r--  1 root root 262144 2006-07-02 21:34 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 2006-07-02 21:34 ivtv-fw-dec.bin
-r--r--r--  1 root root  14264 2006-07-02 21:35 v4l-cx25840.fw
-rw-r--r--  1 root root 155648 2006-07-02 21:35 v4l-cx2341x-init.mpg
-r--r--r--  1 root root 376836 2006-07-02 21:35 v4l-cx2341x-enc.fw

---

### Post by SPW06 on 2007-08-02
A simple upgrade to Ubuntu 7.04 Feisty Fawn solved this

---

