---
title: "The non-disappearing problem with laggy Flash in Ubuntu"
date: 2011-10-15
forum: Multimedia Software
---

### Post by Jeinhor on 2011-10-15
Hi there,

Well, as the title states, I've had this problem for as long as I've been using Ubuntu, on and off. In some (rare) installations, it has been working, but mostly it hasn't.

Judging by threads, posts and blog posts on the Internet, I'm not alone with this problem. It was for example recently seen again in the forum for the development version of Oneiric: [http://ubuntuforums.org/showthread.php?t=1857294&highlight=fullscreen+flash](http://ubuntuforums.org/showthread.php?t=1857294&highlight=fullscreen+flash). There's even an xkcd about it: [http://xkcd.com/619/](http://xkcd.com/619/) :D

My thought with this thread is to gather information of the cause of the problem and what solutions are out there now. Actually, I would be happy if I could just get a definite answer, like "well, it's because of graphics drivers, they aren't good enough, we can't do nothing about it" or something like that.

So,
[LIST=1]
[*]What are your experiences? Laggy flash, or no laggy flash?
[*]Does it matter what browser you use?
[*]Do you use proprietary drivers?
[*]Graphics card, is nVidia better than ATi at this?
[*]Your solution, if any?
[/LIST]

Well, these are my experiences:
[LIST=1]
[*]Laggy flash, unfortunately.
[*]No, tried both Firefox and Chrome on my current 11.10 install.
[*]Yes, nVidias latest (installed via jockey, I think).
[*]nVidia ION, the one built into Zotac HD-ND22.
[*]
[/LIST]

And then, this is one of the solutions I found on the Internet. Helped me once, hasn't helped since.

```
echo "OverrideGPUValidation=true" > ~/mss.cfg
sudo mkdir /etc/adobe
sudo mv ~/mss.cfg /etc/adobe
```

---

### Post by Henk Poley on 2011-11-08
Could audio be involved? The slow start behavior is something that appeared a while ago. It hasn't been the case since the beginning on ubuntu 10.04 on the ZBOX ND22, it appeared with a recent-ish update. 

There were other strange things with Flash though, like for example that Flash video 'shines through' other tabs  when they have the right color on the page (I believe black).

---

