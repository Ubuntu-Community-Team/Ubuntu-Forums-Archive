---
title: "mesa3d problem"
date: 2006-09-25
forum: Multimedia &amp; Video
---

### Post by ego_brain on 2006-09-25
hi. i'm very sorry it had to come to me writing this... but i followed every howto i could find on installing fglrx...but no sucess.

no matter which driver i install, fglrxinfo says:
```
egobrain@egobrain-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

```

any help would be apreciated!

l.p.  Domen

---

### Post by WalmartSniperLX on 2006-09-25
Try this

log out, and in the xserver select to restart the xserver, and load back into your session

Also reinstalling the driver helps

Also did the howto you used tell you to recompile the kernel after the update?

---

### Post by WalmartSniperLX on 2006-09-25
I used this

[http://www.ubuntuforums.org/showthread.php?t=204910](http://www.ubuntuforums.org/showthread.php?t=204910)

and make ure you have all the repositories open first. Goto System/Admin/Software Properties and check off all the boxes


Make sure you change the name of the driver in the tutorial to the driver ver. you downloaded

---

### Post by ego_brain on 2006-09-27
well i did everything... i'm just not sure how to recompile the kernel... "depmod -a"? i tried the howto you posted...but no go...tnx anyways!

Domen

---

### Post by podunk on 2006-09-27
I've decided ATI cards are just junk. Actually it's not the cards, my ATI card works good in Windows - it's ATI's commitment to support a significant percentage of their customers when they chose to exercise their freedom of choice.

 I have a *very* old Nvidia card and installing the driver and getting compiz set up was a piece of cake. It runs glxgears pretty slow compared to the output I read others have - but it does run it. I have a fairly new ATI card - Radeon 9200 and I can't get the ATI driver to work.

Reading these forums folks post needing help with Nvidia and it's a short thread. ATI posts go on for page after page. :-)

And it's really silly. If ATI would release their source code I bet there are tons of Linux gurus who would jump all over it and whip out a driver in no time flat. Since however there are licensing issues ATI can't do that - which is OK - but what is not OK is for them to release junk Linux drivers that don't fully implement their hardware.

I wrote a very polite letter to the CEO of ATI and told him that I had been a very loyal ATI customer, 5 of the 6 video cards I have bought were ATI, but due to driver problems with their card in Linux I was going to have to switch to Nvidia. His address is:

David Orten
ATI RESEARCH, INC.
62 Forest Street
Marlborough, Massachusetts
U.S.A. 01752

As long as we keep buying ATI cards or just quietly switch brands nothing will change.

I'm not intelligent enough to write software, so I'll never be able to help the Linux community in that way. One of the things I can do though is vote with my wallet, and make sure the companies I vote against know the reasons I didn't buy their product.

---

