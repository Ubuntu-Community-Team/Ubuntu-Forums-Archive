---
title: "DivX for Linux - Ubuntu codec packages"
date: 2008-09-16
forum: Multimedia Software
---

### Post by zolero on 2008-09-16
Halihoha.

I've created two divx4linux packages from the latest binary releases from DivX.com and I like to share them with this beloved community.

The very latest release (version 6.1.1 from 2006.01.26) follows Windows variants quality and is highly recommended.

The second one (version 5.1 from 2003.04.28 ) is a rare piece. That's the reason why I've posted it too. It is very useful when one need to compile something with divx4linux capability enabled (provides the encore2.h header file), for example other media apps which relying on this codec's API (such as Zapping TV viewer).

Also grab them from here:[INDENT][divx4linux6_6.1.1_20060126_zolerubuntu1_all.deb]("http://rapidshare.com/files/145654471/divx4linux6_6.1.1_20060126_zolerubuntu1_all.deb")
[divx4linux5_5.1_20030428_zolerubuntu1_all.deb]("http://rapidshare.com/files/145654562/divx4linux5_5.1_20030428_zolerubuntu_all.deb")
[/INDENT]Enjoy... 8-)  :lol:

---

### Post by eye208 on 2008-09-16
I'm curious: Is there any reason to use the proprietary DivX codec instead of the open source Xvid one? Has there ever been a codec comparison test that did not prove Xvid superior to DivX? Has there ever been a "DivX compatible" standalone MPEG-4 player that could not be tricked into accepting Xvid-encoded files simply by replacing the AVI header FourCC "XVID" with "DX50"?

---

### Post by zolero on 2008-09-16
You're right about Xvid quality **eye208**. But even so, there're pieces of code which ***expressely needs*** to have the proprietary codec headers to compile and work. In other words: it can't be harmful or wrong to have these.

For just in case, that somehow they were requested and since that's the situation, I've provided them in their distro's native package format for those of us, who need and want these. If you don't need them, please simply ignore my post.

---

