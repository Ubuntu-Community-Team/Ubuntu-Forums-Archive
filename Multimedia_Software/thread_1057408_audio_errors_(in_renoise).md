---
title: "audio errors (in renoise)"
date: 2009-02-01
forum: Multimedia Software
---

### Post by iseeclouds on 2009-02-01
I use Ubuntu 8.10. just installed full linux-version of renoise 2.0. when i open it i get these kind of errors:

“failed to create a RealTime priority thread for ALSA......Highly recommended to use RealTime priority audio threads with ALSA and JACK....”

“failed to open the jack client. Please make sure that the Jack server is running!”
“jack failed to open. Trying to open ALSA instead...”
“failed to open the ALSA device 'hw:0,0 (ALC663 Analog)' (Device or resource busy).”

also, my keyboard doesn't function inside renoise.
i read some renoise tutorials and stuff but i really can't figure it out.

i really don't know anything about linux so could anyone tell me what i should doe (and how)? thanks in advance!

---

### Post by markbuntu on 2009-02-01
The rt kernel is broken in 8.10 for one but your bggest problem is that jack is not running and alsa is busy. Go here and read the section " UbuntuStudio and jack" and follow the links to get jack set up properly. Once you do that you should be able to get jack running and then start renoise. To connect your keyboard you need to have renoise using jack and use patchage to connect it.


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by iseeclouds on 2009-02-02
thanks for the help. i installed JACK. renoise can run now (altough it still ask for rt kernel when i start it), but i can't save anything as wav or i can't listen music while renoise is running.
i've been told that for renoise it's best to just get Ubuntu studio 8.04. it's the easiest way, is this right?
i now have a dual boot of both vista and ubuntu 8.10 on my computer. how can replace 8.10 with studio 8.04?

---

