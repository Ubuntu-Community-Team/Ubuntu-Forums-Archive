---
title: "[SOLVED] dv2710us ubuntu Ver. 8.10 video driver"
date: 2008-12-28
forum: Multimedia Software
---

### Post by Relief on 2008-12-28
So I have just installed ubuntu Ver. 8.10 and I seem unable to find video card support. The only solution I found for my model of laptop is using envey, but after installing I receive an error when attempting to use it saying that my OS is not supported.

This is my first attempt at going away from windows and would love to make ubuntu work, but without vid card support I cannot use this system. Anyone have any options for me?

- Relief

---

### Post by gettinoriginal on 2008-12-28
In terminal copy and past these, one at a time:

```
 sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list -O /etc/apt/sources.list.d/medibuntu.list 
```

```
 wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update 
```

There are proprietary drivers and non proprietary drivers, this allows your driver to be accepted.

---

### Post by Relief on 2008-12-28
Sorry if I am a bit dense here, I did as you suggested, but I am at a loss as to what to do next. 

- Relief

---

### Post by gettinoriginal on 2008-12-28
System > Admin > Hardware Drivers  let it search for proper driver, then activate it.  Then:
System > Pref > Appearance > Visual Effects  they should be set to Extra or Custom.

---

### Post by Relief on 2008-12-28
When attempting to use the hardware drivers tool and install the NVIDIA driver i get this error "SystemError: Failed to lock /var/cache/apt/archives/lock"... 

I am at a loss here, also, sorry if I seem dense, I just have never used anything outside of windows (yeah I know, windows...)

- Relief

---

### Post by gettinoriginal on 2008-12-28
Make sure you do not have terminal or synaptic open, usually when you get that message is when more than one instance of apt running.  When you have closed them, try the hardware driver search again.  Don't worry, you will get the hang of it.  :P

---

### Post by Relief on 2008-12-28
You were correct, and it seems my video issue is solved. Thanks a lot. 

Though, on the topic of drivers is there anything else I need to attend to, chipset drivers, etc?

- Relief

---

### Post by gettinoriginal on 2008-12-28
Usually, Ubuntu will install out of the box, but if anything gives you problems, then you need a work around, but as the saying goes, if it ain't broke, don't fix it.  LOL  But do not be afraid to come to the forums with any problem, we were all new here once :P  Please go to tools and mark this as solved.  And although it is not required, just since you are new here, if you want, there is a gold medal at the right hand bottom corner of a post, it is for thanking someone who helps you.  Enjoy Ubuntu, and good luck

---

