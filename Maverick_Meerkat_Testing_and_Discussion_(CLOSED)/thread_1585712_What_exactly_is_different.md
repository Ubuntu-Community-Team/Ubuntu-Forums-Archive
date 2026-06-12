---
title: "What exactly is different?"
date: 2010-09-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mamamia88 on 2010-09-30
I just upgraded from lucid and can't really see any significant changes. So what is cool in this release I should check out?

---

### Post by snowpine on 2010-09-30
The biggest difference is that every application in Ubuntu 10.10 is approximately 6 months newer than 10.04. :)

---

### Post by Rob2687 on 2010-09-30
There was that news this summer about a patent expiring so does that mean that bytecode font rendering enabled?

---

### Post by dagrump on 2010-09-30
I really couldn't say, some under the hood changes. It could have some cosmetic changes, to the default.
It's been a relatively smooth ride here. 
Lot of things are really more influenced your hardware choices, than anything else.

---

### Post by 23dornot23d on 2010-10-01
All the information is [**here on Maverick**]("https://wiki.ubuntu.com/MaverickMeerkat/TechnicalOverview")

But the things that I have noticed as we have gone through development ...

Touchscreen - mobile support - 64 bit ....... 
Graphics Driver Changes .....
Speed of boot up and shut down .....
Wireless changes ...

( 2 backward steps ... for me ...... and my Acer Aspire 7730 ZG Laptop )

Wizardpen no longer working and sound is not picking up so I have to alter a file to get it to work.

But other than that ..... the devlopers have a [[COLOR=Blue]_**list ..... of blueprints**_[/COLOR]]("https://blueprints.launchpad.net/ubuntu/maverick/+specs?show=all")

---

### Post by dagrump on 2010-10-01
Oh it hasn't fixed 23dornot23d keyboard, It still has that sticky dot, dot,dot,dot key!

---

### Post by 23dornot23d on 2010-10-01
ah ah  lols ..........................:)  ........................ :guitar:

---

### Post by areteichi on 2010-10-01
> Over the last week, I've been playing around with the beta of the forthcoming Ubuntu release - Maverick Meerkat or version 10.10 - which is scheduled to be officially unveiled on October 10.

And I have just one question to ask: why is it being released at all? What major changes  are present to justify an upgrade? If all that the new version has to show is incremental changes in version numbers of major applications, why is there the need for so much hoo-haa?

Is Canonical, the company behind Ubuntu, guilty of becoming a prisoner of its own hype, and unable to revert to some kind of commonsenical schedule that would reflect the correct state of affairs?

[http://www.itwire.com/opinion-and-analysis/open-sauce/42082-ubuntu-1010-a-meaningless-release](http://www.itwire.com/opinion-and-analysis/open-sauce/42082-ubuntu-1010-a-meaningless-release)

---

### Post by MishaAct on 2010-10-01
> **mamamia88 said:**
> I just upgraded from lucid and can't really see any significant changes. So what is cool in this release I should check out?
Bug with advanced A4tech mouses, laggy nvidia proprietary driver, even more laggy opensource driver. Hm, I like ubuntu fonts @ 9pt and no hinting. The default configuration (10pt and slight hinting) is ugly. Liberation is better choice for this size and hinting settings. Unfortunatelly, 9pt configuration is only usable at monitors with large pixel size (19@1280x1024, 22@1680x1050, etc. It's too tiny at my home 20@1600x1200). Tomboy is better when combining Left and Right click menus in one indicator menu. Gdebi gui was replaced with USC, which is ever stupid solution IMO since the latter is one of the most clunky software ever did. The theme was much better within interim iterations than today. Todays one reminds me a girl at my job, she's beautiful but looks a little too vulgar just like the latest theme variant ))

Empathy can merge contacts from different addresses and protocols. gnome-terminal can find a text, but the gui for this is so inconvenient they would better use grep. Most upstream changes are minor one.

---

