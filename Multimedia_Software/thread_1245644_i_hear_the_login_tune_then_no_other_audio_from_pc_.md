---
title: "i hear the login tune then no other audio from pc at all"
date: 2009-08-20
forum: Multimedia Software
---

### Post by stinger30au on 2009-08-20
for a few days now on my 9.04 desktop i can log in to ubuntu and i hear the music play when i log in and no matter if i play an mp3 or ogg or dvd or what ever i feel like, i get nothing

if i boot up off the live cd, everything works fine

i have checked the basics like the volume controll and that is all fine

i have done some reading thru other threads and found a few commands to run

sudo lshw -c multimedia
 
  *-multimedia            
       description: Multimedia audio controller
       product: AC'97 Sound Controller
       vendor: Silicon Integrated Systems [SiS]
       physical id: 2.7
       bus info: pci@0000:00:02.7
       version: a0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52 module=snd_intel8x0

plus

 aplay -l yields
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


im sure the audio went stupid after an update. i could reinstall 9.04 but i think that would be pointless as i would wind up in the same situation after it had finsihed its updates

if i run

alsamixer

from shell, nothing is muted

any ideas?
thanks

---

### Post by stinger30au on 2009-08-20
fixxed it

done some more searching and  found i had to fireup shell and do this

sudo apt-get install gnome-alsamixer

then restart pc and go to system, preferences, sound

then set everything to alsa audio

restart

fixxed!

yippie

---

