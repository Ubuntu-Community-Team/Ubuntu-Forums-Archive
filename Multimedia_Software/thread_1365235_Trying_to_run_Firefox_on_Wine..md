---
title: "Trying to run Firefox on Wine."
date: 2009-12-27
forum: Multimedia Software
---

### Post by Jotaro on 2009-12-27
Well, I have decided to try and run Firefox on Wine.
I used to play on GaiaOnline's online roleplaying game called "zOMG", but it wouldn't connect to the servers when I am on Ubuntu, but it does it fine on Windows.
So, it seems that the ONLY way to do it is by running Firefox on Wine to play it..
So....how do I run Firefox on Wine?

---

### Post by taurus on 2009-12-27
Well, you could download the windows version (.exe) and see if you can install it with wine.

Otherwise, try ie4linux.

[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

---

### Post by Jotaro on 2009-12-27
> **taurus said:**
> Well, you could download the windows version (.exe) and see if you can install it with wine.

Otherwise, try ie4linux.

[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)
Ok, this may be able to fix my problem. Thanks!
I will try this, and if I STILL can't access the webpage, I will post back.

---

### Post by Jotaro on 2009-12-27
Ok, it worked, however.
When I reach the page that plays the game, it get this message:
"You need Adobe Flash Player 9"
So....any idea how I can run FIREFOX on Wine?

---

### Post by taurus on 2009-12-27
Have you installed a flash plugin for your browser(s)?

---

### Post by Jotaro on 2009-12-27
> **taurus said:**
> Have you installed a flash plugin for your browser(s)?
For my Firefox browser, I have installed:
"DivX Web Player"
DivX Web Player version 1.4.0.233
"QuickTime Plug-in 7.2.0"
"Shockwave Player 10.0 r42"
"VLC Multimedia Plugin"
"Windows Media Player Plug-in 10"

---

### Post by taurus on 2009-12-27
See if you can download the windows version of firefox.  Then, install it with wine and see what happens.

```
cd ~/Desktop
wine filename.exe
```
Assuming that you have already installed and configured wine first before you use it.

p.s.  You probably need java plugin too.  Install ubuntu-restricted-extras package for all the plugins then.

---

### Post by Jotaro on 2009-12-27
> **taurus said:**
> See if you can download the windows version of firefox.  Then, install it with wine and see what happens.

```
cd ~/Desktop
wine filename.exe
```Assuming that you have already installed and configured wine first before you use it.

p.s.  You probably need java plugin too.  Install ubuntu-restricted-extras package for all the plugins then.
Ummm.....for some reason, I am now being told that my password is incorrect even though I KNOW that it is the right password...
Can you tell me what happened?

---

### Post by taurus on 2009-12-27
You mean when you run the sudo?  

Didn't you have that problem the first time you ran the "sudo fdisk -l" command?

---

### Post by Jotaro on 2009-12-27
> **taurus said:**
> You mean when you run the sudo?  

Didn't you have that problem the first time you ran the "sudo fdisk -l" command?
Well, ever since I downloaded and installed the "Internet Explorer on Wine" package and installed it, my computer has been running slowly, so I decided to uninstall it. I deleted the files, and was going to "Synaptic Package Manager" to uninstall it there too. It asked for my password, I gave it, it told me "Wrong Password". I tried it on "Users and Groups" and it accepted my password. It accepts it at other places, but not at Synaptic. Help?

---

### Post by taurus on 2009-12-27
Maybe it's time to reboot.

---

### Post by Jotaro on 2009-12-27
Ok, I will restart my computer, and come back to try again.

---

### Post by Jotaro on 2009-12-27
Ok, I'm back. So, how can I run Firefox on Wine?

---

### Post by taurus on 2009-12-27
Please look at my previous replies because you keep asking the same question and I am too tired to keep typing the same thing since it's real late (or early) over here.

I am out of here...

---

### Post by Jotaro on 2009-12-27
> **taurus said:**
> Please look at my previous replies because you keep asking the same question and I am too tired to keep typing the same thing since it's real late (or early) over here.

I am out of here...
Sorry, I just looked back on the previous posts...
"See if you can download the windows version of firefox.  Then, install it with wine and see what happens.

 	Code:
 	cd ~/Desktop
wine filename.exe 
Assuming that you have already installed and configured wine first before you use it.

p.s.  You probably need java plugin too.  Install ubuntu-restricted-extras package for all the plugins then."
1. How do I configure Wine?
2. How do I install the "ubuntu-restricted-extras package" ?
Also, I am sorry for repeating myself.

---

### Post by lovinglinux on 2009-12-27
Recurring to Wine is not really the best option, specially considering that Firefox runs on Ubuntu. If you are still interested on solving your native Firefox issues, then check [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). 

Have you disable ipv6 to see if you can connect to the server?

---

