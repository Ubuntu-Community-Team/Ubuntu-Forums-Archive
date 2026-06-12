---
title: "Recent ubuntus ans wireless: a difficult marriage"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by franzmaximilian on 2010-03-18
Having both a USB dongle and a PCI card that should work with Linux but actually don't on a Kubuntu Karmic, I have been reading extensively through this and many other forums (also in other languages).

Apart from some "historically impossible" chipsets, i have seen very few success stories, while there is a lot of people who experiences regression (i.e. their wireless used to work on older versions).
What is worst for many many users is that there is apparently nothing wrong in their settings and some, like me, can even see the networks but not connect to them.

A few could solve their problems and get a connection using workarounds that do not explain what was wrong in their configurations or settings. After attempting many different solutions some were lucky, while some with the same cards didn't succeed.

I have two laptops with Kubuntu Karmic installed and connecting to wireless flawnlessly. Both where updated from 8.04 to 9.10.
The problematic one is a brand new desktop, with 9.10 as it's first OS installed.  Could this mean anything? I don't know.

All in all, I suspect that the real problem is NOT in our cards, dongles or settings. It must be somewhere inside Ubuntu. I don't know if it is the kernel, the network manager, some obscure service or what else: I am not qualified to tell.
All I know is that my USB dongle worked on older distributions (different than Ubuntu) out of the box. And that my PCI card is Linux certified on its carton box and reported as working in Ubuntu docs.

I wish to urge some REAL expert to have a look at the present Ubuntu - Wireless situation with a wide sight, not focusing on a single problem, but trying look behind. My guess is that a solution could be find at some unexpected place...

The only contribution I can offer is testing whatever may come out of all this. I have no programming skills at all.

Thank you all for your attention.

Franz

---

### Post by doas777 on 2010-03-18
my best advice is check mad-wifi compatibility for your card. if it passes their tests, then buy it. otherwise...
one of the issues may be the ongoing feud between teh kernel devs and the folks that use ndiswrappers. the kernel devs don't want tainted code to have the same access to kernel functions that fully open modules do.

---

### Post by chili555 on 2010-03-18
> i have seen very few success storiesI have; you have evidently not read far enough. Moreover, almost no one comes to the forum to post that their card works perfectly, although there are even a few of those.

I have used five different wireless cards in my Ubuntu experience, all worked perfectly and only one needed ndiswrapper.

We're not likely to know the real ratio of working vs. not working. We are also not helped by chipset manufacturers who come out with a new chipset almost monthly and steadfastly refuse to provide drivers for Linux.

Not to be too blunt about this subject, but there is also a lot of user error here; wireless switch was off, didn't know about System > Administration > Hardware Drivers, and even didn't know about the Network Manager icon, and even more.

Now, do I think wireless is just fine? No. Do I think it's as dire as you seem to imply? Also, no.

---

### Post by alexfish on 2010-03-18
Hi

a better place for this is here 

[http://ubuntuforums.org/forumdisplay.php?f=103](http://ubuntuforums.org/forumdisplay.php?f=103)

however  reading and learning from these forums will develop your programming skills

then someday you to will be able to pass on this Knowledge

regards

alexfish

---

### Post by franzmaximilian on 2010-03-18
> **chili555 said:**
> I have; you have evidently not read far enough. Moreover, almost no one comes to the forum to post that their card works perfectly, although there are even a few of those.

I have used five different wireless cards in my Ubuntu experience, all worked perfectly and only one needed ndiswrapper.

We're not likely to know the real ratio of working vs. not working. We are also not helped by chipset manufacturers who come out with a new chipset almost monthly and steadfastly refuse to provide drivers for Linux.

Not to be too blunt about this subject, but there is also a lot of user error here; wireless switch was off, didn't know about System > Administration > Hardware Drivers, and even didn't know about the Network Manager icon, and even more.

Now, do I think wireless is just fine? No. Do I think it's as dire as you seem to imply? Also, no.

I have no will to be polemic, really. And i must say that I have seen lots of your posts in this forum, all full of good will to be of help and offering high quality contributions.  And you are possibly right that not everybody comes back to the forums to say "it's ok now, thank you guys".
I also agree that many are just user errors. In his career, any service engineer has been called to run urgently to a customer, only to find an unplugged device.
I also know that chipset manufacturers do not provide information or drivers and that reverse engineering requires tremendous efforts to che community. I am fully aware of all that. And finally I said already that I have two cheap laptops equipped with Karmic and connecting nicely throug their internal Wifi cards.

What I wanted to point out is that too many users experience difficulties that should not be there. If a user can use a given card out of the box and another cannot manage to connect with exactly the same card (same revision, same OS, same everything) something must be wrong somewhere.
If my USB dongle works just fine if inserted in a friend's Suse 11.1 and refuses to connect in my Karmic, something must be wrong. If many (too many) seek help because their cards used to work on previus releases of Ubuntu, but not in the most recent ones, something must be wrong. But not the users.
My knowledge and experience is in different fields than microelectronics and software. I can only argue that the only difference that may cause a card to work on compuer A equipped with Karmic and fail on computer B equipped with Karmic is the hardware differences between A and B. Why that? I don't know. It could be a poor hardware implementation that only reveals when wireless instruction flow through the system components, or a poor kernel or module implementation of some low level task or the effect of moon tides or a spell cast by a luddist on some boards. I don't know. I only know that a card or a dongle that works for some out of the box, should work for everybody with the same OS.

Again, warm thanks to you and to all those who contribute to this wonderful community.

Franz

---

### Post by franzmaximilian on 2010-03-20
A confirmation that things happen randomly:

Since my last attempt to have the PCI wireless card connect to a network (which was seen by the card), I have switched on the computer a couple of times, only to work on Open Office. I didn't modify any setting, nor made any upgrade.
Well, today I swiched on again and the miracle happened: the card conncted BY ITSELF as soon as boot was completed!  :o

I should be happy of this, and I am in some way, but I can't rely on something that happens or not without intervention. Will it connect tomorrow? And next week?

What if one day I'm back to viewing the presence of the network but cannot connect to it?  I haven't the faintiest idea of what is really happened inside my PC today, so I will not be able to do anything but reboot and pray...

---

