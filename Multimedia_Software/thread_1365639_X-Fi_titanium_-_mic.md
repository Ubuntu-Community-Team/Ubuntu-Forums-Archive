---
title: "X-Fi titanium - mic"
date: 2009-12-27
forum: Multimedia Software
---

### Post by eclectik on 2009-12-27
Hi, as the title suggests I have an X-Fi titanium PCI-e, its working fine in terms of audio, and was with the default Ubuntu 9.10 drivers.

Though I used Soundchecks ALSA upgrade script to update ALSA.  Though it changed nothing.

The problem is my mic doesnt work. Im pretty sure its because the __flexi-jack it has, as the mic port doubles as a line-in jack too. 

In windows the Line-in jack is defaulted, and you have to manually change the option in the software to have the mic work. Though I cant figure out how to do this in a Linux environment. I tried the Creative Linux drivers but they didnt even compile:

```
$ sudo make
[sudo] password for eclectic: 
make -C /lib/modules/2.6.31-16-generic/build M=/home/eclectic/Downloads/XFiDrv_Linux_Public_US_1.00
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  LD      /home/eclectic/Downloads/XFiDrv_Linux_Public_US_1.00/built-in.o
  CC [M]  /home/eclectic/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o
/home/eclectic/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:14:26: error: sound/driver.h: No such file or directory
/home/eclectic/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c: In function ‘ct_card_probe’:
/home/eclectic/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:55: error: implicit declaration of function ‘snd_card_new’
/home/eclectic/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.c:55: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/eclectic/Downloads/XFiDrv_Linux_Public_US_1.00/xfi.o] Error 1
make[1]: *** [_module_/home/eclectic/Downloads/XFiDrv_Linux_Public_US_1.00] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'
make: *** [all] Error 2

```

Has anyone been able to figure this out?

:confused:

---

### Post by RedSingularity on 2009-12-27
Have pulseaudio installed?

---

### Post by eclectik on 2009-12-28
Yes sir, I do indeed.

[I]$ sudo apt-get install pulseaudio
[sudo] password for eclectic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pulseaudio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
eclectic@eclectic-desktop:~$ pulseaudio
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

[/I]As you can see, it shows options for my mic in Ubuntu, but I have no audio on it.
[IMG]http://i27.photobucket.com/albums/c176/eclec/audprob.png[/IMG]


[B]I manged to fix it. Using alsamixer I was able to mute the line-in which immediately popped the ambient sounds in my ears. In other words, my mic is working \o/

[/B]Thanks for your reply RedSingularity.

[COLOR=Red]**EDIT2:**[/COLOR] [COLOR=Black]Ok, so I have it sound from the mic. But its still not seen as a system sound. in other words, I cant record from it, and Teamspeak errors on the mic. Also I cant mute the mic, so I hear it constantly, even with the mic muted in the sound properties (note that I CANT mute the mic in the alsamixer options).

Please, some help would be awesome, I really want to ditch windows. This has been a plan of mine for a long time. Before I always used Ventrilo and xfire, which shamefully held me back from a full switch. Now I have xfire working fantastically due to the brilliant plugin for Pidgin. Also now that TS3 is almost on par with Ventrilo (still resource hungry compared to Vent, but its still BETA), Im willing to ditch my vent server for TS3 (which I already have running on my server).

I was excited to think I was there and done. but this mic is holding me back.
[/COLOR]

---

### Post by eclectik on 2009-12-28
Sorry, edited the post, as I havent fxed the issue, just got closer-ish :/

---

### Post by RedSingularity on 2009-12-28
How about the device chooser.  I found i had to manually choose my mic in the device chooser.

---

### Post by igrok2 on 2010-01-19
bump.  Any progress?  I am having the same issue.

---

### Post by sports.car.guy on 2010-01-19
> **eclectik said:**
> Yes sir, I do indeed.

[I]$ sudo apt-get install pulseaudio
[sudo] password for eclectic: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pulseaudio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
eclectic@eclectic-desktop:~$ pulseaudio
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

[/I]As you can see, it shows options for my mic in Ubuntu, but I have no audio on it.
[IMG]http://i27.photobucket.com/albums/c176/eclec/audprob.png[/IMG]


[B]I manged to fix it. Using alsamixer I was able to mute the line-in which immediately popped the ambient sounds in my ears. In other words, my mic is working \o/

[/B]Thanks for your reply RedSingularity.

[COLOR=Red]**EDIT2:**[/COLOR] [COLOR=Black]Ok, so I have it sound from the mic. But its still not seen as a system sound. in other words, I cant record from it, and Teamspeak errors on the mic. Also I cant mute the mic, so I hear it constantly, even with the mic muted in the sound properties (note that I CANT mute the mic in the alsamixer options).

Please, some help would be awesome, I really want to ditch windows. This has been a plan of mine for a long time. Before I always used Ventrilo and xfire, which shamefully held me back from a full switch. Now I have xfire working fantastically due to the brilliant plugin for Pidgin. Also now that TS3 is almost on par with Ventrilo (still resource hungry compared to Vent, but its still BETA), Im willing to ditch my vent server for TS3 (which I already have running on my server).

I was excited to think I was there and done. but this mic is holding me back.
[/COLOR]


You need to setup your mic to capture from. Right now it is just being sent to your speakers. Once you do that it should be all set. You need to with whatever your volume settings app is open up channel configuration and add capture to them.

---

### Post by u6ik on 2010-03-08
This may be a slight side step, but if you have a X-Fi sound card, you will probably also have the default sound chipset of the motherboard too. My solution to this issue was to set up the X-Fi Audio for my speaker output and then wire the microphone through the motherboard sound chipset. A few setting tweaks in the Ubuntu sound preferences (Input set to Internal Audio Analog Stereo and Output set to CA0106 Soundblaster Analog Stereo) and you are there!

This does not resolve the issue with the X-Fi Audio card, but it will get you up and running until Creative/Ubuntu/A kindly programmer come up with a proper solution.

---

