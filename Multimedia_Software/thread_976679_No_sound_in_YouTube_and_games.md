---
title: "No sound in YouTube and games"
date: 2008-11-09
forum: Multimedia Software
---

### Post by Stalker72 on 2008-11-09
I don't get the sound to work in YouTube and in games (mostly Counter-Strike in Wine). I get sound in Rhythmbox though, but not in Amarok.

_Speakers_: [Bose Companion 5]("http://www.bose.com/controller?url=/shop_online/speakers/computer_speakers/companion_5/index.jsp")
_Connection type_: USB

Any idea about what causes this problem?

Stalker72

---

### Post by DrDagostino1 on 2008-11-09
What version of Ubuntu are you running?

---

### Post by Stalker72 on 2008-11-10
> **DrDagostino1 said:**
> What version of Ubuntu are you running?
I'm using 8.10 (Intrepid Ibex).

Stalker72

---

### Post by Jamtarts on 2008-11-10
I have similar actually, I just assumed I didn't have the soundcard installed properly, but I'll have a look again,

as far as I can see the card is installed ok, so you've got me thinking now, I'll try some other programs tonight and see if it's the same,

thanks for posting a new lead,

---

### Post by quazi on 2008-11-10
Try running ```
padsp firefox
``` and see if that makes audio work for flash videos.

---

### Post by psyke83 on 2008-11-10
Stalker72,

It seems that PulseAudio isn't configured correctly on your system. Follow steps 2-5 of the [Intrepid PulseAudio]("http://ubuntuforums.org/showthread.php?t=866965") guide.

> **quazi said:**
> Try running ```
padsp firefox
``` and see if that makes audio work for flash videos.

Adobe Flash hasn't supported OSS for years, that won't help.

---

### Post by Stalker72 on 2008-11-10
> **psyke83 said:**
> Stalker72,

It seems that PulseAudio isn't configured correctly on your system. Follow steps 2-5 of the [Intrepid PulseAudio]("http://ubuntuforums.org/showthread.php?t=866965") guide
I get errors. :(

Stalker72

---

### Post by gandaran on 2008-11-10
check how you type or copy/paste
you have a extra **$** in the command line, remove it

---

### Post by DrDagostino1 on 2008-11-10
I have had similar sound problems that I thought was the device driver but one day I stumbled upon an interesting fix quite randomly. All I did was set all the playback devices in the sound preferences to ALSA and all my sound problems were fixed! Just go to System>Preferences>Sound to do this.

---

### Post by psyke83 on 2008-11-10
> **DrDagostino1 said:**
> I have had similar sound problems that I thought was the device driver but one day I stumbled upon an interesting fix quite randomly. All I did was set all the playback devices in the sound preferences to ALSA and all my sound problems were fixed! Just go to System>Preferences>Sound to do this.

On Hardy, that will appear to solve a lot of problems - but it's not an ideal fix by any means. In reality you are bypassing the core problem (a conflict between applications trying to gain exclusive access to the sound card due to a  PulseAudio misconfiguration). The required changes were deemed too intrusive for Hardy, so you'll have to resolve this [manually]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472").

Intrepid is different - PulseAudio should be configured correctly by default.

Two notes:
1. System/Preferences/Sound only controls GStreamer applications (Totem, Rhythmbox, Sound Recorder and some other official GNOME applications). Everything else is unaffected.
2. On Intrepid: even if you choose the ALSA driver in System/Preferences/Sound, sound will continue to be played by PulseAudio. The only difference is that GStreamer applications will direct output to PulseAudio via the ALSA "passthrough" (PulseAudio ALSA plugins).

---

### Post by Stalker72 on 2008-11-11
> **gandaran said:**
> check how you type or copy/paste
you have a extra **$** in the command line, remove it
It still doesn't work.

Stalker72

---

### Post by gandaran on 2008-11-11
> It still doesn't work.

you doing it the wrong way!
type 
sudo apt-get remove libflashsupport
not 
$ sudo apt-get remove liflashsupport
you got it now!

---

### Post by Stalker72 on 2008-11-12
I did it correctly this time, but when I change the Sound settings to Autodetect, there's no sound in my **USB** speakers. It has to be set to "Bose Corporation Bose USB Audio USB Audio (OSS)" to function. Sound doesn't work on YouTube and in games either.

Stalker72

---

### Post by kkilps on 2008-11-12
Do this
sudo killall pulseaudio
sudo alsa force-reload
alsamixer
go to "external" make sure it has MM if it doesn't hit m and then hit escape. Try youtube again.

---

### Post by warreng on 2008-11-12
Not sure if this helps you, but I was getting no sound on BBC iplayer. alsamixer didn't seem to help, but by default it does not show all mixer settings. alsamixer -Dhw shows more mixers including one that is reset to 0 each time I reboot my PC (seems to be a recent bug - it worked OK on Intrepid before the last updates I applied).

Having done this, sound is now back in web / iplayer.

---

### Post by Stalker72 on 2008-11-12
> **kkilps said:**
> Do this
sudo killall pulseaudio
sudo alsa force-reload
alsamixer
go to "external" make sure it has MM if it doesn't hit m and then hit escape. Try youtube again.
Where is "external"?

Stalker72

---

### Post by Stalker72 on 2008-12-26
> **psyke83 said:**
> On Hardy, that will appear to solve a lot of problems - but it's not an ideal fix by any means. In reality you are bypassing the core problem (a conflict between applications trying to gain exclusive access to the sound card due to a  PulseAudio misconfiguration). The required changes were deemed too intrusive for Hardy, so you'll have to resolve this [manually]("http://ubuntuforums.org/showpost.php?p=5587712&postcount=472").

Intrepid is different - PulseAudio should be configured correctly by default.

Two notes:
1. System/Preferences/Sound only controls GStreamer applications (Totem, Rhythmbox, Sound Recorder and some other official GNOME applications). Everything else is unaffected.
2. On Intrepid: even if you choose the ALSA driver in System/Preferences/Sound, sound will continue to be played by PulseAudio. The only difference is that GStreamer applications will direct output to PulseAudio via the ALSA "passthrough" (PulseAudio ALSA plugins).
I use Intrepid and still have the problems.

I only get sound in Songbird, Rhythmbox, Totem, etc.

Stalker72

---

