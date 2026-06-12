---
title: "If I jailbreak my I-pod touch 32gb, will my computer recognize it/use it???!"
date: 2010-05-18
forum: Multimedia Software
---

### Post by hozo on 2010-05-18
Hey guys, I'm an ubuntu noob and hating it. 
I have an I-pod touch 32gb (not sure what gen, how do I find that out?!) 
I'm sure you've heard of this before, computer doesn't recognize it as a multimedia device, it thinks its a camera - thus I cannot open files or do anything with it!
I want to add music from my computer and I am very annoyed. 
If I 'jailbreak' my ipod, will it allow me to use it on my computer?!
Also, what risks am I taking by jailbreaking it? 
THANKK YOOUUU!!!!

---

### Post by jbrown96 on 2010-05-18
Nope no need to. In 10.04, the device can be used in rhythmbox (installed by default), gtkpod, and amarok (kind of buggy). 
You need to install a couple of programs ```
sudo apt-get install libimobiledevice0 libimobiledevice-utils
```

check out the project's webiste. They have a nice video [http://www.libimobiledevice.org/](http://www.libimobiledevice.org/)

---

### Post by hozo on 2010-05-19
Thanks, but when I copied that code into the terminal it didn't work:
"E: Couldn't find package libimobiledevice0"
What do I do!!? I'm getting impatient with Ubuntu!!!

---

### Post by hozo on 2010-05-19
ahhh just looked I have Ubuntu 7.10 !!!!

---

### Post by manzuk on 2010-05-19
It's time to upgrade!
There's no problem with jailbreaking and rhythmbox sync. Actually I have a 3GS Iphone jailbroken (firmware 3.1.2 with Spirit) and music sync works perfectly!

---

### Post by hozo on 2010-05-23
How do I upgrade??? Well is it possible to do it without jailbreaking anyway?

---

### Post by RobOrr on 2010-05-23
Yeah, it works with both a normal ipod touch and a jailbroken ipod touch (tested it with my 32Gb one, although I'm using the 3.1.0 firmware so not entirely sure if it'll work with 3.1.2)

just make sure that you have the above libraries installed, and rhythmbox can alter the music on there.

---

### Post by hozo on 2010-05-25
okay thanks, but what above libraries?!

---

### Post by hozo on 2010-06-14
Look guys, I don't think you understand. I have NO IDEA how ubuntu works. Can some one pretty please tell me step by step what I need to do (how download these "libraries" and where) or whatever it is that I need to do to make it work. THANK YOU!

---

### Post by Jake007g on 2010-06-14
> **hozo said:**
> Look guys, I don't think you understand. I have NO IDEA how ubuntu works. Can some one pretty please tell me step by step what I need to do (how download these "libraries" and where) or whatever it is that I need to do to make it work. THANK YOU!

First off, you want to update to 10.04. Press ALT+F2 and type:

> update-manager

Click 'Upgrade to the new Ubuntu release 10.04". Go along with the update process, it may take a while.

Once you are running Lucid Lynx (10.04), download the required libraries, by opening up a terminal (Found in applications > accessories) and typing this command:

> sudo apt-get install libimobiledevice0 libimobiledevice-utils

Now, simply open up Rhythmbox and plug in your iPod. Your iPod should be recognised on the left hand side, simple drag your albums from your music library onto your iPod :-)

Hope I helped.

---

