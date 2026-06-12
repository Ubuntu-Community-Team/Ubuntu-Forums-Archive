---
title: "Need help fixing media players in 7.10"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by squirage on 2007-11-07
Hi All,

  I just wanted to start a new thread on this because once again I have looked at a myriad of solutions which have not yet worked for me.

  After fixing my sound and youtube problems in 7.04 I decided to upgrade to 7.10 because I wanted Open Office 2.3 and was hoping that a synaptic install of kdenlive could help me get that program working.

  I am now back to flash video freezing or crashing firefox. I have installed 3.0 even though it still says 2.0.0.8 I also tried wiping all the plugins manually and re-installing the nonfree flash plugins. To no avail. Previously what had worked was a combination of installing pulse audio and alsa-oss and editing the DSP value in firefoxrc. But all that is still there after the upgrade. I also tried installing some of the things recommended with jackd, but I just got more errors.

  After upgrade the brand new problems were Rhythmbox freezing and totem and mplayer crashing when I try to play video. In the terminal I get this:
```
rhythmbox 
JACK tmpdir identified as [/dev/shm] 
Killed

 totem 
JACK tmpdir identified as [/dev/shm] 
JACK tmpdir identified as [/dev/shm] 
** Message: Error: Failed to write data to the esound daemon 
esdsink.c(415): gst_esdsink_write (): /play/abin/audiosinkbin/audio-sink/bin6/autoaudiosink1/autoaudiosink1-actual-sink-esd: 
system error: Broken pipe 

Killed 
``` and system resources show CPU1 at 100% when trying to play a song in Rhythmbox. Also /dev/shm only ontains a file called pulse-shm-1582622278, even after loading that jack stuff.

Mplayer says Fatal error! Error opening/ initializing the selected video_out (-vo) device.

I also tried installing Listen, and it did not work either.

gxine and xine do work, which makes this all an even bigger mystery.](*,)

I feel like I have leapt backwards at this point. It is pretty discouraging.

---

### Post by jaypipes on 2007-11-08
Same problem here... :(

---

### Post by squirage on 2007-11-08
Hi jaypipes,

  I haven't really fixed anything but I did find something here [http://ubuntuforums.org/showthread.php?t=407237](http://ubuntuforums.org/showthread.php?t=407237)

mtscaef said > System > Preferences > Sound
I set all of the 'Devices' to be ALSA instead of Autodetect
Then goto the 'System Beep' tab and unCheck the 'Enable system beep'
Then Close.

I DIDN'T even have to logout and back in! That fixed it.
Hope it works for you if you run into the problem again! And for anybody else!

I did it and now Totem plays video and music with no sound output. Mplayer still fails on music and video. If I open sound files in audacity I can hear them.

I also get this error from rhythmbox now ```
Internal Gstreamer error: state change failed. Please file a bug at http://bugzilla.gnome.org/enter_bug.cgi? product=Gstreamer.
```

I guess I need to report it.

Maybe this will help you.

---

