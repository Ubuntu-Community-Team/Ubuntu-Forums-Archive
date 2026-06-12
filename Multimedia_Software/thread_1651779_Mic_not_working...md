---
title: "Mic not working.."
date: 2010-12-23
forum: Multimedia Software
---

### Post by untappedpilot2 on 2010-12-23
I have a Fujitsu Lifebook A6220 running Ubuntu 10.04 Upon first installing my system the built-in mic and web cam worked with Empathy. After pushing all available updates to my laptop the microphone no longer works. I have tried some troubleshooting available in the forums (ie. adjusting alsamixer settings; updating with linux-backports install pkg; installed aumix as well) nothing seems to be working. Please let me know what further information is needed to troubleshoot my issue. --Thanks

---

### Post by untappedpilot2 on 2010-12-25
bump.. anything on this?

---

### Post by Syed75 on 2010-12-25
System<preferences<Sound

GO to the input and make sure you checked off the right microphone.

---

### Post by untappedpilot2 on 2010-12-26
what do you mean checked off the right mic?

---

### Post by Peanuts123 on 2010-12-26
Do as he says and you have to turn your mic up all the way past 100%. Thats what mines was doing and after I did this mines worked fine. Try it and let me know what happened.

---

### Post by ExemplarUbuntu on 2010-12-26
I have similar problems and it is all down to pulseaudio. The only way I can get the sound system to function properly is to make sure pulseadio is not working.

killall pulseaudio
ps -A | grep puls

it will start again after a few seconds so I have disable mine by editing /etc/pulse/daemon.conf and replacing a = with a - (dash)

I have spent weeks trying to find solutions to choppy audio and inability to get the mic working in Skype and this is the only thing that has worked.

---

### Post by Syed75 on 2010-12-26
> **untappedpilot2 said:**
> what do you mean checked off the right mic?

Chose the right microphone and turn it up to 100%.

I had the same problem and it turned out that I needed to turn my mic on. :p

---

### Post by untappedpilot2 on 2010-12-26
So in the 'Input' tab I have 3 different mics available. Microphone 1, Microphone 2 and Line-In. I have it turned all the way up and I have even adjusted the settings in 'alsamixer' to be turned up all the way. Mic 1 is the only one that seems to work at all and during my test captures the only playback is static. Any other ideas? Also do you have the same card as I do? Here is the output of ```
derek@ubuntu:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
```

---

