---
title: "Microsoft LifeCam HD-5001 Drivers"
date: 2015-06-07
forum: Multimedia Software
---

### Post by 4ntonio.p3r3ira on 2015-06-07
Hi
I'm having trouble with my camera. It sends video trough Skype but no sound. I can't seem to find drivers for anything but Microsoft (as usual with their products) is there any way for me to find drivers for it? Should I go for WineHQ?

---

### Post by Bucky Ball on 2015-06-07
*Thread moved to **Multimedia**.*

Welcome. Might have more luck here. Feel free to ask any questions about anything you don't understand. ;)

> **4ntonio.p3r3ira said:**
> Should I go for WineHQ?

No. Are you sure you haven't got the audio stream from the camera disabled in Pulse Audio Volume Control?

Play something from the camera so you are seeing the vision on the computer, open PAVControl and hit the 'Playback' tab. Can you see the sound stream from the device? Go to the 'Input' tab and check which device is set there. Is it set to the camera input? Is it available? How do you have the camera plugged into the computer? HDMI so you know there should be audio over HDMI audible?

---

### Post by 4ntonio.p3r3ira on 2015-06-07
Thanks for the help! Input its now set for the camera. The connection is USB not HDMI. I don't have an app to test if the camera is working I have to see if my sis logs in on Skype to see if she ears me now. LOL =)

---

### Post by Bucky Ball on 2015-06-08
Make a test call. You will find 'Echo/Sound Test Service' in your contacts list in Skype. Make as many test calls as you like with that and experiment with your audio settings. You know you're getting vision, all you need is to check for sound and you can do it like that. ;)

Make sure you are tweaking the audio with Pulse Audio Volume Control, not directly with the ALSA mixer (although we may need to dig there if you still get nothing).

---

