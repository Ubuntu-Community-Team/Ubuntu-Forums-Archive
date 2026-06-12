---
title: "&quot;Error: Unknown filesystem, grub rescue&gt;&quot; with Ubuntu 11.04"
date: 2011-04-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Natalio on 2011-04-09
Hi guys,

I'm new to the forum and pretty much an Ubuntu newbie. The thing is, I was on my laptop today and suddenly Chromium crashed and everything freezed, so I had to turn my laptop off manually. When I turned it back on, I got this message:

"Error: unknown filesystem
grub rescue>"

So, I've been reading everything I found related to this message and Ubuntu 11.04, but since it's a Beta release, I couldn't find much. The real problem here is that I read plenty of solutions for this problem, but I can't try any of them because when I try to load a Natty (or a 10.04, tried both) Live CD, I get something like a Terminal but I can't do anything! I mean, there's a black screen, I can type things on it but nothing ever happens.

I also have Windows 7 installed but haven't used it since I installed Ubuntu 10.04 (then updated to 10.10 and about a week ago updated to 11.04)

Any thoughts? Any recommendations regarding what I should do to be able to enter Ubuntu via a Live CD?

Thanks in advance.

EDIT: btw, I think that it may be important to point out that I've been having problems with one of the internal hard drives for some time, if that's something that could be relevant. Oh, and other thing, everything is 32-bit editon.

---

### Post by Natalio on 2011-04-10
Idk if this is against the rules, but a little bump here to see if anybody can help me.

---

### Post by Sidewinder1 on 2011-04-10
It certainly should boot to Live CD; and you should be able to select "Try Ubuntu". If it doesn't, are you certain that you amended your bios settings to boot to CD first, then internal HD.?
I don't even want to go the "failing hardware/hard disk" route.

HTH,
Side

---

### Post by Sidewinder1 on 2011-04-10
By the way, _*Welcome to Ubuntu Forums!*_
=D>

---

### Post by Natalio on 2011-04-10
> **Sidewinder1 said:**
> It certainly should boot to Live CD; and you should be able to select "Try Ubuntu". If it doesn't, are you certain that you amended your bios settings to boot to CD first, then internal HD.?
I don't even want to go the "failing hardware/hard disk" route.

HTH,
Side

Hi, and thank you for answering. Yes, I am certain because it actually boots, then I'm able to choose Try Ubuntu or to Install it, once I choose Try Ubuntu, this black screen appears.

An hour ago I was trying again and after approx. 10 mins of this black screen, the Ubuntu "dots" appeared, and then after a while, it started running another black screen, but this time with a lot of information and numbers. But once it finished, nothing happened. This was with my 10.04 copy. And then I tried with the 11.04 distro, the same thing happened, but then it gave me a timeout of 180 seconds, and after that the "Ubuntu 11.04" and the dots thing appeared again.

So, I'm really lost here. And I tried to install Windows 7 again, because I really need my laptop right now, but that's another thing I can't do right now! I never had any problems installing ANY Windows version, and now I get a "cannot boot from cd - code: 5" thing.

BTW, sorry that I'm not giving enough information about the black screen thing. I really don't know what those numbers means, so I'm going to try again and try to copy some of them.

Thank you very much for your answer and your welcome!

---

### Post by Sidewinder1 on 2011-04-10
No problem, that's why we're here .:D
How old is the laptop?
What is the make and model?
Will it boot to Win. 7?
If so, does the boot seem normal in terms of time, lack of error/advisory messages?

---

### Post by Natalio on 2011-04-10
> **Sidewinder1 said:**
> No problem, that's why we're here .:D
How old is the laptop?
What is the make and model?
Will it boot to Win. 7?
If so, does the boot seem normal in terms of time, lack of error/advisory messages?

Nevermind about this, I finally got to boot the Live CD (I waited for about half an hour but finally it booted).

The thing is, I'm trying to restore the grub, but when I get to the terminal and type "sudo mount /dev/sda2 /mnt" as shown in the [GRUB 2]("https://help.ubuntu.com/community/Grub2") guide nothing happens. I mean, I've been waiting for about 20 minutes and nothing.

Any thoughts about this? And btw, sorry that I didn't try waiting longer before, I just figured that if it took longer than 10 minutes to boot, it was never going to.

---

### Post by Natalio on 2011-04-10
Ok, it finally finished running the command. I got the following:

"mount: wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail or so"

I'm really missing here. Any recommendations are appreciated.

---

### Post by Sidewinder1 on 2011-04-10
I'm not terribly proficient with the syntax when using the terminal, especially with the mount command. One thing that I have noticed, when entering commands, most times when it's correct (no error messages), seemingly, nothing happens. 
After issuing the mount command listed above did you try:
```
sudo update-grub
```

