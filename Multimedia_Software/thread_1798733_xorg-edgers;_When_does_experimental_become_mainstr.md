---
title: "xorg-edgers; When does experimental become mainstream?"
date: 2011-07-06
forum: Multimedia Software
---

### Post by phredbull on 2011-07-06
I started using Ubuntu Karmic on my old laptop w/ATI GPU and quickly realized the benefits of the xorg-edgers PPA. I understand that these packages are considered bleeding-edge, and do sometimes cause breakage. For me though , the pluses have vastly outweighed the minuses, which were negligible. I can't use any proprietary drivers w/my old card, and 3d is basically non-functional with the standard open ATI drivers. With xorg-edgers, I can use Compiz, play OpenArena and Quake Live.
Now after over a year and a half, 15 kernels and nearly 4 releases later, I'm really not sure how much progress has been made with the mainstream open ATI drivers, though I have been enjoying 3d with xorg-edgers.
I really don't know how much of the bleeding-edge performance is due to the drivers, the kernel, xserver, or other libraries. I'm just looking forward to the day when my GPU is fully functional OOTB.
Can anyone comment on how packages go from experimental to mainstream? Speculate on when open ATI development will be complete, and will that be all that is required for properly accelerated graphics?

(BTW, I am aware of the ATI open drivers mega-thread and have been following it.)

---

### Post by pme 72 on 2011-07-06
Phoronix.com has a lot of articles, discussions and forum posts about ATI driver development. Articles usually contain a link to a discuss about the content. If you follow the Ubuntu forum ATI drivers are coming of age thread you will probably find some interesting reading.

---

### Post by handy on 2011-07-07
**@phredbull:** There have been some recent (since 11.04) upgrades to the Gallium stack that have bought about the first 3D speed increases for my R600 card for many months. Whether these improvements have had any effect on your GPU I don't know.

If you aren't having any problems using the ppa, it is just as easy to stick with it, especially with Ubuntu as the changes come through so slowly (well, at least in comparison to Arch).

The couple of times I've temporarily gone off, of the git driver stack over the last 21+ months was when a bug came down stream. Even when I include those incidents I'm still thoroughly impressed with the reliability of the git kernel & driver stack. 

The entire experience has really been quite an education. :)

---

