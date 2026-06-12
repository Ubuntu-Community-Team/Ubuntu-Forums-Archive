---
title: "JACK Output Problem"
date: 2011-01-10
forum: Multimedia Software
---

### Post by Cerapter on 2011-01-10
I'm on Ubuntu 10.04 64bit, and I've got JACK and Pulseaudio both installed, though I don't run them simultaneously. I also have LinuxSampler and Rosegarden, and I have the necessary ALSA drivers.

Pulseaudio can output to my external sound card, but JACK doesn't, even if I tell it to. I've seen its full name (Guitar Rig Mobile IO) and chosen it as the output device under Settings, but to no avail. It still sends the output to the internal (and crappy) sound card.

Do you know what I might be doing wrong?

---

### Post by cchhrriiss121212 on 2011-01-10
Open jack control from the menu then click on setup. Select the device you want to use under the interface option, leave input and output device as default.

---

### Post by Cerapter on 2011-01-11
At first it didn't work. But then I tried *truly* disconnecting Pulseaudio (I hadn't done it right before), and I think that worked.

So, solved. :D

By the way, do you know of a good way to kill off JACK? When I run other applications, it tends to freeze rock solid, killall doesn't work, and I have to log off to use it again.

---

### Post by cchhrriiss121212 on 2011-01-11
I use htop to kill things if they go wrong and it hasn't let me down so far. If jack is consistently freezing up you should try to troubleshoot why it is happening.
Which apps cause it to freeze?

---

### Post by Cerapter on 2011-02-18
I'm not sure. It's been well-behaved lately.

Solution to my original problem: setting the external sound card as Interface, and not Output. I don't have to deactivate Pulseaudio - the newer versions of Pulseaudio automatically deactivate when JACK comes along, so far as I understand.

---

