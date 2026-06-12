---
title: "VLC webcam AUDIO capture, which device do I use?"
date: 2009-11-20
forum: Multimedia Software
---

### Post by josefski on 2009-11-20
Ubuntu 9.1
Eeepc 1005 
I'm not finding a single useful piece of information on this one. I'm using VLC to capture video from my webcam. Under streaming I set the video device to /dev/video0. The trouble is, NOTHING I have tried in the /dev directory works for audio.

Even just an example of a setting that actually works for *someone* would be helpful. All the how to sites simply state "enter your audio settings" or contain something hypothetical. 

Where should I tell VLC to look for the audio coming from the microphone?

---

### Post by VertexPusher on 2009-11-20
Enter "default" to capture from the default sound card.

If your webcam has a microphone that is separate from the main soundcard, enter
```
arecord -l
```
into a terminal window to get a list of audio capture devices. The list will look similar to this:
```
**** List of CAPTURE Hardware Devices ****
 card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
   Subdevices: 1/2
   Subdevice #0: subdevice #0
   Subdevice #1: subdevice #1
```
Each card has a number and a name. In the example above, the card name is "Intel". Find out the name of the webcam microphone card, then in VLC enter
```
plughw:name
```

---

### Post by josefski on 2009-11-21
You sir, are a gentleman and a scholar. Thank you very much. 

Problem Solved

---

### Post by josefski on 2009-11-24
I wasn't sure whether to start a new thread for this or not, but, I got the audio to work, as in, it doesn't generate an error message and when I hit "play" I can hear it through the headphones. But now it won't record. I can capture the video stream just fine, but no audio, no matter which container I use. 

Any ideas anyone?

---

### Post by Francewhoa on 2010-03-26
Same here when I hit "play" I can hear the sound through the headphones. But when I hit "convert/save" it won't record the sound. I can record the video stream just fine, but no audio.

---

### Post by leon11 on 2011-04-03
I got it working this way:  My computer has a Hauppauge PVR card (Bt878 chip) with A/V and onboard intel audio (name = I82801DBICH4).  I did what vertexpusher said with some easy tweaking.  I went to System>Preferences>audio>input and selected Internal Audio and made sure it wasn't muted.  Hook up and play your audio source to the correct jack and change CONNECTOR option until the "Input Level" shows dancing bars indicating sound is detected.  Type hw:I82801DBICH4 (in my situation) in VLC's "Audio device name" box, Then type /dev/Video0 in the "Video device name" box. (this might be different for some people.)  Then click "Advanced options..."  Here, try changing "Input" and "Audio Input" values to 1 if it wasn't working otherwise.  For capture cards and cameras with multiple inputs, the correct INPUT value needs to be selected, usually 0, 1 or 2.  Then hit play to test your settings.  I hope this works for you, it took me hours.

---

### Post by leon11 on 2011-04-03
correction: in vlc, capture mode needs to be set to "Video for Linux 2"

---

