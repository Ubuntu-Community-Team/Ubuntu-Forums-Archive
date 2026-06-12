---
title: "Mic (microphone) not working"
date: 2010-03-05
forum: Multimedia Software
---

### Post by jawadahmed on 2010-03-05
I have stereo headset and i can clearly hear sound but the microphone doesnt work. Cant chat or record using it.

My computer is intel pentium 4 ht. 
Ubuntu desktop 9.10. 
There is no extra sound card.
Can any one help?
Also my camera doesnt work, its a usb pc camera. I will make another thread for camera also.

---

### Post by mohansathish on 2010-03-05
Please run the following in terminal and display the output coming for them.
1) lspci 
2) lsusb

So that we can identify the issue clearly

---

### Post by soldar79 on 2010-03-05
When you're trying to get sound work on linux you've to know ALL details about your sound card, including manufacturer and chipset.

Then, you can google the solution out. I've had multiples issues about sound on linux, especially with onboard sound. 

Sometimes the only solution was to wait 'till next version of ALSA, so, don't worry if there's no actual solution. 

Anyway, we need lspci lsusb and dmesg outputs to help you.

---

### Post by lyall on 2010-03-05
how you checked to see if the Mic is muted?

System > Preferences > Sound

Click on the input tab and see if it is Muted is checked

good luck and have fun learning

---

