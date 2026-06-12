---
title: "install ubuntu 10.10 on life studio"
date: 2010-09-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jklopez on 2010-09-17
i want to know if it's possible to install ubuntu 10.10 on my 1tb life studio external hard drive cuz i dual booted my laptop installing ubuntu via usb using universal-USB-installer but theres not enough space left for files and movies so i want to install ubuntu to my life studio external hard drive so i did the same thing put the iso via the usb installer on my external hd but when i boot my computer via usb it just boots windows normaly i'm not sure if i'm doing something wrong or if i just can't install it on the life studio external hd it's factory format is fat 32 but life studio is'nt exacly a normal external hard drive....
                   any info is great even if i'm out of luck...i just want to know if i can or not and if i can...HOW

---

### Post by cariboo on 2010-09-17
You have to install grub to the mbr of your external drive, and then set the bios to boot from the external drive. That way you get the best of both worlds. Your system will boot normally when the external drive isn't connected, and when it is connected you have the choice of booting Windows or Ubuntu.

---

### Post by jklopez on 2010-09-17
cool...all i need to know now is how to install grub to mrb ,what grub? and what is mrb?  thnx :D

---

### Post by metalf8801 on 2010-09-17
> **jklopez said:**
> cool...all i need to know now is how to install grub to mrb ,what grub? and what is mrb?  thnx :D

for grub look here [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

mbr stands for master boot record its the software that is used to boot windows. more info look here [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

Your going to need to make sure you do not remove grub from your internal hard drive. Other wises your going to need to connect the external every time you need to boot your computer even if your not going to be using the external for anything else. One way to do this is to remove your internal hard drive before installing Ubuntu on your external. When you install Ubuntu on the external drive it will also install grub. 

Are you sure you want to use Ubuntu 10.10 before its stable? 

I hope this helps 
Dan

---

### Post by jklopez on 2010-09-17
thnx man your i life saver....and no i ment ubuntu 10.04 ,10.10 isnt stable yet but it looks very promising ,youtube has some good demonstration vid's ,if i run into any problems i'll post it here...thnx again!!!

---

