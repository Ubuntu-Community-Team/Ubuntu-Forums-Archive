---
title: "Lockups with Kubuntu"
date: 2010-07-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-07-23
I installed Kubuntu 10.04 yesterday, and was quite happy with the performance. Seeing as I was so happy with it, I decided to upgrade to Maverick. 

At the time it was running 512Mb ram, and it was unusable, I was seeing 498MB ram used and about 98Mb swap with just the desktop and nothing running.

I have since upgraded to 1Gb and things are now running reasonably, most of the time, but now I'm getting occasional lock ups.

System specs are:

[list]
[*] AMD 3500+
[*] 1Gb Ram
[*] Nvidia 8400GS Video card
[*] 40Gb HDD
[/list]

---

### Post by Untitled_No4 on 2010-07-23
Edit: irrelevant.

---

### Post by 23meg on 2010-07-23
> **cariboo907 said:**
> I have since upgraded to 1Gb and things are now running reasonably, most of the time, but now I'm getting occasional lock ups.

Do you mean complete system crashes, which don't happen on the same machine running Ubuntu? It may be useful to investigate those.

---

### Post by jboywer on 2010-07-23
I tried to install Kubuntu on my laptop, But for some reason it would not get pass the Kubuntu logo. I just gave up and now i'm running Ubuntu 10-4 perfectly.

---

### Post by cariboo on 2010-07-24
> **23meg said:**
> Do you mean complete system crashes, which don't happen on the same machine running Ubuntu? It may be useful to investigate those.

This is a dual boot system XP/Kubuntu, I did the upgrade to see if there were any problems with grub2. I came into a free 160GB drive today, so next week I'll make it a triple boot including Ubuntu and see if the problem persists.

---

### Post by Reiger on 2010-07-24
If it is your first run you may be seeing a lot of disk activity from nepomuk/strigi and related processes.

Also, you may want to check system logs to see if there's a kernel Oops or something.

---

### Post by ELD on 2010-07-24
You may be experiencing this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/585765)

Which no one still knows what's wrong.

---

### Post by Slug71 on 2010-07-24
Im running a Ubuntu install with the XFCE desktop and i get occasional lock-ups too. Sometimes they become quite frequent. Always seems to happen when i have Firefox open and been on a site that uses a lot of Flash.? But i have had it happen just after a boot-up too a few times. I think its related to the bug that ELD linked.

Anyway, i dont think its Kubuntu specific. I actually even get it on a similar Lucid install. Though not as much.

---

### Post by cariboo on 2010-07-24
I have three other maverick, ubuntu and une, installs that don't have any problems, this is the only one so far that locks ups.

These are hard lockups, where nothing works, I can't even ssh in and reboot, the only thing to do is hit the reset button.

---

### Post by VMC on 2010-07-24
> **cariboo907 said:**
> I installed Kubuntu 10.04 yesterday, and was quite happy with the performance. Seeing as I was so happy with it, I decided to upgrade to Maverick. 

At the time it was running 512Mb ram, and it was unusable, I was seeing 498MB ram used and about 98Mb swap with just the desktop and nothing running.

I have since upgraded to 1Gb and things are now running reasonably, most of the time, but now I'm getting occasional lock ups.

System specs are:

[list]
[*] AMD 3500+
[*] 1Gb Ram
[*] Nvidia 8400GS Video card
[*] 40Gb HDD
[/list]

I just installed Kubuntu Lucid 64-bit and also I'm quite pleased with the results. I too was thinking of install Kmaverick on another partition, but have decided to wait awhile. Its been almost a year since I've used Kubuntu and I want to get more driving experience.

I should thank both Mandrive and suse for getting me back to KDE. I tried both with very little success getting codecs installed. So I got hold of a Kubuntu Lucid 64 bit disk and just upgraded the iso using zsnc. Its now part of 10.04.1. Very pleased with the outcome.

I have an AMD Athlon 250 with 4 gigs of ram. Close to your setup, so now I will hold off until a latter date. I have visited the Kubuntu forums in a while to see what's the consensus.

