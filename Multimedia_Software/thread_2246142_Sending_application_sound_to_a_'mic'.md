---
title: "Sending application sound to a 'mic'"
date: 2014-09-28
forum: Multimedia Software
---

### Post by krafczyk-matthew on 2014-09-28
I'm wondering if the following is possible:

I have an application which is making sound. At the same time I'm having a skype chat with someone, and I'd like them to hear the sound from my application.

Would it be possible to duplicate this application's sound and send it into the system mic which skype is using?

Since I'm using ubuntu, I assume this would involve pulseaudio somehow, but if it can be accomplished some other way that's fine too.

---

### Post by deadflowr on 2014-09-28
Lucky for you this was posted a week ago
[http://ubuntuforums.org/showthread.php?t=2245162&p=13126632#post13126632](http://ubuntuforums.org/showthread.php?t=2245162&p=13126632#post13126632)
hope that helps

---

### Post by krafczyk-matthew on 2014-09-29
Excellent! That *does *accomplish the basic task. In a pinch it will work.

However, is it possible to create some kind of virtual microphone in addition to my hardware microphones such that I can send in audio streams of my selection to that microphone, and then use the above described method to select that virtual microphone for input to another program?

---

### Post by CraigPid on 2014-10-01
It is quite possible to route audio from anywhere to anywhere using JACK. I don't use Skype but I imagine that it doesn't have JACK support but there are ways of bridging ALSA and Pulse Audio applications into JACK.

[http://jackaudio.org/](http://jackaudio.org/)

---

