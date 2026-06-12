---
title: "Headphones not working"
date: 2016-02-07
forum: Multimedia Software
---

### Post by boombam123 on 2016-02-07
I am dual booting on a my custom built machine with Windows 10 and Ubuntu. Audio works fine on windows 10. 

The audio will work if I output it through my GPU and to my monitor but my headphone jacks seem to do nothing. Does anyone have suggestions? 

I have tried to uninstall/reinstall/upgrade alsa and it doesn't work. I don't see a headphones option in my alsa mixer. 

The ONLY way I've been able to get sound in my headphones is using pavucontrol to change the profile and then plugging my headphones into my speakers jack (at which point the sound is very muffled/crackled)

here is the alsa infomration. 

[http://www.alsa-project.org/db/?f=b116869f7494d26968e44607aec538271e03ad29](http://www.alsa-project.org/db/?f=b116869f7494d26968e44607aec538271e03ad29)

Thanks

---

### Post by dave157 on 2016-02-15
I use Kubuntu 14.04 and I have no issues with the earphone jack hmm. Did you check the volume control or open the sound configuration in Ubuntu and see what audio device is default? if you can snap a pic of your audio settings post it here.

---

### Post by Bucky Ball on 2016-02-15
Welcome. Install Pulse Audio Volume control if you haven't got it already. Open it. Run some audio. You will see the audio stream in 'Playback'. Next to 'Port' you can choose a different port (device) to output to. Experiment (you may see a headphone option or 'analogue' something in there. 

You can also tweak with the 'Output' tab to makes sure that is also set to the correct port. Make sure you have an audio 'stream' happening (play a long song to give time to tweak).

---

