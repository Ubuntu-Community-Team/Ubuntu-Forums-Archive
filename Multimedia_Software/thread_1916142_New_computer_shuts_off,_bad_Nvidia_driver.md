---
title: "New computer shuts off, bad Nvidia driver?"
date: 2012-01-27
forum: Multimedia Software
---

### Post by 618smartguy on 2012-01-27
So I have recently built a new gaming computer:
   CPU: Intel 3930K
   GPU: GeForce GTX 570
   Motherboard: Intel DX79TO
   Ram: 8 GB Corsair XMS3 (two 4GB sticks, both in blue slots)
   PSU: 650 Watt Blue star
 
the temperature of the cpu is never above 45 and graphics card is never above 60

Usually when I play Minecraft or Portal two, the computer shuts down and reboots in a few seconds, with absolutely no error message or beep etc

At one point for a few days, I was able to play Minecraft, but after about 20 minutes the display went black but the computer remained on and looked no different.

If i attempt to mine bitcoins with Diablominer (a task which uses all or most of the GPU's power, I am not completely sure) the screen goes black and it does not actually mine bitcoins.

I have tried 
```
sudo apt-get install nvidia-current
```and
```
sudo apt-get install nvidia-common
```which installed with no effect

I also tried one other thing, don't recall exactly what it was but it installed nvidia x-server settings or something

Edit: it was nvidia-settings

Finally, running all 12 CPU threads at 100% has no negative effect, and running a minecraft server with multiple users blowing up lots of tnt does not crash anything, ruling out CPU and Ram problems.

I was thinking maybe not enough power, but my friend said that was unlikely

i am confused, help :confused:

---

### Post by 618smartguy on 2012-01-29
I just installed windows 7 and minecraft caused a black screen like described above. Could that suggest that the card itself is broken?

---

### Post by MoreOrLess on 2012-01-30
A high-end nvidia GPU (210-250W, not sure what a gtx 578 is) can use twice the power of a high-end CPU (125W), so it could very well be the PSU. I've never heard of Blue Star PSU's, so it could be a cheap brand and cheap PSU's are bad news.

---

### Post by 618smartguy on 2012-01-30
sorry, 570 typo. I looked up the consumption for the cpu and gpu and the graphics card goes from 150 - 300 watts and the CPU goes from 100 - 200, which should leave another 150 watts at the least. would that really be too little for the rest?

also, is there any way to be sure that it is the power supply? can i log the power usage before it shuts down, and then reboot and see what happened?

---

