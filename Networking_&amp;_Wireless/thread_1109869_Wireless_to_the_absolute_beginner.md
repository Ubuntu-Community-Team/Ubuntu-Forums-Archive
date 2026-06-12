---
title: "Wireless to the absolute beginner"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by leweston on 2009-03-29
Hi all,
I've just started with ubuntu as I've heard it to be a good os. However, I know absolutely nothing about it, and am completely unable to even start connecting to the internet. I use wireless orange, which works great with my xp. What do I have to do? Please help me as I don't want to give up on linux right at the start.

Thanks.

---

### Post by chili555 on 2009-03-29
The first step is to learn a little bit about your wireless device. Let's ask the computer! Please go to Applications -> Accessories -> Terminal and type:```
sudo lshw -C network
```*lshw *means, essentially, 'list my hardware' and *-C network* means 'only for my network devices.'

You will get data about both your ethernet and wireless devices. Post the information here and we'll help you proceed.

---

