---
title: "Eliminating Recording Noise: will a sound card help?"
date: 2013-02-21
forum: Multimedia Software
---

### Post by tvm9742 on 2013-02-21
Hello, I'm having a problem recording audio in 12.04 64 bit. I'm trying to use my MXL 990 through a Mackie 1202 Micro mixer into my 990fxa-UD3's alc889 audio chip, the results: [soundtest.wav]("https://www.dropbox.com/s/cv4nleekmyfbxot/soundtest.wav")
I've tried lots of gain and boost adjustments with no improvement. The noise is definitely being added after the mixer, when I listen through the mixer's headphone jack it is clean and nice,  

so my question is, is there an easy fix for this that I am missing? and if not, will a sound card fix this?

 I'm fairly sure I know the answer, but I don't want to spend the money on a sound card only to be disappointed if there is no change, my thought is that this is happening because Gigabyte's drivers aren't Linux compatible,(i have tried the Linux drivers on the Realtek site, no change)In windows the only problem with the recording is power supply noise, but that isnt the problem here. When in windows I can hear the power supply from around the room beeping up a storm, but in Ubuntu it is quiet.

Thanks for your help

---

### Post by ajgreeny on 2013-02-21
I have no idea about using a sound card instead of the way you do it at the moment, but I think it is worth trying the following which should not take much time, and is totally free of cost.

I am sure you would prefer if it were possible to record with no "noise" in the background, and I have to admit that your sample is incredibly noisy, but have you considered cleaning up the recording with audacity.

When you make a recording, either as you do now or with audacity, make sure there are a few seconds at the start with no sound into the mic, just ambient sound.  Then without stopping recording simply continue to make your recording of whatever.

When you finish recording, use audacity **Effects -> Noise removal** and firstly get a sample of the noise from the first few seconds of the recorded time by selecting just those seconds of the file. Secondly, actually remove that noise profile from the rest of the file by selecting the whole file and using **Effects -> Noise removal** again.  It can make a remarkable difference, though as I say, your sample is incredibly noisy, so it may not do a total job.

---

### Post by tvm9742 on 2013-02-21
I have tried cleaning up the audio clips with audacity and it does work to a degree, but like you said not a total job. It really only cleans up the spaces between the words, the words themselves still sound static-y even though it is less than originally. also I am using this setup as a communications mic so say making a Skype call still sounds awful. Thanks for your suggestion though.

---

