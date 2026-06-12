---
title: "MythMusic Audio terrible"
date: 2008-08-25
forum: Mythbuntu
---

### Post by Meph1st0 on 2008-08-25
I may be jumping the gun the little on this post, but I'm sure you guys don't mind right?

Audio from my recordings, DVDs, or from any videos sound fine, but when I listen to an MP3 in MythMusic it sounds like crap.  Now it's possible that they were all encoded at a low bit rate but the same files sound fine on my ipod in my car and on my laptop.

For example, one of my songs was recorded at 188 kbps (which is kind of a strange bit rate anyway, might have been VBR) in mp3 format.  In fact all of my songs are in MP3 format which, I know is a lossy codec.

Now, I haven't tried listening to the same songs in a different music player, which is why I think I might be jumping the gun on this thread.  I'm going to try that tonight, but in the meantime, are there any other suggestions that you guys might have for me?  Could there be a special setting to set?  What's the deal with using PulseAudio?  

Also, further information.  I'm just using mythbuntu 8.04, integrated audio (I know, another potential issue), and the ALSA driver.  I'm using just a cable going from the audio line out (regular head phone type jack) to the RCA (white and red) connections to the TV.  The TV is then plugged into a receiver via the TV audio out port, again via the RCA connections.

In the case of my integrated audio, would getting a sound card with optical out really make that much of a difference?  My receiver does have an optical audio input.  What would be a moderate quality sound card with optical audio out that you can suggest?  I've read that if I use SPDIF out then PulseAudio won't work.  SPDIF and optical audio out is the same thing right?

Obviously, I have a lot to learn.

---

### Post by Meph1st0 on 2008-08-26
Okay, so.  I checked the audio quality of the same file that I mentioned in my previous post in both MythMusic and through Xine.  I also had my wife check it as well.  The audio quality was definitely better in Xine than in MythMusic.  Could I be using a different codec in MythMusic as opposed to Xine?  Is there a different setting that I need to set in my MythMusic config in the frontend?

---

### Post by volkswagner on 2008-08-26
Post your frontend log while playing an mp3.

Open a terminal and type:
```
tail -f /var/log/mythtv/mythfrontend.log
```

Then play an mp3, and post the results.

Do you settings match for your sound card selection in both the followin?

Utilities/setup>Setup>General settings..page3

and 

Utilities/setup>Setup>Media Settings>Music settings>Player Settings

---

### Post by Meph1st0 on 2008-08-26
Here's the output of the mythfrontend.log file.  I did exactly as you asked.  I started a terminal session and typed in tail -f /var/log/mythtv/mythfrontend.log and then I went back into mythfrontend and played the same song I've been using as my baseline for this thread and this is what I got in the log.

```
jbrown@mythbuntu:~$ tail -f /var/log/mythtv/mythfrontend.log
2008-08-26 20:09:26.468 TV: Changing from WatchingPreRecorded to None
2008-08-26 20:09:26.970 AFD: Opened codec 0xa36fea0, id(MPEG2VIDEO) type(Video)
2008-08-26 20:09:26.970 AFD: codec AC3 has 2 channels
2008-08-26 20:09:26.971 AFD: Opened codec 0x970ac80, id(AC3) type(Audio)
2008-08-26 20:09:27.468 AFD: Opened codec 0xa36fea0, id(MPEG2VIDEO) type(Video)
2008-08-26 20:09:27.468 AFD: codec AC3 has 2 channels
2008-08-26 20:09:27.469 AFD: Opened codec 0x970ac80, id(AC3) type(Audio)
2008-08-26 20:09:28.297 AFD: Opened codec 0xa36fea0, id(MPEG2VIDEO) type(Video)
2008-08-26 20:09:28.297 AFD: codec AC3 has 2 channels
2008-08-26 20:09:28.298 AFD: Opened codec 0x970ac80, id(AC3) type(Audio)
Gesture: UpRight
2008-08-26 20:12:03.836 XMLParse::LoadTheme using /usr/share/mythtv/themes/Mythbuntu-8.04-wide/music-ui.xml
2008-08-26 20:12:06.185 Opening audio device 'default'. ch 6(2) sr 44100
2008-08-26 20:12:06.185 Opening ALSA audio device 'default'.
2008-08-26 20:12:06.294 DPMS Deactivated 
2008-08-26 20:12:12.497 DPMS Reactivated.
2008-08-26 20:12:35.681 WriteAudio: buffer underrun
2008-08-26 20:16:17.085 Could not open settings file /home/jbrown/.mythtv/mysql.txt for writing
2008-08-26 20:16:17.092 Received a remote 'Clear Cache' request

```

Also, I checked the settings in general page 3 and music player settings and they don't have the same sort of configuration settings.  In general page 3 I have Alsa:default selected.  Under the music general settings I have it also set to use the default audio device.

---

### Post by managementboy on 2008-09-05
Hi, could it be that you are using all 6 surround channels, but your reciever has only Stereo... I thing mythtv upmixes stereo to all 6 channels, which withouth 6 speakers should sound bad. Just a thought.

---

