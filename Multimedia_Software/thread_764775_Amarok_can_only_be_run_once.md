---
title: "Amarok can only be run once"
date: 2008-04-24
forum: Multimedia Software
---

### Post by grapeape25 on 2008-04-24
I am using Kubuntu and for some strange reason I can only run Amarok once and then if I close it, the only way I can open it again is if I reboot my computer. If I try to open it after already having ran it once then it will just have the little icon bouncing up and down next to my mouse for about 20 seconds and then nothing happens. I have tried running it from the Konsole and it still doesn't work there either.

---

### Post by Monicker on 2008-04-24
> **grapeape25 said:**
> I am using Kubuntu and for some strange reason I can only run Amarok once and then if I close it, the only way I can open it again is if I reboot my computer. If I try to open it after already having ran it once then it will just have the little icon bouncing up and down next to my mouse for about 20 seconds and then nothing happens. I have tried running it from the Konsole and it still doesn't work there either.

Which version of Ubuntu?  In the past I have had problems on other distros where Amarok would hang because it didnt clear its old socket connections.  I think this was more of a bug with Amarok than with the OS itself,

When its hanging, go to a terminal and do "sudo ps aux|grep amarok".  How many results are returned.

You should be able to kill amarok without rebooting. Try "sudo killall amarok" or "sudo pkill -f amarok".

---

### Post by grapeape25 on 2008-04-24
sudo ps aux|grep amarok output:

> scott     2698  0.0  0.6  19528  8924 ?        R    07:54   0:00 amarok
scott     2700  0.0  2.1  74696 27296 ?        S    07:54   0:00 amarokapp
scott     2711  0.0  0.4  17284  6196 ?        R    07:55   0:16 amarok
scott     2713  0.0  0.4  14456  5476 ?        S    07:55   0:00 dcop amarok pla  

I tried both the kill commands you suggested and didn't work. I also tried to kill it from the processtable which also showed the existing processes being closed but when I started it again they started as well but the app didn't appear.

---

### Post by ben2talk on 2008-10-20
I installed Amarok mostly because i needed to copy my music to another disk, and then start re-importing what I want - it got out of hand. Amarok is better for some things - but to be honest, I think maybe I'll use Rhythmbox for normal use.

I just managed to kill it and restart it - by killing 'amarokapp' the first sign I had a problem.

I can't say this will work every time - but killall amarokapp worked for me THIS TIME.

Is this a bug?

Keep an install of Banshee and maybe a few selected others (Songbird is going to be a killer if it gets all the extras worked out - it's like a Firefox with a tab for Amarok built in)

Banshee is nice  - it just got a mega upgrade cos it's supported for SuSe by Novell. It will come along very quickly I think.

Keep your options open.

---

### Post by sim-value on 2008-10-20
> **Monicker said:**
> 
You should be able to kill amarok without rebooting. Try "sudo killall amarok" or "sudo pkill -f amarok".

Thanks the 2nd comand did it for me .. i always cant open Amarok after needing to Forcequited it ...

---

