---
title: "Please Help Lost Audio / No Audio"
date: 2010-01-02
forum: Multimedia Software
---

### Post by mindbucket on 2010-01-02
I am currently having an issue with 9.10. All Audio was working yesterday, yet now I can't get any audio play back via CD-Video-Mp3-or system audio...

aplay -l  (gives me this output)

conduit@conduit-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I pulled up alsamixer  for some reason I am unable to adjust the master volume control. The Master volume is not muted...although I am able to adjust other input channels {pcm, line, CD, mic, beep,} Master & Front are not able to my knowledge to be adjusted ...

Question : Should I reinstall alsamixer?

The only reason I can think it's not working I had to kill -9 Rhythmbox it locked up on me.

I am at a bit of a loss on a solution at the moment. All help would be well received..

Thanks in advance

---

### Post by |Porsche on 2010-01-02
I have had audio issues with Ubuntu for quite sometime. My fix is to do:
```
lsof | grep pcm
```
kill the processes that are using anything that looks audio related, pulse audio related etc..
After that I do a
```
killall -9 pulseaudio
```
Audio works after that. There are sometimes where pulseaudio doesnt launch after you kill it and other times it does. Do a 
```
ps -ale | grep pulseaudio
```
to see if its running. If it isn't simply launch it by typing pulseaudio.

This works for me.

---

### Post by mindbucket on 2010-01-02
|Porsche Thank you for the fast response!

Sadly however this did not solve the audio issue.
ps -ale | grep pulseaudio (gave me this output)


 conduit@conduit-laptop:~$ ps -ale | grep pulseaudio
1 S  1000  2662     1  0  80   0 - 21192 poll_s ?        00:00:00 pulseaudio

And pulseaudio  (rendered this output)

E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

Again thank you for any and all help !!

---

### Post by mindbucket on 2010-01-02
Also I hear a audio tone when shutting down PC...like a warning beep.?

Anyone with any ideas?

I would not like to do a fresh install again, As I have 9.10 almost where I want it.

Any ideas on code to reinstall alsamixer?

---

### Post by mindbucket on 2010-01-02
> **mindbucket said:**
> Also I hear a audio tone when shutting down PC...like a warning beep.?

Anyone with any ideas?

I would not like to do a fresh install again, As I have 9.10 almost where I want it.

Any ideas on code to reinstall alsamixer?

Not sure why but when I put my pointer on the volume applet 

it reads [Output: 100% 0.00dB Dummy Output]  ???

---

### Post by mindbucket on 2010-01-02
Followed advice from this thread [http://ubuntuforums.org/showthread.php?t=1316634](http://ubuntuforums.org/showthread.php?t=1316634)

sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload

After restart Dummy Output was back..
had to do 

sudo alsa force-reload {sound is back with that code}

____________________________
thanks to 
TacheDeChoco, Surrendermonkey ,mammoth23,
Solved 
editing sudo /etc/modprobe.d/alsa-base.conf 

adding 
options snd-hda-intel probe_mask=1 model=auto 
to bottom of list 
save and restart

---

