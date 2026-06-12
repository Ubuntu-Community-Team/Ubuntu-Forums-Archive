---
title: "Alesis io2 Express + JACK - n00b needs help."
date: 2010-08-20
forum: Multimedia Software
---

### Post by Arizon_Dread on 2010-08-20
Hello!

I just got my Shure PG58 and Alesis io2 Express yesterday (budget equipment I guess). The Alesis card has two channels that each can handle guitar or mic, plus MIDI in/out.

I want to be able to record (mic-audio) through JACK with these HW-parts and route them to Ardour, for instance.
I will happily accept suggestions for intuitive and easy-to-use-software for recording several channels to build up complete songs.
I was playing around with the beatmaker of LMMS for a bit. That's pretty much all the rec-experience I have, so I'm basically a complete n00b in this area.

As I understand JACK, I should route the mic from the left window, into the recording software, in the right window, and if I, for instance, make a beat in lmms that I want to route to ardour, I just connect lmms with ardour (maybe it's a bad example) in JACK and make sure they use the JACK-server as the host. Am I on the right track here?

What happens when I connect the sound card is that JACK shows (under the ALSA-tab) the MIDI channels, but it won't show the mic at all. 

I found this blog (which is quite old) [http://vir.homelinux.org/blog/archives/24-Alesis-IO2.html](http://vir.homelinux.org/blog/archives/24-Alesis-IO2.html) which made me create the file ~/.asoundrc to make the 24/12-bit conversion (I think). 

I seem to be able to record in Audacious (if I use ALSA as host under settings), although I only get one channel to record (got the sound card set to "stereo" on the mic channel), and I can't get audacious to playback the sound either. I can't get JACK to work with audacious and JACK + mic since JACK doesn't pic up the mic.

My PulseAudio Volume control recognizes the mic as I set the io2 as the input (I have my internal sound card set as output here)

I might be mixing drivers and **** wildly without fully understanding how this works, please let me know if I am.

I can provide pictures of my settings later if it's needed, let me know.


Regards,
Hopeful n00b trying to record some home made stuff.
(I'm running Ubuntu 10.04, normal dist, not the ubuntu studio one)

---

### Post by cchhrriiss121212 on 2010-08-20
The sound chain in Ubuntu looks like this: 
sound card > ALSA > pulse/jackd > software

ALSA is the muscle of the audio processing, and pulse is a sound server that works on top of ALSA. Previously many systems would just use straight ALSA, but pulse was introduced to add a few features and give a simple GUI. Jack is also a sound server that works on top of ALSA, so when you start up jack pulse is suspended. Hope that helps you understand how audio works.

> As I understand JACK, I should route the mic from the left window, into the recording software, in the right window, and if I, for instance, make a beat in lmms that I want to route to ardour, I just connect lmms with ardour (maybe it's a bad example) in JACK and make sure they use the JACK-server as the host. Am I on the right track here?
This is exactly how jack works. The only thing I would mention is that LMMS is not very friendly with jack, as it is designed to work without jack. If you want to make beats I'd recommend Hydrogen which is just as simple but has more features. 
If you want a real simple recording DAW, then LMMS is great, but you are missing out on all the extra features and programs you get with using jack audio. It takes a little longer to get used to but it is worth it IMO.

So now, all you need to so is configure jack, which is simple according to the user in that blog. Open up jack and the setup window, which should show your card under the interface dropdown list as something like hw:1. 

Then you can set up jack to use realtime mode. Open a terminal and paste this:
```
sudo gedit /etc/security/limits.d/audio.conf
```
and paste this:
@audio - memlock unlimited
@audio - rtprio 99
Now save and reboot. And if you want even lower latency you should install the rt-kernel from the repos, which I can explain if you are still there after all that. Depending on your PC you could get latency down to <5ms.

---

### Post by Arizon_Dread on 2010-08-20
Thank you very much for your information!

I've tried Hydrogen before, but it always crashed when I tried to save the beats I'd made so I gave up and tried lmms.


I recently bought a new computer and maybe the Hydrogen crashes was due to defect hardware on the old one.

Anyway: I found the card in the input device drop-down in the setup and managed to route the mic to the output to see if it works, and it does!!! 

Thank you very much for your help and explanations! ):P

---

