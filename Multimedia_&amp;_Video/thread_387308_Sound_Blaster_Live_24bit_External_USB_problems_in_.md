---
title: "Sound Blaster Live 24bit External USB problems in Edgy"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by martorrie on 2007-03-18
Hello!

I have a fresh install of Ubuntu 6.1 Edgy. After installation I plugged in my external usb-soundblaster and rebooted. The OS has recognized the device, since aplay -l produces the following:

**** List of PLAYBACK Hardware Devices ****
card 2: External [SB Live! 24-bit External], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Alsamixer starts up normally. The issue I have is that whenever I try to get some sound (either by playing music files or by using the gnome sound control test buttons) - I only get static noise from my speakers. It's this strange tik-tik-tik sound. :confused: 

Any clues about how to get this thing working would be highly appreciated. 

Thx

---

### Post by martorrie on 2007-03-22
Still no luck getting this thing to work... I'm beginning to suspect it's a hardware conflict since my ubuntu boots up slower with the soundblaster connected to usb. And all sound control utilities react veery slow (alsamixer or gnome sound control applet). I've got no other usb devices connected, so beats me..

---

### Post by PCalitrack on 2007-03-25
I have the Soundblaster Live External 24-bit, and have gotten sound to work for all of my speakers. I created a .asoundrc file in my home directory and also disabled my native sound card modules in the file /etc/modprobe.d/blacklist. This has worked for me throughout my linux experience, so hope this helps.

Here's my .asoundrc file:

> 
pcm.dmix51 {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0666
slave {
pcm "hw:0,0"
channels 6
period_time 0
period_size 1024
buffer_size 8192
rate 44100
}
}

ctl.dmix51 {
type hw
card 0
}

pcm.stereo {
type plug
slave.pcm "dmix51"
ttable.0.0 1
ttable.1.1 1
}

pcm.!default {
type route
slave.pcm "dmix51"
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 1
ttable.1.4 1
ttable.0.5 1
ttable.1.5 1
}

pcm.duplicate {
type plug
slave.pcm "dmix51"
slave.channels 6
route_policy duplicate
}


---

### Post by sdgreen on 2007-03-25
This looks good, but how does one use the script. How is it loaded and from where?

I am completely lost when it comes to scripts.

---

### Post by martorrie on 2007-03-26
Thanks PCalitrack. I did find the same settings in the forums and have already tried them to no avail. I don't need 5.1 sound because I only have two speakers which I use(d) to listen music. 

I have posted this as a bug now.

I've tried to read guides on configuring alsa with these setting files, but these guides seem to assume that you are a sound expert, and a programmer.

It has become obvious to me that alsa is a low-level sound driver system that needs a lot of manual configuring and knowledge. Where to get that knowledge from - well, beats me.

---

### Post by limit223 on 2008-05-16
I'll drop a thanks for PCalitrack, too!
I've got my SB live usb card working in all 6 channels (5.1) after I blacklisted the internal card and I changed /etc/modprobe.d/alsa-base 

options snd-usb-audio index=0
options snd-intel8x0 index=1

but still I do not how to make access to controls in alsamix(kmix) for all these channels.
All I can see is PCM and Mic controls in Output

If anyone has an ideea how?
PS: Hardy Heron system here.

---

