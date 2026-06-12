---
title: "Webcam: long initialization time causing issues"
date: 2015-06-11
forum: Multimedia Software
---

### Post by mckeanke on 2015-06-11
Hi.

I've been using Xubuntu 15.04 happily for awhile now, but one thing has bothered me since I started with 14.04: I use my webcam (Microsoft LifeCam HD5001) for my microphone, and whenever I open an application, Skype for instance, which requests access to the microphone, it will work eventually, but after a huuuuuge delay, like 5 full seconds. This isn't so bad when starting a Skype call, since it happens at the beginning of the conversation then works just fine. However, I started playing Guns of Icarus Online, and whenever I attempt to use the voice chat buttons, it invokes that 5-second initialization process of the webcam. Since the game isn't expecting a large delay here, the whole interface hangs until it's done. After letting go of the voice key, the webcam turns off.

Anyway, I'm just looking for a solution or work-around. Is there some way I can speed up the initialization process of the webcam, and if not, how do I make it so it stays on all the time?

---

### Post by mckeanke on 2015-06-27
Um, well, in case anyone's wondering, you can open the PulseAudio volume control panel and it will maintain an open connection to the webcam, thus keeping it powered up and avoiding the issue.

---

