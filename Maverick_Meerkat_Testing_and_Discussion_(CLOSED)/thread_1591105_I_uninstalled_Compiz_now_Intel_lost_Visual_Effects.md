---
title: "I uninstalled Compiz now Intel lost Visual Effects"
date: 2010-10-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sendblink23 on 2010-10-08
Hi there.. I was using fine for a few days compiz on my laptop which worked nicely, so since I'm just testing this 10.10 RC I decided to uninstall it

I ran:
sudo apt-get remove compiz

Then I rebooted, and for some reason in: System > Preferences > Appearance > *Tab - Visual Effects

its all grayed out:
[[IMG]http://img508.imageshack.us/img508/9181/screenshot1t.th.jpg[/IMG]](http://img508.imageshack.us/img508/9181/screenshot1t.jpg)

I have rebooted 2 times and still the same, as well tried running updates but did not have anything new

Any ideas how to get it back up my intel running?

```
sendblink23@ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

```

---

### Post by tjeremiah on 2010-10-08
go to synaptics package manager > type compiz > download that package.

---

### Post by cgroza on 2010-10-08
Well, its logic. You removed the program that was responsible for you desktop effects.

---

### Post by foxmulder881 on 2010-10-08
> **cgroza said:**
> Well, its logic. You removed the program that was responsible for you desktop effects.

Yeah I'm lost when I read this. The OP removed compiz and then complains he has no desktop effects. <confused>

---

### Post by sendblink23 on 2010-10-08
why do i want to reinstall compiz? If the Intel driver worked without it than its not suppose to mess up my intel video - I uninstalled it because I don't plan to use the 3D cube effects anymore, as well I don't want to have the compiz settings in my menu (simple-ccsm  & ccsm) - in other words I wanted to set the laptop as it was before installing compiz

---

### Post by sendblink23 on 2010-10-08
> **cgroza said:**
> Well, its logic. You removed the program that was responsible for you desktop effects.

ITS NOT DESKTOP EFFECTS - its Visual Effects - which is different - pretty certain I did not have to get compiz to use that

---

### Post by deanjm1963 on 2010-10-08
> **sendblink23 said:**
> ITS NOT DESKTOP EFFECTS - its Visual Effects - which is different - pretty certain I did not have to get compiz to use that

Those "Visual Effects" are actually part of compiz. They are sort of the "compiz defaults" - you can install ccsm to customize your effects. The Visual Effects settings are just a "front-end" to setting simple compiz settings.

Hope this helps.

---

### Post by sendblink23 on 2010-10-08
> **deanjm1963 said:**
> Those "Visual Effects" are actually part of compiz. They are sort of the "compiz defaults" - you can install ccsm to customize your effects. The Visual Effects settings are just a "front-end" to setting simple compiz settings.

Hope this helps.

sorry guys, my bad - I always thought compiz didn't come in the OS naturally... I always clicked the links in "The Great Desktop Effects FAQ" to enable them(I always assumed that was installing compiz) 

well thanks everybody, now come and kick my bum bum 10x for being dumb

---

### Post by deanjm1963 on 2010-10-08
> **sendblink23 said:**
> sorry guys, my bad - I always thought compiz didn't come in the OS naturally... I always clicked the links in "The Great Desktop Effects FAQ" to enable them(I always assumed that was installing compiz) 

well thanks everybody, now come and kick my bum bum 10x for being dumb

No problems ... I've done worse in my time using linux.

Those Visual Effects are only enabled if compiz supports your hardware, but are installed by default. Intel has good compiz support, that's why it's enabled without you having to do anything.

Cheers :)

---

### Post by Cenotaph on 2010-10-08
i guess this is the downside of trying to do the dirty work for the user in a system like Ubuntu: confusing ppl :) can't help but wonder what confusions can the Software Center cause as well

---