If so and you were unsuccessful, perhaps below might help:

[http://ubuntuforums.org/showthread.php?p=6391959&mode=linear#post6391959](http://ubuntuforums.org/showthread.php?p=6391959&mode=linear#post6391959)
or

[http://ubuntuforums.org/showthread.php?p=7505203&mode=linear&highlight=Grub+dual+boot#post7505203](http://ubuntuforums.org/showthread.php?p=7505203&mode=linear&highlight=Grub+dual+boot#post7505203)

HTH,
Side

---

### Post by Sidewinder1 on 2011-04-10
Please disregard my above post; we were typing at the same time . :D
I'm sorry, but when the highly technical nonsense starts:"wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage...", I get lost and start feeling like a Bozo.
I will say that the more I read, the more it sounds like a hardware/disk problem.
If you can boot the live CD, try:System-->Administration-->Disk Utility and see if that program can "see" your HD; if so, there are some tests that you can run: SMART Data, 
" Check File System", that may be able to diagnose/fix your problem.

Beyond that, I'm not sure that I can be much more help; but, don't give up yet!!!

Side

---

### Post by Natalio on 2011-04-10
SMART has been detecting a failure for some time now, but nothing new really. I haven't been able to fix it, and have tried many ways. The hard drive model (I don't recall wich is it) is known for having this issue with SMART.

Anyway, thank you very much for your time and consideration in answering my questions. I hope that anyone can come up with something else because I really need my laptop back.

Thank you

---

### Post by bodhi.zazen on 2011-04-10
> **Natalio said:**
> Idk if this is against the rules, but a little bump here to see if anybody can help me.

Please use the testing forums for support of 11.04

---

### Post by Sidewinder1 on 2011-04-10
Ah, heck, bodhi, I noticed that too and, being caught up in the analysis of the problem, forgot to mention it, humblest apologies that you had to take your time to mention what I should have advised in the first place. 

Natalio: It may or may not be an issue but Natty 11.04 is beta (as you already know) and hasn't even been, officially released yet.

As one of my elementary teachers once said, "Don't say you're sorry, just don't let it happen again".

Side

---

### Post by Natalio on 2011-04-10
> **bodhi.zazen said:**
> Please use the testing forums for support of 11.04

I'm sorry, I should've checked that out first.

Should I start a new thread there or could you move it?

Thanks.

---

### Post by bodhi.zazen on 2011-04-10
> **Natalio said:**
> I'm sorry, I should've checked that out first.

Should I start a new thread there or could you move it?

Thanks.

NP. I moved it already.

Your problem could be most anything from a bug in natty to a hardware problem.

I would start by running fsck from a live CD.

---

### Post by Natalio on 2011-04-10
Thank you very much for moving the thread.

Right now I'm trying to re-install Natty, the thing is, right now it's been about half an hour since I pressed the "Forward" button in the "Preparing to install Ubuntu" screen. So I guess it's definitely a Hard Disk problem, but it could also be related to a Natty bug, and that's basically why I'm writing this, because if I was sure that it was solely a Hard Disk issue, that's it.

Anyway, is there any reports of Natty taking 30+ minutes to get pass the Preparing to Install Ubuntu screen?

BTW, I was able to boot a Live session but couldn't repair the GRUB, so that's why I'm trying to reinstall it. Can you think of any other way that I might be able to install Ubuntu without having this issues? I also have the 10.04 distro but it never gets to the Language screen (the first one to appear in the installation process).

---

### Post by sdowney717 on 2011-04-10
> ```
SMART has been detecting a failure for some time now
```

my guess is the hard drive has a problem.
I think even if you get it reinstalled it might be a waste of time as it will go out again.

dont the hard drive makers offer a downloadable hard drive check program that boots?

---

### Post by Natalio on 2011-04-10
I know that maybe what I'm trying to do is a waste of time, but I really need to get my laptop up and running again. Right now I'm logged into the Live CD and seeing what I can do from there. Any suggestions as to what can I do to reinstall Ubuntu or Windows? See, I need to finish something for my job ASAP and it needs to be done there, that's why I'm trying to get that laptop back on. 

Yes, almost every hard drive maker offers that kind of tools. I'm going to check that, thanks.

---

### Post by bodhi.zazen on 2011-04-10
> **bodhi.zazen said:**
> I would start by running fsck from a live CD.

This ^^

[http://www.kernelhardware.org/how-should-run-fsck-linux-file-system/](http://www.kernelhardware.org/how-should-run-fsck-linux-file-system/)

[http://linuxpoison.blogspot.com/2009/04/how-to-checkrepair-fsck-filesystem.html](http://linuxpoison.blogspot.com/2009/04/how-to-checkrepair-fsck-filesystem.html)

---

