---
title: "No sound with MAME"
date: 2010-01-02
forum: Multimedia Software
---

### Post by dunkirk on 2010-01-02
I've been trying to get MAME up and going on Karmic, but I can't get sound working. I'm a long-time Gentoo user. Normally, I would have emerged MAME, and been up and running with my sound system of choice already compiled in. I'm trying Ubuntu, and experiencing perhaps a perfect situation to really compare the two.

I see that "sdlmame" and good, old-fashioned "xmame" (with .x11 and .SDL variants) in the repo. Various posts say that sdlmame is the new hotness, but I've tried both. One thing I notice with sdlmame is that I can't escape from it. Every time I try, it locks up, and I have to `kill -9' from another machine to get my screen back. For now, I'm going to assume that this is due to the sound issue, and reserve judgement on it.

I managed to get sound going, briefly, I think, because I was using sdlmame and libsdl1.2debian-pulseaudio. However, the sound was so stuttering and performance was so poor, I kept trying different things.

sdlmame doesn't give me any help at all at the command line.



david@enterprise ~ $ xmame.SDL -ldp
warning: no mixer plugins available
Digital sound plugins:
sdl                            Simple Direct Library DSP plugin



david@enterprise ~ $ xmame.x11 -ldp
GLERROR: cannot access OpenGL library libGL.so
GLERROR: dlerror() returns [libGL.so: cannot open shared object file: No such file or directory]
Use of OpenGL mode disabled
XDGAOpenFramebuffer failed
Use of DGA-modes is disabled
Digital sound plugins:
esound                         Esound DSP plugin                               
alsa                           Alsa Sound System DSP plugin                    
waveout                        Wave File Output DSP plugin 


I tried installing the libsdl-mixer and libsdl1.2debian-all (instead of -pulseaudio or -alsa), but this hasn't fixed this.

The bottom line is that someone, somewhere packaged "MAME" for Ubuntu, and they assumed some things. What are those things? What's the best chance I have of getting this working? Which version should I be using, and with what sound system? How should/can I configure this to work?

---

### Post by dunkirk on 2010-01-02
I see that if I do this at the command line:

sdlmame -audiodriver pulseaudio -rp /data/Gaming/MAME/rom popnpop

I still do not have sound. HOWEVER, I see that my CPU is NOT pegged, and I can hit the escape button and leave the program. I'm not sure where to take this from here, but it seems to be a step toward a workaround.

---

### Post by dunkirk on 2010-01-02
Aha! "pulseaudio" is bad, "pulse" is good. 

david@enterprise ~ $ sdlmame -verbose  -audiodriver pulse -rp /data/Gaming/MAME/rom popnpop

Setting SDL audiodriver 'pulse' ...

Audio initialized - driver: pulse, frequency: 48000, channels: 2, samples: 512
sdl_create_buffers: creating stream buffer of 57344 bytes


But I still don't hear anything....

---

### Post by dunkirk on 2010-01-02
I don't know why, but this is now working. The only thing I can see is that I switched back to libsdl1.2debian-pulseaudio, and then to libsdl1.2debian-all when it started working. 

sdlmame -verbose -audiodriver pulse -rp /data/Gaming/MAME/rom popnpop

Now my problem is that I want to be able to save these "defaults" when I launch sdlmame from a command line. I can `sdlmame -createconfig ...' with all the other options, and get a config file made, but I can't get sdlmame to read that config file later, even with a `-readconfig'. I guess I can create a wrapper that I can point gmameui at, but I wish it was more straightforward.

And, of course, this screws up updating the list of games...

---

### Post by dunkirk on 2010-01-02
And now every time I start up gmameui, it starts looping through every game in sdlmame. What a freakin ballache this has been.

I was trying to switch away from Gentoo because of the enormous timesink it is. Looks like Ubuntu is just the same crap, different day.

---

### Post by gadbermd on 2010-01-05
Same problem here. I just recently upgraded from Jaunty to Karmic and ran into the exact same issue, no sound, sdlmame would peg the processor when you tried to exit and the only way to escape was to Ctrl-Alt-F1 to a terminal and "kill -9" the process. Thanks BTW Dunkirk for doing the legwork on this, the fix for me was the same: adding the "-audiodriver pulse" command line option. Very annoying.

---

### Post by chuckyp on 2010-01-18
Well the config for sdlmame is in /etc/sdlmame somewhere and it will read it on boot. I've also had problems with getting sound working without X. For somereason when you install xubuntu-desktop or ubuntu-desktop sound starts working for sdlmame. There is a package that is missing.

---

### Post by Yellow Pasque on 2010-01-18
Maybe this will clear things up for you:
[http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html](http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html)

---

### Post by carlob on 2010-01-23
I had the same problem (in Ubuntu Karmic: either no sound or heaviliy distorted sound when using -audiodriver alsa) and I solved this by going to synaptic and installing the package libsdl1.2debian-pulseaudio.
This automatically removes libsdl1.2debian-alsa (or libsdl1.2debian-all).
After this, sdlmame automatically recognizes my audio driver and everything goes ok.

---

### Post by lymphor on 2010-08-31
I'm new to Ubuntu and I apologize if I'll say something that's not useful.
I had problems with MAME audio too: I started using Gmameui and could not hear any audio.
I finally solved my problem by abandoning Gmameui and starting to use Kxmame.
Hope this helps, good luck! :D

---

### Post by jamessimo on 2010-09-23
> **lymphor said:**
> I'm new to Ubuntu and I apologize if I'll say something that's not useful.
I had problems with MAME audio too: I started using Gmameui and could not hear any audio.
I finally solved my problem by abandoning Gmameui and starting to use Kxmame.
Hope this helps, good luck! :D


This has actually helped! I can now have sound on all my MAME games! Shame it is such a horrid looking front end :(

---

