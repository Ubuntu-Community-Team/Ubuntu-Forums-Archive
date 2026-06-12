---
title: "Gnomeradio problem"
date: 2010-05-01
forum: Multimedia Software
---

### Post by Vortex_nc on 2010-05-01
Hi guys

I have a new install of Karmic on my system with a flyvideo 3000 tv card installed. My problem is that it doesn't find any radio channels and the input channel is completely wrong.

I don't have any sound on gnomeradio and can't find the config files to change the input channel. The only input option available to me is dig1 - can anyone point me in the right direction?

I have already read the Howto for this tv card and changed the device to radio0 in the setup. I have setup tvtime perfectly with sound channel as well as with a 5.1 surround configuration. 

I really need help with this one because I am missing my favourite radio channel. and I want to get rid of my windows installations once and for all!

Update: I did a system update and some things have changed: the radio tower graphic on gnomeradio is now green (I assume it is getting a signal) but no sound yet.

Regards and advanced thanks

Vortex

---

### Post by Rodemire on 2010-05-08
hi,
i have a similar problem,i see you have been posting on multiple threads. I've spent a lot of time looking for the solution and it seems there isnt any out there yet. I dont have much internet access so camt do a system update anytime soon.
If anyone can help out, please do, i hate logging on to windows just so i can listen to FM radio.

---

### Post by Vortex_nc on 2010-08-18
This is somewhat of a shameless bump (has been 3 months) 

I still cannot get gnomeradio to output sound, after reading my dmesg I know that the signal is catching on the card but still no sound.

The card is a Flyview2000 which does not support digital sound output. Unfortunately gradio reports the only mixer source as dig1, no other options.

I would really appreciate any help.

Update: I have since this thread switched to kradio4 and a kubuntu system. still no luck. kradio crashes under kde and on my gnome ubuntu install (updated to lucid since first post in thread) kradio only gives me static. The gnome kradio install I think is my best bet but I need to know what stream URL to use (pipe or device) as playback mixer. /dev/mixer gives me static and /dev/mixer:pcm,mic,line all gives me device not recognized errors

---

### Post by calande on 2012-02-24
Same problem here!

---

