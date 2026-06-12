---
title: "Wrong ATI driver after Install, Cannot Start x server"
date: 2006-09-16
forum: Multimedia &amp; Video
---

### Post by Darkling on 2006-09-16
For almost as long as I can remember, I have never been able to install a Linux distro, and have it work immediately. The problem is always the same, Cant Start x, and the solution always works, change the driver in the device section of xorg.conf to radeon instead of ati.

I have had this problem on an ATI 9600XT(AGP) on a P4 and Athlon XP, a X600(PCIE) on an Athlon 64 and a X800GTO(PCIE) also on an Athlon 64. I have also seen countless posts on various forums for various distro's with exactly the same problem.

This has been going on for years now, and I have seen it with so many different systems, that it simply cant be my fault.

I am certain that I am not alone, how many other people have this problem?

---

### Post by pay on 2006-09-17
I had that problem with my x800GTO but not my 9600xt...

---

### Post by wpshooter on 2006-09-17
I have a similar problem on 3 of my 4 machines that are all using various ATI video cards.

My machines do not refuse to start X but I get **out of range** messages on all of the machines except the one that is running the oldest card, a Radeon 7000.

I have to install FGLRX and then go in and edit xorg.conf from ATI to FGLRX for the video card section and I am good to go.

But as you say, as old as most of these ATI cards of mine are you would think that this would have been fixed by now.

Good luck.

---

### Post by the fish on 2006-09-17
> **wpshooter said:**
> I have a similar problem on 3 of my 4 machines that are all using various ATI video cards.

My machines do not refuse to start X but I get **out of range** messages on all of the machines except the one that is running the oldest card, a Radeon 7000.

I have to install FGLRX and then go in and edit xorg.conf from ATI to FGLRX for the video card section and I am good to go.

But as you say, as old as most of these ATI cards of mine are you would think that this would have been fixed by now.

Good luck.

i have a radeon 7000 how do i make it work

---

