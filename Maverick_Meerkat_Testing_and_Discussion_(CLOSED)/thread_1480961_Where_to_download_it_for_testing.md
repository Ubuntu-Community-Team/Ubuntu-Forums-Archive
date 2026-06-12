---
title: "Where to download it for testing?"
date: 2010-05-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by rexes13 on 2010-05-12
Hey there.I want to download Maverick Meerkat to test it.Anybody knows where please inform me!

---

### Post by taavikko on 2010-05-12
At the moment nowhere.
You can upgrade existing lucid install to it.

when they start spinning the wheels, image can be found at:
[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)

---

### Post by rexes13 on 2010-05-12
> **taavikko said:**
> At the moment nowhere.
You can upgrade existing lucid install to it.

when they start spinning the wheels, image can be found at:
[http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)
You know how?

---

### Post by taavikko on 2010-05-12
> **rexes13 said:**
> You know how?

I do.
But recommending it, no.

If you still want to pursue your wishes on testing maverick
```
sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list & sudo aptitude update && sudo aptitude full-upgrade
```

---

### Post by rexes13 on 2010-05-12
> **taavikko said:**
> I do.
But recommending it, no.

If you still want to pursue your wishes on testing maverick
```
sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list & sudo aptitude update && sudo aptitude full-upgrade
```
Ok thanx...
i will try my luck out

---

### Post by dino99 on 2010-05-12
> **rexes13 said:**
> Hey there.I want to download Maverick Meerkat to test it.Anybody knows where please inform me!

newbie+new toy = new whinings  :confused:

---

### Post by rexes13 on 2010-05-12
> **dino99 said:**
> newbie+new toy = new whinings  :confused:
Wouldnt say that i am a newbie.The fact that i dont know how to upgrade it doesnt make me a newbie!

---

### Post by dino99 on 2010-05-12
> **rexes13 said:**
> Wouldnt say that i am a newbie.The fact that i dont know how to upgrade it doesnt make me a newbie!

:shock:

---

### Post by rexes13 on 2010-05-12
> **dino99 said:**
> :shock:
I mean how to upgrade to a development branch release!

---

### Post by zika on 2010-05-12
@taavikko "I won't answer to difficult questions!" : There are no difficult questions, answers are the ones that are difficult ... :) (I could not resist to commit this flagrant off-topic...)
(Yeah, I've seen that You've written guestions... :), that made me respond...)

---

### Post by taavikko on 2010-05-12
> **zika said:**
> @taavikko "I won't answer to difficult questions!" : There are no difficult questions, answers are the ones that are difficult ... :) (I could not resist to commit this flagrant off-topic...)
(Yeah, I've seen that You've written guestions... :), that made me respond...)

I have :shock:

Then it might be the time to change my signature...
to something that defines me...

---

### Post by zika on 2010-05-12
> **taavikko said:**
> I have :shock:

Then it might be the time to change my signature...
to something that defines me...No, [guestion](http://www.urbandictionary.com/define.php?term=guestion) was so cool... :)

---

### Post by jerrylamos on 2010-05-13
Last 4 releases early on changing apt sources.list got going.  At first not too unreasonable.  Then the updates started flooding in and WHAM!  All sorts of things busted.  

Better have a separate partition or two for such testing and keep a relatively good running Lucid and Karmic around....

Jerry

---

### Post by kansasnoob on 2010-05-14
At this point if you haven't broken it you haven't been trying hard enough :lolflag:

---

### Post by ranch hand on 2010-05-14
> **kansasnoob said:**
> At this point if you haven't broken it you haven't been trying hard enough :lolflag:
I expect that we have help coming along those lines though.  If we are starting with the .24 kernel and working our way to .25 there should be a fairly good chance for breakage to happen without our help.

---

### Post by phillw on 2010-05-15
Hi, give me a nudge when the RC iso for Mangy Moose alpha1 (I **still** think Ranch Hand should name the releases) is out, I'm guessing end of May? Have a partition ready and waiting. If it's anything like 10.04, it will be a pleasure to test & fun when the devs have a 'bad day' and break all our systems ;-)

Regards,

Phill.

---

