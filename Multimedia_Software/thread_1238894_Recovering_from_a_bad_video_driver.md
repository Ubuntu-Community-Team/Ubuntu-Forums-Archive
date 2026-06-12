---
title: "Recovering from a bad video driver"
date: 2009-08-12
forum: Multimedia Software
---

### Post by josephmo on 2009-08-12
Having spent several hours perfecting my installation (Desktop 9.04, 64 bit), I opened up the Hardware Device applications, and noticed that the proprietary device driver was not enabled (ATI/AMD). So, I foolishly clicked on enable it. When it was done, Ubuntu told me it wanted to reboot.

When I logged in, my screen turned into a bunch of colored dots. I tried hitting Esc while booting, and there was an option to fix the video problems, but that did not work. How do I go recover?

---

### Post by Isaacgallegos on 2009-08-12
I also want to know this!!!

Also this, which is sort of related: 
[http://ubuntuforums.org/showthread.php?t=1236956](http://ubuntuforums.org/showthread.php?t=1236956)

---

### Post by Isaacgallegos on 2009-08-13
Any update josephmo?

---

### Post by markbuntu on 2009-08-13
What card do you have?

---

### Post by efgevh on 2009-08-13
the way to recover is to boot recovery mode, drop to root shell, then
sudo apt-get remove xorg-driver-fglrx
then 
sudo rm /etc/X11/xorg.conf
reboot

---

### Post by josephmo on 2009-08-15
I am now trying out Fedora. All the suggestions regarding editing xorg.conf did not work (and I restored the original one). I did not try deleting it.

---

### Post by josephmo on 2009-08-15
One more thing: my card is ATI 4870x2, so don't believe what the instructions say: it is not going to work on Ubuntu Linux. I have not tried it on Fedora, but I am not inclined to try. Too bad, because I cannot take advantage of the 3D special desktop effects (and they do come in handy at times).

---

### Post by markbuntu on 2009-08-17
To get the 4870x2 card to work you need to do

aticonfig --adapters=all --initial

You need to do this to initialize the driver with multiple gpus but that may have changed recently

---

