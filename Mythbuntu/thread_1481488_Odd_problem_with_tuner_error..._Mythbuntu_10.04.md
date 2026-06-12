---
title: "Odd problem with tuner error... Mythbuntu 10.04"
date: 2010-05-12
forum: Mythbuntu
---

### Post by agamotto on 2010-05-12
Hallo all, I have put 10.04 on a machine, and have been updating it each time they come out, and have recently discovered an odd problem regarding my television tuners...

I have 1 pvr-150, and 1 HVR-1800 by Hauppauge.  They work fine for the most part, but since doing a clean install of 10.04, I get a seemingly random 'error with tuner' in the System Status.  I can't figure the pattern, as I turn this machine off daily.  Some times it goes days with out this showing up, sometimes it is with every boot.  What log/s should I pull and post to help clarify it?
:confused:

---

### Post by jlagrone on 2010-05-13
I've been having similar problems.  Basically, it looks like mythbackend is being initialized before the proper drivers are loaded so mythtv does not see the card.  Anyway, restarting mythbackend after startup solves the problem for me.  Kind of a pain, but it works.

---

### Post by db260179 on 2010-05-13
> **jlagrone said:**
> I've been having similar problems.  Basically, it looks like mythbackend is being initialized before the proper drivers are loaded so mythtv does not see the card.  Anyway, restarting mythbackend after startup solves the problem for me.  Kind of a pain, but it works.

Unfortunately it is a timing issue. I've attached a modified mythtv-backend.conf that checks to see if the tuner card is ready before starting mysql.

Run Thunar as root (gksu thunar), goto /etc/init, make a copy of mythtv-backend.conf, then copy my version into that folder.

My conf has this assumptions: -
/var/log/mythtv/mythbackend-init.log
mysql.txt is located in ~/.mythtv/ and /etc/mysql

Hope this helps?

P.S you might need to adjust the sleep number in the mythtv-backend.conf to a higher value to give the firmware time to load up

---

### Post by LowSky on 2010-05-13
Sweet I've been looking for someething like this for a while. Thanks db260179. I will test it on my setup.

---

### Post by db260179 on 2010-05-13
> **LowSky said:**
> Sweet I've been looking for someething like this for a while. Thanks db260179. I will test it on my setup.

no problem!

It's ironic, as ubuntu gets faster things start to break :-)

---

### Post by grandpaken on 2010-05-13
I have a similar problem but only when waking up from S3 Sleep.  My PVR-150 does not work 25% of the time and have to reboot.  I've since changed my routine to turn off the PC rather than put it to sleep which works but then again...any processes that need to wake the PC to run do not.  

> **db260179 said:**
> Unfortunately it is a timing issue. I've attached a modified mythtv-backend.conf that checks to see if the tuner card is ready before starting mysql.



---

### Post by db260179 on 2010-05-14
> **grandpaken said:**
> I have a similar problem but only when waking up from S3 Sleep.  My PVR-150 does not work 25% of the time and have to reboot.  I've since changed my routine to turn off the PC rather than put it to sleep which works but then again...any processes that need to wake the PC to run do not.

This article may help

