---
title: "nVidia 32mb card problem"
date: 2008-03-25
forum: Multimedia &amp; Video
---

### Post by notoriousmagik on 2008-03-25
Hello guys,

Please forgive me for my noobness, I hope this is posted in the correct section.

My names Matt and last night installed Ubuntu for the first time on the advice of being a great starting point for beginners.

I tried installing it with my graphics card in but wouldn't work,
after previous experience with windows installations I knew this was my first port of call. So I removed it and just used the onboard graphics with which Ubuntu installed and worked fine.

Earlier today I decided to install the card....

I installed the card and started it up, Ubuntu recognised the card and auto installed the drivers and then asked to restart.

After restarting it would go through the regular start-up procedures and then hang on a blank screen.

I then attempted to restart it without the card in which made no difference.

After that I ran the Safe Mode option which hung at the command line:

root@default-desktop:~#

I've attached photo's for illustration, please forgive the v.poor quality but cant do a screen shot! :( 

Could someone please help me with this, I would be very grateful, 
if u need anyone information please just ask!

Thanks in advance Matt

---

### Post by unoodles on 2008-03-25
At the command prompt with the new video card in, try typing: gdm

---

### Post by notoriousmagik on 2008-03-25
Thank you for the swift reply,

I presume i need to enter this on the safe mode screen?

Could you please explain what this command does and what the problem is?
I would just like to learn what has happened

Thank you again

---

### Post by unoodles on 2008-03-25
I am unsure exactly of what your problem is.

gdm stands for Gnome Display Manager. It should open you login screen.

---

### Post by Tomatz on 2008-03-25
Hi Matt have some popcorn :popcorn:

At that nasty black screen with the command prompt type this:

**sudo dpkg-reconfigure -phigh xserver-xorg**

Its self explanitory from there (reboot after) :)

(if that don't work try it omitting the **-phigh**)

---

### Post by notoriousmagik on 2008-03-25
Thanks *munch *munch

Im torn now lol

I'll let you know whats happens

---

### Post by Tomatz on 2008-03-25
I've gotta go now but if that don't work do this at the command prompt:

**sudo apt-get install nvidia-glx-legacy**

Then:

**sudo nvidia-glx-config enable**


I'll check back later to see how you got on :)

---

### Post by notoriousmagik on 2008-03-25
Ok, the xconfig command worked but totally confused me tbh, I really dont know what im doing!

I tried the gdm command which thankfully brought me back to the mainscreen with the card back out.

This is my limit of knowledge as what to do next

Thanks for the great help by the way!

---

### Post by Tomatz on 2008-03-25
> **Tomatz said:**
> 

**sudo apt-get install nvidia-glx-legacy**

Then:

**sudo nvidia-glx-config enable**



Those commands should get your old nvidia card working they are the nvidia legacy (old) drivers. The 2 commands will install and configure the nvidia legacy drivers. You can just do it in a terminal :)

If it borks then just take the card out and:

**sudo dpkg-reconfigure -phigh xserver-xorg**

---

### Post by notoriousmagik on 2008-03-25
Thanks man, i'll give it a try tomorrow, i've had enough frustration for one day, guess its all part of the learning curve. Here's a nice Youtube video as reward Enjoy! [http://youtube.com/watch?v=h4iyksLeo7w]("http://youtube.com/watch?v=h4iyksLeo7w")

---

### Post by Tomatz on 2008-03-26
> **notoriousmagik said:**
> Thanks man, i'll give it a try tomorrow, i've had enough frustration for one day, guess its all part of the learning curve. Here's a nice Youtube video as reward Enjoy! [http://youtube.com/watch?v=h4iyksLeo7w]("http://youtube.com/watch?v=h4iyksLeo7w")


Lmao!

:lolflag:

---

