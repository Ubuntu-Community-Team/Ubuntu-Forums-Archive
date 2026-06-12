---
title: "How to prevent FGLRX updates"
date: 2009-07-04
forum: Multimedia Software
---

### Post by juelze on 2009-07-04
So, I've had good luck with Intrepid, except some video aspects were less then ideal (slow playback on a lot of video and streaming video).  When I went to Jaunty everything worked great until FGLRX driver got installed.  So, I reinstalled Ubuntu and again everything is working fine, but how do I prevent FGLRX from getting on my system?  I know that in the Synaptics Manager you can lock a certain version of a package.  However, what package do I need to lock?  Also, if I lock that package, will it prevent FGLRX from showing up in updates?  

I'm hoping my 9800 Pro will serve me for what I do as I don't want to put a lot of money into my machine.  

Any help is appreciated!

Cheers,
Juelze

---

### Post by juelze on 2009-07-05
Bump.  Any help would be appreciated!!

---

### Post by oldrocker99 on 2009-07-07
:biggrin:Well, if you're willing to do a fresh reinstall, there should be no trace of any FGLRX drivers on your system. My system, under System/Administration/Hardware Drivers only offers an alternate for my laptop's wireless chip.

I have no problem with my wireless connectivity, so I never enabled it. (If it ain't broke... ) (In fact, that's a good piece of advice with using Linux in general.) :wink:Ubuntu makes things extra easy for the beginner, and it is still possible to hose your system, and still easy to restore back to your original system quickly. But I digress.

](*,)The sad truth is that ATI users are currently on the short end of the stick. The only drivers available are open source, and, while they're at least usable, they are only about 33% as fast as the FGLRX drivers were under 8.10.

The good news is that the open-source community involved with Xorg is very well aware of the problem with the incompatibility between FGLRX drivers and Xorg1.6. (If I have the version number right)

ATI DID release technical specs on their chips to the open-source community, and the open-source drivers will only get better, and probably by the time Karmic Koala comes out.

We can hope.

:guitar:

---

### Post by juelze on 2009-07-08
> **oldrocker99 said:**
> :biggrin:Well, if you're willing to do a fresh reinstall, there should be no trace of any FGLRX drivers on your system. My system, under System/Administration/Hardware Drivers only offers an alternate for my laptop's wireless chip.

I have no problem with my wireless connectivity, so I never enabled it. (If it ain't broke... ) (In fact, that's a good piece of advice with using Linux in general.) :wink:Ubuntu makes things extra easy for the beginner, and it is still possible to hose your system, and still easy to restore back to your original system quickly. But I digress.

](*,)The sad truth is that ATI users are currently on the short end of the stick. The only drivers available are open source, and, while they're at least usable, they are only about 33% as fast as the FGLRX drivers were under 8.10.

The good news is that the open-source community involved with Xorg is very well aware of the problem with the incompatibility between FGLRX drivers and Xorg1.6. (If I have the version number right)

ATI DID release technical specs on their chips to the open-source community, and the open-source drivers will only get better, and probably by the time Karmic Koala comes out.

We can hope.

:guitar:


THanks for the post.  I bid on a 6800 Nvidia AGP card on Ebay so maybe that'll solve my problems.  Thanks again for your info!

---