### Post by Rob2687 on 2010-10-01
> **areteichi said:**
> [http://www.itwire.com/opinion-and-analysis/open-sauce/42082-ubuntu-1010-a-meaningless-release](http://www.itwire.com/opinion-and-analysis/open-sauce/42082-ubuntu-1010-a-meaningless-release)

This guy should just skip every other release or use every 3rd release if he really wants that 18 month cycle.

---

### Post by teh603 on 2010-10-01
My Inspiron 1564 (i3/Arrandale) now resumes from Suspend/Hibernate without needing a patch from a PPA. Most other i3 laptops should be able to resume as well.

The option to manually check for updates seems to have been removed from kpackagekit.

And that guy from itwire.com needs to go stuff himself.

---

### Post by randomizer101 on 2010-10-01
2.6.33 was the first kernel version that properly supported the ATA TRIM command, so if I am planning on running Ubuntu on my SSD (which currently holds Windows since it benefits more from the speedup) I have every reason to upgrade. Of course I can just upgrade the kernel. I personally didn't find Maverick to be a groundbreaking release while testing it in a VM, and my thoughts echo those of the itwire author to some extent.

Is it worth upgrading? Perhaps. Will you be missing alot? Probably not.

---

### Post by inportb on 2010-10-01
Well, let's see... proper touch support for my netbook is nice.

---

### Post by qamelian on 2010-10-01
It runs much nicer on my aging laptop than any release since Breezy. Lucid in particular tended to make my laptop runmuch hotter under load than I was comfortable with, actually causing it to frequently shutdown from over-heating. No such issues so far with Maverick!

---

### Post by inportb on 2010-10-01
I just noticed the new UI font, and I think it's quite nice.

---

### Post by MishaAct on 2010-10-01
> **qamelian said:**
> It runs much nicer on my aging laptop than any release since Breezy. Lucid in particular tended to make my laptop runmuch hotter under load than I was comfortable with, actually causing it to frequently shutdown from over-heating. No such issues so far with Maverick!
It runs the same with lucid at my home PC, but very slow at my job. The 12309 feels too much (Intel 965 chipset).

---

### Post by MishaAct on 2010-10-01
> **inportb said:**
> Well, let's see... proper touch support for my netbook is nice.
This thing is untested. BTW, it causes many bugs. The perfect example is the bug with permanent keyboard layout switching. Another example is A4Tech X7** left button bug. In my opinion these bugs are both stoppers, it would be very strange to release 10.10 before fixing them.

---

### Post by andrewabc on 2010-10-01
> **randomizer101 said:**
> 2.6.33 was the first kernel version that properly supported the ATA TRIM command, so if I am planning on running Ubuntu on my SSD (which currently holds Windows since it benefits more from the speedup) I have every reason to upgrade. Of course I can just upgrade the kernel. I personally didn't find Maverick to be a groundbreaking release while testing it in a VM, and my thoughts echo those of the itwire author to some extent.

Is it worth upgrading? Perhaps. Will you be missing alot? Probably not.

The sad part is that apparently to get TRIM working you need to add -discard to fstab.

So there will be a lot of angry people who were told TRIM works with this release, but you have to enable it by editing a config file. And I'm sure lots of people expect it to work by default, and will not know the difference and their SSD will be slower and have less life because of it.

---

### Post by VMC on 2010-10-01
> **Rob2687 said:**
> This guy should just skip every other release or use every 3rd release if he really wants that 18 month cycle.

The first comment on that link tells it all. Also, he didn't even mention the new Xorg Xserver 1.9, that made for faster boot times. At least, that's what I experienced.

---

### Post by psusi on 2010-10-01
> **andrewabc said:**
> And I'm sure lots of people expect it to work by default, and will not know the difference and their SSD will be slower and have less life because of it.

Except that in practice, it doesn't actually make any noticeable difference.

---

### Post by cariboo on 2010-10-01
> **MishaAct said:**
> This thing is untested. BTW, it causes many bugs. The perfect example is the bug with permanent keyboard layout switching. Another example is A4Tech X7** left button bug. In my opinion these bugs are both stoppers, it would be very strange to release 10.10 before fixing them.

Have you created bugs for your problems, the devs can't fix a problem if they don't know about it.

---

### Post by alaukikyo on 2010-10-01
A 6 month release cycle means more evolution than revoution the os keeps getting better and better and you get all the betterments quickly!!
if you want to see revoutions then download the ubuntu 7.10 iso and compare it with the final maverick release i am sure you will find it a better changes than xp-> vista or vista->7!!

---

### Post by MishaAct on 2010-10-01
> **cariboo907 said:**
> Have you created bugs for your problems, the devs can't fix a problem if they don't know about it.
They did of course. But canonical guys don't consider them as important since most of them are english speaking and both these bugs refers to switching layout.

---

### Post by psusi on 2010-10-01
> **MishaAct said:**
> They did of course. But canonical guys don't consider them as important since most of them are english speaking and both these bugs refers to switching layout.

While they all do speak english, it isn't everyone's native language.

---

### Post by andrewabc on 2010-10-01
> **psusi said:**
> Except that in practice, it doesn't actually make any noticeable difference.

Benchmarks prove otherwise.

[http://www.anandtech.com/show/2829/15](http://www.anandtech.com/show/2829/15)
[http://www.anandtech.com/show/2865/2](http://www.anandtech.com/show/2865/2)
[http://www.anandtech.com/show/3681/oczs-vertex-2-special-sauce-sf1200-reviewed/4](http://www.anandtech.com/show/3681/oczs-vertex-2-special-sauce-sf1200-reviewed/4)

Explanation of TRIM
[http://www.anandtech.com/show/2738/10](http://www.anandtech.com/show/2738/10)

There are lots of other benchmarks to show the benefits of TRIM.

[img]http://images.anandtech.com/reviews/storage/OCZ/Vertex2/oczvertex2-afterrandomsequentialthenrandomwrite.jpg[/img]
[img]http://images.anandtech.com/reviews/storage/OCZ/Vertex2/oczvertex2-afterrandomsequentialthenrandomwrite-TRIM.jpg[/img]
Yep, no difference there before and after TRIM. :rolleyes:

---

### Post by cariboo on 2010-10-01
> **MishaAct said:**
> They did of course. But canonical guys don't consider them as important since most of them are english speaking and both these bugs refers to switching layout.

Bug numbers?

---

### Post by psusi on 2010-10-01
Benchmarks != in practice.

For it to matter you first have to write to every block on the disk, which doesn't tend to happen very often under normal use.

---

### Post by mamamia88 on 2010-10-01
so far the only difference i've noticed is the pretty theme and a few cool wallpapers

---

### Post by MishaAct on 2010-10-01
> **cariboo907 said:**
> Bug numbers?
[https://bugs.launhpad.net/indicator-application/+bug/625793](https://bugs.launhpad.net/indicator-application/+bug/625793)
[https://bugs.launchpad.net/udev/+bug/637208](https://bugs.launchpad.net/udev/+bug/637208)

---

### Post by MishaAct on 2010-10-01
[http://blogs.gnome.org/sudaltsov/2010/08/20/keyboard-indicator-in-ubuntu-10-10-disclaimer/](http://blogs.gnome.org/sudaltsov/2010/08/20/keyboard-indicator-in-ubuntu-10-10-disclaimer/)

---

### Post by andrewabc on 2010-10-01
> **psusi said:**
> Benchmarks != in practice.

For it to matter you first have to write to every block on the disk, which doesn't tend to happen very often under normal use.

But over time if no TRIM is done, eventually wouldn't many blocks get written to, thus you would see a performance loss?

I know those benchmarks are for worst case scenario. It's a quick way to show what TRIM can do. They are not going to wait 12 months of normal usage and then do a review of enabling TRIM and how it affected performance.

I mean if they did the "write to every block test", but don't perform TRIM, does performance improve on its own (assuming no garbage collection either)? As far as I know it wouldn't (in the case of Indilinx/Intel drives).

---

### Post by psusi on 2010-10-01
Performance doesn't degrade until (almost) every block has been written to.  Eventually it may happen, so trim is all well and good, but people worry about it far more than they should.

---

### Post by andrewabc on 2010-10-01
> **psusi said:**
> Performance doesn't degrade until (almost) every block has been written to.  Eventually it may happen, so trim is all well and good, but people worry about it far more than they should.

It's in the kernel, and as far as I know there are no downsides to it, so why ubuntu can't detect SSD and enable it by default I don't know.

---

### Post by psusi on 2010-10-01
> **andrewabc said:**
> It's in the kernel, and as far as I know there are no downsides to it, so why ubuntu can't detect SSD and enable it by default I don't know.

The upstream kernel developers felt that since it is not yet well tested, it could silently destroy your data, so they left it off by default.

---

### Post by randomizer101 on 2010-10-01
> **psusi said:**
> Performance doesn't degrade until (almost) every block has been written to.

Which can happen before you fill the drive to capacity even for the first time.

---

### Post by Baul on 2010-10-02
> **alaukikyo said:**
> A 6 month release cycle means more evolution than revoution the os keeps getting better and better and you get all the betterments quickly!!
if you want to see revoutions then download the ubuntu 7.10 iso and compare it with the final maverick release i am sure you will find it a better changes than xp-> vista or vista->7!!

How right you are!:)

---

