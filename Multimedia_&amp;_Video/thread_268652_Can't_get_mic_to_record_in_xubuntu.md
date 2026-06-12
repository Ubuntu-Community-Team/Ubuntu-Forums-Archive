---
title: "Can't get mic to record in xubuntu"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by flipop on 2006-09-30
Hello!

I have been using xubuntu for two weeks and i can't get the microphone to record.

(I think it would be good to give a short introduction to what i've tryed to do). I have been trying to get skype to work and now I'm using the Beta version and I can call the 'Skype test call'-service. Now I can hear the voice but it don't record anything.

I first thought that it was a skype problem but now I have tryed to record using arecord but it don't record anything. I can hear my own voice in the headset when the mic isn't muted. I have selected to capture from mic in alsamixer.

I can't find any good "Howto configure alsa in xubuntu-guide". 

Any ideas?


Filip

---

### Post by ryu kun on 2006-10-05
exactly the same problem. microphone outputs but won't record. apparently there is no answer.

---

### Post by cakmin on 2006-10-08
> **ryu kun said:**
> exactly the same problem. microphone outputs but won't record. apparently there is no answer.

Oh noooo...seriously, no one can help with this problem?

I have exactly the same problem, at first I can still hear my voice although it was very very small, but now I completely hear nothing when I do a test call with Skype. When I tried to configure my Ekiga it gave an error, saying impossible to open the selected audio device (VIA 82C686A/B rev 50)...and blah..blah.

---

### Post by Hairyred on 2006-10-12
And another. Mic and line in do work, but no record. I have tried sound recorder, Audacity, Ardour, nothing. Asus mobo M2N-sli deluxe onboard AD1988b sound chip.

---

### Post by dapf on 2006-10-24
Exactly the same problem here, I've just changed to Dapper and my system is up to date. Isn't there still no answer?

Intel Chipset

---

### Post by shal on 2006-10-24
Hello!

Had the same problems. I read on somewhere this forum the solution:

# sudo alsactl names
# sudo alsactl store
# sudo reboot

This will create alsa config file in /etc. And will enable mic input (front). My soundcard is HDA Intel (sigmatel). Before this worked only rear sound output. Now works front sound input (mic) and rear output.

Yep, after reboot run alsamixer and enable/unmute all recording to 100%.

---

### Post by rogerdrange on 2006-11-10
NOOO!

I did like you said:

# sudo alsactl names
# sudo alsactl store
# sudo reboot

And now my soundcard doesn't work! No sound works anymore. I think ubuntu can't find my soundcard no more. 

Help, anyone?? :)

EDIT: In Totem, the sound works properly. But only there.

---

### Post by th2 on 2006-11-17
Tried that method, but still can't record with my mic at all.  I have a Sound Blaster Audigy SE and am running Xubuntu (the latest I believe).

---

### Post by nado on 2006-12-11
I had trouble using my mic in Skype and had to install Kmix to get it working.  I prefer to avoid adding uneccessary applications, especially KDE applications, so I looked for another alternative that didn't require me to install anything additional. This worked for me, I hope this helps you too.

> to get your mic working, if skype is not recording from it, try the following:

- switch to the alsamixer view 'Capture' with TAB or start it with **alsamixer -V capture -c CARDNUM**
- make sure you have 'Mic' and 'Capture' sliders marked selected as CAPTUR ... to do this hit space  I just entered the text marked in bold into a terminal and pushed the mic levels up.  I found this at the Skype forums, for the rest of the post with some screenshots look [here]("http://forum.skype.com/index.php?showtopic=66544")

---

### Post by brt on 2007-02-23
> **shal said:**
> 
# sudo alsactl names
# sudo alsactl store
# sudo reboot



YO ! I also have nvidia 430 MCP and this did the trick :)  

great! thanks!

---

