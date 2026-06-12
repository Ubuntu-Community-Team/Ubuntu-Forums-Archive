---
title: "webcam mic doesn't work with PulseAudio"
date: 2009-10-04
forum: Multimedia Software
---

### Post by Fibonacci on 2009-10-04
Hello.

I've got a Logitech Quickcam Communicate MP (ID 046d:09a1) with an inbuilt microphone, but I can't get it to work with PulseAudio.
On pavucontrol, I can see the bar under said mic move when I make some noise, so it's not defective. But neither in Skype nor in gnome-sound-properties can I hear what I said into the mic played back. Also, gnome-sound-recorder doesn't even run while pavucontrol is running, instead displaying only the following error message:

Your audio capture settings are invalid. Please correct them with the "Sound Preferences" under the System-Preferences menu.


I found a nearly identical thread on this forum, but the solution there was to disable PulseAudio before running Skype and re-enabling it afterwards. In that case, I guess I should disable PA before running *any* program that captures audio (and thus, shouldn't I just remove it once and for all and go back to ALSA?), but the latest Skype version doesn't work right without PA.
So I'd rather have a solution that doesn't involve removing PulseAudio (or buying another mic).

Thanks in advance.

---

