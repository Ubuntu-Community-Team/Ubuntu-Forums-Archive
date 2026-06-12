---
title: "Blank screen after GRUB loader"
date: 2008-05-21
forum: Multimedia Software
---

### Post by TR13 on 2008-05-21
Hi, I just finished installing Ubuntu and after i choose the O/S in the grub loader, i get an error from my monitor "H. Frequency and V. Frequency out of range". I have a 19" monitor and a XFX 8600GT.  Please Help ..

---

### Post by overdrank on 2008-05-21
> **TR13 said:**
> Hi, I just finished installing Ubuntu and after i choose the O/S in the grub loader, i get an error from my monitor "H. Frequency and V. Frequency out of range". I have a 19" monitor and a XFX 8600GT.  Please Help ..

Hi and please do not make multiple threads on the same subject
see you other thread
[http://ubuntuforums.org/showthread.php?p=5012390#post5012390](http://ubuntuforums.org/showthread.php?p=5012390#post5012390)

---

### Post by TR13 on 2008-05-21
Hi, Sorry about that.. Thanks anyways.. it worked. One more thing.. I have started Ubuntu and i wanted to change my screen resolution to 1400x900.. but the option is not available.. how do i change it..?

---

### Post by overdrank on 2008-05-21
> **TR13 said:**
> Hi, Sorry about that.. Thanks anyways.. it worked. One more thing.. I have started Ubuntu and i wanted to change my screen resolution to 1400x900.. but the option is not available.. how do i change it..?

Ok have you install the drivers for the nvidia card? You may look at the restricted drivers located under system, administration. Then you will need to install nvidia-settings via synaptic manager located under system, administration. Then you can use the nvidia settings adjust your resolution. using the command ```
gksu nvidia-settings
```

---

### Post by TR13 on 2008-05-21
Thanks, Will install the driver and see what happens..

---

### Post by annaa on 2009-03-02
Overdrank - many thanks for posting the answer! (I got the same error doing something stupid, and your solution fixed it.)
Your time here is appreciated!!

---

