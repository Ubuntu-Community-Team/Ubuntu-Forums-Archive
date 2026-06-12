---
title: "Nvidia Driver Problem"
date: 2008-10-21
forum: Multimedia Software
---

### Post by Looshin on 2008-10-21
I recently decided to give Ubuntu a second try and after a fresh installation I decided to check my Systems/Admin/Hardware Drivers only to find that there's nothing there. I have a Nvidia 9600GT so I decided to install the new nvidia driver found under Add/Remove however there are still no drivers listed under Hardware Drivers. I had many driver problems the last time I installed Ubuntu as well, anyone know if my video is perhaps unsupported or have any suggestions how to fix this problem? Thanks in advance.

---

### Post by Looshin on 2008-10-24
Anyone?

---

### Post by doas777 on 2008-10-24
make sure you have all your repositories enabled in System -> Administration -> Software Sources.

then open a terminal and enter:
```

sudo apt-get update

```

then reboot and see if you have a restricted driver available yet.

I think you may be able to install the nvidia driver with 
```

 sudo apt-get install nvidia-glx-new nvidia-settings

```

but I can't gaurentee that that will work for you. might be worth a try however.

good luck,
franklin

---

### Post by eternalnewbee on 2008-10-24
I read somewhere in the Forums that Ubuntu until now doesn't have support for the newest cards, but that this will probably be solved in 8.10 ( and I'm just assuming that you've got version 8.04 installed... )

---

### Post by Looshin on 2008-10-24
> **eternalnewbee said:**
> I read somewhere in the Forums that Ubuntu until now doesn't have support for the newest cards, but that this will probably be solved in 8.10 ( and I'm just assuming that you've got version 8.04 installed... )

Thanks this is pretty much what I was expecting, I tried both of doas777's suggestions without success and given that I can hear my video card fan being extremely loud (happened with my Windows partition too before I had a video driver installed) I assumed that the driver wasn't working. Guess I'll just hold out for 8.10.

---

### Post by eternalnewbee on 2008-10-24
Won't be long now...

---

### Post by doas777 on 2008-10-24
> **Looshin said:**
> Thanks this is pretty much what I was expecting, I tried both of doas777's suggestions without success and given that I can hear my video card fan being extremely loud (happened with my Windows partition too before I had a video driver installed) I assumed that the driver wasn't working. Guess I'll just hold out for 8.10.

I'm sorry it didn't work out for you. you could try envyng for installing the proprietary driver from nvidia.com. might be worth a try. you can find a tutorial [here]("http://albertomilone.com/envyngfaq.html#A").

good luck,
frank

---

### Post by Looshin on 2008-10-24
> **doas777 said:**
> I'm sorry it didn't work out for you. you could try envyng for installing the proprietary driver from nvidia.com. might be worth a try. you can find a tutorial [here]("http://albertomilone.com/envyngfaq.html#A").

good luck,
frank

Thanks I tried that before and it just messed things up even worse, I wasn't able to increase my resolution beyond 640x480, I think I'll just wait as it'll only be another week or so.

---

