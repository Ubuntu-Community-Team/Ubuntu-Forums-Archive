---
title: "What does XGL do? Do I have it by default in 7.10?"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by cudds on 2007-11-29
Hello guys,

I have my vostro 1700 with it's Nvidia official driver running 7.10 without a problem but some of the compiz effects are a lil choppy.
I was reading about xgl and was wondering if this will be turned on by default in 7.10 or if there is a way I can find out if it's running?

Thanks.

---

### Post by ThinkDave on 2007-11-29
Install xserver-xgl to get it working (sudo apt-get install xserver-xgl). Just check the running processes to see if xgl is there System->Administration->System Monitor->Processes.
You don't need scripts to load it anymore it loads automatically. To get rid of it just remove the package.

Edit: doesnt nvidia have good AIGLX support... XGL probably wont help you unless your running an ATI card.

---

### Post by cudds on 2007-11-29
> **ThinkDave said:**
> Install xserver-xgl to get it working (sudo apt-get install xserver-xgl). Just check the running processes to see if xgl is there System->Administration->System Monitor->Processes.
You don't need scripts to load it anymore it loads automatically. To get rid of it just remove the package.

Thanks Dave - I'll give it a go tonight.

Just a thought that some of the sticky tutorials are out of date and do point to running scripts and what not - I guess they've been updated further on the thread but it's hella confusing for us rookies.

---

### Post by cudds on 2007-11-30
> **ThinkDave said:**
> Install xserver-xgl to get it working (sudo apt-get install xserver-xgl). Just check the running processes to see if xgl is there System->Administration->System Monitor->Processes.
You don't need scripts to load it anymore it loads automatically. To get rid of it just remove the package.

Edit: doesnt nvidia have good AIGLX support... XGL probably wont help you unless your running an ATI card.

Just noticed your edit about nvidia support for AIGLX - so is it not worth going with XGL or is there another route?

---

### Post by gamma on 2007-12-01
I'd personally recommend XGL if you're going to be using compositing. AIGLX essentially took a lot of XGL's code and brought it into Xserver (if I remember correctly). Both work well, but I find I get way better performance on my Nvidia Geforce FX 5200Go notebook card with XGL. Also there are several rendering bugs that have been addressed in XGL/glitz that haven't found their way to AIGLX (solid black windows at times).

---

