---
title: "Soundblaster: No sound output"
date: 2014-05-07
forum: Multimedia Software
---

### Post by nicholasapapbologna on 2014-05-07
Hi recently I have downloaded ubuntu 14.04 and when starting up I hear no sound, I don't hear it anywhere in Ubuntu. Pulseaudio shows and output to the soundcard but nothing goes to the speakers. I have the Creative labs sound blaster zx.  My speakers work and the onboard sound card works.  

When entering ALSA I try to raise surround or any of the other options but the value doesnt increase, i can only adjust the PCM and Master.  I have tried changing the slot on the Mobo but made it worse and it wasnt even detecting the sound card ( it had power).  I have tried other solutions from other threads but to no availe but i notice that when i run the: 
```

Sudo apt-get update
```
I get 404 errors on some packages and at the end of the list i see that the "W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages)  404 Not Found"

and

"W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/trusty/main/binary-i386/Packages)  404 Not Found"

Also when i uninstall and reinstall ALSA the sound icon dissapears, but doesnt help in anyway.

Before i had Ubuntu 13.10 (I think) and had the same problem.

When running the command ```
aplay -l
``` I get the list of devices and the one i am interested in is  Creative [HDA Creative], device 0: CA0132 Analog.


Thanks for reading,

Nicky

P.S. I am new to this forum so excuse any errors or misconseptions and stuff.

---

### Post by pnarciso on 2014-05-07
Soundblaster Z is a lemon on linux it simply doesnt output any sound and there is no support. And it seems nobody cares about it.

---

### Post by mörgæs on 2014-05-08
Moving to Multimedia. Let's see if someone here is able to do magic, but the chances are small.

---

