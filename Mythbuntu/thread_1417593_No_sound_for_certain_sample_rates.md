---
title: "No sound for certain sample rates"
date: 2010-02-27
forum: Mythbuntu
---

### Post by wilma92010 on 2010-02-27
I have my system playing back through spdif digital and it works great for TV, recordings, and DVDs.   It also plays many videos with sound.

However, many videos it will play but with no sound, regardless of format.   I have narrowed it down to the fact that I can hear audio for videos with a sample rate of 44100 that log as follows:

2010-02-27 10:45:59.458 AFD: Opened codec 0x4aedb40, id(WMAV2) type(Audio)
2010-02-27 10:45:59.461 AFD: Opened codec 0x1414e00, id(WMV3) type(Video)
2010-02-27 10:45:59.462 Opening audio device 'default'. ch 2(2) sr 44100
2010-02-27 10:45:59.462 Opening ALSA audio device 'default'.
2010-02-27 10:45:59.551 Mixer unable to find control Master
2010-02-27 10:45:59.551 Mixer unable to find control Master
2010-02-27 10:45:59.552 Mixer unable to find control Master
2010-02-27 10:45:59.552 Mixer unable to find control Master
2010-02-27 10:45:59.552 Mixer unable to find control Master
2010-02-27 10:45:59.576 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2010-02-27 10:45:59.594 OSD Theme Dimensions W: 640 H: 480
2010-02-27 10:45:59.713 TV: StartPlayer(0, Watching Video, main) -- end ok
2010-02-27 10:45:59.713 TV: Changing from None to Watching Video
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 320 x 240
YadifDeint: Using existing thread.
2010-02-27 10:45:59.718 Video timing method: USleep with busy wait
2010-02-27 10:45:59.719 Realtime priority would require SUID as root.
2010-02-27 10:45:59.764 ScreenSaverX11Private: DPMS Deactivated 1

NOTE:  I think the "Mixer unable..." message is a red herring, doesn't mean anything.

All other sample rates will play but with no sound, but does not throw an error as follows:

2010-02-27 10:44:17.860 TV: Attempting to change from None to Watching Video
2010-02-27 10:44:17.914 TV: StartPlayer(0, Watching Video, main) -- begin
2010-02-27 10:44:17.934 AFD: codec WMAV2 has 2 channels
2010-02-27 10:44:17.936 AFD: Opened codec 0x1414fb0, id(WMAV2) type(Audio)
2010-02-27 10:44:17.937 AFD: Opened codec 0x14155f0, id(WMV3) type(Video)
2010-02-27 10:44:17.938 Opening audio device 'default'. ch 2(2) sr 32000
2010-02-27 10:44:17.938 Opening ALSA audio device 'default'.
2010-02-27 10:44:18.012 Mixer unable to find control Master
2010-02-27 10:44:18.012 Mixer unable to find control Master
2010-02-27 10:44:18.012 Mixer unable to find control Master
2010-02-27 10:44:18.012 Mixer unable to find control Master
2010-02-27 10:44:18.013 Mixer unable to find control Master
2010-02-27 10:44:18.038 VideoOutputXv: XVideo Adaptor Name: 'ATI Radeon AVIVO Video'
2010-02-27 10:44:18.061 OSD Theme Dimensions W: 640 H: 480
2010-02-27 10:44:18.160 Realtime priority would require SUID as root.
2010-02-27 10:44:18.161 TV: StartPlayer(0, Watching Video, main) -- end ok
YadifDeint: In-Pixformat = 1 Out-Pixformat=1
YadifDeint: size changed from 0 x 0 -> 320 x 240
YadifDeint: Using existing thread.
2010-02-27 10:44:18.168 Video timing method: USleep with busy wait
2010-02-27 10:44:18.180 TV: Changing from None to Watching Video
2010-02-27 10:44:18.247 ScreenSaverX11Private: DPMS Deactivated 1


Again, no error, but no sound either.

I have tried almost every combination of audio configuration under Mythfrontend setup, but nothing seems to have any effect.  

I have also tried mplayer as the player, and even, as a "hail mary" tried to get mplayer to resample as there appears to be a command line parameter for that (but I am probably mis-understanding that functionality).

Any advice would be great.   I would hate to have to re-encode these videos.

Thanks in advance.

Wilma

---

### Post by nickrout on 2010-02-27
many sound cards will not send 44.1k sound to the digital output. you need to set asound.conf to resample. See eg [http://www.gossamer-threads.com/lists/mythtv/users/401946#401946](http://www.gossamer-threads.com/lists/mythtv/users/401946#401946)

---

### Post by wilma92010 on 2010-02-27
Thanks for the pointer to more information.  

I might also try a new sound card (now using the MB sound).   

Wilma

---

### Post by nickrout on 2010-02-28
at least try to get this one going first!!

---

