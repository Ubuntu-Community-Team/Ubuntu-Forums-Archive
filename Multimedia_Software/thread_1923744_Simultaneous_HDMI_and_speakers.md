---
title: "Simultaneous HDMI and speakers"
date: 2012-02-11
forum: Multimedia Software
---

### Post by sssuizaaa on 2012-02-11
Hello all,

I have an Asus laptop running 11.10 with the following sound card:
 **** List of PLAYBACK Hardware Devices ****  
 card 0: Intel [HDA Intel], device 0: ALC269VB Analog [ALC269VB Analog]  
 Subdevices: 1/1  
 Subdevice #0: subdevice #0  
 card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]  
 Subdevices: 1/1  
 Subdevice #0: subdevice #0  
 
I had no sound on the HDMI so I went to sound settings, selected the hardware tab and changed the profile to Digital Stereo (HDMI) Output and I got sound over the HDMI connection. However the sound in the laptop speakers disappeared. I looked for the solution and I installed the pulseaudio settings, went to simultaneous output tab and then selected the "add virtual output device for simultaneous output on all local sound cards".
By doing so, a new sound output device appeared in the output tab of the sound settings called simultaneous output to internal audio digital stereo (HDMI). If I select this virtual output device, nothing changes, I still have sound over HDMI but that's it. I've seen that I would probably have to have more output devices but I do not know how to do this. It all seems to be controlled by the profile I select in the hardware tab. When I change the profile the output device changes and it is only one. I can add the virtual “simultaneous” one but that does not make anything change.
 Any help with this would be appreciated.
 Regards,
 sssuizaaa

---

### Post by sssuizaaa on 2012-02-13
Nobody?

sssuizaaa

---

### Post by lindsayward on 2012-02-13
Hi. I have my card outputting everything over HDMI except I have set VLC to output through the analogue out. 
Do you want a duplicate of the audio over both outputs at once - or separate things at once?
Have you tried connecting speakers to your connection rather than the internal speakers (I guess that wouldn't make any difference)?

---

### Post by sssuizaaa on 2012-02-13
Hi lindsayward, thank you for your reply,

Actually my goal was to duplicate the audio over both outputs at but being able to select applications to use one output or the other would be great as well. Right now I cannot do (or I do not know how to do) any of these options.

As I said, no matter which profile I select I can only choose one output. If I select the HDMI profile then it is the HDMI output, if I select the analog profile, then what is available is the analog output, even if I have the "add virtual output device..." as indicated in this link: [http://askubuntu.com/questions/57319/analog-and-digital-audio-output-at-the-same-time](http://askubuntu.com/questions/57319/analog-and-digital-audio-output-at-the-same-time). nothing changes.

Find below one of the images of that link. You can see three outputs, the analog, the HDMI and the simultaneous. I'm only able to see one (analog or HDMI) and the simultaneous one (in case I have added it using pulse audio preferences.

Regards,

sssuizaaa

---

