---
title: "No audacity playback devices"
date: 2008-07-05
forum: Multimedia Software
---

### Post by peejaroni on 2008-07-05
When I run audacity to edit a file, and then play the file, it won't play, and an error message shows up that says: Error while opening sound device. Please check the output device settings and the project sample rate.
When I look at the audio i/o screen there are no playback devices listed...

---

### Post by peejaroni on 2008-07-05
I reinstalled audacity and it still didn't work, and when I tried downloading and then using the aoss audacity command I got:
audacity: pcm_pulse.c:480: pulse_prepare: Assertion `pcm->stream' failed.
Aborted

---

### Post by peejaroni on 2008-07-06
Also, when I shut everything down and then start up just audacity the playback devices appear, is there a way for them to always show up?

---

### Post by lanchongzi on 2008-07-07
i have a similar problem
however
i found a solution on the web like this:
open the Volume control(top panel - the little speaker thing - at least in my case )
click: edit - preferences
scroll down to "Mix" and "Mix Mono" check both boxes, then close it
now in the Volume control there should be a field entitled" Switches" click on it
and check "Mix"
close it and open audacity
in adacity go to edit-prefrences- audio I/O and choose ALSA default for both recording and playback


well, it worked fine yesterday
BUT today for some reason i can not choose playback Alsa default anymore
recording is fine

suxx

---

### Post by peejaroni on 2008-07-07
I don't have mix or mix mono.

---

### Post by eArquilla on 2008-07-07
I think my problem is similar to yours.

Audacity just does not detect jack at all, works fine without it however. When jack is running, audacity will not play files, giving your same error message. It doesn't list freebob or jack as a playback option (it did on my 32 bit install of opengeu, now i have 64bit ubuntustudio)

sorry if these are two completely unrelated issues.

---

### Post by peejaroni on 2008-07-08
I think yours is different, I don't use jack.

---

### Post by coleyman on 2008-07-24
I recorded in on "Front Mic Input" into Audacity and it recorded fine. I try to play it back and the meters show it working, but I get no sound. I get sound from other sources such as movies (even off of my digital camera) and CDs and MP3s. Just nothing from Audacity. I also don't have mix or mono on my volume drop down preferences. The only thing in "Switches" is my headphones.
Jeff

---

### Post by david.rahrer on 2008-08-05
> **peejaroni said:**
> I reinstalled audacity and it still didn't work, and when I tried downloading and then using the aoss audacity command I got:
audacity: pcm_pulse.c:480: pulse_prepare: Assertion `pcm->stream' failed.
Aborted

I'm having the same issue exactly.  I thought it might be related to [this bug]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3470") but that seems to have been patched last December.  I'm using the lastest libasound2-plugins (Intreped backport I think) 1.0.16, but it doesn't help.  Not much on Google either.  Assuming that 480 number refers to a line number in pcm.pulse.c, I searched for just the last half of the error and still didn't get much.

Anyone more experienced available to see what this might be?  The bug above gives a good explanation of what causes the error itself.  I'm still unable to get Audaciy (or anything) to record from capture on Hardy.  All other sound functions great.

Thanks.

---

### Post by Patricrawley on 2008-08-14
bump, im having the same problem and none of these solutions seem to be a permanent fix or available for me.

---

### Post by bergersau on 2008-08-14
Try this:
Close all running audio applications.
Then start audacity with the command
**pasuspender audacity**

And set the sound devices in audacity to OSS.

I think you might be encountering the Audacity+Pulse Audio bug thats now well documented.

---

### Post by eye208 on 2008-08-14
[How to fix all PulseAudio-related issues in 2 minutes](http://ubuntuforums.org/showthread.php?t=885437)

Oh, and don't use OSS. It's backwards. ALSA is the sound system of Linux.

---

### Post by markbuntu on 2008-08-14
The official Pulse audio faq reccomends the use of pasuspender to get audacity to work. Of course, this halts the pulseaudio daemon.  Audacity is written to use portaudio so it does not work all that well with oss, alsa or pulse, or jack for that matter. 

Wen I try to use it with jack, it crashes and then shows up in the jack connections box. The plugins that audacity uses for alsa and oss are also buggy and crash prone. I have never got it to work successfully the way I want.

Use ardour instead, it is far better.

---

### Post by keinea on 2008-08-15
I had a similar problem that had me going for a few hours;  I had just installed Audacity and was trying to solve some recording issues, when at some point I lost audio for all my applications.  

Thinking that the Audacity installation had something to do with the loss of audio I got side tracked into believing the audio configuration became corrupted.  When in fact the loss of audio was due to unintentionally changing a setting on the gnome-volume-control panel.  

See the attached screenshot - fixNoAudio.jpg


The System --> Preferences --> Sound utility was used to test the audio.    

The command line > gnome-volume-control   setting was where the unintentional change was made.




Once I solved the "no audio all applications" issue, I finally solved my playback//recording issues with Audacity.

First I had to change the default Audacity install preferences:

Audio I/O &#8594;
    Playback Device = OSS: /dev/dsp         
    Recording Device = ALSA: HDA Intel: ALC268 Analog (hw:0,2)

and I unchecked the "Playthrough - Play other tracks while recording new one"


I also had to add "Recording - Capture 1 (vs Capture)" in the preferences for the gnome-volume-control. This enabled the controls for my laptops front input mic jack, which allowed me to increase the input volume and mute it.


See the attached screenshot - Audacity_configWorks.jpg



This just goes to show, that sometimes trying to fix one issue can open up and create and additional problem.

Hope this is information is helpful to someone out there.


Sincerely,
keinea
:cool:


Toshiba Satellite A305-S6825
ubuntu-mobile 2.6.24-19-generic Hardy Heron

---

