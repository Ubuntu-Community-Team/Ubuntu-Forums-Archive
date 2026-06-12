---
title: "Sound Recorder"
date: 2011-07-29
forum: Multimedia Software
---

### Post by vlvlvl on 2011-07-29
Is there a Sound Recorder like the Total Recorder for Windows?
Someone told me to use Audacity, but Audacity recorded the mic input (e.g. the net radio sound through the speakers together with the noise of the room). Maybe I just cannot find the right settings.

---

### Post by ajgreeny on 2011-07-29
What are you trying to record?  You could stop the mic being the capture device easily in many ways, alsamixer is what I use, but it depends on what version of ubuntu or the ubuntu family you are using.

---

### Post by vlvlvl on 2011-07-29
I have Ubuntu 10.04 Lucid Lynx 64 bit.
The problem is that Audacity just records from the mic and nothing else.
I would like to record netradio etc.
Audacity records it, but only from the speakers together with room noise.

---

### Post by ajgreeny on 2011-07-29
I accept that it is not straightforward to record the sounds going through your soundcard, but try this.  Open up **pulseaudio-volume-control** from sound and video menu, with audacity open and recording, never mind at the moment if it does not record.  Now on the pulseaudio-volume-control go to the recording tab and set it to "Monitor of internal audio" or something similar, depending on your hardware.  You may need to install **pavucontrol** if it is not already installed, which I don't think it is by default.

You should now be able to record everything going through the sound card, including any streaming radio, and as long as you switch of or turn down the mic volume in alsamixer you will not get any mic input to audacity.

However for streaming radio there are better ways than using audacity, which may allow you to simply dump the stream to file as it comes down by using streamripper/streamtuner, or even good old mplayer.  Come back here again if you want to go further with that possibility.

---

### Post by vlvlvl on 2011-08-01
Thank you for the advice.
I think I do not bother with Audacity any more.  Would be glad if you explain the streamripper/streamtuner, or mplayer options.

---

### Post by ajgreeny on 2011-08-02
Install streamtuner and streamripper from the repos and when you run streamtuner it will do all the work for you, and record streaming audio using streamripper.

I use both applications but normally just use streamripper from script files to record streams at specific times using cron (actually gnome-schedule), which means I can set up recordings for times when I am not at the computer.

The difficult bit can be finding the correct URLs for the streams, but usually you can get that from the appropriate webpage.

Example script
```
#!/bin/bash
/usr/bin/streamripper <URL> -t -r -d /home/*user*/Radio
```This is simple as you can see, and simply gives the streamripper path, the URL, and options: -t for new file number each time, -r for a relay to port 8000 so you can listen as it records by pointing your media player to [http://localhost:8000](http://localhost:8000), and -d for the file pathway or destination.

The script for mplayer is similar.
```
#!/bin/bash
/usr/bin/mplayer <URL> -dumpstream -dumpfile stream.mp3
```

---

### Post by dniMretsaM on 2011-08-02
Just so you know, you can change where Audacity records from.

---

### Post by ajgreeny on 2011-08-03
> **dniMretsaM said:**
> Just so you know, you can change where Audacity records from.
That was where this thread started; the OP could not manage to do that and we were looking to show how it is done.  Not successfully, however, hence these other suggestions.

---

