---
title: "sound problem"
date: 2010-08-19
forum: Multimedia Software
---

### Post by irakla7777777 on 2010-08-19
hello all
i had sound problem problem on ubuntu 10.4 , then i remove everything alsa and pulseaudio and install again. and it did not work
then i compile new kernel to 2.6.35.2 and can hear sound but problem is , when play some music or audio file , cannot play other sound . for example flash on youtube... i either have twinkle voip client installed error occur when play some music :

Critical: Cannot open ALSA driver for PCM playback: Device or resource busy

what can i do ?

---

### Post by irakla7777777 on 2010-08-19
anybody knows alsa configuration ...

---

### Post by hudsonl on 2010-08-19
> **irakla7777777 said:**
> anybody knows alsa configuration ...


I had some conflicts with ALSA and PulseAudio ... 


 So **I removed the PulseAudio Sound Server and rebooted and it works now.**

Go into Synaptic Package Manager ...
  Select "**pulseaudio**"  (PulseAudio sound server)  - **Mark for Complete Removal**
     - Select OK for all the dependencies
     - Select Apply

  - Reboot after removal is completed.

If it doesn't work ... re-install using  Synaptic Package Manager

You might also try disabling the sound on the BIOS.  If you  have a sound card and integrated sound on your motherboard ... multiple  "cards" seemed to make it "flaky"

---

### Post by jabeavers on 2010-08-19
I'm no expert, but I'm pretty sure that only one program can open a sound device at a time. So, if one program is playing sound, another cannot do it at the same time. That is where the sound server comes in. Pulse opens the sound device, and the programs that want to play sound connect to pulse that mixes the sounds and sends it to the device.

Perhaps one of your programs is setup to use alsa instead of pulse, then when another program tries to open the sound device, it can't because it is busy (as the error indicates). See if you can set default sound device to pulseaudio, or make sure the program playing sound is setup to use pulseaudio. Again, no expert, so I can't tell you how to do this.

John

---

### Post by irakla7777777 on 2010-08-20
yes you are right
but problem is that i dont know how to set pulseaudio as default
I tried to set pulseaudio as default from meny manual pages...but it not work
may i do something wrong..
can anybody tell me how to set pulseaudio as default 
? 
?
?

---

### Post by simosx on 2010-08-20
I think you might have messed up your system regarding audio.

There are people that advise to remove PulseAudio; do not listen to them.

You mention that at some point you could only play audio through one program at a time; this is the effect of the removal of PulseAudio.

On the positive side you managed to recompile the Linux kernel which is an amazing feat for new users.

What I recommend is, 
1. if you can, do reinstall Ubuntu 10.04 so that you have a clean starting point.
2. follow [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) in order to figure out where the problem is. The page has advice on how to collect debugging information, which helps to help you. Post the link once you collect the info.
3. in the majority of the cases, the problem is with Alsa; you either have a too new sound card, or the sound card is not autodetected (needs some help).

---

### Post by hudsonl on 2010-08-20
> **simosx said:**
> 

There are people that advise to remove PulseAudio; do not listen to them.




I can ONLY tell you what I did and it worked ... in troubleshooting sometimes the best thing to do eliminate variables to narrow down your focus.

Two points to consider:

1. It's broke now ... if you remove PulseAudio ... reboot and it's still broke ... then big deal.
2. If removing PulseAudio doesn't work ... re-install it and your back to where you were.

[http://www.linuxtoday.com/news_story.php3?ltsn=2010-04-03-001-35-MM-HL-UB](http://www.linuxtoday.com/news_story.php3?ltsn=2010-04-03-001-35-MM-HL-UB)

---

### Post by simosx on 2010-08-20
Anyone can suggest articles to linuxtoday.com; it does not add credibility to the content of the submission.

It is possible to try to play audio and record using Alsa only without having to remove PulseAudio. You can use 'aplay' and 'arecord' which can help you test if Alsa is operational. Then, you can figure out if there is some setting with PulseAudio.

The majority of the audio problems are related to the Alsa support; Ubuntu comes with an oldish Alsa version and most probably the latest supports your hardware. In this case, you can search for AlsaUpgrade in this forum and use it to install either the latest stable Alsa (1.0.23, from April 2010) or the 'snapshot' version which is the very latest version of Alsa.

In several cases, the model of the sound card is not autodetected so you may have to give a hint to Alsa on which card you have. Ideally, you then inform the Alsa developers to add your soundcard details so that future versions autodetect your hardware. Many people ommit this step, so people end up coming here for help.

Canonical hired an audio developer a few months ago so that any hints as to which model of soundcard you have can be selected from user-space, so you do not have to recompile the kernel/alsa. I hope this brings results to the next version.

---

### Post by irakla7777777 on 2010-08-23
correct is  that if some program use alsa other program cannot use it because alsa is busy. to prevent this problem you must set pulseaudio as default ... then all program connect to pulseaudio then pulseaudio to alsa...


evrything works ok...


many thanks to all and sorry for bad english :)

---

