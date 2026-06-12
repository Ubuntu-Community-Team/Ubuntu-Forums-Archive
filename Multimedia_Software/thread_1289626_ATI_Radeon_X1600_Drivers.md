---
title: "ATI Radeon X1600 Drivers"
date: 2009-10-12
forum: Multimedia Software
---

### Post by olihawes on 2009-10-12
Hi, I'm new to Ubuntu, and I'm trying to get drivers for my graphics card to install. I've downloaded them from the ATI website, and tried to execute the .run file with this command:

```
sudo bash ati-driver-installer-9-3-x86.x86_64.run
```

It goes fine, and even comes up with a title, but then always gives me this:
```
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-11-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.girakh

```

The graphics card is an ATI Radeon X1600, in a 17" Intel iMac. I've tried it in 9.04 and 9.10, both virtualised in VirtualBox with Mac OS 10.6.1 as host OS, and both with the same error.

Thanks in advance for any help =D

---

### Post by ssri on 2009-10-13
1) Catalyst 9.3 will only work with Xserver v1.5.2, not v1.6.x and above.  So, you may have to downgrade your Xserver ([http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue))

2) Catalyst 9.3 only supports kernels 2.6.28 and below.  There is a patch for 2.6.29 [([http://aur.archlinux.org/packages.php?ID=25105](http://aur.archlinux.org/packages.php?ID=25105));([http://www.linuxquestions.org/questions/linux-hardware-18/fglrx-9.3-patch-for-2.6.29.x-kernel-722858/](http://www.linuxquestions.org/questions/linux-hardware-18/fglrx-9.3-patch-for-2.6.29.x-kernel-722858/))].  In short, best to stick with the opensource drivers for your environment.

---

### Post by olihawes on 2009-10-13
Ah, thank you. I didn't realise there where open-source drivers.

I've downloaded one from x.org, but I am unsure of how to install it. There doesn't seem to be any form of executable file, and there aren't any instructions either.

Sorry for being useless =P

---

### Post by morrie on 2009-10-13
I posted to a thread here about that error:
[http://ubuntuforums.org/showthread.php?t=1288652](http://ubuntuforums.org/showthread.php?t=1288652)

(Solved the error, but the install still failed).

Maybe you can get it to work and tell me how?

I have a Radeon X1650(AGP).

After my attempt, I rebooted to find that the screen was unviewable and had to start from scratch (with Open Source drivers).

Trying to fix a problem where the screen "sleeps" during movies and games after about 10-20 min. (without PM and screensaver on)  and goes unrecoverable.

---

### Post by mcduck on 2009-10-13
> **olihawes said:**
> Ah, thank you. I didn't realise there where open-source drivers.

I've downloaded one from x.org, but I am unsure of how to install it. There doesn't seem to be any form of executable file, and there aren't any instructions either.

Sorry for being useless =P

You don't have to do anything to use the opensource drivers. They are used by default.

---

### Post by olihawes on 2009-10-14
> **mcduck said:**
> You don't have to do anything to use the opensource drivers. They are used by default.

Sorry, I don't understand.

At the moment, I have a folder containing the drivers sitting in my home directory. How do I get Ubuntu to use it as a driver? Do I just need to place it in a certain location?

Again, sorry for being hopeless.

---

### Post by mcduck on 2009-10-14
When you install Ubuntu it will automatically use the opensource drivers for your graphics card. They come on the install disk, and are enabled by default. You don't need to download them, or do anything to use them. You are already using them.

---

### Post by olihawes on 2009-10-18
Oh right! Thanks for that =)

OK, then I have a new problem - why can't I run Ubuntu at full 1440x900 resolution?

---

### Post by websvc on 2009-12-18
You should not have to do any thing. 
I'm using an ATI x1600XT 256Mb with 2 Acer 19" running at 1440x900 in dual view. 

I was looking on how to install the ATI drivers, but it seems it's better to stay put! 

Cheers

---

### Post by waynefoutz on 2009-12-18
Welcome to my hell. I have ATI Radeon x1270. If you install Intrepid (8.10) instead of Karmic, you can get Catalyst 9.3 running fine, no, not fine, BEAUTIFUL. ATI stinks, this is their fault. They made the video system in my one year old laptop obsolete 3 months after I purchased it.  You need xorg-xserver 1.5.2 or lower running, which is what Intrepid is using. Problem is Intrepid becomes obsolete in April. The latest kernel update was supposed to fix this, the open source drivers were going to be improved. It failed miserably in my opinion.2d and Compiz work fine, but no 3d.  Hopefully the next build will have better open source drivers. In the meantime, I'd go with intrepid, or what I plan on doing is abandoning Ubuntu all together for the time being and installing Debian 5.0. It has a compatible xorg for the ATI drivers.

---

### Post by osirisgothra on 2013-02-13
> **waynefoutz said:**
> Welcome to my hell. I have ATI Radeon x1270. If you install Intrepid (8.10) instead of Karmic, you can get Catalyst 9.3 running fine, no, not fine, BEAUTIFUL. ATI stinks, this is their fault. They made the video system in my one year old laptop obsolete 3 months after I purchased it.  You need xorg-xserver 1.5.2 or lower running, which is what Intrepid is using. Problem is Intrepid becomes obsolete in April. The latest kernel update was supposed to fix this, the open source drivers were going to be improved. It failed miserably in my opinion.2d and Compiz work fine, but no 3d.  Hopefully the next build will have better open source drivers. In the meantime, I'd go with intrepid, or what I plan on doing is abandoning Ubuntu all together for the time being and installing Debian 5.0. It has a compatible xorg for the ATI drivers.


EXACTLY what i was thinking as well... ATI/AMD does do this and it's their dirty scheme to keep people buying new video cards. X1600 and simmilar are actually still capable of VERY good performance... but ATI/AMD does not wish us to be content, that doesnt make them money. So, they make it obsolete by not releasing new drivers that are updated, not implementing support for OpenGL 2+, and if you use windows at all you'll notice no DX10 support either... as for the opensource, they are just following suit and because its not supposed to be private developers job to keep up on the updates of older hardware (not to mention, not getting paid to do so) they would expect AMD to take care of their long-time loyal customers. god forbid that, you buy a video card that is "top of the line" and by the time you get it home it's obsolete. Who here remembers the 3dfx voodoo# fiasco... talk about disappointing.. but atleast it got picked up by other developers a little, but by that time we all went to nvidia and ati.. oh well.. anyone know if nvidia has these caveats? i havent upgraded my video card for fear of the instant obsoleteness of a 300$+ purchase in over 5 years now..

---

### Post by Yellow Pasque on 2013-02-14
Please don't bump ancient threads to rant, but I will respond in the slight chance that it will actually clear your confusion..

> not implementing support for OpenGL 2+
Funny, that. My glxinfo says:
```
OpenGL renderer string: Gallium 0.4 on AMD RV710
OpenGL version string: 3.0 Mesa 9.1-devel (git-a527b21)
OpenGL shading language version string: 1.30
```

OpenGL 3.x is forthcoming (mesa/gallium should have full 3.3 this year). Not that it matters for the X1600, since it only supports OpenGL 2.x anyway...

> if you use windows at all you'll notice no DX10 support either
Again, the X1600 is not capable of DX10 on a hardware level.

> ATI/AMD does do this and it's their dirty scheme to keep people buying new video cards.
That's a terrible scheme if that's the goal, because angering your customers generally doesn't bode well for you when it comes time for their next purchase. AMD's strategy is to transition users of older products to the ope-source driver.

> anyone know if nvidia has these caveats?
They do, though they generally update legacy driver branches for a few more years than AMD because nvidia doesn't support/develop open-source drivers.

> ? i havent upgraded my video card for fear of the instant obsoleteness of a 300$+ purchase in over 5 years now..
I hope you didn't pay $300 for an X1600. Hardware (especially GPU's) is a terrible investment anyway.

So to sum it up, I'd recommend you drop your unreasonable expectations of a high-end GPU being good for more than a few years. That's never been the case regardless of brand or OS.

---

### Post by QIII on 2013-02-14
Thanks, Temüjin.

osirisgothra, feel free to start another thread.

And with that, back to bed.

                                  *Thread closed.*

---

