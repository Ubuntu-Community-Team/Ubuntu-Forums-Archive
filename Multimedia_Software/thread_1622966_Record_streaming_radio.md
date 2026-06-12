---
title: "Record streaming radio ??"
date: 2010-11-16
forum: Multimedia Software
---

### Post by oygle on 2010-11-16
I am not able to record streaming radio. Have tried VLC, sound recorder, Audacity, but cannot record/save the sound.

The site is [Revelation Worship Radio]("http://www.revelationworship.com/worshipradio.html") , seems to be done in Flash/shockwave, but I can hear the sound just fine with headphones, and seem to have it all setup for record. Installed the Pulseaudio 'extras', and the sound does seem to coming'in', but I cannot save the file. Well, the file is empty.

There is another link there - [Holy Fire Ascending & Descending]("http://www.revelationworship.com/archives/index.php?option=com_preachit&tmpl=component&id=5&view=audiopopup"), can hear it okay, but not record.   :(

Any clues please ?

Oygle

---

### Post by ell02 on 2010-11-16
[http://ubuntuforums.org/showthread.php?p=8043003](http://ubuntuforums.org/showthread.php?p=8043003)

Recording what is playing in the Speakers
Now that you have the Pulse Audio Controls this is easy. Open the Pulse Audio Volume Control from pa device chooser. Click the Input Devices tab. At the bottom click the box nest to Show: and select All Input Devices. Now, along with all the hardware input devices there are Monitors for them that will give you access to their outputs. To set the default device to one of the Monitors click on the green icon. To test this open Sound recorder and, with something playing through the device you selected the monitor for click record and record a few seconds. Now play it back. Viola!!

---

### Post by oygle on 2010-11-17
Thanks for your reply. I tried that, but no difference. Must be something in how I have it setup ?

Oygle

---

### Post by andrew.46 on 2010-11-17
Hi Oygle,

The second link can easily be downloaded as follows:
```

wget 'http://www.revelationworship.com/media/HolyFireDescending.mp3'
```

I did not have so much luck with the first link :(.

Andrew

---

### Post by oygle on 2010-11-17
Hi Andrew,

Thanks, yes I was able to see what MP3 files were on the second link. The first link, the radio station audio is all Flash/shockwave, and must be 98% there, as when I do the 'record sound', the Pulse Adio meter shows that it is definitely recording.

But when I stop the recording, stop the sound from the website, and try playing what has been recorded, no sound ??  I think it even shows playback on the meter, but I can't hear anything.

Oygle

---

### Post by lykeion on 2010-11-17
I had no problem recording using the method described by ell02.
When recording with Sound Recorder, did the level meter move to show you had input?

---

### Post by oygle on 2010-11-17
Yes, the level meter moved when it was recording. Here are the settings from the volume control, with sound and with recording sound running.

---

### Post by lykeion on 2010-11-17
You shouldn't use the microphone when recording, just the monitor output.
And I'm not sure why the PulseAudio Volume Meter is shown as a stream on the Recording Tab. For me it just shows Sound Recorder: Record stream from...

EDIT
Just to make sure, what do you record the stream as in Sound Recorder. Try to change to .ogg and see if it works better.

---

### Post by oygle on 2010-11-17
> **lykeion said:**
> You shouldn't use the microphone when recording, just the monitor output.

I tried to 'mute' the mic in volume control in 'sound recorder'; that didn't work.

Then on input devices tab in Volume Control, I tried to mute the mic there, but that didn't work. The only other options in that dropdown are 'Microphone 2 and Line-In.

> **lykeion said:**
> 
And I'm not sure why the PulseAudio Volume Meter is shown as a stream on the Recording Tab. For me it just shows Sound Recorder: Record stream from...

I had PA volume meter running, that's probably why.

> **lykeion said:**
> Just to make sure, what do you record the stream as in Sound Recorder. Try to change to .ogg and see if it works better.

Yes, I have been using .ogg

Thanks,

Oygle

---

### Post by lykeion on 2010-11-17
Sorry but I can't help you further. Hopefully someone else more knowledgable in the matters will step in...

Nice chattin' with you anyway and good luck.

EDIT
You can mute the mic in Sound preferences: 
Click Volume icon (at top panel) > Sound Prefrences... > Input Tab > Click Mute at Input volume for your mic connector

---

### Post by oygle on 2010-11-17
Okay, thanks for your help.  :)

---

### Post by mc4man on 2010-11-17
Just to mention, there is a little gui to recording thru pulse that seeemd to work well. ( tested it out for someone several months ago
Saves as ogg, mp3 or wav

Project page
[http://outrec.sourceforge.net/](http://outrec.sourceforge.net/)
Page w/ pdf instr.
[http://outrec.sourceforge.net/support.html](http://outrec.sourceforge.net/support.html)

---

### Post by Habitual on 2010-11-17
found this here yesterday, maybe it will help...

Create this script.
```

#!/bin/bash
# Copyright 2008-2009, Kees Cook <kees@outflux.net>
#
# Records the PulseAudio monitor channel.
# http://www.outflux.net/blog/archives/2009/04/19/recording-from-pulseaudio/
#
#**This script require sox**
#**sudo apt-get install sox**

if [ -n "$1" ]; then
    OUTFILE="$1"
else
    TIME=$(date +%d-%b-%y_%H%M-%Z)
    OUTFILE="recording_$TIME.wav"
fi

# Get sink monitor:
MONITOR=$(pactl list | grep -A2 '^Source #' | grep 'Name: .*\.monitor$' | awk '{print $NF}' | tail -n1)

# Record it raw, and convert to a wav
echo "Recording. Ctrl-C or close window to stop"
parec -d "$MONITOR" | sox -t raw -r 44100 -sLb 16 -c 2 - "$OUTFILE"

# End of sound_cap.sh

```

chmod 700 /path/to/sound_cap.sh

To use it...
Surf to an audio website and start Play. Open a terminal and execute /path/to/**sound_cap.sh "Name of the Song.wav"**

it will show "Recording. Ctrl-C or close window to stop" and put a WAV file in the directory it ran from ala
recording_16-Nov-10_2312-EST.wav / recording_16-Nov-10_2314-EST.wav
(These were made without the naming the song, i.e., sound_cap.sh)

When the Music stops playing, go back to the terminal and Press Ctrl-C

Replay at your leisure.

HTH.

---

### Post by oygle on 2010-11-17
> **mc4man said:**
> Just to mention, there is a little gui to recording thru pulse that seeemd to work well. ( tested it out for someone several months ago
Saves as ogg, mp3 or wav

Project page
[http://outrec.sourceforge.net/](http://outrec.sourceforge.net/)
Page w/ pdf instr.
[http://outrec.sourceforge.net/support.html](http://outrec.sourceforge.net/support.html)

Okay, thanks. Is the repository 'safe' to add ? I couldn't find outrec in Synaptic, but did find sox.

Oygle

---

### Post by oygle on 2010-11-17
> **Habitual said:**
> found this here yesterday, maybe it will help...

Create this script.

Thanks for that. I noticed a few other scripts on that site, one uses gstreamer.

So, I understand that this script uses the monitor approach, and gets the audio from that. How would it go getting continuos playing of radio songs, like at [http://www.revelationworship.com/worshipradio.html](http://www.revelationworship.com/worshipradio.html) ?

Oygle

---

### Post by mc4man on 2010-11-17
> Is the repository 'safe' to add
Sure - all it has in it is outRec. Or you could click download and pick the 3rd listed file - outrec_0.0.3-1_all.deb

Just gave it a try in maverick - works fine as long as you're using pulse audio. Basically it just uses the script or similar as shown in post 13.

If you don't click on either mp3 or ogg it will save as wav (saves in home folder/outrec in date-hr-min format

For Shoutcast-servers and Icecast-servers streamripper (kstreamripper or kradioripper are frontends) CAN work pretty good, usually is able to break into separate tracks based on metadata, though sometimes it doesn't get it quite right.

---

### Post by oygle on 2010-11-17
What I didn't mention (and it may, or may not be important), is that I'm using a steroe headphone for this. That is, there is a mic and headset, mic is input and headset/headphones are output.

Although I see that recording from the actual/physical sound card is where the audio must be obtained from, not from a headphone set, or any other output devices. Even the output jacks are not used, for this sound recording, it's all done from the sound card. Well, that's my understanding, so thought it best to mention it.

Attached are the pics of the external jacks from the computer, the sound card setup.

Seems funny that the way this is setup at present, the mic seems to be 'getting in the way', as i can see a small rise in an input meter, if I move the headset, as it picks up sound from the mic.

---

### Post by oygle on 2010-11-17
Well, outrec did the job.   :popcorn:

Thanks everyone for your help. Tried outrec on both of those links, and it worked just fine for both. The only 'weird' thing was you an save as MP3 or OGG, and the first 'record' was saved as MP3, yet the file was saved as WAV (bigger file). However, the second recording, saved as MP3, did save as MP3.

I won't even attempt to try this in sound recorder again, not after using outrec.  :D

Thanks.  :)

Oygle

---

### Post by mc4man on 2010-11-17
> the first 'record' was saved as MP3, yet the file was saved as WAV (bigger file). However, the second recording, saved as MP3, did save as MP3.
What you may have seen - it appears when recording to .mp3 that it's saved as a .wav, when you stop the recording it's converted to .mp3
If choosing ogg it's recorded directly to .ogg

(you should be 'careful' with the play/pause button, it looks like it's to listen to your recording after you finish. (but before closing

If you happen to click on **during recording** it will start playing the recording from the beginning but then that will be recorded on top of what you are still recording...

---

### Post by oygle on 2010-11-17
mc4man - Thanks for your tips on saving. I'll try and remember to **not** use the pause/play button. Incredible how a small app like outrec solved this problem. Thanks for your help, much appreciated.  :)

Oygle

---

