---
title: "Need Linux Distro with Working Audio Drivers"
date: 2015-07-06
forum: Multimedia Software
---

### Post by Wiking on 2015-07-06
Hi,

Is there a Linux distro that has audio drivers that actually work?
I really don't have the time to try and fix the audio driver every time it fails, which from my experience is inevitable.

I just need something simple that won't fail and actually works.

thanks

---

### Post by Kale_Freemon on 2015-07-06
Audio drivers work fine on Ubuntu in my experience. 

May be helpful to know what hardware you're running on.

---

### Post by ajgreeny on 2015-07-06
I am not sure, but it looks as if you are asking for help here, so I have moved the thread to Multimedia forum from the Chat section which is not for requests for help, but as the name suggests, just for chat.

As Kale asks, what is your hardware and what have you tried so far to get audio working?
Has audio ever worked for you and if so how did you get it working?

---

### Post by Wiking on 2015-07-06
Hi, thanks for replies.

I'm not going to waste any more of my time trouble shooting this problem for the hundredth time.

I just need recommendations on linux distros with working audio drivers, preferably one that doesn't use pulseaudio. 

thanks.

---

### Post by MartyBuntu on 2015-07-06
Let us know what problems you had in the past with your audio setup and also what hardware is in your computer, to better give you a recommendation

---

### Post by Dertuny on 2015-07-06
I had problems with my intel hda realtek alc880 (lg s1 express dual netbook) on all the newest distros with kernels up from 3.16, i tried the newest 4.1 and the problem is the same, no sound to the speakers. The only way i found to get it work all is install or use kernels 3.16 or before.
This is a possible solution with my experience.
Edit: try lubuntu 14.04

---

### Post by VMC on 2015-07-06
Here is some info on the "realtek alc880". Read the first fix:
[http://askubuntu.com/questions/462655/lubuntu-14-04-no-soundcard-detected-hda-intel-realtek-alc880](http://askubuntu.com/questions/462655/lubuntu-14-04-no-soundcard-detected-hda-intel-realtek-alc880)

---

### Post by Dertuny on 2015-07-07
Thanks for the link. I found that before.
This is the fix all the people say to resolve problems with audio in linux, but nothing new (good or bad) happens adding options to modprobe. I think the only way for me is play with hda jack retask, but i don't understand the app.

---

