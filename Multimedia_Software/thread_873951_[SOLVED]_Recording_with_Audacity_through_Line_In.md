---
title: "[SOLVED] Recording with Audacity through Line In"
date: 2008-07-29
forum: Multimedia Software
---

### Post by m_ad on 2008-07-29
No matter what device I pick, I get no audio through Line In in Audacity. Can someone help me setup my system to record with Audacity?

In Audacity Preferences under Recording, I have the options:
ALSA: default
ALSA: hda NVidia
OSS: /dev/dsp

I've attached a screenshot of alsamixergui.

---

### Post by Ben Carlin on 2008-07-29
Hey audacity does not work for me either.. Where is the Recording Tab? I don't even have that under preferences? This is very frustrating.. I know my mic works as I have tested it in "Sound Recorder" after changing the defualt input from AUX to Line-in... Help!

---

### Post by djxcon on 2008-07-29
In the alsamixer screen shot, do you have the capture devices turned up?  Also, do you have Jack installed.  If so, you could capture your audio through Jack and then set Audacity to record the feed from Jack. The front end gui for Jack is qjackctl.  Note: you should not _need_ Jack...just an idea though.

---

### Post by m_ad on 2008-07-29
It appears that both my capture devices are turned all the way down. I can't turn them up though.

---

### Post by djxcon on 2008-07-29
Not sure why you cannot enable the capture device.  Have you check the alsa page to see if your card is supported?

