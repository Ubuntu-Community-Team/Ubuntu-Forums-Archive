---
title: "Very Low Volume : Sennheiser HD 201 &amp; Ubuntu 12.04"
date: 2012-05-26
forum: Multimedia Software
---

### Post by satya10123 on 2012-05-26
Hi guys,

I have been facing this problem since I started using Ubuntu. My Sennheiser HD 201 headphone works fine with windows 7 and even with my Galaxy smartphone. But when I use it in Ubuntu, I can hardly hear any sound. The volume is very low. I tried using VLC, but the volume starts to burst while increasing above 150% and even at that level i could hardly listen to anything on my headphone.

But again, if the headphone works fine on windows and my phone then it should work fine in ubuntu as well.

Please help!

---

### Post by The Cog on 2012-05-26
I have no idea if this is any help to you, but I had a problem with headphone volume yesterday. In sound settings, switching from headphone to speaker fixed it. I think that the laptop I was using somehow told the software that I was on headphones, but conected the headphones to the logical speaker output - the sound software was disabling the "speaker" output because it thought I was connected to the "headphone" output.

---

### Post by gordintoronto on 2012-05-26
Tell us what you see in each of the tabs in "Sound". Tell us about your computer, is it a laptop, what brand and model?

---

### Post by satya10123 on 2012-05-27
> **gordintoronto said:**
> Tell us what you see in each of the tabs in "Sound". Tell us about your computer, is it a laptop, what brand and model?

Yes, I have a laptop. Lenovo 3000 Y500 Series. The headphone is connected via audio output plug(not usb). In the sound tab, it shows that the headphone is recognized(as in screenshot).

---

### Post by gordintoronto on 2012-05-27
Sorry, I don't have a suggestion.

---

### Post by satya10123 on 2012-05-28
Anyone, please ??

---

### Post by satya10123 on 2012-05-29
I think I found out the problem but I am unable to solve it.

I am posting a screenshot of ALSA Mixer which has my Headphone volume to none. but when I try to increase it nothing happens it stays at 0. So I think this is the problem. But can anyone tell how to resolve it??

---

### Post by satya10123 on 2012-05-29
Ok.. finally the problem is solved.

Got the solution here >> [http://ubuntuforums.org/showthread.php?t=1536057](http://ubuntuforums.org/showthread.php?t=1536057)

---

### Post by gordintoronto on 2012-05-29
Raising the other volumes?

---

### Post by satya10123 on 2012-05-30
Yes, I increase all the others volumes to their maximum value and this worked. Sound level improved drastically. The **headphone** value still being stuck at 00 level though.

---

