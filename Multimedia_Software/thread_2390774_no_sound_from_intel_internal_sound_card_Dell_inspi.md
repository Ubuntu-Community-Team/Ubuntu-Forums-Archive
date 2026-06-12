---
title: "no sound from intel internal sound card Dell inspiron 530"
date: 2018-05-02
forum: Multimedia Software
---

### Post by viaciofano on 2018-05-02
Hi hope you can help me to get my sound card working. I know it works with LTS 16.04. I upgraded to 18.04 and cant work out what to do next. I have the sound card listed as dummy? is this right? i can alter the volume but no sound is coming out. I know it is working but something is not quite right??

vincenzo@inspiron530:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
vincenzo@inspiron530:~$ 

i have been trying for days going through some of the trouble shooting guides with no success. 

thanks in advance.

Vincenzo

---

### Post by Yellow Pasque on 2018-05-02
Start here: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by viaciofano on 2018-05-02
[http://www.alsa-project.org/db/?f=3c0771ee5d5a07cbcdbb34698a0ad5ca9cab3a48](http://www.alsa-project.org/db/?f=3c0771ee5d5a07cbcdbb34698a0ad5ca9cab3a48)


Temujin, thank you  I have the link above.

Vincenzo

---

### Post by Yellow Pasque on 2018-05-02
I don't have a lot of time to look at the info at the moment, but I skimmed through it and everything looks good. I would try resetting the pulseaudio user configuration and restarting pulseaudio:
```
rm -rf ~/.config/pulse*
pulseaudio -k
```

---

### Post by viaciofano on 2018-05-02
Temkujin, I appreciate your time and help. I tried the commands and looked up to see if i could find any other help. 

I am stuck again as the following happened with no change

vincenzo@inspiron530:~$ rm -rf ~/.config/pulse*
vincenzo@inspiron530:~$ pulseaudio -k
vincenzo@inspiron530:~$ pulseaudio --check
vincenzo@inspiron530:~$ pulseaudio -D
E: [pulseaudio] main.c: Daemon startup failed.
vincenzo@inspiron530:~$ rm -rf ~/.config/pulse*
vincenzo@inspiron530:~$ pulseaudio -k
vincenzo@inspiron530:~$ pulseaudio --check
vincenzo@inspiron530:~$ pulseaudio -D
E: [pulseaudio] main.c: Daemon startup failed.
vincenzo@inspiron530:~$ pulseaudio
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.
vincenzo@inspiron530:~$ -l /dev/snd.

-l: command not found
vincenzo@inspiron530:~$ 
vincenzo@inspiron530:~$ -l /dev/snd
-l: command not found
vincenzo@inspiron530:~$ sudo service pulseaudio restart
[sudo] password for vincenzo: 
Failed to restart pulseaudio.service: Unit pulseaudio.service not found.
vincenzo@inspiron530:~$

---

### Post by viaciofano on 2018-05-02
Temkujin, I appreciate your time and help. I tried the commands and looked up to see if i could find any other help. 

I am stuck again as the following happened with no change

vincenzo@inspiron530:~$ rm -rf ~/.config/pulse*
vincenzo@inspiron530:~$ pulseaudio -k
vincenzo@inspiron530:~$ pulseaudio --check
vincenzo@inspiron530:~$ pulseaudio -D
E: [pulseaudio] main.c: Daemon startup failed.
vincenzo@inspiron530:~$ rm -rf ~/.config/pulse*
vincenzo@inspiron530:~$ pulseaudio -k
vincenzo@inspiron530:~$ pulseaudio --check
vincenzo@inspiron530:~$ pulseaudio -D
E: [pulseaudio] main.c: Daemon startup failed.
vincenzo@inspiron530:~$ pulseaudio
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.
vincenzo@inspiron530:~$ -l /dev/snd.

-l: command not found
vincenzo@inspiron530:~$ 
vincenzo@inspiron530:~$ -l /dev/snd
-l: command not found
vincenzo@inspiron530:~$ sudo service pulseaudio restart
[sudo] password for vincenzo: 
Failed to restart pulseaudio.service: Unit pulseaudio.service not found.
vincenzo@inspiron530:~$

---

### Post by Yellow Pasque on 2018-05-03
Do you remember if you were prompted to keep/replace configuration files for pulseaudio when you upgraded? If so, which did you choose?
I would try to reinstall pulseaudio:
```
sudo apt-get install --reinstall pulseaudio
```
I'd also consider trying to get a verbose log:
[https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by viaciofano on 2018-05-04
Temujin, thanks I have tried that and it was no successful. I did post the output to a bug and they have confirmed that it is a bug. They also said it is now fixed but i have not been able to get my card working. This is the confirmation. 


[regression] output device not recognized anymore since update 1:8.0-0ubuntu3.9

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1767784](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/1767784)

I can see the issue is found but not a clear way for me to follow. I have updated on the software the last tab to update more softeware but not been able to progress.

thanks in advance. Vincenzo Iaciofano

---

### Post by Yellow Pasque on 2018-05-08
I don't see any indication that any change was made to the pulseaudio package in 18.04. [http://changelogs.ubuntu.com/changelogs/pool/main/p/pulseaudio/pulseaudio_11.1-1ubuntu7/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/pulseaudio/pulseaudio_11.1-1ubuntu7/changelog)
The last change in the package was March 14
You should ask for clarification in regards to 18.04/bionic in the bug report.

---

### Post by viaciofano on 2018-05-10
ubuntu-bug -s audio

the command i used to upload a bug to ubuntu and carried out checks. this helped me as i am a newbie to the commands and control outputs. 

Temujin thanks I have submitted another bug. I managed to trick the pc into working by playing music from my phone while booting up. I now have sound but no sound card confgiured on my settings. I await news from the new bug. 

thanks for your help

---

