---
title: "Nvidia Gtx 460 drivers?"
date: 2011-04-26
forum: Multimedia Software
---

### Post by ShoutingRyan on 2011-04-26
I really need help re-installing my Nvidia Gtx 460 drivers.

I actually managed to do it last time I rebuilt [SIZE="1"](to remove windows partition)[/SIZE], but that was by failing at a set of instructions to the point that it made another set of instructions that previously didn't work, work. --I have no idea how to even find those pages anymore, yet alone what each command was in the terminal.

[SIZE="1"]But then I had to install windows again for Portal 2 and I can't get these working for minecraft.[/SIZE]

Please keep it simple, as I still get confused navigating by terminal.

> 
Ubuntu 10.4 (64x)
Nvidia GeForce GTX 460
Gateway LX6810


---

### Post by Yellow Pasque on 2011-04-26
The easiest way is to use this PPA to get recent nvidia drivers: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid)

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-graphics-drivers
```

---

### Post by ShoutingRyan on 2011-04-26
> **Temüjin said:**
> The easiest way is to use this PPA to get recent nvidia drivers: [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates?field.series_filter=lucid)

```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-graphics-drivers
```

That was one half of what got it working last time. I can't understand it in it's entirety. 

Hmm... I just noticed a code block in the quote block while typing this message. It didn't show up on the post.

Okay, third line of the code block didn't work.
> 
ryan@ryan-desktop:~$ sudo apt-get install nvidia-graphics-drivers
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-graphics-drivers


---

### Post by WannabeFantasma on 2011-04-27
you could download the drivers from the nvidia site (for linux ofcourse)

and than save it to Desktop

then open terminal type in : cd Desktop

then type : sudu sh N(press tab and it will show Nvidia......)

and you should be able to install.
Edit: You need to do this every time you install new kernel so other solution might be better

---

### Post by inobe on 2011-04-27
> **ShoutingRyan said:**
> That was one half of what got it working last time. I can't understand it in it's entirety. 

Hmm... I just noticed a code block in the quote block while typing this message. It didn't show up on the post.

Okay, third line of the code block didn't work.


```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```

now go to hardware drivers and select recent nvidia then activate.

---

### Post by Yellow Pasque on 2011-04-27
> now go to hardware drivers and select recent nvidia then activate.
That will just install the nvidia binary driver that came with Lucid, which apparently is too old for gtx460. I'm not sure why my code snippet didn't work.

---

### Post by inobe on 2011-04-27
> **Temüjin said:**
> That will just install the nvidia binary driver that came with Lucid, which apparently is too old for gtx460. I'm not sure why my code snippet didn't work.

it's the way i did it, and always did, works fine with avenard repo and ubuntu-x-swat repo.

simple, add repo, update sources, load current driver in hardware drivers, running the latest 270'xx driver.

---

### Post by ShoutingRyan on 2011-04-27
> **inobe said:**
> ```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```

now go to hardware drivers and select recent nvidia then activate.

Wow, that actually worked. I couldn't hit activate, but I tried both the 173 and the 96 that were there from the software center, when I switched back to current, it worked better than before.

(also I don't have the problem that I had last build where I had to up the resoultion from every cold boot.)

Thanks!!! :D

---

### Post by inobe on 2011-04-27
> **ShoutingRyan said:**
> Wow, that actually worked. I couldn't hit activate, but I tried both the 173 and the 96 that were there from the software center, when I switched back to current, it worked better than before.

(also I don't have the problem that I had last build where I had to up the resoultion from every cold boot.)

Thanks!!! :D

that's great :)

go into system> administration> nvidia xserver settings..

what driver is listed?

---

### Post by andyvy on 2012-02-23
> **inobe said:**
> ```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```

now go to hardware drivers and select recent nvidia then activate.

I would also do **sudo apt-get upgrade** after.

There are a few xserver & fglrx files that get upgraded before Hardware Drivers can see your card.

---

