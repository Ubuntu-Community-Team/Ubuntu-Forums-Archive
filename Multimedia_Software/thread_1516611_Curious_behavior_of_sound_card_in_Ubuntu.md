---
title: "Curious behavior of sound card in Ubuntu"
date: 2010-06-24
forum: Multimedia Software
---

### Post by sujitvp on 2010-06-24
Hello,

I have dual booting desktop which has an onboard audio device (Intel Corporation N10/ICH 7 Family High Definition Audio). 

My desktop has two headphone outlets, one in the front and one in the back. I typically keep my speakers connected to the back while the headphones connected to the front jack.

In windows, I see each of these jacks as separate audio destinations (Realtek Audio driver what gets loaded), and I can send audio out specifically to either of these (but not to both)!

In linux, I only see one audio destination and the audio comes from both front and back jacks equally. I wonder why this constraint exists.

Now, ideally I would like the option to turn on one, the other or both out jacks. However, I will settle for just the ability to turn off one of the jacks at a time. Is there any way to get the ability to send audio either to the front or back jack alone?

Thanks.

---

### Post by solar george on 2010-06-24
You could try installing the [pavucontrol]("apt://pavucontrol") package which gives you a more advanced/complex volume control program and see if it can see the outputs separately.

---

