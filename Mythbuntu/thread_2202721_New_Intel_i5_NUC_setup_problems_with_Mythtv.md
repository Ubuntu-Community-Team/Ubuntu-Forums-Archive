---
title: "New Intel i5 NUC setup problems with Mythtv"
date: 2014-01-30
forum: Mythbuntu
---

### Post by hugh4 on 2014-01-30
Hi All,
I'm having a few problems with getting mythtv running perfectly on the NUC.
The hardware config is:

Intel i5 haswell NUC (firmware ver 23)
30GB msata SSD
wifi
4TB external USB hard drive
homerun network tuner
IR keyboard

Software:
mythbuntu 12.04.3
kernel 3.13.1

I've updated the kernel from 3.8.0-29 to 3.12 then 3.13.1, don't know if this is the cause or not for issues 1 and 3 below but didn't have these two problems before. Kernel 3.13.1 seems to give me the correct audio settings now.

Problems:
1. From boot, watchtv in mythfrontend does not work. displays "please wait" then goes back to the menu. To get it working I run mythbackend setup, do nothing except stop the backend and start it again, then everything works.
2. The USB hard disk seems to disappear or unmount randomly so then nothing works, usually after hours of use. The hard disk is mounted in etc/fstab.
3. Watching live TV using the frontend works fine except for 1. above, however, watching recorded programs or downloaded videos I now get "frame tearing" about 1/6 the way down the screen. I've only observed this in 3.12 and 3.13.1 unless I've changed some setting and not realised it.
Any help would be greatly appreciated.
Thanks,
Hugh

---

### Post by tuat2 on 2014-01-31
I don't know anything about your hardware, but I experienced your problem no. 1, which was caused by issues with firmware uploading to the tuner card. The firmware didn't upload at first use/initialization of the tuner. Maybe you can check into that direction. For the USB disk problem, check dmesg (syslog), maybe you'll get some infos there.

---

### Post by scstanton1337 on 2014-01-31
I think that both your tearing and "Please Wait" issues are related.  I also have an i3 NUC and was never able to get the VAAPI drivers to work properly for hardware video decoding.  As a result, I had to use the Normal (software) decoding profile which also presented tearing.  I wish the VAAPI code would be updated/fixed/whatever but it seems like that's not a priority with the Myth team.

---

### Post by oldfred on 2014-01-31
I ran across this which may be helpful:

 Intel NUC
[http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html](http://blog.dustinkirkland.com/2013/12/everything-you-need-to-know-about-intel.html)
[http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html](http://blog.dustinkirkland.com/2013/12/why-i-returned-all-of-my-i3-intel-nucs.html)

---

### Post by hugh4 on 2014-02-01
Thanks for the replies.
With problem 3. I changed the video playback from normal to high quality open gl and so far playing back recordings has been good. 
Thought audio was going ok but having 5.1 set instead of stereo, speakers are all mixed up, i.e right speaker playback comes out of back left etc. Stereo setting seems fine, nuc goes to Yamaha A2020 and seems to get surround sound ok.
Have mythtv 0.25, thinking of upgrading to 0.27 to see if that helps.
i read somewhere that a pause in the boot sequence may help but need to find the link again. 
Did look at dmesg but couldn't see anything obvious.
Cheers,
Hugh

---

### Post by hugh4 on 2014-02-06
An update.... Still need some help.

With the HDhomerun, I've found off the web to change the startup process load order. However, all these are old posts and say change /etc/rc5.d (change S##mythbackend to S99mythbackend) and mythbackend is not in this file or others of the type rc#.d. 

Where/how is the mythbackend script run at startup?

With the hard disk randomly disappearing, the only thing I could find was check cables and try another USB port. Swapped to another port last night so fingers crossed.
Cheers.

---

### Post by tuat2 on 2014-02-07
What you are looking for is in /etc/init/mythbackend.conf. The services in this directory are "upstart jobs". It's an event driven system, so it doesn't start programs sequentially, but if their defined requirements are met. Like mythbackend is started (I believe) after the network and udev completed initialization/startup.

To make the backend start later, you basically have two options:
1) Tweak the "start on" line.
2) Add a sleep task (a new .conf file in /etc/init) with some seconds of delay and add this task to/as the pre start script in the mythbackend.conf. (You need a separate task, because the sleep command has no effect when added to the mythbackend.conf directly.)

---

### Post by hugh4 on 2014-02-07
Ok I've created the following conf file called sleephi.conf
# Sleep script for HDhomerun to initialize 
description "mythbackend wait"
start on (local-filesystems and net-device-up IFACE!=lo)
script 
    sleep 5
end script

So before I edit myth-backend.conf just want to check that I change the start on line to:

start on (local-filesystems and net-device-up IFACE!=lo and sleephi)

Is that correct?
thanks
hugh

---

### Post by hugh4 on 2014-02-12
Having major problems with the hard disk disappearing. This can happen even while watching a recorded program.

I've checked the log files:
1. dmesg seems ok except for ACPI errors and an IR pnp error
2. kernel log shows "Feb  9 16:20:21 NUC kernel: [91260.574677] EXT4-fs warning (device sdb1): __ext4_read_dirblock:681: error reading directory block (ino 2, block 0)" type errors
3. syslog gives 
"Feb 12 10:39:01 NUC CRON[8029]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
Feb 12 10:44:46 NUC kernel: [58715.046741] EXT4-fs error (device sdb1): ext4_find_entry:1309: inode #200278017: comm mythbackend: reading directory lblock 0"

The CRON job seems to happen 4 to 5 minutes before the disk disappears. Could this be causing the problem? This cron job runs every 30 minutes so may have nothing to do with it.
All recordings and videos are stored on the 4TB external hard disk, all system files are on the internal SSD.
Any ideas?

---

### Post by hugh4 on 2014-02-13
Just to add when it disappears lsblk -f gives sdc1 instead of sdb1 /mythtv.

---

