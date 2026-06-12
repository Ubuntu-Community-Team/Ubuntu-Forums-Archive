---
title: "Squeezeslave locks out audio"
date: 2012-07-17
forum: Multimedia Software
---

### Post by dhysk on 2012-07-17
I have squeeze server and squeezeslave running on my main machine and it mostly works great.

The issue is, for it to be practical, I need squeezeslave(the audio player) to run on bootup so nobody has to be logged in and we can still stream music around the house using our droid devices as remotes.

I have a script that runs at startup sitting in the init.d directory and all is well.  Exept for the fact that if you actually play music before someone logs in when they do they will have no sound.  If someone logs in before you play music than squeezeslave will be the one locked out.

I figure it has something to do with the fact its running from the system level and ALSA doesn't like to play nice between the system and user level?  Is there a way to remedy this?

If i start squeezeslave as a user all is well, other than the fact that you would have to log in and remain so for music to play.

Any ideas?

---

### Post by dhysk on 2012-07-19
is there anyway to mix sound between 2 users maybe?

---

### Post by dhysk on 2012-07-20
I think I'm king of no replies for starting threads ;)..

Some more things to add that may help guide me in the right direction.

--I have 2 audio devices
```
@desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 0: ES1371/1 [ES1371 DAC2/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: AudioPCI [Ensoniq AudioPCI], device 1: ES1371/2 [ES1371 DAC1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

--I use the on board device for my main output.
--When I boot and squeezeslave starts from init.d, via startup or command line using 'sudo service startsqueezeslave.sh start', it 'steals' my onboard card so when a user logs in their sound gets directed to the PCI card and it starts playing in the headphones.
--When I stop the service while logged in than user sound will go back to using the on board sound.

---

