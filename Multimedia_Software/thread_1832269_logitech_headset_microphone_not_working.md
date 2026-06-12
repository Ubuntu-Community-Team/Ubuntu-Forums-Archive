---
title: "logitech headset microphone not working"
date: 2011-08-24
forum: Multimedia Software
---

### Post by L2U2K2E on 2011-08-24
hi.

I am using a MSI GX630 Laptop with Xubuntu 11.04 installed. I am attempting to use a logitech H230 headset ([here]("http://www.logitech.com/en-us/webcam-communications/internet-headsets-phones/devices/8609")) which works fine on other computers running windows but is now not working in  Xubuntu. 

when plugged in, the headphone work, but skype does not record any sound from the microphone.

I am happy to provide any additional information I can, hopefully someone can help me.

I am studying abroad in Sweden and need my microphone working to speak  with my family in the states. I also have an internal microphone which is does not seem to be working ([thread here]("http://ubuntuforums.org/showthread.php?p=11183369#post11183369"))

thank you!

---

### Post by L2U2K2E on 2011-08-25
bump

---

### Post by thewolfman on 2011-08-26
You need to check and see if you are using "pulse audio" and if you are, go into Skype settings and make sure that Skype does not have control over the sound manager.

Install "paman" and then re-boot your PC, start Skype and go into the audio settings and take out the tick in the "allow Skype to control sound levels" box, then open volume sound preferences and look at "input". Make sure that the correct device is selected.

Hope this helps you.

Regards thewolfman:P

---

### Post by L2U2K2E on 2011-08-26
it works now! I don't think I did everything you said, but unchecking allow skype to control your sound helped for sure! I didn't change anything in paman, but I did go back into the normal Xfce Alsa mixer and under the "options" tab I changed one of the inputs to "Mic." I know I had tried this previously with no success, but now it works!

thank you!

---

