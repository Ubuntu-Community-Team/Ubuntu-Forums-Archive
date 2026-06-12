---
title: "Pulseaudio hisses like an angry cat; rings like my ears after a pantera concert."
date: 2010-07-27
forum: Multimedia Software
---

### Post by quequotion on 2010-07-27
Pulseaudio's volume control causes hissing with surround sound.

expired, closed, unresolved bug report:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/525705](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/525705)

I have posted about this before...

At least every version of pulseaudio that has come out since Karmic has had this problem. Before Karmic I hadn't tried to configure surround sound so I can't say how it was.

I've seen a variety of interesting hacks around. The most popular way seems to be redirecting pulseaudio's volume control to PCM but that hasn't worked so well lately. The second most popular way involves spelling out the capabilities of your card by hand so pusleaudio doesn't screw up, but that inevitably leads to losing features you don't know how to configure (and doesn't work either... the hissing comes back after a while)

I recently had a great adventure of completely resetting all pulseaudio settings and hacks i had done to work around this (most of which had worked at one time or another but each update seems to break something). Final solution: extract all data files from the pulseaudio .deb in apt's cache directly to / (after watching apt-get install --reintall; aptitude reinstall; and dpkg-reconfigure not give me a clean install) and delete all pulseaudio/alsa related user configuration files in ~.

There's a workaround, by adjusting the volume with alsamixer the ringing will vanish (along with a good chunk of volume).

I've found if I set pulseaudio's volumes to max (in the "Ouput Devices" tab of volume control) then toggle any of the volumes in alsamixer (ie Main to 97% then back to 100%) and relock the pulseaudio volumes then the ringing goes away and the volume can be adjusted, even by the media keys. It still rings a bit at low volumes. *Note: pulseaudio's max volume is well above the level alsamixer will push the card.

The volume slider in System->Preferences->Sound can be used to boost the volume quite a bit *without* causing any loss in quality or ringing. Unfortunately, the extra range and volume of this slider cannot be controlled from pulseaudio. Pulseaudio's volume controls move the slider down, but not up beyond a certain point.. Moving any of the sliders for balance, fade, etc. causes the same hissing and ringing as before.

Now that I'm mostly done ranting-

What is broken? (and don't tell me it's a latent ALSA bug)

---

