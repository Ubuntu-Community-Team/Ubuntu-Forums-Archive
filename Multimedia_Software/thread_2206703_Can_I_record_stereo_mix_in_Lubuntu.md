---
title: "Can I record stereo mix in Lubuntu?"
date: 2014-02-20
forum: Multimedia Software
---

### Post by eliezer2 on 2014-02-20
HI,
I am on Lubuntu 13.10. I'd like to know if there is a way to do a stereo mix recording(both the sound that I hear from the computer and the michrophone) in Lubuntu. 
I have Pulseaudio and Audacity installed. Is there any other sowtwares that I need to install? 

It would be even better if I could record the sound from the computer on one track and the michrophone on another track so I can edit them separately.
By the way I am new to linux distributions and I like lubuntu very much. I am also new to this forum. I guess this is the right place to post this.
Thanks in advance.

---

### Post by tgalati4 on 2014-02-20
It's possible, but it depends on your sound card.  Bring up your volume control mixer and go into preferences and click all of the switches so that they show up in your panels.  Then move the sliders up and down with a sound source so you can see which channel controls the microphone and which controls the internal PCM channel.  Audacity can record separate channels but you will have to play with the inputs and levels to see if you can get a satisfactory recording.  Normally one would use an external mixer to accomplish this task.

---

### Post by dontunderstand on 2014-02-28
You might want to give a try to Ubuntustudio or similar audio work specific distros.
(AVlinux or me personaly have added [KXstudio]("http://kxstudio.sf.net") [repos]("http://http://kxstudio.sourceforge.net/Repositories") to my Lubuntu 12.04)
Jack audio system is to be run, you can route any output to any input channel (and the other way). 
Frontends for starting jack-audio and routing are different in different distros.
So some learning and getting used to is needed.

It may work if you install the following in your Lubuntu:
jack-audio
qjackctl - gui for starting and stopping jack-audio system
patchage - gui for routing audio channels
ardour - gui recorder

audacity and pulseaudio probably are not compatible with jack-audio in Lubuntu,
(but at least in kxstudio they are all made to work together)

Oh, and i start alsamixer (from terminal) to regulate channel volumes.

---

