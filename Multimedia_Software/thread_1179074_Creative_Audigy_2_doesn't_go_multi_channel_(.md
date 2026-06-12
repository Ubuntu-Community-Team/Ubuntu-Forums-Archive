---
title: "Creative Audigy 2 doesn't go multi channel :("
date: 2009-06-05
forum: Multimedia Software
---

### Post by ig0r89 on 2009-06-05
Hello!
I've decided to move to (K)ubuntu from Open Suse!
First thing that annoys me is sound: 
- I have a Creative Audigy 2 Value sb0400 (5.1) 
- I use ALSA 1.0.20 on Kubuntu 9.04
- My System settings -> Multimedia looks like: [http://img193.imageshack.us/img193/4708/snapshot1u.png](http://img193.imageshack.us/img193/4708/snapshot1u.png)   
You can see there Rear/Center/Front/etc channels. How can I join them in one? To hear 5.1 ?

Few commands:
> lspci | grep audio
05:00.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Valuealsamixer is not muted

My Kmix: [http://img218.imageshack.us/img218/3599/snapshot3f.png](http://img218.imageshack.us/img218/3599/snapshot3f.png)

And here is my ~/.asoundrc:
> pcm.sndcard{
type hw
card 0
device 1
channels 6
}
pcm.dmix6 {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0660
slave {
pcm sndcard
rate 48000
channels 6
period_time 0
period_size 512
buffer_time 0
buffer_size 10240
}
}
pcm.ch51dup {
type route
slave.pcm softvol
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
}
pcm.softvol {
type softvol
slave {
pcm “dmix6&#8243;
}
control {
name “softMaster”
card 0
count 2
}
}
pcm.duplex {
type asym
playback.pcm “ch51dup”
capture.pcm “hw:0&#8243;
}
pcm.!default {
type plug
slave.pcm “duplex”
}
I think I'm not the only one who run in that problem, but I can't find any answer in search :(

---

### Post by ig0r89 on 2009-06-05
Few details:
I have a Gigabyte P45 DS3L Motherboard, but I've disabled sound in BIOS.

Here is a screenshot from alsamixergui: [http://img231.imageshack.us/img231/4875/snapshot4w.png](http://img231.imageshack.us/img231/4875/snapshot4w.png)
I've "lowed" channels that I can manipulate (Surround/Center/LFE) Surround - is my Rear, Center - Center, LFE - Subwoofer
But I can't manipulate Front (It's 100% on screenshot - but I can't hear any sound :( )

And here is my config, if that can help with the problem: [http://www.alsa-project.org/db/?f=6851c10b44455555ae94800dee488f472cc3156e](http://www.alsa-project.org/db/?f=6851c10b44455555ae94800dee488f472cc3156e)

I'm afraid of one thing:

> 
!!Loaded ALSA modules
!!-------------------
snd_emu10k1

But then I have:
> 
!!AC97 Codec information
!!---------------------------

Is that OK?

And:
> 
!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

Should I have them Running?

Thanks!

---

### Post by ig0r89 on 2009-06-05
OK, I think I'm close:
I've managed to turn the Front speakers **on** by **muting** the "IEC958 Optical Raw" Channel in alsamixergui (anybody knows why it started working?)

But now I have another problem - My Subwoofer behaves like ordinary speaker - It just plays the sound - not the bass. 
What do I have to do now?

I played with this muting and the sound comes from: "Audigy Analog Output Jack" For sure.

---

