---
title: "Switching from ATI to Nvidia - How to?"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by aldenhg on 2007-04-27
Hi all,
I'm fed up with the lack of any meaningful hardware support for my 9800 Pro, so I just ordered myself a 7600GS off of newegg. I'm just wondering how I should install the new driver. I was thinking that before I switch the cards I would set the driver in my xorg.conf to 'VESA', then I'll power down, swap the cards and use the Envy script. Is there a better way to do this?

---

### Post by reclusivemonkey on 2007-04-28
You can switch the driver to "nv" before you power off and switch cards. This is the open source nvidia driver which should be fine with your card and is included in the kernel modules. No offence to the write of the envy script, but I wouldn't use it. The nvidia-glx-new deb in the repos is IMHO the best way to install a compatible nvidia driver in Feisty. There has been a lot of work done in Feisty to make sure the nvidia modules match up with the kernel and I've not had a single issue since February (right through Feisty's testing period into release).

---

### Post by aldenhg on 2007-04-28
> **reclusivemonkey said:**
> The nvidia-glx-new deb in the repos is IMHO the best way to install a compatible nvidia driver in Feisty.

Which nvidia-glx should I use with the 7600 GS? I understand that there's the vanilla one, and then something like nvidia-glx-legacy and nvidia-glx-new.
Also, are the flags in the Device section of my xorg.conf file going to have to be re-done? Are those flags for Xorg or do they reference the driver?

---

### Post by reclusivemonkey on 2007-04-29
> **aldenhg said:**
> Which nvidia-glx should I use with the 7600 GS? I understand that there's the vanilla one, and then something like nvidia-glx-legacy and nvidia-glx-new.
Also, are the flags in the Device section of my xorg.conf file going to have to be re-done? Are those flags for Xorg or do they reference the driver?

I have a FX5200 which works fine with nvidia-glx-new so I would definitely go with that one.

---

### Post by aldenhg on 2007-04-29
> **reclusivemonkey said:**
> I have a FX5200 which works fine with nvidia-glx-new so I would definitely go with that one.

Thanks for the info. I'll report back once it arrives.

---

### Post by aldenhg on 2007-05-02
Well, it arrived, I followed all of your directions and now I have a wonderfully performing new card! Thanks a bunch!

---

### Post by reclusivemonkey on 2007-05-03
Excellent, glad it all went smoothly =]

---

