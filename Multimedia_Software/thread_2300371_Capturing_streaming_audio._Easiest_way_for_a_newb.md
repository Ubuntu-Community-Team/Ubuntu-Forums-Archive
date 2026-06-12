---
title: "Capturing streaming audio. Easiest way for a newb?"
date: 2015-10-25
forum: Multimedia Software
---

### Post by ozark_hillbilly on 2015-10-25
Goal: capture audio (non-music) portion only of video segments and save to a mp3 type file. I then want to access the saved file(s) from a wired network device on my LAN through my miniDLNA server software.
I have no experience in multimedia so I am searching for the most straightforward way to do this. I have Audacity but can't get the app to "see" the streaming audio off the video clip. There is also a PulseAudio program I read about on this forum, as well as "Streamripper" which I have downloaded. Streamripper works in terminal mode and has a lot of parameters/syntax I know nothing about correctly setting up.

Any clues or directions are appreciated. One obstacle for me could be that I have no separate audio/video card; everything is resident on the motherboard. But I would consider getting an external card if I could achieve my goal.

---

### Post by ozark_hillbilly on 2015-10-25
I have since discovered there is an app called 'Audio Recorder' that meets these requirements. Very straightforward to use.
information link: [http://itsfoss.com/record-streaming-audio/](http://itsfoss.com/record-streaming-audio/)

sudo apt-add-repository ppa:osmoma/audio-recorder
sudo apt-get update
sudo apt-get install audio-recorder

software is interpreting emoticon in first line of code above, not sure how to turn off; see link for clarification.

---

### Post by shantiq on 2015-10-31
Ozark entered in code see # above in Advanced reply mode the emoticon disappears :]

```
[COLOR=#617984][FONT=monospace]sudo apt-add-repository ppa:osmoma/audio-recorder
[/FONT][/COLOR][COLOR=#617984][FONT=monospace]sudo apt-get update
[/FONT][/COLOR][COLOR=#617984][FONT=monospace]sudo apt-get install audio-recorder[/FONT][/COLOR]


```

---

### Post by yoshii on 2015-11-02
On my Ubuntu Studio v14.04.3 audio-recorder works but is slightly buggy.  If I record a WAV file, it is only mono and it's at the wrong header samplerate.  If I record as FLAC it's in stereo but still the wrong header samplerate.  So what I do is convert the FLAC to WAV, import the wave into OcenAudio and set the header samplerate to 40516.875 and the do the resample command to 44.1 kHz and it comes back down to normal pitch and has the correct header.  Then I convert it to FLAC again and delete the old versions.  But still it's better than nothing.  I tried other techniques that failed.

---

### Post by shantiq on 2015-11-02
Alternatively t[his here]("http://ubuntuforums.org/showthread.php?t=1710642&p=11053351#post11053351") is an excellent way to grab desktop sound

---

### Post by Cinderboot on 2015-11-04
Solution#1
Use Audacity together with pavucontrol.

Audacity is a fantastic audio recorder / mixer, and pavucontrol will allow audacity to record from the sound card (what you hear through your speakers).

If I find the original thread of how to setup pavucontrol I'll link here, but it's fairly straightforward.

Solution#2
Use avconv

I forget all the options but this is great if you know exactly where you want to extract audio and how long you want to record for.

man avconv  will give all the options.

---

### Post by shantiq on 2015-11-05
> **Cinderboot said:**
> 

If I find the original thread of how to setup pavucontrol I'll link here, but it's fairly straightforward.



this is the [setting]("http://ubuntuforums.org/attachment.php?attachmentid=197595&d=1310816125") you pick on pavucontrol


ps   then to return to original setting afterwards

---

### Post by yoshii on 2015-11-06
> **shantiq said:**
> this is the [setting]("http://ubuntuforums.org/attachment.php?attachmentid=197595&d=1310816125") you pick on pavucontrol


ps   then to return to original setting afterwards

I don't have any of those options on my pavucontrol... which version are you using?

---

### Post by shantiq on 2015-11-06
hi yoshi.  Oh that is because i have an external soundcard added
All one needs to know is to pick **Monitor of internal etc **to grab desktop sound   and then to change back once done

---

