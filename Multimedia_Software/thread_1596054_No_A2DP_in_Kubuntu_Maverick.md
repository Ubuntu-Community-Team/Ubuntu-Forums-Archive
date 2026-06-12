---
title: "No A2DP in Kubuntu Maverick"
date: 2010-10-13
forum: Multimedia Software
---

### Post by conor on 2010-10-13
Hey folks, 

Having an issue with A2DP in Maverick.

Whenever I connect my headset, both 'Headset Service' and 'Audio Sink' are shown as being connected. I'm only getting mono audio. 

I tried clicking disconnect on 'Headset Service' but it disconnect both. Selecting connect on 'Audio Sink' also connect 'both' and gives mono output.

Fresh install. Any ideas?

---

### Post by jctots on 2010-10-14
i have also the same issue using ubuntu. my s9-hd will only work in mono but not in A2DP in maverick. it is working great on lucid.

---

### Post by blaer on 2010-10-16
Had the same issue here. 

Open "bluetooth devices" (click on the bluetooth icon in the notification area)
In the contextmenu (2nd mouse key) of the headset device connect to the "audio sink" and disconnect from the "headset service"

---

### Post by conor on 2010-10-17
> **blaer said:**
> Had the same issue here. 

Open "bluetooth devices" (click on the bluetooth icon in the notification area)
In the contextmenu (2nd mouse key) of the headset device connect to the "audio sink" and disconnect from the "headset service"

There is no context menu in the devices screen. 
Are you using BlueDevil on Kubuntu Maverick?

There is a context menu for the tray icon with these options, but they don't change anything (refer to first post).

---

### Post by hawk88 on 2010-10-20
Go to Sound preferences > Hardware

Select the headset. Then select A2dp profile.

If that doesn't work, remove device from paired bluetooth devices. Install bluez-btsco pakage and try again

---

### Post by conor on 2010-10-20
> **hawk88 said:**
> Go to Sound preferences > Hardware

Select the headset. Then select A2dp profile.

If that doesn't work, remove device from paired bluetooth devices. Install bluez-btsco pakage and try again

There is no such option in the Phonon option set.
Installing bluez-btsco didn't work either. 
Tried using the Phonon Gstreamer backend, but still no joy.

Thanks for the suggestions, though.

---

### Post by ThePianoGuy on 2010-12-15
Hi conor.

You need to set your pulseaudio bluetooth profile from hfp/hsp to a2dp. This is a PulseAudio settings so you need a kind of pulse audio control center / mixer. Gnome has this under Sound preferences, but KDE unfortunately doesn't have this yet AFAIK. I solved this by installing pavucontrol (lightweight gtk+ application) and set the profile to A2DP at the most-right tab.

---

### Post by spamalam on 2010-12-27
Thank you piano man, installed selected the option under my headphones for high quality playback and its great.

Now I can listen to:
[http://open.spotify.com/track/5xKVYMxOHB2XRLCUafFrz6](http://open.spotify.com/track/5xKVYMxOHB2XRLCUafFrz6)
as my kubuntu within kubuntu explodes when i start up my dodgy code.

Thanks!

---

### Post by Linux Lurker on 2011-03-18
> **ThePianoGuy said:**
> Hi conor.

You need to set your pulseaudio bluetooth profile from hfp/hsp to a2dp. This is a PulseAudio settings so you need a kind of pulse audio control center / mixer. Gnome has this under Sound preferences, but KDE unfortunately doesn't have this yet AFAIK. I solved this by installing pavucontrol (lightweight gtk+ application) and set the profile to A2DP at the most-right tab.

I don't know why I didn't check that first.  Since transitioning to to pulse audio, I use pavucontrol quite often.  However, I sometimes forget the far-right tab configuration for individual devices.
Thanks for the suggestion.
Works a charm. Now I can use bluetooth audio with my MythTV setup in the bedroom.

---

