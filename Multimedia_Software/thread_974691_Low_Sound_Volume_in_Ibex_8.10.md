---
title: "Low Sound Volume in Ibex 8.10"
date: 2008-11-07
forum: Multimedia Software
---

### Post by The Pinny Parlour on 2008-11-07
I am liking the new version of Ubuntu, but the low volume really stinks.
I am having to turn all volume controls to 'max' just to hear things.  Can anyone share what is going on?

Thank you

---

### Post by khel on 2008-11-08
same problem :(

---

### Post by 73ckn797 on 2008-11-08
In terminal try "alsamixer" and see what volume is set on.

The volume on my laptop is not loud but can be heard. The speaker is not, I am sure, made to be like my desktop speakers and especially as loud as my Fender Princeton 650 amp.
:guitar:

---

### Post by dhanes420 on 2008-11-08
I'm having the same problem:

8.10 Kubuntu, SB Audigy LS (CA0106), Intel IEC958 onboard disabled.

Using PulseAudio, straight ALSA had the same problem.

Using alsamixer everything is turned up, but if I push the Analog volume too high the sound playback is scratchy.

My hardware volume does absolutely nothing.

Amarok, xine, mplayer all have the problem.

---

### Post by 73ckn797 on 2008-11-08
Look at the following links and try.

[http://ubuntuforums.org/showthread.php?t=966581&highlight=Low+volume](http://ubuntuforums.org/showthread.php?t=966581&highlight=Low+volume)

[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Do an advanced search for "sound low". That is what I did to help you out.

---

### Post by tom66 on 2008-11-08
Make sure all secondary controls, e.g. PCM are set to 100% from the volume control. You can set them by right-clicking on the speaker icon in the system tray.

---

### Post by 73ckn797 on 2008-11-08
Any other questions that arise may best be solved first by using Ubuntu help: [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

Advanced searches are also a good way to locate answers. They require a bit more time but can save you posting questions and waiting for the answers sometimes.

---

### Post by hi.io on 2008-11-08
I also had this problem after upgrading from 8.04 to 8.10 on my dell m1330 laptop and alasamixer didn't work but this did though:

```
gnome-volume-control
```

Set all relevant levels to 100%, the one responsible for my sound was the front, which can be added through preferences.

---

### Post by dhanes420 on 2008-11-08
Hello all again,

I'm using Kubuntu, so I do not have the same utilities that everyone has mentioned for gnome.

Additionally, even though lsmod shows snd_pcm, I do not have PCM selections in Kmix, Alsamix. Weird.

---

### Post by 73ckn797 on 2008-11-09
> **dhanes420 said:**
> Hello all again,

I'm using Kubuntu, so I do not have the same utilities that everyone has mentioned for gnome.

Additionally, even though lsmod shows snd_pcm, I do not have PCM selections in Kmix, Alsamix. Weird.


Have you tried an advanced search (option at top of thread page) using key words (listed at the bottom of a thread page as Tags) and designated specifically for Kubuntu?

---

### Post by psyke83 on 2008-11-09
Now that PulseAudio registers as the default sound device in Intrepid, it's inevitable there's going to be a little confusion for users when adjusting volume.

In the past, running "alsamixer" used to select your physical sound card by default, but now it selects the "virtual" PulseAudio master volume control - this is not necessarily what you want it to do.

Gain access to your real card via:

```
$ alsamixer -Dhw
```

Ensure the Master and PCM levels are set to the volume you require, and also ensure PulseAudio is set to the max as well.

---

### Post by dhanes420 on 2008-11-10
Pulse is set to 100%, if in PAM i set the sinks or sources to above 100%, i lose all sound.

In Alsamixergui or alsamixer -Dhw I don't have PCM inputs for some reason.  Analog Center/Front/Rear/Side are set high, but if I set the front too high the sound is scratchy.  IEC958 is muted.  The sound only comes out of the front speakers, no center or rear.

Additionally I cannot alter (down or up) the volume with the Creative 6.1 speaker hardware volume control.

---

### Post by dhanes420 on 2008-11-10
Was watching the Pulse Volume Control applet, on the Playback tab.

Shows the plug-in amarokapp: Alsa Playback => both channels (no rear or front, just left and right) are cranked all the way over to the right, but the dB is showing 0.00.   Output devices tab shows them both at 100%

---

### Post by liquidpele on 2008-12-28
Thank you!!   

Running "gnome-volume-control" in the command line and increasing the "master front" volume did the trick for me.  It was set to zero for me on a fresh install of 8.10...  wtf!!  Now my volume works though.

---

### Post by smfai on 2009-02-12
> Running "gnome-volume-control" in the command line and increasing the "master front" volume did the trick for me. It was set to zero for me on a fresh install of 8.10... wtf!! Now my volume works though.

thank you! Same problem! 
Set the master front and PCM 100% will be ok.

---

### Post by EtherBunny on 2009-02-12
I just got a new Dell XPS m1330 and everything works great except for this sound problem. The max sound, and I mean MAXIMUM - every column on 100% in gnome-volume-control and alsamixer - is still only about 25% of the volume I get in windows. 

I have to keep the master volume at 100% just to hear sound.

Any other ideas? 'cause playing with the mixers ain't working.

---

### Post by hogsmate on 2009-04-16
thank you 73ckn797 the links you gave were very helpful :popcorn:

---

### Post by dhanes420 on 2009-04-16
> **EtherBunny said:**
> I just got a new Dell XPS m1330 and everything works great except for this sound problem. The max sound, and I mean MAXIMUM - every column on 100% in gnome-volume-control and alsamixer - is still only about 25% of the volume I get in windows. 

I have to keep the master volume at 100% just to hear sound.

Any other ideas? 'cause playing with the mixers ain't working.

Check to make sure your Digital Audio Out is not checked.

---

