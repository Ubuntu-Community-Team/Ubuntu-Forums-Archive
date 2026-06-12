---
title: "The hell that is HDMI audio 10.10"
date: 2011-10-18
forum: Mythbuntu
---

### Post by chipppy on 2011-10-18
Good Morning

I am trying to get HDMI working and not winning YET!
The pic works bueatifully.  The sounds is no existant

Right working through [http://www.mythtv.org/wiki/Digital_Audio_Tutorial]("http://www.mythtv.org/wiki/Digital_Audio_Tutorial")
I cannot find /etc/asound.conf?????

> To fill in the details
NVidia Geforce 210 GPU
Drive version 260.190.06
VBIOS cersion 70.18.66.00.0b

Mythtv installed over Xubuntu 10.10 from Software centre (not Mythbutnu 10.10) fully updated but not connected tot he net at the moment

Working through [http://www.mythtv.org/wiki/Digital_Audio_Tutorial]("http://www.mythtv.org/wiki/Digital_Audio_Tutorial")
> Alasmixer version 1.0.23
2 sound cards 
0 = HDA Intel
1 = HDA NVidia
```
amixer set 'IEC958 Playback AC97-SPSA' 0
unable to find simple control 'IEC958 Playback AC97-SPSA', 0 
```

```
aplay -l
Card 1:NVidia [HDA NVidia] device (3,7,8 and 9) NVidia HDMI [NVIDIA HMDI] Subdevices:1/1
```

```
sudo nano /etc/asound.conf
```
brings up an empty page

```
locate asound.conf
/usr/share/doc/libsound2/examples/asound.conf_jack
/usr/share/doc/libsound2/examples/asound.conf_oss
```

It would appear that asound.conf is missing.

What have I done wrong to not have an asound.conf and where do i get one from, or how do I get one to generate????

cheers
chipppy

---

### Post by larsolav on 2011-10-18
You shouldn't need a asound.conf
Have you made sure you have unmuted digital audio in alsamixer?
Are you using 0.24.x? If so, scan for audio devices in the genrela Mythtv frontend setup. Use the arrow keys to change the selection to the appropriate HDMI audio output.

---

### Post by shad0w_walker on 2011-10-18
I have the same card (GT210)
Easiest thing I found was do this. Turn off your onboard audio in the BIOS. Gives you less options to be messing with when trying to get it up and going. After that, open up a console and run
```
alsamixer
```
To start with, just unmute everything in there and turn it up to a decent level. You can mute what you don't need later. After that, go into mythfrontend, head to settings -> setup -> General
The 4th page there should be for sound settings, press the scan for audio devices button, then scroll through the options til you see one that says something about either 'Nvidia' or 'HDMI' and hopefully something down the bottom about 'AC3, 5.1/7.1' that sort of thing. Go through the rest of the screens to finish that section, just leave as it is.
If that card doesn't work, try the next one in the list and so on.

---

### Post by papibe on 2011-10-18
Hey chipppy, I have a 310M which may be similar to yours. This [thread]("http://ubuntuforums.org/showthread.php?t=1668737&highlight=hdmi+audio") solved my problems with audio over HDMI.

Note that you don't have to actually do the modprobe and initramfs thing. If you get the right device, you can set it on player, and you are good to go (in my case was plughw:NVidia,9)

Hope it helps,
Regards.

---

### Post by chipppy on 2011-10-18
Good Morning

K I have everything turned on in the audiomixer and alsamixer (terminal) and at 100%

Went into Setup ==> General ==>page 4

Changed to both 
ALSA:HDMI and ALSA:plughw 0,3
Speaker configurations:Stereo and 5.1

Still no luck.
I have noticed that I cannot increase the volume from 0 now using either the ] (volume increase) or \ (mute/unmute) keys.

I am thinking that both are linked somehow and that if I cannot get the volume off 0 then I will not be able to confirm which settings are working.

Any ideas how to fix the stuck on 0 volume issue???

Cheers
chipppy

---

### Post by nickrout on 2011-10-18
> **chipppy said:**
> Good Morning

K I have everything turned on in the audiomixer and alsamixer (terminal) and at 100%

Went into Setup ==> General ==>page 4

Changed to both 
ALSA:HDMI and ALSA:plughw 0,3
Speaker configurations:Stereo and 5.1

Still no luck.
I have noticed that I cannot increase the volume from 0 now using either the ] (volume increase) or \ (mute/unmute) keys.

