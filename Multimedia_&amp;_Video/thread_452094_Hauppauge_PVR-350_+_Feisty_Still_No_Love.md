---
title: "Hauppauge PVR-350 + Feisty: Still No Love?"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by sarahr on 2007-05-22
Hi, all - 

I've been working to get Feisty up and running on the box I've designated for it, with the end result being, hopefully, to run mythtv.

Imagine my dismay when I read something a bit earlier tonight that suggested to me that the particular Hauppauge card is not going to work under Feisty, specifically (I've been following the excellent Ubuntu guides, btw, to get this far). 

So.  Can anyone confirm/negate that the Hauppauge PVR-350 does capture, BUT DOES NO OUTPUT, under Feisty + MythTV?

Anyone have any further info with regard to this, the nature of this problem, and the likelihood of it being resolved at some point (i.e. should I be looking at getting some other capture card?)?

Thanks.

---

### Post by newlinux on 2007-05-23
According to:

[https://help.ubuntu.com/community/MythTV_Feisty_hardware_list#head-6d34a57c5684f0eab989f8091c4ff39893b16521](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list#head-6d34a57c5684f0eab989f8091c4ff39893b16521)
It captures but TV-out doesn't work, as you state.

However this:

[https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out)
seems to give a guide for getting it to work. hope some of that is helpful.

---

### Post by Neuralgia on 2007-06-04
does it work with other program?

I  don't understans exactly what NO TV OUT means?

a) Not working with MythTV, but works with any other program
b) Not working at all
c) Can't send signal to TV

:?

---

### Post by rhpot1991 on 2007-06-04
The directions here work perfectly:
[https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out](https://help.ubuntu.com/community/MythTV_Feisty_hardware_pvr-350_TV-out)

Basically the problem is that ivtv only supports input and you need ivtv-fb loaded.

---

