---
title: "No sound after suspend/hibernate"
date: 2009-12-07
forum: Multimedia Software
---

### Post by whalogreg on 2009-12-07
I recently did a fresh install of 9.10 on my Gateway MD7818 laptop. I've never had any issues with sound before on this laptop with linux or windows until now. When ever my laptop sits unused for a period of time, or goes into suspend OR hibernate, I lose sound after waking it up. Any idea where I can start with this?

---

### Post by RedSingularity on 2009-12-07
When the sound is down look at the System>Admin>system monitor and see if pulseaudio is running.

---

### Post by whalogreg on 2009-12-07
Yes, pulseaudio is running.. It is in "sleeping" status..

---

### Post by RedSingularity on 2009-12-08
Ok when you have no sound try this................

sudo killall pulseaudio && sudo pulseaudio && exit

---

### Post by whalogreg on 2009-12-08
This is my output..

greg@greg-laptop:~$ sudo killall pulseaudio && sudo pulseaudio && exit
[sudo] password for greg: 
W: main.c: This program is not intended to be run as root (unless --system is specified).
E: core-util.c: Home directory /home/greg not ours.

---

### Post by RedSingularity on 2009-12-08
Oh sorry try this.............

sudo killall pulseaudio && pulseaudio && exit

---

### Post by whalogreg on 2009-12-09
Output...

E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

---

### Post by RedSingularity on 2009-12-09
Ok try running them like this then............

1)  sudo killall pulseaudio

then...............

2)  pulseaudio & exit

---

### Post by DanYoSon on 2009-12-09
i am having the same problem and tryed the commands getting the same output as whalogreg.

something that i knoticed was when watching the prosess 'pulseaudio' in system monitor when running sudo killall pulseaudio it does not dissapear or change. even killing it in system monitor does not work. hope this helps.

---

### Post by RedSingularity on 2009-12-09
Try deleting the pulse folder in your home dir.  When in the home directory press ctl+H  to display hidden folders.  Find the folder named .pulse and delete it.  Then reboot.

---

### Post by DanYoSon on 2009-12-10
deleting the folder did not do anything for me, any other ideas??
let me know if you need other info.

---

### Post by RedSingularity on 2009-12-10
Have you tried reinstalling pulse?  

sudo apt-get autoremove --purge pulseaudio

then.........

sudo apt-get install pulseaudio

---

### Post by btforsythe on 2010-03-15
Any luck? I'm running Fedora but have the same issue.

> **whalogreg said:**
> I recently did a fresh install of 9.10 on my Gateway MD7818 laptop. I've never had any issues with sound before on this laptop with linux or windows until now. When ever my laptop sits unused for a period of time, or goes into suspend OR hibernate, I lose sound after waking it up. Any idea where I can start with this?

---

### Post by jukingeo on 2010-04-03
Hello all, 

I have a Dell Dimension 4600 with an MAudio Delta 44 sound card on Ubuntu Studio 8.04.  I also have the same problem in which my audio is muted when I resume from suspend/hibernate.

I have tried some of the hints posted earlier in this thread and that didn't work, the latter part of the thread just confuses me.

Anyway, what I found that DOES get me my audio back without rebooting is to go into the terminal and type this:

sudo alsa force-reload

This DOES get my sound back.  Now I know the easy way out would be to create a button on my desktop to click on when my computer resumes, BUUUUT, I don't want that, I would like my machine to resume WITH my sound restored as well without any extra hoop jumping.  Does anyone know of a way to get that?

Thank You,

Geo

---

### Post by jfenn2199 on 2010-05-08
Well a work around that has worked for me was upon resume

Volume Control > Mute All> Unmute 


And sound resumes.  Again it's just a work around.

---

### Post by teet on 2010-06-02
> **jfenn2199 said:**
> Well a work around that has worked for me was upon resume

Volume Control > Mute All> Unmute 


And sound resumes.  Again it's just a work around.

I'm running ubuntu 10.04 lucid lynx.

The mute all --> unmute thing works for me as well.  Thanks for the tip!

Now if I could just figure out how to automate that.

-teet

---

### Post by whalogreg on 2010-06-05
> **teet said:**
> I'm running ubuntu 10.04 lucid lynx.

The mute all --> unmute thing works for me as well.  Thanks for the tip!

Now if I could just figure out how to automate that.

-teet

