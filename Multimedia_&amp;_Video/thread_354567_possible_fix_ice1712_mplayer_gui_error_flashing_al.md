---
title: "possible fix: ice1712 mplayer gui error flashing alsa-control box"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by Khaz on 2007-02-06
I submitted this to the MPlayer mailing list highlighting problems with everyone's favorite soundcard the M-Audio Audiophile 2496.

Problem is with a rapidly flashing error dialog:
alsa-control: unable to find simple control 'PCM',0
 
Running 6.06 Dapper Ubuntu, with Mplayer version MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8
Alsa is currently at 1.0.10 and is working fine (as well as can be expected.)
 
Loading movies/music in the GUI is an issue because I'm using the ice1712 M-Audio Audiophile 2496 sound card. I will tell you my current fix for the spammy flashing error box in GMplayer: Load up GMplayer and right click the control window;** go to Preferences>Audio; at the bottom is a checkbox "Enable Software Mixer". Checking this box fixed the problem for me when using the GUI to play items.**
 
My current configuration is using envy24control on PCM1 and PCM2, Ganging the sliders together, and on channel 1, dropping the sliders to 70, and on channel 2 setting them at 25. Now I right click on my volume on my start panel>Preferences, and set it to use Alsamixer on my card on 'Multi'. It's very 'hacky' because volume control is very inaccurate and I can't figure out why alsa won't output properly to a single channel on the card.
 
My audio card doesn't use PCM control for volume like OSS does and therefore I've got to change the mixer control to a 'Multi' channel on the Alsamixer. Command-line 'mplayer xxx.mp3' is not a problem; Command-line 'mplayer xxx.avi' is not a problem. The error does not occur when running command line mplayer and this is why I'm confused; as soon as the GUI version is loaded, incredible error box spam is produced making the movie unwatchable (imagine having a flashing error box every frame). Why does the command line version avoid this problem?
 
I've obviously tried using [gmplayer xxx.avi -ao alsa -mixer-channel 'Multi',0] in terminal. No effect. Editing the /.mplayer/config with a mixer-channel=Multi,0 and variations fails. 
 
Just in case you suggest OSS as an option: I've tried patching the /proc/asound/card0/oss_mixer with the terms [PCM "Multi" 0], [VOLUME "Multi" 2] as suggested on the Alsa wiki ([http://alsa.opensrc.org/Mapping_oss_mixer_controls_to_alsa_mixer)](http://alsa.opensrc.org/Mapping_oss_mixer_controls_to_alsa_mixer)). Interesting how this page mentions my chipset as a problem. Now when I use (G)Mplayer with the [-ao oss] flag, I get a wickedly clipped and inappropriately loud sound, the error disappears, and the volume control is useless. Obviously unaccepable. This is due to a bug in OSS Emulation in ALSA using ice1712 drivers, namely "The ICE1712 chipset supports only an unconventional format, interleaved 10-channels 24bit (packed in 32bit). Therefore you cannot mmap the buffer in a conventional (mono or 2-channels, 8 or 16bit) format using OSS emulation." ([http://alsa.opensrc.org/OssEmulation](http://alsa.opensrc.org/OssEmulation)) That's crazy-speak to me and it seems like OSS support is broken for this chipset in ALSA. This leaves me without OSS support; so remapping PCM and VOLUME controls in the oss_mixer file works but leaves me with messed up sound.
 
Checking the Preferences>Audio tab of the GUI has some interesting options; I checked the alsa driver settings and have 3 boxes that allow me to change device, mixer, and mixer channel. How do I add to these drop boxes?
 
But mostly, why doesn't the [-ao alsa -mixer-channel 'xxx',x] have any effect onf Gmplayer?
 
Thank you,
Kyle Zwarich

---

### Post by jellyfisharepretty on 2007-04-04
I have the exact same problem, except on a sb live! 24bit.  Been using the cmd line, but i miss the convenience of the gui.  And  mplayer is just my favorite video player... don't want to give it up for vlc or xine or some other.

Damn you message box !  The video would play fine if you didn't appear!

---

### Post by peaceburn on 2007-10-26
Hey, 

I know this thread is rather old, and maybe the stuff below is explained elsewhere, but this is the first time I got rid of the AWFUL MESSAGE BOX about the mixer channel 'PCM',0 with my SoundBlaster 24bit Live!. Thanks to Khaz, it came to my mind that I have to do the simplest thing - put **"Analog Front" as mixer channel.**

I'm attaching a screeny of my configuration , it's a 2.0 stereo, not sure how it'll work with 5.1 or other setups, but you can use it as starting point. The other names like "Analog Center", "Analog Rear" , you can take them from sound mixer. 

[[IMG]http://img81.imageshack.us/img81/3156/screenshotaudiodrivercolp6.th.png[/IMG]](http://img81.imageshack.us/my.php?image=screenshotaudiodrivercolp6.png)


Thanks again Khaz, your post was my inspiration :)

---

