---
title: "Help me replace my video card drivers please."
date: 2009-08-18
forum: Multimedia Software
---

### Post by rmjohnson144 on 2009-08-18
I currently have a nvidia GTX 295 video card and I am replacing it with an ATI HD4350.  How do I uninstall the nvidia drivers?  can I just install the ATI drivers while leaving the nvidia driver installed?

Thanks
-=Mark=-

---

### Post by realzippy on 2009-08-18
...the nvidia card will work much better than the ATI....

---

### Post by bboston7 on 2009-08-18
TIP:  Don't use ATI, their drivers are much worse.

But if you really want to, here is how:

Open System > Administration > Hardware Drivers.

Highlight your card and click disable or uninstall.  Then, open up your computer and install your ATI card.  Boot up ubuntu and open the hardware drivers window once more and click install on the ATI driver.

Once again, your Nvidia card is going to be much better

---

### Post by rmjohnson144 on 2009-08-18
I just dumped the nvidia card as a GTX 295 is overkill for linux.  Plus I use my machine for video more than anything and nvidia doesn't support hardware acceleration (at least on the 295) and I knew the ATI cards do, plus they support dx10.1 and have sound in their cards so HDMI will play sound without running a second audio wire to my computer.

I know ATI has linux issues, but I have had somewhat success in the past. This HD4350 is new and may have issues for a while, but I use this as backup more than anything and it rarely gets used.

anyway, I had to manually install the nvidia drivers, so they won't show up in hardware manager.  Is there a command with the compilation of the driver that uninstalls them?  do I just delete some files/folders?

Thanks for the replies
-=Mark=-

---

### Post by realzippy on 2009-08-18
"nvidia doesn't support hardware acceleration (at least on the 295)"

I am shure this is not true.But,if you really want the choppy ATI:

**sudo sh NVIDIA-Linux-yourdriverversion.run --uninstall**

Same as installing,adding: --uninstall

---

### Post by rmjohnson144 on 2009-08-18
Thanks, that seemed to do the trick.

Do you know what packages need to be installed to compile the ATI drivers from their website (Catalyst 9.7)?  The instruction links seem to be dead and give me nothing at all.

also, I plan on upgrading my card in the near future.  This HD4350 is my testing/backup card for when things go wrong, but it is all I have now and was hoping to get it to work in hopes the hardware decoding will work.

was hoping to wait for a DX11 card before I upgrade though.

Thanks for the help
-=Mark=-

---

### Post by realzippy on 2009-08-18
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat92-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat92-inst.pdf)

sorry,thats for 9.7 :
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat97-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat97-inst.pdf)

seems to be:

XFree86-Mesa-libGL
libstdc++
libgcc
XFree86-libs
fontconfig
freetype
zlib
gcc

---

### Post by hopwon on 2009-08-18
> **rmjohnson144 said:**
> Thanks, that seemed to do the trick.

Do you know what packages need to be installed to compile the ATI drivers from their website (Catalyst 9.7)?  The instruction links seem to be dead and give me nothing at all.

also, I plan on upgrading my card in the near future.  This HD4350 is my testing/backup card for when things go wrong, but it is all I have now and was hoping to get it to work in hopes the hardware decoding will work.

was hoping to wait for a DX11 card before I upgrade though.

Thanks for the help
-=Mark=-

I have bought the same card and its driving me insane getting th thing to work at a decent resolution without crashing. Can get it to run at 1024x768 but thats it if I want to play video.
Let me know if you manage to succeed!

---

### Post by rmjohnson144 on 2009-08-18
> **realzippy said:**
> [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat92-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat92-inst.pdf)

sorry,thats for 9.7 :
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat97-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat97-inst.pdf)



Thanks for the link.  I actually had Catalyst 9.8, but it was the same setup as 9.7 and worked wonderfully.  I only played a few videos, but no stutter at all.

Thanks again
-=Mark=-

---

### Post by hopwon on 2009-08-19
> **rmjohnson144 said:**
> Thanks for the link.  I actually had Catalyst 9.8, but it was the same setup as 9.7 and worked wonderfully.  I only played a few videos, but no stutter at all.

Thanks again
-=Mark=-

I did the same and managed to install the 9.8 driver without issue (needed a reboot), but I do get horizontal lines sometimes in video playback. Not sure yet if thats a result of the codec or driver. I need to do some more testing.

---