Wish that worked for me. Still got nothing on this.. :(

---

### Post by jukingeo on 2010-08-14
Hello All,

I am surprised that I am reading that Lucid still has the hibernate/resume problem with the audio.  You think after all the versions since Gutsy that they would have solved that issue by now.  I am a little peeved about reading that.

At any rate what has been working on my system (currently Hardy) is:

sudo alsa force-reload

I have since made made a desktop button so I don't have to type that every time in the terminal, but I still have to enter my password, and that is a pain.  If I COULD automate it on resume, then I would be fine with that.  What would be better is if you could disable the mute on hibernate in the first place.

Geo

---

### Post by woodensoul on 2011-03-27
I'm having the same problem with no sound after resuming from hibernation and none of the posted solutions work.  I'm running the AMD 64 bit version of 10.10 on a Gateway laptop.  

In addition to the sound problem, my touchpad doesn't work on resume either.  It takes a restart to get it to work.

I'm new to ubuntu and these forums.  Is there a "bug tracker" or something similar so that I can see if this is a know bug that is being worked on?

---

### Post by jukingeo on 2011-04-02
> **woodensoul said:**
> I'm having the same problem with no sound after resuming from hibernation and none of the posted solutions work.  I'm running the AMD 64 bit version of 10.10 on a Gateway laptop.  

In addition to the sound problem, my touchpad doesn't work on resume either.  It takes a restart to get it to work.

I'm new to ubuntu and these forums.  Is there a "bug tracker" or something similar so that I can see if this is a know bug that is being worked on?

Hello, Welcome to the forums.

I hate to be the harbinger of bad news, but this has been an on-going problem that for some reason never gets properly fixed.  I have a new machine now with Lucid 10.04 and what happens now is worse than the issue I had with 8.04.  Yes, that is right, it is worse.  Now my machine gets stuck in a loop when it goes into hibernate.  In fact it does this with all power saving modes.

As of now I have given up on using hibernate with Ubuntu and just let the screen go into a screen saver and if I know I am going to be away from the machine long, I just turn it off.

It does strike me as weird as to why a simple (or what seems to be a simple) issue like this has been lingering from release to release.  I have reported it several times (as many others have I am sure of that).  It could be that it may not be a priority issue.  I hope it does get fixed soon though.   At least with version 8.04, all I had to do was create a script button to initiate the sound reset when I returned to my machine.   Now I can't even use hibernate at all.

I have not looked into a work around for 10.04 (or above), but there might be one.

Good luck!

Geo

---

### Post by lidex on 2011-04-03
From alsa documentation
> reloading modules across APM suspend-and-resume
-----------------------------------------------
During suspension many peripherals are switched off; on resuming the
machine these peripherals need to be re-initialized.  Many ALSA
drivers do this properly but some still do not.

If this problem affects you and if your ALSA drivers are built as
loadable modules and your kernel supports module unloading then you
can work around the problem by unloading the driver before suspending
and loading it again after resuming.  This will be done for you
automatically if you add the name of the problematic sound card driver
module to the variable force_unload_modules_before_suspend variable in
/etc/default/alsa.  E.g., if your CS46XX and AZX cards don't work
properly after resuming from APM suspend, add the names of their
driver modules to the list:

    force_unload_modules_before_suspend="snd-cs46xx snd-azx"


restoring sound volumes across APM suspend-and-resume
-----------------------------------------------------
alsa-base provides an APM script in /etc/apm/scripts.d/alsa to
automatically store/restore sound volumes during APM suspension.
Since this option relies on alsactl, please install the recommended
alsa-utils package.

unloading modules
-----------------
If you want to unload ALSA driver modules then you will have to stop
all applications that are using ALSA device files.  You can do both
in one step by running:

    alsa force-unload


---

### Post by woodensoul on 2011-04-04
"restoring sound volumes across APM suspend-and-resume
-----------------------------------------------------
alsa-base provides an APM script in /etc/apm/scripts.d/alsa to
automatically store/restore sound volumes during APM suspension.
Since this option relies on alsactl, please install the recommended
alsa-utils package."

I'd love to try the quoted fix, but...

How do I find which sound card driver is loaded?

How can I install alsa-utils package.  A web search doesn't return much.  Once it's installed, how do I automate the sound restoration upon resume?

---

### Post by lidex on 2011-04-05
Try the simple version first. You can just specify "all" and all the modules will be unloaded. To edit:
```
gksu gedit /etc/default/alsa
```

Add **all** between the quotes in this line:
```
force_unload_modules_before_suspend=""
```

So now it looks like this:
```
force_unload_modules_before_suspend="all"
```

Save the file and close. Now suspend/resume and see if it worked.

BTW alsa-utils is in the default ubuntu install.

---

### Post by woodensoul on 2011-04-09
Thanks for the tips.  I did what you said, but still get the same behavior on suspend/resume.  Hibernate/resume works though.

It doesn't really belong in this thread, but my touchpad doesn't work after suspend/resume either.

---

### Post by lidex on 2011-04-10
Reload alsa as a work-around:
```
sudo alsa force-reload
```

---

### Post by pastim on 2012-05-28
I had the same problem with my maudio 2496 card (snd_ice1712).  After coming out of hibernation it would not work at all. I tried the solutions proposed in earlier posts but none worked.

I also have a USB headset (snd_usb_audio) and a creative xfi card (snd_ctxfi), which both work fine.  After much searching I found a solution for me (on 12.04) on a German site at:

[http://forum.ubuntuusers.de/topic/suspend-problem-m-audio-audiophile-24/](http://forum.ubuntuusers.de/topic/suspend-problem-m-audio-audiophile-24/)

The script I used is below, called resume_maudio in /etc/pm/sleep.d

```

!/bin/bash

. /usr/lib/pm-utils/functions

resume_maudio() {
    sudo rmmod -w snd_ice1712 snd_usb_audio snd_ctxfi &
    sudo fuser -s -k /dev/snd/*
    sudo modprobe snd_ice1712
    sudo modprobe snd_usb_audio
    sudo modprobe snd_ctxfi
    sudo killall pulseaudio
    sudo pulseaudio --system -D

    amixer -q -c 0 set 'DAC',0 100%
    amixer -q -c 0 set 'DAC',1 100%
}

case "$1" in
        hibernate|suspend)
                # Stopping is not required
                ;;
        thaw|resume)
                resume_maudio
                ;;
        *) exit $NA
                ;;
esac

exit $?

```

then

```

sudo chmod +x /etc/pm/sleep.d/resume_maudio

```

I was concerned that the adjustment of the maudio DAC levels would not always work because the card numbers vary, but since the maudio card is the first to be re-instated, the scripts appears to work OK.

To see which snd_... modules you have, you can use lsmod.

On coming out of hibernation all cards are muted, but unmuting them isn't hard, and least they work :D.

---

### Post by nbd on 2012-11-08
Thanks pastim!

Seems that this ice1712 bug dates back a long time: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93273](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93273)

Same solution also here: [http://ubuntuforums.org/showthread.php?t=1282745](http://ubuntuforums.org/showthread.php?t=1282745)

---

