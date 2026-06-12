---
title: "Audacity"
date: 2007-05-13
forum: Multimedia Production
---

### Post by jelkimantis on 2007-05-13
It seems like I'm the only one having this problem, so I'm stuck.  Usually I just cruise the forums for a half hour and get the answers I need.

Here is my problem:  Audacity used to work and now it doesn't.  I had it working great on Edgy.  No problems whatsoever.  

With the feisty update, it now gives me a weird squelching noise when I attempt to record.  It's not dumping any errors on me, so I don't know where to begin. 

I've also lost the monitors off of the microphone and speaker, so I'm assuming that it's lost connection to the sound card.

Sound card is an Intel, but I want to say Realtek? Anyway, Any guidance here would be greatly appreciated.

jsl

---

### Post by lexen on 2007-05-16
I've had a problem like that before.  What it was for me was that for some reason I had to record in stereo and with it playing back other tracks.  If I changed either of those two options it would record a very bad track where the audio was there, it was just hidden behind a bunch of static.  

     If you are having problems with your sound card, that would make a lot of sense because I have heard a few people mentioning that they have problems with their sound card when they switch to feisty.

     Maybe none of this will help you, but that's all I've got.

---

### Post by Pocadotty on 2007-05-16
Check your sound card and setting by double clicking the speaker in the top panel.  Make sure your capture source is what you want by clicking on the recording tab.  Once everything looks good here, leave it open and bring up Audacity.

go to Edit Preferences and click on the Audio I/O tab.  Make sure your settings here match what it says in volume control. for instance:

if Volume control says "Volume Control: Intel ICH6 (Alsa mixer)" then your device choice in Audacity should be "ALSA: Intel ICH6..."

The problem your describing sounds like Audacity is trying to read from the wrong sound driver or device(if you have multiple sound cards).  If your volume control says your using alsa, use alsa in Audacity, if volume control uses OSS, use OSS in Audacity.  Problems like this are likely just a result of a setting being off.

Also make sure JACK isn't running, because Audacity and JACK don't get along well in my experience.

Hope that helps,

Cheers

---

### Post by heffo_j on 2008-02-27
Hi there,

I have had a problem getting Audacity to work with my intel card. However, I finally figure it our.

1) In the Audacity preferences window I have Alsa (default) set for both record and playback.

2) In Alsa mixerPlayback tab, I have Master, PCM on. Ext Mic and Int Mic MUTED.

3) In the Alsa Mix Recording Tab I have Digital as ON (not muted) 

4) In the Alsa Mixer Switches tab, I have Int mic CHECKED but NOT the IEC958 and the Line in.

Now this is rather strange behaviour to me but it works.

I'm running the Alsa driver 1.0.16. Each iteration is getting worse. There was time when the kernel, distro, and driver worked perfectly on my HP laptop. Now it is a mess. The LED buttons (what ever they are called) no longer control the sound, the system no longer mutes when I plug in the external speakers and headphones.


As for Jack, it just never seems to work right no matter how I fiddle with it....
I don't what is to blame for this but gee it is annoying.

Cheers
John

---

### Post by mickthejew on 2008-02-29
I feel your pain brother, I had no Mic with Alsa 1.0.14 and I upgraded to 1.0.16 (just being able to upgrade was a nightmare) now I have no sound at all and no information to help me to get it to work.

I'm 1 day from going back to XP.

---

