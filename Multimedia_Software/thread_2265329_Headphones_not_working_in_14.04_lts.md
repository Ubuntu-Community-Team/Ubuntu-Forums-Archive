---
title: "Headphones not working in 14.04 lts"
date: 2015-02-14
forum: Multimedia Software
---

### Post by Navroze on 2015-02-14
Can someone help me out my headphones are not working on ubunutu 14.04 LTS i have searched tirelessly over the net and could not find anything. The only thing i can upload is the alsa config for my laptop please let me know the fix.
[http://www.alsa-project.org/db/?f=c4ba5a2806b8cd91ee5dbcb5b54c1c59e7adce02](http://www.alsa-project.org/db/?f=c4ba5a2806b8cd91ee5dbcb5b54c1c59e7adce02)

---

### Post by ajgreeny on 2015-02-14
Have you looked in pulseaudio-volume-control (from the Volume icon in the panel click **Sound Settings**) where in the "Output Devices" tab there is usually a separate setting for headphones in the dropdown click-box.

You can also use command **alsamixer** in terminal and check that the levels of outputs are not set too low.
Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

---

### Post by Navroze on 2015-02-14
Done everything but nothing seems to work i have sent the config link above has it got anything to do wiht that

---

### Post by cicada2 on 2015-02-15
Just about everyone here knows more than I. When I brought alsamixer up in the terminal window the first time, I didn't realize I had to use the arrow key -> to tab over to "headphones"... then use the ^ up arrow to increase. Goodluck.

---

### Post by deadflowr on 2015-02-15
Does sound work without the headphones plugged in?
(I'm guessing the laptop has an internal speaker)

What's the laptop(name,brand,etc), also.
Anything you might know about the sound card, too (if you can)

---

### Post by Navroze on 2015-02-15
Yup my sound works perfectly fine with the speakers but once I plug in my headset it does not work plus another thing i have noticed is that when i connect the headphone the driver is not shown in the sound output tab in sound settings. The link below will give u all the details about my laptop sound card,etc
Here it is [http://www.alsa-project.org/db/?f=c4...4c1c59e7adce02]("http://www.alsa-project.org/db/?f=c4ba5a2806b8cd91ee5dbcb5b54c1c59e7adce02")

---

### Post by ajgreeny on 2015-02-15
> **Navroze said:**
> Yup my sound works perfectly fine with the speakers but once I plug in my headset it does not work plus another thing i have noticed is that when i connect the headphone the driver is not shown in the sound output tab in sound settings. The link below will give u all the details about my laptop sound card,etc
Here it is [http://www.alsa-project.org/db/?f=c4...4c1c59e7adce02]("http://www.alsa-project.org/db/?f=c4ba5a2806b8cd91ee5dbcb5b54c1c59e7adce02")
I don't understand your comment about the driver not being shown.  On my system the Sound-Settings output tab has never shown the drivers (I am assuming you mean the software sound drivers).

You call it a headset; is it dual purpose headphone/microphone on the one input plug?  They can cause problems related more to the single plug hardware than any software problem.

---

### Post by Navroze on 2015-02-17
nope its not dual purpose i have a separate plus for the microphone.

---

