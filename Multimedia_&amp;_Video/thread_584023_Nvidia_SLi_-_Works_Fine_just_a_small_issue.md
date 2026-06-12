---
title: "Nvidia SLi - Works Fine just a small issue"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by drpepper on 2007-10-20
Hey

I have two Nvidia 6800GT Cards in Sli, they work fine, the restricted drivers work perfectly. My only problem is that Ubuntu is using the wrong graphics card to output. It has done this on edgy, feisty and gusty. Live-CD and installed. The POST screen, bios and Windows all use the correct card, but when I use Ubuntu I have to plug my monitor into the other card. I've tied dpkg-reconfigure xserver-xorg and I'm not too sure what I'd need to change. Ideas?

Cheers

---

### Post by markywmson on 2007-10-20
i too am having this same problem.  XP and POST and everything else recognizes the correct card.  Also... do i have to install the nvidia drivers for it to recognize?  i'm just getting a black screen on boot (including after plugging in to the other card).  just curious how you got it to work

thanks, and thanks to everyone for any help.

-mark

---

### Post by drpepper on 2007-10-22
I see the boot splash screen on the same card as XP and POST, but everything from the GDM onwards is on the wrong graphics card. However, installing the restricted drivers has made no difference on mine. Does your Ubuntu actually work via the incorrect graphics card but no boot screen via either card?

---

