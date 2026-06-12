---
title: "audio settings"
date: 2008-05-01
forum: Multimedia Software
---

### Post by wombil on 2008-05-01
Hello All,
When I go to applications>sound and video> sound recorder, I get a message stating,"Your audio capture settings are invalid.Please correct them in the multimedia settings".
How do I get to the multimedia settings and how do I correct them?
I suppose I would set them all at default if I could find the place to do it.
I have been mucking around a lot trying to get skype working and probably changed some things.Still no sound out in skype tho.
I have ubuntu 7.10

---

### Post by rakavka on 2008-05-03
Hi guys , I'm new to linux.
Yesterday I installed ubuntu 8.04 and have a similar problem. No audio capture is working. Tried this [link]("https://help.ubuntu.com/community/AudioCapture") but it didn't work. Also I have tried all the devices in sound preferences/sound capture. All tests gave me white noise.I don't understand why there is no autodetect like in other devices. Also I hear white noise in my speakers. But when I mute the mic, it disappears.

I'm starting to love this OS but this little things are frustrating  :)

Thanks

---

### Post by tiggsy on 2008-06-20
Another noob trying to record. Same symptoms. When I open Sound Recorder i get an alert box with "Your audio capture settings are invalid. Please correct them in the Multimedia Settings." I've done the speaker settings thing, found the recorder tab (had to close and reopen after enabling Microphone capture - there wasn't a "Capture" option shown). Still get the same thing when I try to start Sound Recorder.

I'm trying to record a short message for my website. I used to do this with something also called Sound Recorder on Windoze with no problem... (I don't have windows any more, for the foreseeable).

Forgot to mention, I'm using Hardy - warts and all.

---

### Post by sallymc on 2010-01-11
I'm having the same problem.  Any solutions out there?

---

### Post by Yellow Pasque on 2010-01-11
sallymc, does this command allow you to access the multimedia settings?
```
gstreamer-properties
```

---

### Post by sallymc on 2010-01-13
Yes Temujin, it does.  The test for the default output makes a noise and the default input test  is silent. Does this help you?

---

### Post by sallymc on 2010-01-13
And Temujin, perhaps this will help you too:  The default input pipeline says :

halaudiosrc udi=/org/freedesktop/Hal/devices/pci_1039_7502_sound_card_0_alsa_capture_0

Holding thumbs.  Sally

---

### Post by sallymc on 2010-01-14
> **Temüjin said:**
> sallymc, does this command allow you to access the multimedia settings?
```
gstreamer-properties
```

Yes Temujin it does.  The test for the default output makes a sharp noise and the default input test is silent.

The default input pipeline says : halaudiosrc udi=/org/freedesktop/Hal/devices/pci_1039_7502_sound_card_0_alsa_capture_0

Holding thumbs.  Sally

---

### Post by Yellow Pasque on 2010-01-14
There's another tab in that dialog where you'll find the video settings, including the video input..

---

### Post by sallymc on 2010-01-14
> **Temüjin said:**
> There's another tab in that dialog where you'll find the video settings, including the video input..

  	 	 	 	 	 	  On the video tab, the plugin box reads 'video for Linux 2 (v4l2).  The test reads 'Cannot identify device '/dev/video0' .


Then the terminal read :


sally@sally-desktop:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(429): gst_v4l2_open (): /pipeline1/v4l2src3:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(429): gst_v4l2_open (): /pipeline2/v4l2src5:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(429): gst_v4l2_open (): /pipeline4/v4l2src6:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device '/dev/video0'. [v4l2_calls.c(429): gst_v4l2_open (): /pipeline5/v4l2src7:
system error: No such file or directory]

---

### Post by Yellow Pasque on 2010-01-14
Oh, sorry, you were asking about audio input. YOu should be able to set the audio input to Pulseaudio, or set it to custom and write 'pulsesrc' (no quotes) in the pipeline box.

---

### Post by sallymc on 2010-01-14
> **Temüjin said:**
> Oh, sorry, you were asking about audio input. YOu should be able to set the audio input to Pulseaudio, or set it to custom and write 'pulsesrc' (no quotes) in the pipeline box.

I did this Temujin.  It made no difference to the sound.  I can hear something, but it is very feint.  When I shout loudly into the mic, the reproduction improves, but it is very muffled.  So there is something there.

Perhaps I should tell you that I am trying to record on Audacity.  The message is :

'Error while opening sound device. Please check the input device settings and the project sample rate.'

I am a real newbie.  Could this be an incorrect setting with Audacity, or is it an Ubuntu problem?

Thanks for your patience.

---

### Post by Yellow Pasque on 2010-01-14
Try killing pulseaudio before startin Audacity:
```
sudo killall pulseaudio
```
I know Audacity used to have issues with pulseaudio (because audacity uses a library called portaudio). I'm not sure whether the issues between portaudio and pulseaudio were ever fixed.

---

### Post by sallymc on 2010-01-14
> **Temüjin said:**
> Try killing pulseaudio before startin Audacity:
```
sudo killall pulseaudio
```I know Audacity used to have issues with pulseaudio (because audacity uses a library called portaudio). I'm not sure whether the issues between portaudio and pulseaudio were ever fixed.

Message reads :
pulseaudio: no process killed

Any other suggestions?

---

