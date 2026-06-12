---
title: "Major troubles with Ubuntu 11.04 alpha 3"
date: 2011-03-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by trust-no-one on 2011-03-09
Hello everyone,

I have been using Ubuntu 10.10 since it was released, and today decided the new 11.04 alpha 3 looked cool. I installed it, but now I cannot boot. It either freezes on checking battery state, or when I try to get into recovery mode I either get a terminal or a graphical system where I cannot do anything as nothing appears aside errors. What can I do to get my system running again?

My system is a desktop with AMD Phenom ii 965 processor. I have a Radeon HD 5770 graphics cards and Asus motherboard. I have two WD hard disks as well. I would like to get my system running, but do not mind using a Live CD Slax or Puppy until another release (anything beats this stupid windows I'm using right now!)

TIA,
tno

PS - Just to let anyone who cares know, the Ubuntu logo is very off center to me when I boot (in fact it isn't centered at all - it is on the right and wraps to the left!).

---

### Post by migah on 2011-03-09
I have exactly the same problem. Just installed the Alpha and it is freezing to that same thing.

I can use desktop with failsafeX mode, but not in normal mode. And in failsafe mode it is missing all the navigation panels and everything is stuck in upper left corner.

-Migah-

---

### Post by mörgæs on 2011-03-09
You are more than welcome to try 11.04, but please remember that if using an alpha version, you are the one helping people, for example by reporting bugs, not the one asking for help. 

More on 11.04 here:
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

If this is a true bug, you can report it here:
[http://www.launchpad.net/ubuntu/](http://www.launchpad.net/ubuntu/)

---

### Post by trust-no-one on 2011-03-09
> **migah said:**
> I have exactly the same problem. Just installed the Alpha and it is freezing to that same thing.

I can use desktop with failsafeX mode, but not in normal mode. And in failsafe mode it is missing all the navigation panels and everything is stuck in upper left corner.

-Migah-

Yeah, that's exactly my problem

> **mörgæs said:**
> You are more than welcome to try 11.04, but please remember that if using an alpha version, you are the one helping people, for example by reporting bugs, not the one asking for help. 

More on 11.04 here:
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

If this is a true bug, you can report it here:
[http://www.launchpad.net/ubuntu/](http://www.launchpad.net/ubuntu/)

Yep, sure, I'll go do that now. I remember seeing the prompt in Ubuntu, but it wasn't responsive enough for me to submit anyway... This is probably all my fault, I shouldn't have been so stupid as to install it as my main OS.

---

### Post by howefield on 2011-03-09
Moved to  "*Natty Narwhal Testing and Discussion*"

---

### Post by Dutch70 on 2011-03-09
> **trust-no-one said:**
> Yeah, that's exactly my problem

Yep, sure, I'll go do that now. I remember seeing the prompt in Ubuntu, but it wasn't responsive enough for me to submit anyway... This is probably all my fault, I shouldn't have been so stupid as to install it as my main OS.

A good way to try development releases is with Virtualbox, or create a small partition on your hdd and install it there. That's what I did, after trying it in Virtualbox, and it's not as difficult as you may think. 

That being said, Natty was working fairly well for me since alpha3 came out on the 3rd, but today, Ubuntu One, Nautilus, & Plymouth are crashing to point that renders it unusable.

---

### Post by trust-no-one on 2011-03-09
> **Dutch70 said:**
> A good way to try development releases is with Virtualbox, or create a small partition on your hdd and install it there. That's what I did, after trying it in Virtualbox, and it's not as difficult as you may think. 

That being said, Natty was working fairly well for me since alpha3 came out on the 3rd, but today, Ubuntu One, Nautilus, & Plymouth are crashing to point that renders it unusable.

Yeah, I have (or maybe now had) VMWare Workstation installed, but just went lazy and clicked update and now it won't work. Anyways, I guess I just have to be patient!
tno

---

### Post by lancest on 2011-03-09
> **Dutch70 said:**
> 
That being said, Natty was working fairly well for me since alpha3 came out on the 3rd, but today, Ubuntu One, Nautilus, & Plymouth are crashing to point that renders it unusable.

Same here. ClI comes in handy. Looking forward to stable.

---

### Post by Dutch70 on 2011-03-09
Another good way to try it is with a usb stick.

---

### Post by Alkalino on 2011-03-17
I had the same trouble the same day, what i just did is made un update from another screen terminal (Alt + F1), typed "sudo apt-get update" and "sudo apt-get upgrade", that was like made an update from the update manager, really hope this works for you. Sorry if my English is not so good.

---

### Post by d1g1t on 2011-03-17
my system froze at 'checking battery state' after I installed fglrx. removing it fixed the problem

---

### Post by axle_foley00 on 2011-04-02
I had the same issue even with beta 1 and it turns out it was because I had Guest Additions installed in VirtualBox. The guest additions also gives the functionality of the nvidia proprietary drivers so I think that's really the issue. Once I removed guest additions it booted properly, but just without the new launcher bar due to no compiz/nvidia drivers.

---

