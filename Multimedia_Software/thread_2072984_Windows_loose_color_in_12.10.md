---
title: "Windows loose color in 12.10"
date: 2012-10-18
forum: Multimedia Software
---

### Post by geovino on 2012-10-18
I installed 12.10 this morning and later in the day I was in Firefox and all of a sudden the browser turned white and strange patterns were in the address box. I opened Nautilus and it had the same discoloring that Firefox had.I tried to take a screen shot but after reboot it went back to normal. 

I have a Nvidia Geforce 8400 video card. What could cause this? 

I have another hdd on this PC with 12.04 64 bit on it and it never had that video problem. 

I didn't get additional hardware to pop up and tell me what nvidia card to install. Maybe that would help?

---

### Post by wojox on 2012-10-18
> **geovino said:**
> 
I didn't get additional hardware to pop up and tell me what nvidia card to install. Maybe that would help?

You maybe running nouveau driver and not the nvidia.

---

### Post by geovino on 2012-10-18
> **wojox said:**
> You maybe running nouveau driver and not the nvidia.

I know it's nouveau, because I didn't install any drivers. Maybe I should install the nvidia 173 which I've used before. Or the newer driver?

---

### Post by wojox on 2012-10-18
> **geovino said:**
> I know it's nouveau, because I didn't install any drivers. Maybe I should install the nvidia 173 which I've used before. Or the newer driver?

I'd try it. :P

---

### Post by geovino on 2012-10-18
just tried to install the nvidia 173 and I get this message:

here's the screenshot.

---

### Post by wojox on 2012-10-18
What does it say in the terminal:
```
sudo apt-get update; sudo apt-get install nvidia-current
```

---

### Post by geovino on 2012-10-18
> **wojox said:**
> What does it say in the terminal:
```
sudo apt-get update; sudo apt-get install nvidia-current
```

davek@dave-quantal:~$ sudo apt-get update; sudo apt-get install nvidia-current
[sudo] password for davek: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
davek@dave-quantal:~$

---

### Post by geovino on 2012-10-19
tried running: 

sudo apt-get update; sudo apt-get install nvidia-current

this morning. This time it installed, but after reboot the resolution changed to 1280-1024 when it should be 1600x900 and the taskbars on the top and left are gone. Nvidia failed again. No way to do anything at this point. No taskbars , no controls

I'm back to 12.04. It didn't caused these problems. :(

---

### Post by mc4man on 2012-10-19
Till fixed if you wanted to install any proprietary driver you'd need to first make sure that linux-headers-generic (linux-headers-3.5.0-17-generic) is installed BEFORE trying the driver install.
Mentioned here [http://ubuntuforums.org/showpost.php?p=12304169&postcount=3](http://ubuntuforums.org/showpost.php?p=12304169&postcount=3)

This represents a major oversight either in the ubiquity installer or how the deps of nvidia-* & fglrx are written (quite inexcusable really
I filed 2 bugs though I can't see how this is an unknown situation that should be addressed as soon as possible

As far as a 8400 card you'd want any of the nvidia-currrent or experimental, not 173

Myself have a 8400m (laptop), in 12.10 I actually  find nouveau the better choice

---

### Post by geovino on 2012-10-19
> **mc4man said:**
> Till fixed if you wanted to install any proprietary driver you'd need to first make sure that linux-headers-generic (linux-headers-3.5.0-17-generic) is installed BEFORE trying the driver install.
Mentioned here [http://ubuntuforums.org/showpost.php?p=12304169&postcount=3](http://ubuntuforums.org/showpost.php?p=12304169&postcount=3)

This represents a major oversight either in the ubiquity installer or how the deps of nvidia-* & fglrx are written (quite inexcusable really
I filed 2 bugs though I can't see how this is an unknown situation that should be addressed as soon as possible

As far as a 8400 card you'd want any of the nvidia-currrent or experimental, not 173

Myself have a 8400m (laptop), in 12.10 I actually  find nouveau the better choice

Thanks for the info. It's odd how up until this version 12.10, Ubuntu would always have the additional hardware icon pop up to install the nvidia driver for this PC. This time it didn't have any additional driver icon to even look for in the Dash Home. So the command I ran was not the right thing for this PC and it's OK. The Nouveau worked fine but there isn't much of a difference between 12.04 and 12.10 for me so I'm just as happy running 12.04 LTS. 

I'm giving Lubuntu 12.10 a try... simpler design, but very fast and responsive. I like it. :)

---