[http://www.mythtv.org/wiki/ACPI_Wakeup#S3_.28Suspend_to_RAM.29](http://www.mythtv.org/wiki/ACPI_Wakeup#S3_.28Suspend_to_RAM.29)

Following on from my mythtv-backend.conf

changing sleep to sleep 30, then adding a sleep for mythwelcome startup script to sleep 45. seems to help alot.

---

### Post by grandpaken on 2010-05-14
> **db260179 said:**
> This article may help

[http://www.mythtv.org/wiki/ACPI_Wakeup#S3_.28Suspend_to_RAM.29](http://www.mythtv.org/wiki/ACPI_Wakeup#S3_.28Suspend_to_RAM.29)

Following on from my mythtv-backend.conf

changing sleep to sleep 30, then adding a sleep for mythwelcome startup script to sleep 45. seems to help alot.

    Thanks, I had come across that article when I was researching the issue but rebooting the system after wakeup didn't sound like a great solution.  Is there some kind of bash script that could be run on S3 wake to reinitialize the capture card driver...something like unmounting and remounting a drive?  In my case it's not a timing issue as the PVR-150 is dead to the world no matter what app I try to use it with or how long I wait.

---

### Post by db260179 on 2010-05-14
> **grandpaken said:**
> Thanks, I had come across that article when I was researching the issue but rebooting the system after wakeup didn't sound like a great solution.  Is there some kind of bash script that could be run on S3 wake to reinitialize the capture card driver...something like unmounting and remounting a drive?  In my case it's not a timing issue as the PVR-150 is dead to the world no matter what app I try to use it with or how long I wait.

It is probably best not to use S3 suspend.

If you still want to persist, a script to restart the udev and hal will re-initialise the drivers. Me personally I would stick to the normal shutdown and wakeup. Booting these days with ubuntu 10.04 is so fast suspend seems sluggish.

---

### Post by dividehex on 2010-05-14
> **db260179 said:**
> Unfortunately it is a timing issue. I've attached a modified mythtv-backend.conf that checks to see if the tuner card is ready before starting mysql.

Run Thunar as root (gksu thunar), goto /etc/init, make a copy of mythtv-backend.conf, then copy my version into that folder.

My conf has this assumptions: -
/var/log/mythtv/mythbackend-init.log
mysql.txt is located in ~/.mythtv/ and /etc/mysql

Hope this helps?

P.S you might need to adjust the sleep number in the mythtv-backend.conf to a higher value to give the firmware time to load up

That upstart script worked for me. I just had to increase the sleep timer to 60.  Thanks!

---

### Post by mjpoetic on 2010-05-15
> **agamotto said:**
> Hallo all, I have put 10.04 on a machine, and have been updating it each time they come out, and have recently discovered an odd problem regarding my television tuners...

I have 1 pvr-150, and 1 HVR-1800 by Hauppauge.  They work fine for the most part, but since doing a clean install of 10.04, I get a seemingly random 'error with tuner' in the System Status.  I can't figure the pattern, as I turn this machine off daily.  Some times it goes days with out this showing up, sometimes it is with every boot.  What log/s should I pull and post to help clarify it?
:confused:

How did you get the HVR-1800 working with MythTV?  I have been scratching my head trying everything that hasn't worked yet. MythTV just has the "Channel Scan" button disabled (under the Channel Editor in mythtv-setup).  It knows the card is there but I can't figure it out.

---

### Post by lank23 on 2010-05-15
I also had this issue with my PVR-150 while doing testing on 10.04. I found a different solution that I posted in this thread.

[http://ubuntuforums.org/showthread.php?t=1414630]("http://ubuntuforums.org/showthread.php?t=1414630")

---

### Post by agamotto on 2010-05-17
I will try that this evening, and see what happens!

---

### Post by agamotto on 2010-05-17
I am not sure how/why the 1800 works in my system, but I have never had a problem with the digital portion of it.  Now, if only the analog tuner could get working...

---

### Post by benlyboy on 2010-05-20
Hi 
I have been living with this problem for a while. Any time my system is powered off, after restarting I have to shut down then restart my backend to get my tuners working.

I tried db260179's mythtv-backend.conf but with at in place my tuners don't seem to work at all

My system is 9.10 and mythtv 0.23


Should that config file have worked with my system?

---

### Post by dangd301 on 2010-05-21
Hi Guys<
 
Im a Newbie, and trying to migrate to Ubuntu, but everytime i try to install something it seems soooo complicated. I hjave a Hauppauge PVR 150, and cannot get it to work, i sure its because im so confused in what programs i need to install. Is there an easy or a windows kind of way in install this? Am i using the wrong Distro for what i need to do?  How do i know what i need and not need install? Im about to give up.

---

### Post by agamotto on 2010-05-22
Thanks for the revised backend.conf file... it did indeed solve the problem!  Now if someone could just get DVD burning again under MythArchive... grin

---

### Post by discobean on 2010-07-20
db260179, good script, but there is a bug, it does not actually work because the test for the device passes every time as true, so it actually never enters the sleep loop.

Replace: while [ -c !$t ]; do
With: while [ ! -c $t ]; do

This will fix the problem, and you will no longer need to have any additional sleeps in the script after the modified part.

---

