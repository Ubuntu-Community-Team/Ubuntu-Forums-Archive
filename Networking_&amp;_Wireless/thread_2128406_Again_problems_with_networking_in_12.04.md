---
title: "Again problems with networking in 12.04"
date: 2013-03-23
forum: Networking &amp; Wireless
---

### Post by danbuz on 2013-03-23
I wont discus that after 10.04 I gave up ubuntu - 10.04 was close to perfection. Anyway It came 11.04 I had HP laptop with 2 gigs of ram and old M intel processor. Than i had big problems with internet and it was explained to me that my hardware is old. I installed mint and just did my job.

Since than I was 2 years i bought myself new machine with intel i7, 8gigs of ram and powerful nvidia video. And this morning I decided to give 12.04 a try (again I will not discus that 12.10 is a mess - it looks more like mac than ubuntu anymore, not to talk about this commercial nonsense with amazon, PROBABLY 12.04 IS THE LAST UBUNTU I DECIDED TO TRY). However, I put the disk, tried to connect to internet in live mode, it shows that it is connected BUT AGAIN NO INTERNET. Some kind of guru tried to explain me that this is because I use samsung and the support is not very good. I have no idea what to do - im not techie, just wanted to install it and to use internet and stuff.

what should I do? where to check for solution?

mint connects again?! why is that way - i was told that mint is based on ubuntu. than why mint is smooth every time?

---

### Post by sanderj on 2013-03-23
If Mint works for you, and you like it, why bother with Ubuntu ... ?

---

### Post by danbuz on 2013-03-23
To answer you - because I'm with ubuntu since 8 version (i was).
as I said 12.04 is the wast ubuntu I like. Have solution to the problem or just want to spam with useless questions?

---

### Post by sanderj on 2013-03-23
> **danbuz said:**
> To answer you - because I'm with ubuntu since 8 version (i was).
as I said 12.04 is the wast ubuntu I like. Have solution to the problem or just want to spam with useless questions?

"Useless questions"? Do you want to be helped, or do you want to rant?

Let's assume you want to be helped: open a terminal and post your output of:

```
mtr -nrc2 8.8.8.8
```

Be friendly in your followup, or I'll welcome you to my ignore list.

---

### Post by danbuz on 2013-03-23
> **sanderj said:**
> "Useless questions"? Do you want to be helped, or do you want to rant?

Let's assume you want to be helped: open a terminal and post your output of:

```
mtr -nrc2 8.8.8.8
```

Be friendly in your followup, or I'll welcome you to my ignore list.

my*** apologies ***if I dont sound friendly. But I didnt see how the previous question was connected with the solution of my problem.

when I paste the line it shows:

[****]("http://www.google.com/search?hl=en&client=ubuntu&hs=wrl&channel=fs&q=apologies&spell=1&sa=X&ei=fMFNUYSZIsTStAaI-IDYDw&ved=0CCsQvwUoAA&biw=1301&bih=678")
root@ubuntu:/home/ubuntu# mtr -nrc2 8.8.8.8
HOST: ubuntu                      Loss%   Snt   Last   Avg  Best  Wrst StDev
root@ubuntu:/home/ubuntu# 


Thant's it - i tried to install wicd on live but no success.

---

### Post by sanderj on 2013-03-23
What's the output of 

ifconfig

Is an ethernet cable connected?

---

### Post by danbuz on 2013-03-24
> **sanderj said:**
> What's the output of 

ifconfig

Is an ethernet cable connected?


I discovered what the problem is - a bug. After removing the internet issue, strange thing happened - tried to make fresh install over the whole hard disk, everything went smooth, and after installing it asked me if I want to reboot or go on live. I rebooted, removed the usb after reboot and the system didn't want to load. JUST BLINKING BLACK SCREEN with non stop rebooting and appearing of "_" without quites and then again reboot.

I downloaded the iso from ubuntu again, again tried to install and again everything was ok untill i rebooted- the same story. When I use it live everything is ok. I downloaded on live mode some tool to revocer the grub loader, just to try if this is the issue but again NO RESULTS.

the version of the release is 12.04lts and the machine is **Samsung RF511 with i7 intel**

---

