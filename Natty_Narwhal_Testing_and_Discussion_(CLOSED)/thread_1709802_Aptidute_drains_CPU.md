---
title: "Aptidute drains CPU"
date: 2011-03-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Jonny87 on 2011-03-18
Can any one explain why aptitude seems to be running so much and draining precious CPU? I have attached a screen shot of terminal running top. I've tried killing it but can't seem to stop it. If its relevant I should mentioned that I've changed from standard Ubuntu 11.04 to now running Kubuntu 11.04, by installing the Kubuntu packages.

---

### Post by cariboo on 2011-03-18
Do you have any idea why so many instances of aptitude are running? I just ran:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

I only had one instance running during the whole process, with a quick jump to 20% cpu usage just at the end of the update command, the rest of the time it was bouncing between 4%-7%.

---

### Post by Jonny87 on 2011-03-19
> **cariboo907 said:**
> Do you have any idea why so many instances of aptitude are running? I just ran:

```
sudo aptitude update && sudo aptitude safe-upgrade
```I only had one instance running during the whole process, with a quick jump to 20% cpu usage just at the end of the update command, the rest of the time it was bouncing between 4%-7%.

I have no idea why there are so many going? As I said I have tried killing them but it won't work. I've also tried to stop it from looking for updates and restarted the system (in case that by some chance had something to with it) still no luck. My cpu is constantly sitting at any where from 80 - 100% and I'm confident that having multiple aptitude running is the major cause.

---

### Post by Jonny87 on 2011-03-19
Does anyone have any clue how I can solve this issue with my cpu running so high??

---

### Post by cariboo on 2011-03-19
You already know why your cpu usage is high, it's because you are running multiple instances of aptitude.

Does it still run multiple instances of aptitude after a restart?

What command do you use when using aptitude?

---

### Post by Jonny87 on 2011-03-19
> **cariboo907 said:**
> You already know why your cpu usage is high, it's because you are running multiple instances of aptitude.

Does it still run multiple instances of aptitude after a restart?

What command do you use when using aptitude?

Yea I do know that its aptitude but I want to get it solved.

Yea it still happens after restart. I've tried everything I can think of. Running updates, reinstalling the aptitude package, changing settings and restarting. I'm about at the point of doing a full reinstall. I don't want to as that means having to reinstall all the other apps as well. and the main reason I like to use the development versions is because I tend to learn more about Linux by finding out how to fix issues.

I don't usually use the aptitude command, I tend to use the GUI tools. And if I do use the command line I use "apt-get" not usuall aptitude (though I have used it a few times to learn what it is).

---

### Post by mc4man on 2011-03-19
> I don't usually use the aptitude command, ...
Then uninstall aptitude, there is no grand reason one has to use it.
In the overall scheme of things I think it's beneficial to ocassionally do a fresh install of natty, at least till later in Beta or RC

---

### Post by cariboo on 2011-03-19
+1 to what mc4man said, I'm still curious to know what command you used to start 4 instances of aptitude.

---

### Post by mc4man on 2011-03-19
> still curious to know what command you used to start 4 instances of aptitude.
In that regard might be interesting to use htop (in a larger terminal window if need be) instead of top
It should show the process and command

---

### Post by Jonny87 on 2011-03-19
> **mc4man said:**
> Then uninstall aptitude, there is no grand reason one has to use it.
In the overall scheme of things I think it's beneficial to ocassionally do a fresh install of natty, at least till later in Beta or RC

This solved the issue. I was contemplating uninstalling it but wasn't sure if aptitude was tied to other parts of the system and didn't want to risk causing more damage. Though like you guys I still would like to know what caused it. I may reinstall it later down the track and see if the problem returns. Thanks for your help each of ya's.

---

### Post by cariboo on 2011-03-20
Just to let you know, aptitude is no longer included in the default desktop installation, so you'd have to install it yourself on a fresh Natty installation.

---

### Post by Jonny87 on 2011-03-20
> **cariboo907 said:**
> Just to let you know, aptitude is no longer included in the default desktop installation, so you'd have to install it yourself on a fresh Natty installation.

Oh ok, why have they removed it (just out of curiosity)?

---

### Post by mc4man on 2011-03-20
> Oh ok, why have they removed it (just out of curiosity)?
I believe the main reason was to save space on the live cd

In general ubuntu encourages users to use Software Center and Update Manager to manage packages, ect.

---

### Post by Harry33 on 2011-03-20
> **mc4man said:**
> I believe the main reason was to save space on the live cd

In general ubuntu encourages users to use Software Center and Update Manager to manage packages, ect.

This is the recent direction with Ubuntu.
Although, one shoud be aware of the fact, that using Update Manager with development version (Natty for example) really is not very helpful solving dependency problems.
A partial upgrade often still is suggested, and that is bad. It is so easy to mess up the system with it.
There is Synaptic for the users who want to know exactly what will happen and why, on any update, upgrade. And most importantly, even before you press OK.

---

