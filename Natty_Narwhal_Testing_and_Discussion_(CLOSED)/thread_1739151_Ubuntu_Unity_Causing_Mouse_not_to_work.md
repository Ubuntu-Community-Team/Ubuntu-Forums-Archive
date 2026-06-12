---
title: "Ubuntu Unity Causing Mouse not to work"
date: 2011-04-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Mindswap1 on 2011-04-25
Ever Since I upgraded from Maverick, my Mouse has not been working the same. Every time I start up the computer I have to unplug my mouse, and then replug it for it to start working. This only happens in Natty, and I have been using Ubuntu since 9.04, and had no problems until now. How can I fix this? 

My Mouse is: Microsoft Basic Optical Mouse v2.0

---

### Post by KegHead on 2011-04-25
Hi!

Natty is in beta.

How often do you upgrade?

Is your kernel current?

KegHead

---

### Post by Mindswap1 on 2011-04-25
So I check for updates 2-3 times a day, and I'm am certain that my kernel is current, but to be honest I'm not sure. My Kernel version is 2.6.38-8-generic. According to the output i got when i put 

```
uname -r 			 		
```

Into the terminal. 

And I know its beta but the release is 4 days away so I thought by now the problem would have been solved :/.

---

### Post by KegHead on 2011-04-25
Hi!

Your kernel looks ok.

Do you upgrade via the terminal:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Advise

KegHead

---

### Post by Mindswap1 on 2011-04-25
> **KegHead said:**
> Hi!

Your kernel looks ok.

Do you upgrade via the terminal:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Advise

KegHead


Um well I occasionally update via terminal However when I do I only use sudo apt-get upgrade or update. I never used the other commands you mentioned. And is the -f important? Should I run all the commands you mentioned?

---

### Post by d3v1150m471c on 2011-04-25
Is xserver-xorg-input-mouse installed? when I upgraded to lucid this was missing, for reasons unknown to me, as well as several other xorg packages. I had to purge and install the xorg packages from maverick to fix this. 

edit:
You might want to check out apt-oops on my site below. It didn't fix everything when I upgraded but it did make my system usable enough for me to repair it properly.

---

### Post by Mindswap1 on 2011-04-25
> **d3v1150m471c said:**
> Is xserver-xorg-input-mouse installed? when I upgraded to lucid this was missing, for reasons unknown to me, as well as several other xorg packages. I had to purge and install the xorg packages from maverick to fix this.

I searched through synaptic package manager, and it said I had it installed.

---

### Post by KegHead on 2011-04-25
Hi!

Yes, I and many folks update via my post. [COLOR="Red"]It's very complete[/COLOR].

-f forces the update  (it's commonly used).

KegHead

---

### Post by Mindswap1 on 2011-04-25
I did the update, and sadly it didn't fix the problem :/. Is there anything else could do.

---

### Post by KegHead on 2011-04-25
Hi!

Are you using Unity?

If so, try classic.

system...admin...login

choose "classic"

Restart

Advise.

KegHead

---

### Post by Mindswap1 on 2011-04-25
Um that didn't do the trick. The mouse actually does not even work at the log in screen. I have to take it out, and plug it in for it to work.

---

### Post by KegHead on 2011-04-26
Hi!

Tell us about your machine...specs...etc

KegHead

---

### Post by Mindswap1 on 2011-04-26
OK :) So I Have a Compaq Presario SR5710F with an Amd Athlon X2 44550e Dual Core Processor. I have 3gb of ram. And a NVIDIA GeForce 6150 SE Graphics Graphics Card.

---

### Post by KegHead on 2011-04-26
Hi!

Just curious about any bios updates?

KegHead

---

### Post by Mindswap1 on 2011-04-26
Um I don't know how to update my bios so I doubt I got one unless Ubuntu updated it when I did a system update. >.< sry for the lack of info.

---

### Post by KegHead on 2011-04-26
Hi!

Are your drivers up to date for your video card?

KegHead

---

### Post by Mindswap1 on 2011-04-26
Hai um well before I had this online guide that helped me add the NVIDIA and AMD PPA which was supposedly supposed to give me the latest drivers, but that website it no longer around so I don't know how to add the ppa again.

I am pretty sure I have the latest proprietary driver installed though seeing as how there is only one option.

---