Thanks for bringing this topic of kde Maverick up.

---

### Post by cascade9 on 2010-07-24
> **cariboo907 said:**
> At the time it was running 512Mb ram, and it was unusable, I was seeing 498MB ram used and about 98Mb swap with just the desktop and nothing running.


o.O. Woah, thats a lot of RAM use for idle.  

BTW, is that 32bit or 64bit?

---

### Post by cariboo on 2010-07-24
Not that it would make that much difference, but it's 32-bit.

---

### Post by cascade9 on 2010-07-25
> **cariboo907 said:**
> Not that it would make that much difference, but it's 32-bit.

Woah! that means that if it was 64bit, it would use nearly a gig (since 64bit is twice as big as 32bit) :lolflag: 

I'd actually like to see how much difference it 32bit vs 64bit does make to memory use, but I doubt it would make much difference as well.

---

### Post by cariboo on 2010-07-26
It turns out that it was a harware problem, I moved the partition to another drive using clonezilla, and no more lockups, ram usage is  down too, with chromium, synaptic and 2 terminals running ram usage is at 476Mb.

---

### Post by VMC on 2010-07-26
> **cariboo907 said:**
> It turns out that it was a harware problem, I moved the partition to another drive using clonezilla, and no more lockups, ram usage is  down too, with chromium, synaptic and 2 terminals running ram usage is at 476Mb.

 Mine is using over 1-gig of ram. You did say your were using this on a 32-bit system. I wonder if that's why.

---

### Post by xebian on 2010-07-26
> **cascade9 said:**
> Woah! that means that if it was 64bit, it would use nearly a gig (since 64bit is twice as big as 32bit) :lolflag: 

I'd actually like to see how much difference it 32bit vs 64bit does make to memory use, but I doubt it would make much difference as well.

A byte of RAM is the same size anywhere.

---

### Post by cariboo on 2010-07-26
On this system, 

[list]
[*] AMD 240
[*] 2Gb ram
[*] Nvidia GT210
[/list]

I'm currently using:

```
free -m
             total       used       free     shared    buffers     cached
Mem:          2008        992       1016          0         43        354
-/+ buffers/cache:        **594**       1414
Swap:         1906          0       1906
```

With chromium and deluge running

---

### Post by VMC on 2010-07-27
I have an 
[LIST]
[*]AMD 250
[*]4 gig ram
[*]nVidia GeForce 6150
[/LIST]

```
user@user:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3711        917       2793          0         29        392
-/+ buffers/cache:        496       3214
Swap:         2000          0       2000


```

I'm running Kubuntu 10.04.1 amd64 current, and Google Chrome only.

---

### Post by cascade9 on 2010-07-27
> **xebian said:**
> A byte of RAM is the same size anywhere.

Yeah. I made a (bad) joke, I guess you havent seen people say '64bit uses twice as much RAM as 32bit' then. 

In reality, it doesnt...though I have heard that 64bit will uses slightly more RAM than 32bit. Never really tested that myself, the only 64bit capable machine I own has 2GB, and with that much RAM its not going to make much difference. IIRC with my system, KDE4.X idles at about 200MB....no, thats not kubuntu. I cant really check that now, the LCD monitor on my system is borked and moving the CRT from this system to my other system is a PITA.

---

### Post by NightwishFan on 2010-07-27
Linux manages ram in a complex manner. If you have 'less' ram it will also seem to use 'less' ram by some tools. Though 512mb should honestly be sufficient for basic tasks on any DE, though it is fast becoming not.

---

### Post by Slug71 on 2010-07-27
Im starting to think my lock-ups are hardware/ram? related too.

---

### Post by Asraniel on 2010-07-27
run memcheck, you will know more

---

### Post by cariboo on 2010-07-27
In my case it was a faulty hard drive, it passes all tests with flying colors, except the rotational speed is reported at 5564 rpm instead of 7200rpm.

---

