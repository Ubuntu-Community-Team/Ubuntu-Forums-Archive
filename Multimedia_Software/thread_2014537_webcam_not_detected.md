---
title: "webcam not detected"
date: 2012-07-02
forum: Multimedia Software
---

### Post by yumna on 2012-07-02
hey my webcam is not being detected in ubuntu .. it started working automatically when i connected it first time, but suddenly it shows a message in skype "previous webcam not detected" what does it means? i've re-installed ubuntu and skype also, but it shows the message that its not detected. :( i've tried alot. but it doesn't work. please help me. what should i do? i am using ubuntu first time.

---

### Post by ajgreeny on 2012-07-02
Does it work with **cheese**, or is it just skype that is the problem?

You may need to install cheese, as I can't remember if it's in the default list of applications.

---

### Post by steve7777777 on 2012-07-11
> **yumna said:**
> hey my webcam is not being detected in ubuntu .. it started working automatically when i connected it first time, but suddenly it shows a message in skype "previous webcam not detected" what does it means? i've re-installed ubuntu and skype also, but it shows the message that its not detected. :( i've tried alot. but it doesn't work. please help me. what should i do? i am using ubuntu first time.

Did you install Cheese? What is the model of webcam?

---

### Post by tumutanzi.com on 2012-07-11
Is the hardware driver correct? or the hardware itself? did you tried it on Windows?

---

### Post by cariboo on 2012-07-11
To make sure your webcam is detected, open a terminal, anid type:

```
lsusb
```

The above command will give you a listing of all the usb devices connected to your system.

I'm using my tablet at the moment, so I can't give you an example.

Once you've made sure the webcam is detected, unplug it, then plug it back in again. In the same terminal, type:

```
dmesg | tail -n10
```

The above command will tell you if the webcam is detected properly, and if the correct drivers is loaded.

---

