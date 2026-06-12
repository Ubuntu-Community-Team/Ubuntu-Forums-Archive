---
title: "Recording through Audacity in Ubuntu 16.04"
date: 2017-01-08
forum: Multimedia Software
---

### Post by AnupamMitra on 2017-01-08
I installed Audacity. Though it plays quite okay but I failed to record through Audacity. Need suggestions. It is needless to mention that I have gone through the available posts in many forums but the issue couldn't be solved.

---

### Post by TheFu on 2017-01-08
Is the microphone or other device to be recorded recognized?  Without facts, we cannot help.  My USB mic shows up in the list of available recording devices. Selecting it just works.

---

### Post by ajgreeny on 2017-01-08
Does your microphone work in other applications with which you have tried it?
Can you hear anything from your speakers if you have it set as input device?

---

### Post by AnupamMitra on 2017-01-08
Yes, I can hear from the speakers of my computer  when I play any audio/video file. Even it is audible if I play any audio file through Audacity. It might be that I failed to select proper recording device in Audacity as there are so many options to choose.

---

### Post by TheFu on 2017-01-08
Thought the question was about recording stuff, not hearing stuff? 2 different things.

---

### Post by ajgreeny on 2017-01-08
> **TheFu said:**
> Thought the question was about recording stuff, not hearing stuff? 2 different things.
Yes it is, but at least we now know that the microphone does work.

Start recording something in audacity, then open Sound Settings (pulseaudio volume control) and check your settings there on both the **Input Devices** and **Recording** tabs; I suspect you will find one of them is set too low or muted completely, or even using the wrong device.

---

### Post by AnupamMitra on 2017-01-08
@ TheFu - Yes, I do know that these (hearing & recording) are two different things. That's why initially I mentioned at #1 - "Though it plays quite okay but I failed to record through Audacity".

---

### Post by Dennis N on 2017-01-08
I leave the Audacity selections for host / output device / input device as: ALSA / default / default 

For recording from microphone, I select the input device in pulse audio volume control > input devices tab > microphone. Then return to Audacity window and start monitoring the mic while using it. 

During monitoring, set input volume level in pulse audio volume control > recording tab. (Note: Nothing shows in the recording tab unless you are either monitoring or actually recording)

After setting the recording level, you are ready to do the real recording with the 'record' button.

---

### Post by AnupamMitra on 2017-01-08
> **Dennis N said:**
> I leave the Audacity selections for host / output device / input device as: ALSA / default / default 

For recording from microphone, I select the input device in pulse audio volume control > input devices tab > microphone. Then return to Audacity window and start monitoring the mic while using it. 

During monitoring, set input volume level in pulse audio volume control > recording tab. (Note: Nothing shows in the recording tab unless you are either monitoring or actually recording)

After setting the recording level, you are ready to do the real recording with the 'record' button.

Thanks for your reply. My case is different. I want to record a particular portion of an Audio MP3 file through Audacity. This audio file is being played through VLC or Rhythmbox Player. And while I'm going for recording in Audacity, inspite of using 'record' button, proper graphs or waves, which is a sign of recording, is not visible. Instead, a straight line is being drawn at the time of recording which is useless. Hope, I could express my problem.

---

### Post by tea for one on 2017-01-08
> **AnupamMitra said:**
> Thanks for your reply. My case is different. I want to record a particular portion of an Audio MP3 file through Audacity. This audio file is being played through VLC or Rhythmbox Player. And while I'm going for recording in Audacity, inspite of using 'record' button, proper graphs or waves, which is a sign of recording, is not visible. Instead, a straight line is being drawn at the time of recording which is useless. Hope, I could express my problem.

This tutorial should prove useful:-

[http://confoundedtech.blogspot.co.uk/2012/04/ubuntu-record-what-you-hear-on-ubuntu.html](http://confoundedtech.blogspot.co.uk/2012/04/ubuntu-record-what-you-hear-on-ubuntu.html)

Kind regards

---

### Post by Dennis N on 2017-01-08
> **AnupamMitra said:**
> I want to record a particular portion of an Audio MP3 file through Audacity. This audio file is being played through VLC or Rhythmbox Player.

Since you have an existing mp3 file, just import that file into Audacity and then you can edit the content. When done, export as mp3.

From what you say you want to do, you would select the portion to be kept, and then use **file > export selected audio** to save what you selected.

---

### Post by ajgreeny on 2017-01-08
As you want just a portion of an existing mp3 you could also use the command line application mp3splt which will split an mp3 in a variety of ways, most probably you need the timing of the start and finish of the portion you want which you can set to 100ths of a second if you need to.

mp3splt, (and that is not a typo with a missing i in the name) will split a file into parts without decoding and re-encoding which audacity would have to do, so there is no potential for quality loss.  I have used it quite a lot to make separate tracks from a long CD recording of all tracks on one side of old vinyl LP records which I can transfer to a CD-RW using an Audio-CD-Recorder.  I then rip that CD-RW to a single mp3, and finally split that with mp3splt.

---

### Post by AnupamMitra on 2017-01-09
> **tea for one said:**
> This tutorial should prove useful:-

[http://confoundedtech.blogspot.co.uk/2012/04/ubuntu-record-what-you-hear-on-ubuntu.html](http://confoundedtech.blogspot.co.uk/2012/04/ubuntu-record-what-you-hear-on-ubuntu.html)

Kind regards

Thanks for providing me this useful link. Really it is very simple to understand and follow. My problem stands SOLVED. Best wishes Tea For One.

---

