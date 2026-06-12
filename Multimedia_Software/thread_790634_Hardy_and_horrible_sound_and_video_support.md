---
title: "Hardy and horrible sound and video support"
date: 2008-05-11
forum: Multimedia Software
---

### Post by crahen on 2008-05-11
I've been trying out Hardy for a few weeks and I've had a lot of trouble getting basic things working that I used to not have trouble with on previous ubuntu release.

One big one is that mplayer is flat out broken. I don't know what exactly is different in Hardy, but anytime I try to use mplayer I'll get what appears to be 1 frame per minute. I don't know why. Also, sound doesn't work.

Another big one is flash. Flash is now able to steal some sort of lock on the sound card. So if I have a browser open and any website contains a flash element the browser process "gets" the sound card. If I later try to play an mp3 or video, I'll have no sound at all until I close my browser. I don't know why - no visibility into anything or hints at what could be wrong from ubunutu.

I'm not doing anything special. Any ideas?

---

### Post by ubuntu-freak on 2008-05-11
> **crahen said:**
> I've been trying out Hardy for a few weeks and I've had a lot of trouble getting basic things working that I used to not have trouble with on previous ubuntu release.

One big one is that mplayer is flat out broken. I don't know what exactly is different in Hardy, but anytime I try to use mplayer I'll get what appears to be 1 frame per minute. I don't know why. Also, sound doesn't work.

Another big one is flash. Flash is now able to steal some sort of lock on the sound card. So if I have a browser open and any website contains a flash element the browser process "gets" the sound card. If I later try to play an mp3 or video, I'll have no sound at all until I close my browser. I don't know why - no visibility into anything or hints at what could be wrong from ubunutu.

I'm not doing anything special. Any ideas?

 
Is it just MPlayer with that symptom? What about Totem? Try different sound/video settings in MPlayer's preferences.
 
For your Flash troubles, try this command:
 
**sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport**
 
Restart Firefox.
 
Nathan

---

### Post by Polocoste on 2008-05-12
> **crahen said:**
> 
Another big one is flash. Flash is now able to steal some sort of lock on the sound card. So if I have a browser open and any website contains a flash element the browser process "gets" the sound card. If I later try to play an mp3 or video, I'll have no sound at all until I close my browser. 

I am having this exact same issue, just noticed it today, I could swear everything was working fine from the release of Hardy until today...did one of the update break it? Not sure, but it is annoying me. Has anyone tried reassuringlyoffensive's fix?

---

### Post by vishnu on 2008-05-12
Me too.  None of my players works.  I hope someone can post a fix here.  This is not good at all.

---

### Post by cor2y on 2008-05-12
For the first two posters with flash and audio problems visit the Pulse audio setup thread in this section, the problem is pulse audio is not fully setup by default in hardy.
[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)
The first and last poster with video problems, what exactly are your setups?
Example what video card is it? Are you using the closed or open source drivers for you specific video chipset?
Is it on board video? If it is what is the chipset?

---

### Post by vishnu on 2008-05-13
Not sure of setup.  Sound works on web, videos work great (avi, mpeg, etc)
Just MP3 files.  Players just don't play the file.  Track time indicator doesn't shift.

---

### Post by cor2y on 2008-05-13
then you need the mp3 decoders installed via the ubuntu-restricted-extras package in synaptic.
If thats installed then add the gstreamer-fluendo mp3 plugin.
This is for totem and other gstreamer based media players like rhythmbox.
On the mplayer side get libmad installed.

---

### Post by vishnu on 2008-05-13
Gstreamer worked.  Thanks

---

### Post by shamrock_uk on 2008-05-14
> **reassuringlyoffensive said:**
> Is it just MPlayer with that symptom? What about Totem? Try different sound/video settings in MPlayer's preferences.

I have exactly the same problem as the OP with a fresh 8.04 install. It's quite interesting really, once the flash video takes the soundcard focus, mplayer appears to freeze as described in the OP - it doesn't lock up, just appears to be playing at effectively zero fps.

However, playing the video with Totem plays in extremely slow motion, maybe one frame every 10 seconds and no sound, whilst VLC plays at normal speed but with no sound at all.

Closing the firefox tab with the flash file in fixes video playback completely.

I haven't yet dived into the pulseaudio steps above (and thanks for posting) but definitely a step back from Gutsy. Somewhat strange to include a new audio subsystem in a LTS release maybe?

---

### Post by ubuntu-freak on 2008-05-14
> **shamrock_uk said:**
> Somewhat strange to include a new audio subsystem in a LTS release maybe?

 
Why? LTS is the same as any other release, but with long term support. PulseAudio is default in Fedora also. It's natural for their to be issues in a new release with a new X/device server and sound server.
 
Nathan

---

### Post by blueturtl on 2008-05-15
I was getting the same thing with all my video players but when MPlayer didn't work (it has **always** worked) I decided to take a look at the settings. By default MPlayer uses PulseAudio under Hardy. I switched to ALSA, restarted MPlayer and lo and behold videos now play correctly!

To change MPlayer preferences right click on the video, select 'Preferences' from the menu and from the audio tab select ALSA. That fixed it for me.

---

### Post by pete83 on 2008-05-18
I experienced a similar problem: totem played the video at about a frame a second, and there was no sound.

The solution for me was to turn off desktop effects.

After turning off desktop effects, video once again worked normally in totem.

---

### Post by nip37 on 2008-05-31
I was having same problem after fresh install of hardy, even after tweaking and googling nothing seemed to work, like it use to work before.
I just rolled back my xorg.conf to the Gusty xorg.conf, now every thing is working fine. I dont't know why but with configured xorg.conf for hardy audio and video just dont work for me.

---

### Post by pjrodz on 2009-03-07
any solutions for this one? :(

---

### Post by pjrodz on 2009-03-07
> **cor2y said:**
> For the first two posters with flash and audio problems visit the Pulse audio setup thread in this section, the problem is pulse audio is not fully setup by default in hardy.
[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)
The first and last poster with video problems, what exactly are your setups?
Example what video card is it? Are you using the closed or open source drivers for you specific video chipset?
Is it on board video? If it is what is the chipset?

thanks for the link man, it worked for me :)

---

