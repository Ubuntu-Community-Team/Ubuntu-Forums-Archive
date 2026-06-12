---
title: "No micophone  after updates"
date: 2010-10-25
forum: Multimedia Software
---

### Post by thelugnut on 2010-10-25
I am using Ubuntu 10.10 running on an HP All-in-One 200.

I just installed the latest Ubuntu updates and lost my microphone input.

Audio out works fine.

I tested the microphone on Windows 7 and it works, so it appears to be an Ubuntu problem.

---

### Post by lidex on 2010-10-25
> **thelugnut said:**
> I am using Ubuntu 10.10 running on an HP All-in-One 200.

I just installed the latest Ubuntu updates and lost my microphone input.

Audio out works fine.

I tested the microphone on Windows 7 and it works, so it appears to be an Ubuntu problem.
May have reset your configuration.
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by thelugnut on 2010-10-26
Thanks for the reply.

> May have reset your configuration.
First, for mic problem, check this.
Gnome-alsamixer
Using Alt+F2 run dialog
Code:

 gnome-alsamixer



I have attached a screenshot of gnome-alsamixer. I see a front microphone and a microphone boost. I was expecting to see a just plain microphone. That was a bit of a surprise, but since I hadn't checked prior I can't be sure it hasn't always been this way.

> Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.


The second screenshot of "Sound Preferences" is another surprise for me. It doesn't show a microphone at all. 

I then connected an external microphone and reran the complete sequence above with identical results.

My conclusion is Ubuntu can no longer find my microphone.

Please advise if there are further steps to be taken, If not, I will re-install Ubuntu 10.10 and see what happens. If the microphone works on the initial installation, my plan is to note the updates carefully to see if one or more of them didn't zap the microphone detection process.

What do you think?

---

### Post by thelugnut on 2010-10-26
I don't see the attachments so will try again.

---

### Post by thelugnut on 2010-10-26
I forgot to mention that I have Ubuntu 10.04 on a separate partition and it has none of these problems.

---

### Post by lidex on 2010-10-26
What profile do you have selected? Also did you check in 'edit > soundcard properties' in gnome alsamixer
to make sure relevant items are enabled? Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by thelugnut on 2010-10-26
Sorry to have to ask, but I don't ubderstand " What profile do you have selected?".

Yes to the "soundcard properties"

I executed the code and have a long list of data.

I could not find the upload option you mentioned. I did execute the "[Terminal="Applications->Accessories->Terminal"] and have that long file but really don't know what to do with it.

---

### Post by thelugnut on 2010-10-26
I formatted the partition, and reinstalled Ubuntu 10.10.

Then installed all updates.

The microphone works.

I am waiting for the next two updates prior to signing this thread as solved.

---

