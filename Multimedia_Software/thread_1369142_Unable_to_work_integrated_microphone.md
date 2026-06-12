---
title: "Unable to work integrated microphone"
date: 2009-12-31
forum: Multimedia Software
---

### Post by MuccaPazza on 2009-12-31
Hello, 

After much battling getting my sound to work (playback), I am still experiencing issues with the microphone. I installed the latest ALSA driver (1.0.21 as described in [http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)) which solved the playback issue. 

To describe my problems, I am a basic user, not a tweaker and mostly unfamiliar with Linux.. I am not using 15 different sound cards and have no intention of having some crazy or fancy set-up. I would like my microphone to work so I can use Skype. I know the hardware is likely not at fault since I was running XP previously and everything worked fine.  
 Part of the problem is most threads are so complicated for me to understand and it is tricky to know where to begin. 

Every once in a while, when there are system updates, for some reasons it seems that the ALSA driver version reverts to the previous version (1.0.18, and I have to upgrade it again, because the playback stops functioning again. No huge deal, just annoying. Again, probably part of my ignorance of the contents of the proposed updates. 

I am running Ubuntu 9.04 on a Toshiba Tecra A10.  
 I ran the Volume Control, and the Front Mic Boost and Mic Boost are both up and not muted. However, on the recording tab, the Capture and Digital channels are both muted. I can un-mute them but as soon as I close the Volume Control, they both mute again. The device used is HDA Intel (Alsa mixer).  
 

 I tried to run the Pulse Audio Volume Control and looked at the levels. There is some noise shown, but nothing reacts to my voice or if I make any other sounds, no matter how loud. No matter whether the Capture channel is un-muted: there is no difference in the Pulse Audio Volume Control meter. 


I don't know where to begin and am slightly frustrated by now.. I am considering switching to 9.10 but fear other problems in the wake.  
 Can anyone offer some help or should I seriously consider going back to XP to my great sadness? I really like Ubuntu overall, the open source and the community concepts, but this is tricky stuff for the average user. Perhaps my bad for not having a grasp of the sound architecture of this operating system, and I'll take the blame. However, definitely discouraging.  

Thank you for your potential help.

---

### Post by VertexPusher on 2009-12-31
> **MuccaPazza said:**
> I can un-mute them but as soon as I close the Volume Control, they both mute again.
PulseAudio is messing up your mixer settings. Remove it.
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio
```
Restart the computer, then run this command to quickly test your microphone settings:
```
arecord -f S32_LE -r 48000 -c 1 | aplay -f S32_LE -r 48000 -c 1
```
This will capture audio from your default sound card and send it back. Run alsamixer in a separate terminal window, switch to the playback page (F3) and mute both mic and front mic. Then switch to the capture page (F4), select mic or front mic as capture sources and turn up the capture sliders until you hear the mic signal played back by the sound card. When you've found a setting that works, press Esc to quit alsamixer and stop the arecord command by pressing Ctrl-C. Then make a test call in Skype.

---

### Post by MuccaPazza on 2009-12-31
Hello VP, 

Thank you for taking some time. 
I did what you suggested and heard a white noise like so-called "snow" on a TV.  Despite re-starting the PC, the "capture" level still mutes when the ALSA mixer Volume Control is closed and re-opened. I could live with this if the mic did work properly but wasn't successful. 

I tried a test call in Skype, all I can hear is that same white noise. I tried un-checking the default suggested setting (Allow Skype to automatically adjust my mixer levels) and tried a test call. Playback is fine but I cannot hear what I am trying to record. 
I also tried running Audacity, and once again, I am unable to detect anything the microphone should pick up. 

Did I do something wrong? 
When running alsamixer in the terminal window, the increments in the Font mic boost are 50%, not sure that is normal. I have it set at 50% at the moment. When running alsamixer in its own graphic window, I can adjust it as expected with 1% steps. Perhaps there is some problem there? 
Again, "capture" keeps re-muting everytime I close the alsamixer graphic window. 

Sorry for the lack of talent. 
MP

---

### Post by MuccaPazza on 2010-01-01
First things first: Happy New Year! 

If you need me to provide more details, screenshots, etc, I will happily do so. 

Thank you again for your help so far; 
MP

---

