---
title: "very low sound when using headphones but normal snd through speakers.--followed guide"
date: 2009-03-27
forum: Multimedia Software
---

### Post by Maerwyn on 2009-03-27
Please bear with me, I have tried many things to solve this so I will do my best to explain it all.

The problem is that when I use headphones I can barely hear music, sounds, etc, but when I use speakers only, the volume is normal. 

- First, I checked the sound mixer and verified that nothing was muted and all volume switches were all at an acceptable level. Mic levels are down.

- Next, I upgraded Alsa to the newest version. Once I tried being patient with the installation, everything went just fine with this.

- I checked and my soundcard is being recognized. 

- I specified the soundcard model (ALC883) in: /etc/modprobe.d/alsa-base and saved the changes. Then rebooted.

- I tried all applicable fixes in the Comprehensive Sound Guide, nothing has helped.

-I have rebooted after every change. 

Still no proper sound. If anyone has any suggestions I'd really appreciate it. 

Thanks, 

Melissa

---

### Post by warfacegod on 2009-03-28
Have you tried more than one set of headphones?

I have a pair of headphones with a volume control on the left ear piece. Perhaps yours has a VC somewhere as well, just a thought anyway.

---

### Post by Maerwyn on 2009-03-28
Thanks for the suggestion! I do have volume control on the headphones...but they don't seem to affect the volume at all. Good idea, though. 

-Melissa-

---

### Post by warfacegod on 2009-03-28
"First, I checked the sound mixer and verified that nothing was muted and all volume switches were all at an acceptable level."

What do you consider acceptable? I'm using headphones right now actually and I keep the Amarok (media player) volume at 90% and the Master Volume at 95% and use the analog control on the side of my lap top (much lower than near full of course).

You might simply need to turn one or more of the digital volumes up. Possibly allot, again what do you consider acceptable?

---

### Post by Maerwyn on 2009-03-28
Right now, they're all at 100%. I've tried lowering them, slightly, to see if perhaps having the volumes all the way up was the problem. It doesn't really make any difference. I can lower the volume, but never raise it above a certain point...which is very low.

---

### Post by warfacegod on 2009-03-28
Are you on a laptop or desktop?

If desktop, then are you plugging your phones into the front or back of the tower? If your plugging into the back, make sure your in the right port. Almost every desktop sound card I've ever seen uses green for the normal output. Some use a phones symbol but it's not always clear which symbol goes to which port.

If you're using a laptop, I don't really know what else to tell you, laptops are generally built for headphone use. Being portable and all.

The only other thing I can think of hardware wise is that your sound card might not be strong enough to drive the speakers. EXTREMELY unlikely, but maybe a much smaller set will work sound better

---

### Post by Maerwyn on 2009-03-28
Hey there, 

Thanks for the help...

Well, I'm plugging the headphones into the front of the desktop tower, which is specifically for headphones. 

And you brought up a good point about the hardware...I forgot to mention that I've had Kubuntu installed previously (8.04 and 8.10) and both times I had no trouble with the sound, which is why I find this issue so strange. 

Do you think I need to reinstall again? I really, really hope not.

-M-

---

### Post by warfacegod on 2009-03-28
Try plugging into the back. Have you made any internal changes to the tower recently? Such as an extra hard drive or more RAM. Perhaps the wire leading to the headphone jack from the motherboard got knocked loose.

I rather doubt a reinstall would be needed. I've only had to do one reinstall with ubuntu and that was because of a hard drive with suicidal tendencies. I won't be the one to suggest you try that, though.

You may want to post a new thread in general help. Someone with a more solid grasp of the terminal, than I have, may be able to help you if this is a software issue of some kind.

---

### Post by Maerwyn on 2009-03-28
I plugged the headphones into the back, and I still had the low volume issue. This made me think that it must be a headphone issue, and not my computer, since my speakers worked just fine when plugged into the back. 

I dug around and found an old pair of headphones to try. They work just fine. 

The weird thing is that the original headphones I tried used to work. Ah well, the problem is solved so I will just let it go. 

Thanks for your help!

-M-

---

### Post by warfacegod on 2009-03-28
Certainly.

---

