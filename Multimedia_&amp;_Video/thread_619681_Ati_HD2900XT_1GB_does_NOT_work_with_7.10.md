---
title: "Ati HD2900XT 1GB does NOT work with 7.10"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by araaran on 2007-11-21
Just for everyones information really. I have spent 3 days trying to figure this one out and I found the answer in a rather obscure 1 line sentence in an install guide. RTFM indeed, but Im dyslexic and finding that one line was like a needle in a haystack.

Its official.
**[SIZE="2"]Ubuntu/gutsy 7.10 does not work the ATI's 8.42.3 version driver.[/SIZE]**

I booted X to a blank screen - a known problem.

I now have installed Ubuntu/feisty 7.04 and it works fine with my Ati HD2900XT 1GB card.
I installed the drivers using the following method as Envy did not work for me :(

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by aoanla on 2007-11-21
...yes, it does. I have Gutsy (64bit Gutsy, no less) working with 8.42.3 *right at this moment*, with an X1950 Pro.
The blank screen problem is obscure, but appears to be due to old versions of the fglrx kernel object hanging around on your system after installing new drivers, leading to conflicts.

Ironically, the new Catalyst 7.11 fglrx driver released today (yes, they changed the version numbers) claims better support for Gutsy anyway, so you'd probably have better luck with it if you'd not just downgraded...

---

### Post by araaran on 2007-11-22
> **aoanla said:**
> Ironically, the new Catalyst 7.11 fglrx driver released today (yes, they changed the version numbers) claims better support for Gutsy anyway, so you'd probably have better luck with it if you'd not just downgraded...

...ahhh Poo. Well Evolution will not start and I still have two days of holiday left. Maybe I will try Gutsy again.

thanks for replying :)

---

