---
title: "Nvidia Drivers will not take affect! Please help!!"
date: 2007-10-26
forum: Multimedia &amp; Video
---

### Post by jgullo29 on 2007-10-26
Hello All,

I have installed (enabled) the nvidia-glx-new driver but it simply will not take effect. It says it is enabled etc. I have disabled them and renabled etc multiple times (rebooting as it request) and still they wont take effect. 

Can someone help me? Where am I going wrong?

I use the Nvidia GeForce 6200 256mb


Thank you all so much! (in advance :))

---

### Post by jgullo29 on 2007-10-26
I also just installed Ubuntu for the first time, if that helps at all.



Thanks,

Joey

---

### Post by sanddgroper on 2007-10-26
What version of ubuntu.?
Do you have onboard video as well as the 6200.?
What does your xorg.conf file say in /etc/X11 under
Section "Device" should say "nvidia" for driver.

Cheers
Sandy

---

### Post by jgullo29 on 2007-10-26
Hello Sandy,

Thank you for your Reply!

To answer your questions:

-I have version 7.10

-I do have an onboard as well as the 6200

-Not sure what the xconf says(i'm at work at the moment), how do I check that? (Sorry i am very new!)

-For the device, I think thats where I had trouble, no matter what I selected it kept reverting back to this long one, gosh I can't even remember. I tried just "nvidia" but it wouldn't stick. Any ideas?

Thank you so much!

Joey

---

### Post by taurus on 2007-10-26
Applications -> Accessories -> Terminal
```
cat /etc/X11/xorg.conf
```

---

### Post by jgullo29 on 2007-10-26
Great, thank you! I will check this as soon as I can.



Thanks!

Joey

---

### Post by PmDematagoda on 2007-10-26
Hey there Joey.

As a fellow Nvidia 6200 user, I'm quite surprised that you have problems with it. But I can guarantee you that the VGA card will work. I will help whenever I can.

---

### Post by jgullo29 on 2007-10-26
Wow thank you very much. Yes, actually, a little background, I installed 7.10 on a 40 gig IDE that ended up failing and rebooting the system for no reason. I was able to get the drivers working literally right out of the box. Because of the HD problem i had to use my other one. Since then, i'm having nothing but troubles. No idea why. I really need that 6200 because of some video editing and gaming programs I want to run. But this is how i have always figured out software/hardware issues. Fail and fail and fail and fail until I learn :)


Thanks,

Joey

---

