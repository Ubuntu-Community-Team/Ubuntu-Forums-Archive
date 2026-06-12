---
title: "Video Settings, and NVIDIA drivers.."
date: 2016-05-17
forum: Multimedia Software
---

### Post by Robert_Cline on 2016-05-17
Greetings.


 I hope that this is the proper place to ask this:


 I upgraded my Acer Veriton computer to Ubuntu 16.04, this machine is used as a HTPC. It has a NVIDIA ION GT-218 graphics card.


 I initially tried to use the open-source drivers that were installed automatically, and they are pretty good, but when I play a DVD or ISO in Videos/Totem, there is a visible jerkiness. Annoying.


 Then I selected a NVIDIA video driver, 340.96, from the proprietary drivers list, it works great, no more choppiness.


 The problem with this is that the 'auto' resolution setting in the NVIDIA X-Server is 1920x1080, and my TV is 1680x1050. I can reset to 1680x1050, and everything is fine, but I cannot save the new setting, it resets to 1920x1080 whenever I reboot. 


I have tried opening/configuring the dialog as root, and saving that way, but no success. 


Then I saved the file xorg.config manually, with the 1680x1050 resolution, but it does not display that setting upon reboot, it goes back to 1920x1080. Even though it says 1680x1050.


 So, my question is this: is there a way to tweak my open-source video driver so that the playback on a DVD is smooth, or am I stuck with Nvidia driver that won't remember it's new setting? Or, is there another option?


 Thank you.

---

### Post by CaptSilver on 2016-05-19
How are you changing the resolution? Are you using system settings->displays?

---

### Post by Robert_Cline on 2016-05-19
No, I am using the NIVIDIA X-Server..

---

### Post by Robert_Cline on 2016-05-19
I may have solved it, when you reminded me of the video settings dialog, I went to that and selected the option to sync with the detected monitor, rebooted, and got the correct resolution!

I am making a backup now so that I don't screw it up...

---

### Post by Robert_Cline on 2016-05-19
That did it.. thank you so much, that was making me crazy.

---

