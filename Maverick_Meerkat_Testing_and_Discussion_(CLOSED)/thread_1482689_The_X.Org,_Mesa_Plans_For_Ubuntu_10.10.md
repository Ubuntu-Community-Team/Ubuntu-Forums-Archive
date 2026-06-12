---
title: "The X.Org, Mesa Plans For Ubuntu 10.10"
date: 2010-05-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2010-05-13
[The X.Org, Mesa Plans For Ubuntu 10.10](http://www.phoronix.com/scan.php?page=news_item&px=ODI0Nw)

Hopefully everything gets finished in time for release.

10.04 uses .32 kernel
10.10 might use .35 kernel. That would be a big improvement.
For me new intel drivers would be great. In 10.04 they kept old drivers to help i8xx users.

I don't know much about ati or nvidia drivers but they should get new versions.

10.10, a release with lots of new/good drivers?

Any news on driver improvements for nvidia ion? Thinking of getting one sometime in next 6 months. If going to be improvements for that specifically would be nice to know.

---

### Post by byStanderone on 2010-05-13
...nvidia in general, had read somewhere here in the forums that it is best to stay away from nvidia, particularly its newer firmwares, don't know how true it is. nvidia is withrawing its support for linux use, it is said.

---

### Post by recluce on 2010-05-13
> **byStanderone said:**
> ...nvidia in general, had read somewhere here in the forums that it is best to stay away from nvidia, particularly its newer firmwares, don't know how true it is. nvidia is withrawing its support for linux use, it is said.

Who says that? Is there a quotable source for this rumor?

---

### Post by kansasnoob on 2010-05-13
I was happy when the VIA openchrome drivers worked right in Lucid.

I take care of 30+ boxes with those GPU's and I was panicked when they didn't work in Karmic.

---

### Post by kansasnoob on 2010-05-13
> **recluce said:**
> Who says that? Is there a quotable source for this rumor?

+1! Post a source, otherwise it's just a rumor.

I find that almost unbelievable.

---

### Post by Mblackwell on 2010-05-14
I certainly haven't heard that from my friend that works for their Linux driver team...

---

### Post by wojox on 2010-05-14
> **byStanderone said:**
> ...nvidia in general, had read somewhere here in the forums that it is best to stay away from nvidia, particularly its newer firmwares, don't know how true it is. nvidia is withrawing its support for linux use, it is said.

That is strange. I could see if their drivers sucked, but it's just the opposite.

---

### Post by Seren on 2010-05-14
Concerning Nvidia they are not dropping Linux support, but their policy is to not support in any way the free driver implementation : Nouveau.

Source:
[http://www.phoronix.com/scan.php?page=article&item=nvidia_kills_nv&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_kills_nv&num=1)

On the other hand, ATI/AMD has two or three people working full time (Alex Deucher,...) on the free ati driver and they have released specs and documentation.

Performance wise the two closed drivers are similar (Nvidia might be slightly better), but if it matters to you to use and support free software, you'd better buy an ATI card.

---

### Post by dino99 on 2010-05-14
> **kansasnoob said:**
> I was happy when the VIA openchrome drivers worked right in Lucid.

I take care of 30+ boxes with those GPU's and I was panicked when they didn't work in Karmic.

have you some links, howto or threads to share with us about "openchrome" as many users failed with this chipset ?

---

### Post by byStanderone on 2010-05-14
...didn't bookmarked the page, but would try to find it and have it posted. was a bit worried tho when i read it then, i am using nvidia.

---

### Post by recluce on 2010-05-14
So all that is basically said is that NVidia does not care about Nouveau and will just concentrate to develop their proprietary driver. That is hardly a surprise and not much of a news item either....

---

### Post by krazyd on 2010-05-15
> **andrewabc said:**
> Any news on driver improvements for nvidia ion? Thinking of getting one sometime in next 6 months. If going to be improvements for that specifically would be nice to know.

As the linux kernel video support advances, nvidia's driver falls further and further behind because they refuse to support the regular X software stack. 

One of the most important consequences of that is that X can't be run rootless using the nvidia driver. This is important because having X run as root is a security issue as well as a stability issue. (non-root X can't lock up your computer anymore, since it is just another userspace app)

Here is the blueprint for Maverick: [https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-maverick-rootless-x](https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-maverick-rootless-x)

and here is a good overview of the importance of non-root X: [http://lwn.net/Articles/341033/](http://lwn.net/Articles/341033/)

---

### Post by TrueTom on 2010-05-15
> **krazyd said:**
> As the linux kernel video support advances, nvidia's driver falls further and further behind because they refuse to support the regular X software stack.

They don't refuse, they can't legally.

---

### Post by The Cog on 2010-05-15
> **TrueTom said:**
> They don't refuse, they can't legally.

Can you back that statement up? It seems odd to me that they might not be allowed to provide support.

---

### Post by TrueTom on 2010-05-15
> **The Cog said:**
> Can you back that statement up? It seems odd to me that they might not be allowed to provide support.

[http://old.nabble.com/Re%3A--ubuntu-x---nouveau-now-set-as-the-default-driver-for-Nvidia-hardware-p27673441.html](http://old.nabble.com/Re%3A--ubuntu-x---nouveau-now-set-as-the-default-driver-for-Nvidia-hardware-p27673441.html)

---

### Post by krazyd on 2010-05-15
> **TrueTom said:**
> They don't refuse, they can't legally.

Um, they could provide an open source driver. AMD has shown it can be done.

---

### Post by hikaricore on 2010-05-15
Exactly, the only thing stopping nvidia from contriubting properly is the fact that they don't want their trade secrets exposed.
It has nothing to do with what they can and can't do "legally", it has to do with their unwillingness.

That said they do make a fine product and great drivers, i'm not sure how there could even be a rumor to the contrary..

---

### Post by cariboo on 2010-05-15
It may be that legally Nvidia can't open their drivers, as they are using technology that they are only licensed to use and don't own.

---

### Post by krazyd on 2010-05-15
> **cariboo907 said:**
> It may be that legally Nvidia can't open their drivers, as they are using technology that they are only licensed to use and don't own.

It's the same story with AMD - they didn't open their proprietary driver, they just released hardware specifications and employed developers to work on the open driver and X stack too.

---

### Post by screaminj3sus on 2010-05-15
> **krazyd said:**
> As the linux kernel video support advances, nvidia's driver falls further and further behind because they refuse to support the regular X software stack. 

One of the most important consequences of that is that X can't be run rootless using the nvidia driver. This is important because having X run as root is a security issue as well as a stability issue. (non-root X can't lock up your computer anymore, since it is just another userspace app)

Here is the blueprint for Maverick: [https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-maverick-rootless-x](https://blueprints.edge.launchpad.net/ubuntu/+spec/desktop-maverick-rootless-x)

and here is a good overview of the importance of non-root X: [http://lwn.net/Articles/341033/](http://lwn.net/Articles/341033/)
Yeah this is why I am now glad I have an ati card. right now both fglrx and the oss drivers arent as good as nvidia's proprietary driver, but the OSS drivers are advancing VERY rapidly and I have now switched to them. things are looking good for my ati card in the future.

---

### Post by davidmohammed on 2010-05-15
can someone confirm that the new xorg, mesa etc will leave us i8xx intel graphics users behind with just vesa support?

---

### Post by seeker5528 on 2010-05-15
> **cariboo907 said:**
> It may be that legally Nvidia can't open their drivers, as they are using technology that they are only licensed to use and don't own.

That is still a choice, not a legal requirement. It was their decision to use the same stuff as much as possible between the Windows and Linux drivers and not supply any information to opensource devs. They could maintain their own proprietary driver and still throw the open source devs a bone once in a while.

Later, Seeker

---

### Post by Catharsis on 2010-05-15
> **davidmohammed said:**
> can someone confirm that the new xorg, mesa etc will leave us i8xx intel graphics users behind with just vesa support?

Pretty sure this is just UMS. I haven't been able to find that source though, so if anyone else can....

---

