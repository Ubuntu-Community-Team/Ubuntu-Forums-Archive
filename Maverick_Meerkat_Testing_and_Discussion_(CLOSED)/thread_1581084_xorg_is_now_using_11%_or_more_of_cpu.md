---
title: "xorg is now using 11% or more of cpu"
date: 2010-09-24
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-09-24
Since I upgraded to MM the top process is now xorg, whereas in Lucid xorg virtually never appeared. When the pc is at idle xorg now uses about 11% of cpu. It can momentarily go up to about 33% when opening something. This seems very high to me. Has anybody noticed anything similar? I'm wondering if it's the newer nvidia driver at the root of it.

---

### Post by whoop on 2010-09-24
Mine is 7% idle and about 20% when drawing a new window. So that seems comparable...

---

### Post by Quackers on 2010-09-24
Ok, thanks. Mine used nothing like that much in Lucid, but that was with a different driver. I'll wait and see what happens with the new release.

---

### Post by VinDSL on 2010-09-25
We're talking CPU usage, yes?

I watched top during idle, and Xorg was mostly 1% (occasionally spiking to 2-3% momentarily).

With this browser open (Google Chrome) it's motorboating between 2-6%.

---

### Post by Quackers on 2010-09-25
Yes CPU usage.
I'm using Firefox and in Lucid xorg never seemed to get past 1 or 2% cpu usage. So it's much higher in MM.  However MM "forced" me to use the newer nvidia driver as it seems to be the only one available?? and I'm wondering if that is the cause. Of course all this may disappear after MM'2 release - hopefully :-)

---

### Post by VinDSL on 2010-09-25
> **Quackers said:**
> [...]MM "forced" me to use the newer nvidia driver as it seems to be the only one available?? and I'm wondering if that is the cause.[...]I'm using the nVidia 260.19.06 beta driver.

Works very nicely...  ;)

BTW, I like your sig.  I copied the idea!

---

### Post by Quackers on 2010-09-25
Ha! No problem. It comes from a MacOSX86 type forum, where if your hardware isn't listed in your sig you don't get help, lol.

---

### Post by VinDSL on 2010-09-25
> **Quackers said:**
> Ha! No problem. It comes from a MacOSX86 type forum, where if your hardware isn't listed in your sig you don't get help, lol.Yeah, I've seen this type of sig, over the years, on various boards.  I usually consider it bragadocious, but...

I can see where it would serve a useful purpose on this forum.

As an aside, your nick reminds me of a story.  I had a friend that used to delivery meat and poultry to restaurants.  One day, his boss told him he needed to make an emergency delivery of ducks to a 5-star French restaurant.  They were out.  He told him not to talk to the chef -- not a word.  Just make the delivery and leave.

When my friend made the delivery, he said the chef seemed okay, so he said, "I guess you can't make duck soup without the quackers."

The chef replied, "Oh, so you want to make zee joke, eh?"  And, chased him out of the kitchen.

By the time he returned to the market, the chef had called the owner and ripped him a new one.  My friend said he almost got fired that day. LoL!

Anyway, back on topic...  :D

---

### Post by Quackers on 2010-09-25
Yes, I have to be careful when passing the butchers shop!

I just installed all the latest updates which included nvidia current stuff and although I had some scary moments on reboot, it did boot fine. Xorg is still using 11% at idle and up to 35% when doing things.

---

### Post by Quackers on 2010-10-01
I have just run the latest updates which included some nvidia bits and bobs and I am pleased to report that xorg is now running at about 1% of cpu usage at idle. That's what it used in Lucid, so I will be pleased to mark this thread solved :P
=D>=D>=D>=D>=D>=D>

---

### Post by VinDSL on 2010-10-02
According to *Top*, sitting idle, at my desktop, Xorg is using 1% CPU... occasionally spiking to 2%... but mostly 1%.

I guess they fixed it...  :)

---

### Post by Quackers on 2010-10-02
Yes. It looks a lot happier at 1% than 11%. Temperature is better too (about 8 degrees lower!) :-)

---

