---
title: "Wirless Drivers"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by Muhnamana on 2009-11-22
So I'm brand new to Ubuntu. I took my Windows XP laptop and wanted to learn Linux so installed Ubuntu. Everything installed fine but how can I get my wireless lan driver working?

Again, I'm new to this and still learning. Any help would be appreciated.

---

### Post by gnusci on 2009-11-22
Did you give a look to bapoumba's sticky:

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Give a look over there and then post some useful information so people can help you.

---

### Post by AFI420 on 2009-11-22
theres obviously a huge issue with wireless on this release

---

### Post by Muhnamana on 2009-11-22
Well I typed 
lspci -v | less

and only see Host Bridge, VGA compatible controller, Display controller and
PCI bridge controller. I see nothing about wireless internal card.

I hate to post a wireless ticket issue when I have no clue what information
I need to fill out.

---

### Post by Muhnamana on 2009-11-22
> **AFI420 said:**
> theres obviously a huge issue with wireless on this release

Lovely, so you are telling me I picked a buggy version to learn on?

---

### Post by AFI420 on 2009-11-22
so did I. I figured hey i hate windows and apple is too expensive, why not learn linux. downloaded ubuntu, as that is what my boss suggested. Now ive been dealing with this wireless adapter for a week to no avail. If you just want to play around id suggest getting Sun Virtualbox and loading ubuntu on it. it will setup network connection on its own and you can get used to navigating the OS

---

### Post by Charlietje on 2009-11-22
what does the output of following code gives?

```
lshw -class network
```

---

### Post by coffeecat on 2009-11-22
> **Muhnamana said:**
> Lovely, so you are telling me I picked a buggy version to learn on?

The poster you are responding to has posted an unhelpful, unconstructive and ill-informed comment. Ignore it. There is not a big issue with wireless in Karmic. It is true that some chipsets will be poorly supported or not supported at all, but that's inevitable in the open source world where some manufacturers seem to be actively hostile to Linux and we have to rely on  reverse-engineered drivers.

For what it's worth, I have tried 6 different wireless chipsets in Ubuntu Karmic. Only one caused a slight problem and that was solved by installing some backported kernel modules. Posting courtesy of that particular wireless device at the moment. :)

If you post the information helpful members of the community have requested, your problem may turn out to be easily solveable.

---

### Post by AFI420 on 2009-11-22
> **coffeecat said:**
> The poster you are responding to has posted an unhelpful, unconstructive and ill-informed comment. Ignore it. There is not a big issue with wireless in Karmic. It is true that some chipsets will be poorly supported or not supported at all, but that's inevitable in the open source world where some manufacturers seem to be actively hostile to Linux and we have to rely on  reverse-engineered drivers.

For what it's worth, I have tried 6 different wireless chipsets in Ubuntu Karmic. Only one caused a slight problem and that was solved by installing some backported kernel modules. Posting courtesy of that particular wireless device at the moment. :)

If you post the information helpful members of the community have requested, your problem may turn out to be easily solveable.


sorry....just frustrated with my card

---

### Post by coffeecat on 2009-11-22
> **AFI420 said:**
> sorry....just frustrated with my card

No problem. :) Sorry if I was a bit harsh, but I get frustrated when I see the enormous strides that Ubuntu and Linux have made with regard to wireless downplayed. Yes, it is enormously frustrating when your hardware doesn't work. Just try plugging it into an Apple machine and see how far you get. :wink:

Have you started your own support thread? I'll check your thread list and if so, I'll mosey over there and see if I can help.

---

### Post by AFI420 on 2009-11-22
not yet. Ive saved a list of outputs that it asks for to create a ticket, but Im at work now and wont be home for another hour. Then I have to either get the wired connection to work and upload my outputs or restart into windows and upload to the forum

---

### Post by Muhnamana on 2009-11-22
I decided to create a dual boot, Windows XP and Ubuntu. So i read you need to enable the wireless card in Windows before booting Ubuntu.

How do I go about doing that?

---

### Post by AFI420 on 2009-11-22
> **Muhnamana said:**
> I decided to create a dual boot, Windows XP and Ubuntu. So i read you need to enable the wireless card in Windows before booting Ubuntu.

How do I go about doing that?

i use zero config on xp. the linksys software is crap and bogs the system

---

### Post by Muhnamana on 2009-11-22
> **AFI420 said:**
> i use zero config on xp. the linksys software is crap and bogs the system

Im not using any linksys product. Its a built in Broadcom card.

---

### Post by SteveHillier on 2009-11-22
I have not tried 9.10 desktop with wireless but I did install 9.10 UNR (laptop version) only a couple of weeks ago and it connected wirelessly without any problem.
The laptop I used was an Acer Travelmate 4060WLMi with an Intel PRO/Wireless 2200BG wireless adapter.
This worked so well that last night when I was trying to log in to my router wired (Oh BTW I have 2 routers and 2 bb lines by me) I put the cable into the Ethernet connector which connected to 192.168.0.x and then used the address range for the second router (192.168.1.x) to which I was connected wirelessly - and then wondered why I could not get access to the correct router.  Took me ages to work out what a dumbo i was.
But to the OP, please don't listen to the siren voices I am sure there is an answer out there.

---

### Post by coffeecat on 2009-11-23
> **Muhnamana said:**
> Im not using any linksys product. Its a built in Broadcom card.

You still haven't posted the information other posters suggested, but if it's a Broadcom card, then go to System > Administration Hardware Drivers and see if it is offering to install the Broadcom driver/firmware for you.

---

### Post by Muhnamana on 2009-11-23
Solved. See [link]("http://ubuntuforums.org/showthread.php?t=1334659"). I ended up doing a dual boot but what schim posted in post #4, worked beautifully.

---

