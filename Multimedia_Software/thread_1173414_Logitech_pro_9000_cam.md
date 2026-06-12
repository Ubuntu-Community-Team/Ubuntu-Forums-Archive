---
title: "Logitech pro 9000 cam"
date: 2009-05-29
forum: Multimedia Software
---

### Post by Hunter Thompson on 2009-05-29
I just bought a Logitech PRO 9000 and i'm running ubuntu 9.04 which i though would have drivers for this device installed. But the device is not auto detected and in looking around the net for solutions i find that there are at least 700,000 different opinions as to how to proceed. Ubuntu 9.04 can't play a video cam without all this workaround is real frustrating. Anyone have a solid solution for this??

---

### Post by hansdown on 2009-05-29
Hi Hunter Thompson.

I have the same camera, and it works with cheese.

Click system> administration> synaptic package manager.

Search for cheese, camerama, skype.

Install these, and it should work.

---

### Post by Hunter Thompson on 2009-05-29
Hello Hansdown, Thanx cheese works but no audio and can't find camerma on web or in synaptic. I'm assuming you are referring to the skype on the web

Hunter

---

### Post by hansdown on 2009-05-29
Sorry, it's spelled camorama. Skype is in synaptic.

---

### Post by Hunter Thompson on 2009-05-29
[hansdown]("http://ubuntuforums.org/member.php?u=608207")      Are you kidding? my spelling rejects most spell checkers, 

Best Regards

Hunter

---

### Post by hansdown on 2009-05-30
No, seriously.

The search function in synaptic is not very intuitive.If the spelling

or punctuation is not exact, it will return a failed search.

Hope you get it working.

---

### Post by BennieBlount on 2009-06-05
I just bought a Logitech QuickCam Communicate Deluxe (S 7500). I installed Cheese, Camorama, and Skype. With Cheese I can record and take photos. I don't know what Cameroma is supposed to do but when I try to open it I get a message that says it can't connect to the camera. 

Skype works but it does not recognize or connect to the webcam. Any suggestions on how to use the webcam with Skype?

Thanks,
Bennie

---

### Post by Greydog56 on 2009-06-08
I've only been using Ubuntu for two months so am hesitant to offer solution. Still, I will offer what made the Quickcam 9000 Pro work for me. I just followed advice from other users.

The following worked for me in Ubuntu 32 or 64 bit though image quality is just average. Also, the mic is  strong but has a mild case of sounding like talking in an empty barrel.
Here is my install process and settings it took to get the 9000 pro working in skype:
    loaded cheese, camorama and skype 2.0.0.72
    Sound pref = capture Logitech Quickcam Pro 9000 USB Audio (ALSA)
    mixer = HDA INtel (ALSA mixer) "the onboard sound for my Asus P5Q-E MB"
    volume control = Quickcam Pro 9000 (ALSA mixer) "mike unmute and audio recording on"
    skype = Quickcam Pro 9000 (hw:Q9000,0)
    out and ringing = pulse
    skype set to auto adjust levels
    note: the mic test in preference>sound doesn't work but the audio tests ok in skype and cheese.

Camorama also tells me it can't connect, but if I unistall it, my video stops working. 

Camera image is much better in Windows Vista 32 bit, audio is some better also. I dual boot Vista and Ubuntu 64 so am glad to just get it working in both.

Anyone have additional suggestions to improve my video or audio quality? Thanks

---

