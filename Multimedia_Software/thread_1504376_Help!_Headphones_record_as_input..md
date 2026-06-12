---
title: "Help! Headphones record as input."
date: 2010-06-07
forum: Multimedia Software
---

### Post by beardo_jax on 2010-06-07
I've been going in circles trying to figure out how to keep the sound playing through my headphones from being recorded while using ardour. Then I decided to play a video through the head phones while recording and it STILL came through so I'm guessing there isn't a problem with JACK or ardour. I recorded with sound recorder and it still came through.

Does anyone have any ideas?

---

### Post by beardo_jax on 2010-06-09
There is a new symptom. When I unplug the headphone while recording the sound that was playing through the headphones stop getting recorded. I can play sound through the built-in speakers and record a different track, but then if I want to record vocals or anything else with a mic it will pick up the sound coming from the external speakers.

Any help is appreciated. Thank you.

---

### Post by lidex on 2010-06-10
Have a look here:
[http://forum.audacityteam.org/viewtopic.php?p=75044#p75044]("http://forum.audacityteam.org/viewtopic.php?p=75044#p75044")

Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications-> Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by beardo_jax on 2010-06-10
Thank you for the response!

I installed Pulse Volume Control and it verifies that the headphones create sound under the microphone 2 line. If I yell into the headphones they make the mic2 line move.

I hope I post this code correctly

```
Linux beardo-laptop1 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
``````
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
Advanced Linux Sound Architecture Driver Version 1.0.21.
``````
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ALC268
``````
 ==> /proc/asound/card0/codec#1 <==
Codec: LSI ID 1040
```My laptop is a Toshiba Satellite P205-S7469

I read the post that you linked to. I wasn't able to get a "move stream" option after starting to record in audacity.

I have noticed that the intensity of input by the headphones is greater when a mic is plugged into mic2. Also I tried playing some audio and switching the mic and headphones (headphones plugged into mic2 and mic plugged into headphone jack) and I could hear the audio but not very loud. When I unplugged just the mic and still had the headphones plugged into the mic2 jack, I counldn't hear anything.

I hope this helps. Again, thank you for your help!!

---

### Post by lidex on 2010-06-11
Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=toshiba 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by beardo_jax on 2010-06-13
I'm still having the same problem.

---

### Post by lidex on 2010-06-13
Replace the 'toshiba' in that option with '3stack' (no quotes). Save and reboot.

---

### Post by beardo_jax on 2010-06-14
That did change things around a bit. The headphone jack doesn't work at all now but at least the playback doesn't get record. Now if we could just get playback through the headphones at the same time, I'll be a happy camper.

It also switched mic1 & 2. That doesn't really bother me though.

I tried with 4stack out of curiosity and it gave me the same results as the original problem.

---

### Post by lidex on 2010-06-15
Funny, the toshiba option is specifically for the A205. I would suggest following the alsa-upgrade link in my sig to get v 1.0.23.

---

### Post by beardo_jax on 2010-06-17
I followed the ALSA upgrade directions but it didn't help either. I ended up using the -r option because it stop playing youtube audio as well.

I tried audacity using Vista and it has the same problems there, so does that mean it's a problem with the machine or wiring? I did test out a  free trial of a different recording software(i can't remember which one) on the same machine before replacing the hard drive and everything worked fine then.  I replaced the HD with the exact same one but I didn't change anything else.

I have no idea what else to do.

---