I am thinking that both are linked somehow and that if I cannot get the volume off 0 then I will not be able to confirm which settings are working.

Any ideas how to fix the stuck on 0 volume issue???

Cheers
chipppy

you cannot change the volume in a digital connection unless you use the software miser (and that leads to your nice digital audio being resampled).

---

### Post by chipppy on 2011-10-19
Good Afternoon

I am a lot lost now.  
> you cannot change the volume in a digital connection
So how do I change the volume of the movie that I am playing?

I have a HDMI cable going from the NVidia card to the HDMI input on a Panasonic Vieta 50" Plasma TV.

Am I supposed to get the audio via the same HDMI cable or through some other cable?

Have I missed something here?

Cheers
chipppy

---

### Post by papibe on 2011-10-19
> **chipppy said:**
> 
Changed to both 
```
ALSA:HDMI and ALSA:plughw 0,3
```
Speaker configurations:Stereo and 5.1

That is card 0 (Intel), not the Nvidia HDMI. From you previous command, it should be one of these 4:
```
ALSA:plughw 1,3
ALSA:plughw 1,7
ALSA:plughw 1,8
ALSA:plughw 1,9
```
Did you try the test suggested on that tutorial? If not, run a demo sound for each device to test if the sound is being transmitted to the TV:
```
aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav
aplay -D plughw:1,7 /usr/share/sounds/alsa/Front_Center.wav
aplay -D plughw:1,8 /usr/share/sounds/alsa/Front_Center.wav
aplay -D plughw:1,9 /usr/share/sounds/alsa/Front_Center.wav
```
Regards.

---

### Post by nickrout on 2011-10-19
> **chipppy said:**
> Good Afternoon

I am a lot lost now.  

So how do I change the volume of the movie that I am playing? use the volume control for the tv> 

I have a HDMI cable going from the NVidia card to the HDMI input on a Panasonic Vieta 50" Plasma TV.

Am I supposed to get the audio via the same HDMI cable or through some other cable? you should get  audio through the hdmi cable.> 

Have I missed something here?

Cheers
chipppy


If you have /etc/asound.conf, change its name or delete it if you are confident you can remember what is in it. Similarly ~/.asoundrc for the user running the frontend.

in mythtv settings|general on the audio config page select "scan for audio devices" and then choose the appropriate one.

That's all there is to it.

---

### Post by chipppy on 2011-10-19
Good Evening

> aplay -D plughw:1,3 /usr/share/sounds/alsa/Front_Center.wav
aplay -D plughw:1,7 /usr/share/sounds/alsa/Front_Center.wav
aplay -D plughw:1,8 /usr/share/sounds/alsa/Front_Center.wav
aplay -D plughw:1,9 /usr/share/sounds/alsa/Front_Center.wav

1,7 1,8 1,9 work find but 1,3 fails

> If you have /etc/asound.conf, change its name or delete it if you are confident you can remember what is in it. Similarly ~/.asoundrc for the user running the frontend.

I did make a asound.conf to try and fix this problem, it didnt help.  It is currently named asound.conf.test1.  There is no ~/.asoundrc in my system

> Are you using 0.24.x? If so, scan for audio devices in the genrela Mythtv frontend setup. Use the arrow keys to change the selection to the appropriate HDMI audio output. 

Nope using 0.23.1 + fixes26437 (from Synaptic) ontop of Xubuntu 10.10.
I cannot find anything that looks like a 'scan for audio devices'

Any other ideas

Cheers
chipppy

---

### Post by larsolav on 2011-10-19
> **chipppy said:**
> 

Nope using 0.23.1 + fixes26437 (from Synaptic) ontop of Xubuntu 10.10.
I cannot find anything that looks like a 'scan for audio devices'



