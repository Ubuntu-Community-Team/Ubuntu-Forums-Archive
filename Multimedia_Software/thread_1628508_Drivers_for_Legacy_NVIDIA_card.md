---
title: "Drivers for Legacy NVIDIA card"
date: 2010-11-22
forum: Multimedia Software
---

### Post by Fixitall on 2010-11-22
Hi all,

Got a Gforce4 Ti 4400 graphics card.
After installing 10.10 everything works but not optimal:
I cannot choose any visual effects under appearances
I don't have a NVIDIA menu
Can't use any of the features.

When looking in the 'additional drivers' section, nothing shows up.

Looking at some threads, I tried what is described in: p { margin-bottom: 0.08in; }  
[http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat](http://ubuntuguide.net/how-to-install-nvidia-graphics-driver-in-ubuntu-10-10-maverick-meerkat)

However, the result is crap. As described further down that thread, my screen goes to crap.

So, re-installed everything again and I am now wondering if I should just give up. Not my nature though so here is my question:

My card is supported with the Legacy NVIDIA driver:[B] 96.43.xx driver

Latest version on their website:
[/B]**[B][SIZE=2]Version:[/SIZE]**[/B]

**[B][SIZE=2]96.43.19 Certified[/SIZE]**[/B]

**[B][SIZE=2]Release Date:[/SIZE]**[/B]

**[B][SIZE=2]2010.11.16[/SIZE]**[/B]

**[B][SIZE=2]Operating System:[/SIZE]**[/B]

**[B][SIZE=2]Linux[/SIZE]**[/B]

**[B][SIZE=2]Language:[/SIZE]**[/B]

**[B][SIZE=2]English (U.S.)[/SIZE]**[/B]

**[B][SIZE=2]File Size:[/SIZE]**[/B]

**[B][SIZE=2]15.7                           MB                       [/SIZE]**[/B]

This file is a .bin file.

So what should I do. I read something like if you don't use something from the repository you have to re-install it every time Ubuntu's kernel is updated. However, does the driver in the repository support my legacy card.
Is it wise to install the certified driver and how do I do that?

Hope someone can help me fix this.

---

### Post by s3MA00RRNY on 2010-11-22
NVidia uses dkms to reinstall its driver when the kernel is updated. To install the NVidia driver run (in recovery mode)

sudo telinit 3
sudo sh <nvidia-file>

---

### Post by mc4man on 2010-11-22
Edit: nvidia released new 96 drivers so if you use them it should be ok.

It's possible ubuntu will release new 96 packages for 10.10, the 173.XX were fixed by nvidia, and ubuntu released a new package shortly after (oct. 4), so it's possible the new 96.XX driver will be treated the same ( or a ppa will build
> nvidia-graphics-drivers-173 (173.14.28-0ubuntu1) maverick; urgency=low

  * New upstream release:
    - Add support for X.Org xserver 1.9 (LP: #626918).

---

### Post by Fixitall on 2010-11-24
> **mc4man said:**
> Edit: nvidia released new 96 drivers so if you use them it should be ok.
 
It's possible ubuntu will release new 96 packages for 10.10, the 173.XX were fixed by nvidia, and ubuntu released a new package shortly after (oct. 4), so it's possible the new 96.XX driver will be treated the same ( or a ppa will build
 
mc4man,
Thanks for your answer. 
I am not very experienced with ubuntu so I don't quite understand what that means.
So you are saying that it is possible thatubuntu will update their repository with an ubuntu driver that includes the NVIDIA fix in the 96 package. Would that fix my problem though? Because now I have only basic functions available and I suspect that the perfornace of my card is far from optimal. However, I don't know what driver is currently used but it is for sure one of the ubuntu repositories. So my question is, will the NVIDIA driver not always give me more functionality? What is the difference between the ubuntu packages and the proprietary drivers.
 
> **pcdude2143 said:**
> NVidia uses dkms to reinstall its driver when the kernel is updated. To install the NVidia driver run (in recovery mode)
 
sudo telinit 3
sudo sh <nvidia-file>
 
PCdude,
 
Ok, I will try this tonight. Why was this info so difficult to find? Did I not look good enough?
One thing I don't understand from your answer: Nvidia uses dkms..etc. What does that mean. Is the driver automatically updated after a kernel update or do I have to do that manually? If yes, how does that work?
 
Thanks for educating me.:)

---

### Post by s3MA00RRNY on 2010-11-25
It means that you don't have to worry about installing the driver for every kernel, DKMS does it for you when the kernel is installed, if every goes well.

---

### Post by Fixitall on 2010-11-26
> **pcdude2143 said:**
> NVidia uses dkms to reinstall its driver when the kernel is updated. To install the NVidia driver run (in recovery mode)
 
sudo telinit 3
sudo sh <nvidia-file>
 
PC DUDE, I haven't tried it yet. Am waiting for the weekend. Still some more questions to make sure I have a plan B when things go wrong.
 
My system currently is probably using Nouveau driver. After installing the NVIDIA driver will this automatically be OK? I read something about blacklisting Nouveau. Is that necessary?
Also, how do I verify the new driver is actually used. Is there a way to look this up?
 
What if it doesn't work. Can I roll-back to the Nouveau driver when necessary?
 
Sorry, just trying to be thorough.

---

### Post by s3MA00RRNY on 2010-11-26
Rolling back should be unnecessary, because the NVidia installer will not even run if Nouveau is active, so there is no possibility for conflict. Blacklisting Nouveau is a pain in the rear. I cannot remember how I did it, so good luck to you.

---

