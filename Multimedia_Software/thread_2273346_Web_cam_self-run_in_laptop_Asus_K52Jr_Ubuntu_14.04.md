---
title: "Web cam self-run in laptop Asus K52Jr Ubuntu 14.04"
date: 2015-04-12
forum: Multimedia Software
---

### Post by artur15 on 2015-04-12
Hi, every one!
My built-in web cam in notebook self invoke when my system start, run any soft use web cam, plug/unplug USB devices (mouse or etc.). I need on/off web cam using some utilities like 'cheese' that turn off indicator that light when camera turn on. It's not big problem and I even don't worry about spying (to whom I need :) ) but its distracting me. I'm looking information on web but can't find any. 
Please, help me!

---

### Post by TheFu on 2015-04-12
Let me try to say it back to you.

Your webcam turns on at boot up.  If you run webcam software, it does what you like.  There's a light near the webcam and you'd like to turn that off when it isn't actually recording.

Is that all true?
You can blacklist the webcam driver, but that may not be workable if you ever need to use it. Then you'd have to load the kernel module before any use.

BTW, I've been using 
* simplescreenrecorder - screen catching
* guvcview - webcam recording

There are a few other solutions in these forums. Did you see those by searching?

Whenever someone/blog/article/book says to use **sudo gedit**, please don't. Use **sudoedit** instead. It is safer for a number of reasons.

---

### Post by artur15 on 2015-04-13
Yes it's all true. 

Sorry for my bad English. 

I have been adding to blacklist the webcam driver, but it's really not comfortable because I often use skype conversations. And I was trying plug external USB webcam and it's also was in blacklist.

 I think it's problem with this series laptops - ASUS. Some of them often have such kind of problems. I had also upside dawn picture but I can fix it.

And sorry what you mean you have been using those programs. They may help fix my problem? 
When my webcam turn on itself I turn off it by program "Cheese" or some like this that can turn on webcam (skype etc.) 

I have been trying searching solutions but can't find any. :(

And **sudoedit** it is'n same like **sudo nano**?

---

### Post by Bucky Ball on 2015-04-13
I'm not using Unity so not sure where you'd find it, but have you looked in 'Sessions & Startup' to see what's set to boot at start up? Maybe there is some program set to launch at boot that's starting the camera when you boot Ubuntu ... :-k

Just a thought ... ;)

---

### Post by artur15 on 2015-04-13
> **Bucky Ball said:**
> I'm not using Unity so not sure where you'd find it, but have you looked in 'Sessions & Startup' to see what's set to boot at start up? Maybe there is some program set to launch at boot that's starting the camera when you boot Ubuntu ... :-k

Just a thought ... ;)

I looked but I have no idea what kind of those program can turn it. In addition it also turn on when I plug in /unplug external webcam. Launch google Chrome. I notice that it turn on if I have opened tab that use some media - music, video (facebook, youtube etc.)
[ATTACH=CONFIG]261252[/ATTACH][ATTACH=CONFIG]261253[/ATTACH]

---

### Post by TheFu on 2015-04-13
> **artur15 said:**
> 
And **sudoedit** it is'n same like **sudo nano**?

No, it isn't. There are subtle differences which make using sudoedit much safer. You can check out the manpage for a good description. It uses temporary files and honors the EDITOR env variable (a few other env vars are checked too).

While sudo nano isn't really an issue, not everyone likes/uses nano. sudo gedit has proven to cause issues for some people, whereas sudoedit (even with gedit set as the EDITOR) will NOT cause those issues because of the way that sudoedit works.  Of course, this is not the core issue for this thread.

---

### Post by Bucky Ball on 2015-04-13
In the startup applications screenshots, what is:

> Onboard
no description

?

---

### Post by artur15 on 2015-04-13
> **Bucky Ball said:**
> In the startup applications screenshots, what is:



?

I don't know. I made settings that I can see also system applications. I guess it may be system soft. But I try remove it it's not help.

---