Ah! Audio over HDMI is easier with 0.24.x, go to:
[http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)
and follow the instructions to update to 0.24.1.
Once that is done, you will find the 'scan for audio devices' (or something like that) in the Frontend general setup menu.
That should make your struggle easier.
Cheers!

---

### Post by nickrout on 2011-10-19
> **chipppy said:**
> Good Evening



1,7 1,8 1,9 work find but 1,3 fails



I did make a asound.conf to try and fix this problem, it didnt help.  It is currently named asound.conf.test1.  There is no ~/.asoundrc in my system



Nope using 0.23.1 + fixes26437 (from Synaptic) ontop of Xubuntu 10.10.
I cannot find anything that looks like a 'scan for audio devices'

Any other ideas

Cheers
chipppy

Well there is your very obvious problem. 0.23 is old, the current version is 0.24.1. Use mythbuntu repos to upgrade. Once you are running the current version things should be easier, and support more forthcoming.

---

### Post by chipppy on 2011-10-19
Good Morning

```
ALSA:plughw 0,3
```
If this is the intel card and my working NVidia card would be ```
ALSA:plughw 1, 7
``` where do I edit the 0,3 and change it to 1,7?  This should fix my problem from what I am learning

> 0.23 is old, the current version is 0.24.1. 
Correct but there is a specific reason I am using the older version that make my life a lot easier over time (if I can get the HDMI working).

Any futher ideas on what to try next if I cannot edit somefile to get the 1, 7???

Cheers
chipppy

---

### Post by nickrout on 2011-10-19
> **chipppy said:**
> Good Morning

```
ALSA:plughw 0,3
```
If this is the intel card and my working NVidia card would be ```
ALSA:plughw 1, 7
``` where do I edit the 0,3 and change it to 1,7?  This should fix my problem from what I am learning


Correct but there is a specific reason I am using the older version that make my life a lot easier over time (if I can get the HDMI working).

Any futher ideas on what to try next if I cannot edit somefile to get the 1, 7???

Cheers
chipppy

If you want to use that device to send sound out of mythtv then you need to go to setup|general, its about the 3rd or 4th page, theres a setting for your output device.

---

### Post by chipppy on 2011-10-19
Good Morning

In Setup --> General --> Sound setting
There is ALSA:plughw 0,3 only.  
This is the wrong sound card (Intel onboard).
There is all the other normal options aswell (NULL, JACK, defualt, spdif, steroo, etc) but I am thinking that something like ALSA:plughw 1, 7 is what I should be looking for

What I need to use, by the looks of it, is ALSA:plughw 1, 7 (or 8 or 9) but these are not in the list.
I am trying to find out if there is a way to get 1, 7 (or 8 or 9) into that list.  

Is there a file that I can edit somewhere or do I need to do something else?

This might just be the answer to my HDMI issues

Cheers
Chad

---

### Post by nickrout on 2011-10-19
> **chipppy said:**
> Good Morning

In Setup --> General --> Sound setting
There is ALSA:plughw 0,3 only.  
This is the wrong sound card (Intel onboard).
There is all the other normal options aswell (NULL, JACK, defualt, spdif, steroo, etc) but I am thinking that something like ALSA:plughw 1, 7 is what I should be looking for

What I need to use, by the looks of it, is ALSA:plughw 1, 7 (or 8 or 9) but these are not in the list.
I am trying to find out if there is a way to get 1, 7 (or 8 or 9) into that list.  

Is there a file that I can edit somewhere or do I need to do something else?

This might just be the answer to my HDMI issues

Cheers
Chad

Type in what you like in the field. You are not restricted to the choices.

If you were running 0.24 rather than some old version you could scan for devices. However you are stubborn about using an out of date version and don't have that choice.

---

### Post by chipppy on 2012-12-30
Good Morning

Sorry for not closing out this thread properly months ago.

Typed ALSA:lughw 1,7 and all worked fine.

Thanks heaps for the assistance

Cheers
chipppy

---

