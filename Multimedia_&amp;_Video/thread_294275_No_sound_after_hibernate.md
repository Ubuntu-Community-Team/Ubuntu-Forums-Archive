---
title: "No sound after hibernate"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by pgilmon on 2006-11-06
Hi all.

I can suspend and hibernate my laptop with (almost) no problem, but after hibernating, I get no sound through my Intel-HDA audio device. Suspending, however, works allright.

I have tried restarting alsa (/etc/init.d/alsa-utils restart), with no luck. I have found a way of making it work after hibernating: stopping alsa, unloading all the sound-related modules, loading them again and starting alsa. However, this solution is no acceptable for me, since it requires sutting down gdm and starting it again (otherwise, I can't remove the sound modules beacuse it keeps on telling me that they are being used). Is there a way of unloading and loading those modules without sutting down gnome, or any other solution to get alsa to work after hibernating?

HW: HP Pavillion dv5161, sound detected as Intel HDA, centrino duo.

Thanks in advance.

---

### Post by tommie74 on 2007-06-17
I´ve had the same problem, no sound after waking from hibernate, and found a solution in launchpad. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/80893)

The problem seems to be related to a change in the kernel. An updated kernel is available for download:

[http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb](http://rookery.ubuntu.com/~kyle/kernels/salgado/2007-04-25/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb)

install using package manager or 

```
dpkg -i /home/***your user name***/Desktop/linux-image-2.6.20-15-generic_2.6.20-15.28_i386.deb
```

hope this works for you too, as it did for many others,
Thomas.

---

### Post by tec on 2007-07-24
Another fix working for many users without having to install another kernel seems to set another hibernation mode in the acpi settings.

To try this edit /etc/default/acpi-support
and set 'HIBERNATE_MODE=shutdown'
to 'HIBERNATE_MODE=platform'

If hibernation still works, you should have sound again. If not, undo the changes.
This solution was posted in the same bug thread mentioned above.

---

### Post by tommie74 on 2007-07-24
The fix above:
> To try this edit /etc/default/acpi-support
and set 'HIBERNATE_MODE=shutdown'
to 'HIBERNATE_MODE=platform'
didn't work for me, it made my keyboard disfunctional after hibernation.
But it was worth trying, for installing a new kernel for such a problem is like using a bulldozer to kill an ant.

---

### Post by Jettechen on 2007-08-07
My kernel version 2.6.20.16 and Ubuntu7.04
But modify HIBERNATE_MODE=shutdown to platform seems no use to me.
It still no audio after hibernate/suspend.

---

### Post by scholzilla on 2007-08-07
Have you checked out [this ]("http://ubuntuforums.org/showthread.php?t=511152&highlight=hibernate")post? Though it's meant to fix a complete failure to hibernate, but it both fixed my failure to hibernate and restored my sound after hibernation. I have Intel HDA as well.

Hope this helps!

---

### Post by nacy_4_u on 2007-08-21
[B]Another solution friends (if previous wont work ..)

Friends it just simple step ..
1. hibernate your system with pcm ,master ,line-in turn to mute 
         It can be done by double clickin on sound icon on panel there mute all button .

2. When u wake up from hibernate ..
        Double click on sound icon again and turn them to unmute .

                     It will work ( it did for me )

Another solution firends (if previous dont work)

1. Hibernate your system normally .
2. When you want sound , double click on sound icon on panel and mute all channel like master,pcm ,line-in everythin .
3. Set your systen to suspend(by single right clicking on icon ) from Battery icon (for laptops), desktop can choose other normal way.
       suspending sysem takes around 50 seconds (not a big task )
4. Recover from suspend after few seconds and again open volume control(ctrl+O) and unmute all channels (pcm,master)
5. Play your music player and get sound back ..

                   This will surely work as it workd on more than 10 diffrent config system 
                                          for any further querry in dis contact me on  gmail - [email]nacky4u@gmail.com[/email] / [email]nacky_4_u@yahoo.com[/email]

[/B]

---

### Post by bodymind on 2007-11-13
> **tec said:**
> Another fix working for many users without having to install another kernel seems to set another hibernation mode in the acpi settings.

To try this edit /etc/default/acpi-support
and set 'HIBERNATE_MODE=shutdown'
to 'HIBERNATE_MODE=platform'

If hibernation still works, you should have sound again. If not, undo the changes.
This solution was posted in the same bug thread mentioned above.

it did the trick for me.. thank you :)

---

