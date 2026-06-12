---
title: "Recording volume very low on Dell M1530"
date: 2009-06-05
forum: Multimedia Software
---

### Post by KingNeil on 2009-06-05
The ONLY operating system installed on my Dell XPS M1530 is Ubuntu 9.04. The microphone recording level is so low that it's unusable.

I've tried enabling all the recording parts in Volume Control. The problem is: all of them have a red cross next to the microphone icon: that's Capture, Capture 1, Capture 2, Mux, Mux1 and Mux2. If I uncross it, exit and go back in, the cross is still there.

Anyone have a solution?

Here's a screenshot:

[IMG]http://img235.imageshack.us/img235/7060/screenshotb.png[/IMG]

---

### Post by KingNeil on 2009-06-05
Anyone have any ideas about this?

---

### Post by KingNeil on 2009-06-09
UPDATE: I can go into Audacity and do an "Amplify" effect. That brings my mic to an acceptable level, so that's good.

However, that obviously doesn't solve my problem when using other programs, such as Skype, so what I'm really looking for is some way of doing a mic boost.

Anyone know how I can do a mic boost using Ubuntu? I can't find the option anywhere, and I did have this option on Vista -- so I know it exists.

---

### Post by jekscar on 2009-06-13
Experience the same issue on my Dell 1520. Only working OS is Ubuntu JJ... Does anyone have any idea how to rise mic volume to make skype being usable?


---------------------
Added on Jun 15th
To who may concern: I've solved installing gnome-audio-control-pulse. It doubles the volume icon on the gnome bar but allow you to enable sound input.

Ciao!
-----------------------

Jek

---

### Post by Dave_Jackson on 2009-07-28
Hi all.

I believe I have found a solution. This was tested on my m1530 laptop under 64-bit Jaunty, but probably works on other systems as well. 
This sounds similar to what jekscar said, but his post lacks details on how to achieve this. 

Here is the link where the solution is described:
[http://justscript.blogspot.com/2009/06/ubuntu-dell-m1530all-microphone-boost.html]("http://justscript.blogspot.com/2009/06/ubuntu-dell-m1530all-microphone-boost.html")

Hopefully I've been able to help someone.

I personally set my alsa_input volume at around 134% because I found that setting it much higher resulted in too much background noise being captured during recording.
Of course, your results may vary, so try whatever works best for you. 

Also, I suppose if you find your alsa_output (playback) volume too loud or too soft, this trick may also work there as well.

This seems to be a pretty common problem, so I hope the release team sets the capture volume a bit higher in future releases.

---

### Post by igorzwx on 2009-07-28
And the quality of recordings?

Do you have strange noise, artefacts?

---

### Post by igorzwx on 2009-07-28
"Does anyone have any idea how to rise mic volume to make skype being usable?"

Both Skype and Ekiga work well on my old boxes (Ubuntu 9.04 + OSS4)
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by Dave_Jackson on 2009-07-28
> **igorzwx said:**
> And the quality of recordings?

Do you have strange noise, artefacts?

I'd say the quality of the recordings is decent for a built in microphone.
It would probably be better using a USB microphone or headset. Also, something else that affects quality would be the recording format. 

For example, in Gnome's sound recorder under Record As: you have the option of choosing lossless formats. These lossless formats are generally the best if quality, but not hard drive space is a concern. Basically lossless means it will lose the minimal amount of fidelity to the original recording.

I'm sure you can find similar options in other recording problems such as Audacity. In fact, I would recommend Audacity over Gnome Sound Recorder as it has many more options and actually lets you edit what you record.  

As far as noise, there is some white noise in the background, but I think you're going to have a little of that on any configuration. If you set the volume too high, it will be more sensitive and thus pick up more of this background noise. I think Audacity has an option to try to cancel out background noise in the Effect menu, so you may want to look into that. 

However, if you set it too low, it won't pick up what you're recording very well. So it's about finding a satisfactory balance between the two.

---

### Post by igorzwx on 2009-07-28
I have recorded a lot with Audacity.

Can you record 1 sec of "silence" and then investigate spectrogram with
Audacity tools?

Have you tried such things?

---

### Post by igorzwx on 2009-07-28
Simply: Audacity noise removal tool can remove "natural noise",
but it cannot remove artefacts produced by PulseAudio.

---

### Post by KingNeil on 2009-07-28
> **Dave_Jackson said:**
> 
Here is the link where the solution is described: [http://justscript.blogspot.com/2009/06/ubuntu-dell-m1530all-microphone-boost.html](http://justscript.blogspot.com/2009/06/ubuntu-dell-m1530all-microphone-boost.html)


This seems like a solution that will work. I have a question, though: will Pulse completely replace whatever sound system I have now? Will that have any adverse effects on applications? Or, is this just Pulse for recording? 

I have a nasty feeling this will break the sound in a whole bunch of applications. Just my instinct. I'm no expert, not even an intermediate.

---

### Post by igorzwx on 2009-07-28
Do you mean this thing?

sudo apt-get install pavucontrol

---

### Post by KingNeil on 2009-07-29
> **igorzwx said:**
> Do you mean this thing?

sudo apt-get install pavucontrol

Yes. I want to know if this will break my sound.

---

### Post by igorzwx on 2009-07-29
That pavucontrol in itself is a harmless thing.
It is just a small application, a kind of GUI control to PulseAudio.
You can do the same with command line.
You have already PulseAudio installed by default.
This is the evil, from my point of view.
But if you are content with your pulse,
you should then install pavucontrol and all other pulse tools.
It would make your life more comfortable.
With one mouse click, you could move sound stream where
you want.

---

### Post by KingNeil on 2009-07-29
Thank you very, very much. This works perfectly. Skype now works fine. Voice recording works fine. It's perfect.

This solution needs to get more publicity. There are probably loads of people who have no idea how to get it working.

---

### Post by igorzwx on 2009-07-29
"There are probably loads of people who have no idea how to get it working."
It is true.
But this would not work on my old boxes.

"Skype now works fine"
Can you describe more exactly?
Do you have noise, delay, latency when you use Skype with pulse?
Which processor do you have?

---

### Post by KingNeil on 2009-07-29
Well, Skype didn't used to work, period. I just changed all the sound devices in Skype to Pulse, and now it works.

I'm not sure about latency. I haven't tried a proper call yet. Just the test call.

My processor is: Intel(R) Core(TM)2 Duo CPU     T8100  @ 2.10GHz

---

### Post by igorzwx on 2009-07-29
Many thanks!
Could you please tell me later the results of further testing of Skype too?

---

### Post by KingNeil on 2009-07-29
Yes, I will when I get the chance. No one's even online on my list at the moment ;)

---