[http://www.alsa-project.org/main/index.php/Matrix:Main]("http://www.alsa-project.org/main/index.php/Matrix:Main")

When you go into System -> preferences -> Sound, what have you selected as the recording device?  When you test the recording feature, does it error out? 

I would also encourage you to take a look at the Comprehensive Sound Problems Solution Guide:
[http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by cotcot on 2008-07-29
I recently got my line-in working :

---> right click Volume applet (that is the loadspeaker icon where you change the volume)
---> Open Volume Control
---> Edit
---> Preferences
See if line-in and microphone are checked.
Thick Input Source. That gives a new tab (Option) in the Open Volume window where you can define the capture device for the Input Source.

This is a copy of my post in [[COLOR="Red"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=828932&page=2").

---

### Post by lukjad on 2008-07-29
cotcot has the right answer. I had the same problem a while back and this is what solved it for me.

---

### Post by m_ad on 2008-07-29
I activated the "Capture," "Capture 1" and "Capture 2" under Preferences. Now Audacity says "Error while opening the sound device. Please check the input device settings and the project sample rate." My sample rate is at 44100 and this error happens in both ALSA devices. :confused:

I don't have a "Line In" in the preferences either. See the screenshots.

---

### Post by djxcon on 2008-07-30
Please post the results of the following:

```
aplay -l
```

Then type the following (after you type the - make sure to press tab and then agree to the message about displaying all possibilities): 
```
sudo modprobe snd-
```

Do you see the matching module on this list that you saw in the first command?

---

### Post by m_ad on 2008-07-30
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
matt@ubuntu-desktop:~$ sudo modprobe snd-
[sudo] password for matt: 
FATAL: Module snd_ not found.

```

---

### Post by djxcon on 2008-07-30
> matt@ubuntu-desktop:~$ sudo modprobe snd-
[sudo] password for matt: 
FATAL: Module snd_ not found.

You have to press TAB after typing the hyphen

---

### Post by m_ad on 2008-07-30
I did, all that happened when I pressed tab was a system beep from the box.

---

### Post by djxcon on 2008-07-30
I am not sure why you are getting a beep sound but we would be looking for the STAC92xx module.  

It may be that Alsa does not support the card (not sure on that either).  In the System -> Preferences -> Sound dialog, have you tried setting the record device to something like OSS and then running the test? 

Should have asked earlier on, what version of Ubuntu are you using?

---

### Post by m_ad on 2008-07-30
Using 8.04. In the Sound Preferences, which would be the recording device? Is it under Default mixing tracks?

---

### Post by m_ad on 2008-07-30
I'm starting to think it's my sound card and nothing in the Sound Preferences, no matter what I change Audacity gives me "Can't open sound device" error.

---

### Post by djxcon on 2008-07-30
Look at Sound Capture.  Do you have this set for Alsa?  I would try some of the options in the drop down menu and then click on the Test button.  See if they are erroring out or if the test actually processes.

---

### Post by m_ad on 2008-07-30
It was originally set to ALSA, and it seems if I test any other devices it doesn't progress at all. Just gives the status bar back and forth for a pretty long time.

---

### Post by djxcon on 2008-07-30
This is a good sign.  With this feature, you will either see the progress bar bounce from side to side or it will error out completely.  When you flip it back to Alsa, does it error out or does it also bounce from side to side?

---

### Post by m_ad on 2008-07-30
It just bounces back from side to side :confused:

---

### Post by djxcon on 2008-07-30
I believe this is a good sign...bouncing means you are not getting an error.  

Do you have any other recording programs installed other than Audacity?  I find that Audacity can be a bit slow when changing the settings around.

---

### Post by m_ad on 2008-07-30
No, do you have any recommendations?

---

### Post by djxcon on 2008-07-30
I'll check out a few that I have installed and let you know...stay tuned.

---

### Post by m_ad on 2008-07-30
I liked the looks of Audacity because you can insert splits and save as tracks. I'm coming from Windows with Nero WaveEditor.

---

### Post by djxcon on 2008-07-30
I understand and Audacity is not out of the question...just not great for troubleshooting.  Do you have Sound recorder installed? If so, set your Capture Device to something like PulseAudio and make sure the test gives you the bouncing progress bar. 

Next, open sound recorder. Click on File -> Open Volume Control.  

On the volume control dialog, click file -> Change device.  On this dialog do you see any capture devices?  If so select one. 

Now click record in Sound Recorder.  Do you see that the program is trying to record? Make sure you send an audio feed into the line in and the mic in.  See if either get picked up by this program by playing the sound back. 

If this test fails...you may want to repeat these steps by changing PulseAudio to other options and then re-opening sound recorder for a new test.  Let us know...

---

### Post by m_ad on 2008-07-30
I've tried this with every setting :confused:

It attempts to record, but records blank.

---

### Post by djxcon on 2008-07-30
What devices do you see as the capture device in Sound Recorder --> Volume Control?

---

### Post by m_ad on 2008-07-30
Confused as to where you mean.

As for in the Volume Control, when I go to File->Change Device, I have two capture options:
a) 3: Capture: Monitor Source of ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)
b) 4: Capture: Alsa PC on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)

When I select one of them, the only volume control I see is for 'Master.'

In Sound Recorder, 'Record from input:' I have the options of Capture, Capture 1, Capture 2, Digital, Mux, Mux1 and Mux2.

All possible combinations don't record audio. No errors, just blanks.

EDIT: Actually, when I set the Capture device to 'PulseAudio' in Sound Preferences, the only Record from input in Sound Recorder I get is Master.

---

### Post by m_ad on 2008-07-30
I forgot to mention also, that when I play the device I'm trying to record through I don't get any sound through my speakers. I didn't think much of this since this is the way it was in Windows.

---

### Post by djxcon on 2008-07-30
Let's set the capture device to Pulse Audio in System -> Preferences -> Sounds.  Can you also show a screnshot of the items on this list?

Let's set Sound Recorder to the "Capture: Monitor Source of ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)" device.

Now, do you have an applet on the Gnome toolbar for your audio properties?  Forgive me as I am trying to recall from memory here...If so, open the properties and let's try to set this to a similar capture device if not already.  I am trying to make sure that all possible mixers are in sync, un-muted, and turned up in volume.  

Once you have checked all of these settings, let's try to record something.  Have you also tried the mic in just for the sake of troubleshooting? 

Also, what do you mean by this:
> I forgot to mention also, that when I play the device I'm trying to record through I don't get any sound through my speakers. I didn't think much of this since this is the way it was in Windows. 

---

### Post by m_ad on 2008-07-30
> **djxcon said:**
> Let's set the capture device to Pulse Audio in System -> Preferences -> Sounds.  Can you also show a screnshot of the items on this list?

Let's set Sound Recorder to the "Capture: Monitor Source of ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)" device.

Now, do you have an applet on the Gnome toolbar for your audio properties?  Forgive me as I am trying to recall from memory here...If so, open the properties and let's try to set this to a similar capture device if not already.  I am trying to make sure that all possible mixers are in sync, un-muted, and turned up in volume.  

Once you have checked all of these settings, let's try to record something.  Have you also tried the mic in just for the sake of troubleshooting? 

Also, what do you mean by this:

Screenshot is attached. How do you set Sound Recorder to use a specific device? All I can do is File->
Open Volume Control, which is the same as your next suggestion. They both open the same dialog, Volume Control.

I'll try with mic in now. What I mean by I can't hear audio is, when I play the device that I'm trying to record from (my radio), I don't actually hear the audio through my computer speakers. I didn't think this was an issue as my Windows machine is the same way, although it does record the audio.

---

### Post by m_ad on 2008-07-30
:lolflag: I really appreciate your help djxcon, using putting the jack in Mic In records :)

Now, let's try and get Audacity to record :)

EDIT: Audacity works, I had to set the Recording device to 'OSS: /dev/dsp,' and I can control my volume through ALSA PCM (PulseAudio Mixer) through Volume Control.

By the way, if you're familiar with Audacious (this is my first time using it), how do I insert splits, then save as multiple tracks? I'm assuming Edit->Split is the way to split them, but I don't know how to save the split audio as seperate files.

---

### Post by djxcon on 2008-07-30
Great!  Glad to see this worked out for you.  I am not sure on the splitting track question though but keep at it.

---

### Post by m_ad on 2008-07-30
Weird, I am testing the splits. I have followed [this]("http://audacity.sourceforge.net/help/faq?s=files&i=split") mini tutorial, but when I export the tracks, it says it exported 3 but there are really only 2 :confused:

EDIT: It seems I have to add labels for them to export correctly.

---

### Post by m_ad on 2008-07-31
djxcon, Thanks again for your excellent help :)

---

### Post by ssdt on 2010-06-22
I tried the tips given here and was successful at recording through line-in but the volume was really low even if i had put it up and there was a heavy sound frequency.

---

