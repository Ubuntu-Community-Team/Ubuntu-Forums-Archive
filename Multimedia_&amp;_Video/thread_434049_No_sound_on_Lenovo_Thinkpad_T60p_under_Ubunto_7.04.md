---
title: "No sound on Lenovo Thinkpad T60p under Ubunto 7.04 Fiesty Fawn"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by idunno3 on 2007-05-05
I have Ubuntu 7.0.4 installed on a Lenovo Thinkpad T60p.

Initially, there is no sound and when a sound or video file is played, the tracking counter does not move.  For videos, the first frame is displayed, but that's it.  After a few reboots, the counter will move, or if I'm watching a video, it will play, but there is still no sound.   And when I say no sound, that means no sound in the laptop speakers, on the headphones, or even via the mic (as suggested by some in the forums).

I have spent hours on this, following instructions in the forums and at [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide) and [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto), to no avail.  

alsamixer does not have the sound muted.  

I went into /etc/modprobe.d/alsa-base and tried every since model for hda-intel, the end result being that now when I try to play a file or CD, I get the error message "An error occurred  Could not open resource for writing."  I did not get this error message before altering the alsa-base file.   However, despite this message, the video plays for video files, and the time tracker moves for audio files, but no sound.

In the Device tab of the Sound Preferences window (System -> Preferences -> Sound), I have a number of choices for playback: Autodetect, AD198x Digital, AD198x Analog, ALSA, ESD, and OSS.  No matter what I set the sound options to, I get no sound.  Also, when I try testing each one, I get the error message "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music"Error playing CD.  Reason: Could not open resource for writing.": Could not open resource for writing."  (For OSS - Open Sound System, I get the error message "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not negotiate format").

In the Sound tab of the Sound Preferences window, I have ESD disabled.

I have already reinstalled ubuntu once, and I'm hoping to avoid having to do it again.

Attached are text files with the outputs of various commands I executed while scouring the forums for a solution.

Thanks for any help you can offer!

---

### Post by idunno3 on 2007-05-06
I got the sound to work.  I used the instructions below from the [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto"):

> 
The following command seems to fix some problems (specifically volume/sound quality) but may need to be run after each reboot (see bug #92171, [WWW] [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92171](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/92171))

kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*) ; sudo modprobe -r $(lsmod |grep ^snd |awk '{print $1}') && sudo modprobe snd-hda-codec && sudo modprobe snd-hda-intel model=auto


Now I tried this early on and it didn't work (I got an error message and not only did the sound still not work, but I also started getting error messages when sound applications launched).  However, I tried it again yesterday and it did work.  I have no idea why it worked the second time round.

---

### Post by BroadArrow on 2007-05-25
I had the same problem with a Thinkpad R51.

I installed the latest ALSA drivers, libraries, and utils and now have sound working for applications (eg: XMMS) but still don't have system sound. Eg: the system just does a basic beep when the login screen comes up or when new mail arrives.

I assume I need to tell the system to use ALSA -- does anyone know how I do that? (Bit of a newbie question, I know.) I installed a default sound card chooser and selected my sound card with it but it didn't resolve the problem.

---

### Post by BroadArrow on 2007-06-02
> **BroadArrow said:**
> I had the same problem with a Thinkpad R51.

I installed the latest ALSA drivers, libraries, and utils and now have sound working for applications (eg: XMMS) but still don't have system sound. Eg: the system just does a basic beep when the login screen comes up or when new mail arrives.

I assume I need to tell the system to use ALSA -- does anyone know how I do that? (Bit of a newbie question, I know.) I installed a default sound card chooser and selected my sound card with it but it didn't resolve the problem.

I have since found that I can get XMMS to play using OSS but not ALSA. But I still haven't found the cause of the problem.

---

### Post by rob.webinator@gmail.com on 2007-06-27
I have sound working on my T60p through what appears to be a bit of voodoo.  The steps I took:
1) First, I had no sound via:
Skype 
Rythmbox
Totem
Sound Preferences

2) Tried the "Test" buttons in the "Sound Preferences" dialog => NO Sound
3) I followed [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
4) Tried the "Test" buttons in the "Sound Preferences" dialog => still NO Sound
All the devices in this dialog were set to Autodetect except Sound Capture which was already set to ALSA and Default Mixer tracks which was set to "HDA Intel (Alsa mixer)"
5) Ran:
kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*) ; sudo modprobe -r $(lsmod |grep ^snd |awk '{print $1}') && sudo modprobe snd-hda-codec && sudo modprobe snd-hda-intel model=auto
6) Tried the "Test" buttons in the "Sound Preferences" dialog => still NO Sound
7) Rebooted several times.  Checked for upgrades,..., etc.
8 ) Installed XMMS for the heck of it and played with XMMS Output plugin settings. Still NO sound.  Ultimately reverted these settings to default.
9) In "Sound Preferences" under "Default Mixer Tracks" I selected all tracks for control (Ctrl-a).
10) I repeated 9) under "Volume Control" applet preferences.

***Voodoo***

Suddenly, sound now works in all of the original applications.  To get the mike to work for Skype, I had to turn on audio recording and it helped to unmute the mic boost.

---

