---
title: "fglrx 8.34.6 with 2.6.20 - working!!"
date: 2007-02-21
forum: Multimedia &amp; Video
---

### Post by compwiz18 on 2007-02-21
fglrx working on 2.6.20 with a patch (in the attachment)
just for the benefit of the rest of the world I'll post this here - I found it somewhere on this forum, now I can't seem to find it again so I am assuming other people will have trouble too.

Download the attachment, extract, read the readme file, and do as it says, and you should be on your way.  make sure to reboot after you're done, otherwise it _will_ freeze (at least for me).  Suspend works, as an added bonus :D although I suspect it may have sporadic freezes during intense graphical usage.

I have an ATI 200M Xpress.

disclaimer: I probably won't be able to help you if it doesn't work, although I can probably help you remove it if you can't boot.

update: suspend sort of works (sometimes, when it feels like it - but I think this is because I have an SD card in the card reader) and no freezes (I think, I've had a couple, but I think they were caused by other things)

---

### Post by skug on 2007-02-23
Doesn't work on Mobility Radeon X700, at least not for me. Just gives a black screen with the console cursor frozen in the upper left corner and as an added bonus the whole laptop stops working and needs a hard reboot :P Laptop is an Asus A6Va.

---

skug

---

### Post by uberbrodt on 2007-02-26
I have a 200m xpress and I'm very interested in getting suspend to work.  I just installed Ubuntu Edgy and have the latest fglrx drivers from ATI working on 2.6.17-11 stock kernel.

What were the sources that you used for 2.6.20?  Kernel.org?  When I used Debian, I just grabbed the kernel source from the unstable repositories to get the latest kernel with Debian patches.  Does Ubuntu have an equivalent or can I add the debian repository and use those same sources?

---

### Post by zasf on 2007-03-01
> **skug said:**
> Doesn't work on Mobility Radeon X700, at least not for me.

Same video card but it works here.. not sure if the patch is the same. BTW I used [this one from thinkwiki website]("http://whoopie.gmxhome.de/linux/patches/2.6.20/fglrx-8.34.8-for-2.6.20.patch")

---

### Post by compwiz18 on 2007-03-01
> **uberbrodt said:**
> I have a 200m xpress and I'm very interested in getting suspend to work.  I just installed Ubuntu Edgy and have the latest fglrx drivers from ATI working on 2.6.17-11 stock kernel.

What were the sources that you used for 2.6.20?  Kernel.org?  When I used Debian, I just grabbed the kernel source from the unstable repositories to get the latest kernel with Debian patches.  Does Ubuntu have an equivalent or can I add the debian repository and use those same sources?
Plain kernel downloaded from kernel.org compiled with the Ubuntu .config file.

zasf: Your patch is not the same as mine the one I posted, so it would be worth trying for people having trouble.

---

