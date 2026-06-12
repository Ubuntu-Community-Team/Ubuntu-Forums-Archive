---
title: "HDMI video = no progress screen"
date: 2008-10-22
forum: Mythbuntu
---

### Post by jape42 on 2008-10-22
Hi All,

I'm using HDMI video into my LG TV.  I noticed that while a regular monitor was connected that I get a mythbuntu progress screen+ progress bar as the system starts up and shuts down.

With HDMI video, I don't get this progress status.  The screen is blank.  Any thoughts on this?  I _suspect_ that this screen is using a video mode that cannot be displayed on my TV.  Is there any way to tweak/configure this?

regards

jp

---

### Post by jape42 on 2008-10-25
Alternatively is there any way to disable the GUI startup screen?  At least this way I'd get console progress messages.  This simplistic kind of progress is better than no progress indication at all.

jp

---

### Post by SiHa on 2008-10-26
You need to edit the boot menu file:**/boot/grub/menu.lst**

Scroll down to near the end, the first menu entry, after **## End Default Options##**, you should have a section that looks something like:```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ceef0edd-6b62-4601-b2aa-f21e3a86d29b ro quiet [COLOR="Red"]**splash**[/COLOR]
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

Just change the **splash** to **nosplash**

That will at least get rid of the Graphical startup screen. If You still can't see anything during boot, I think there is a way to change the default resolution used during boot, but I'm afraid I don't know what it is.

---

### Post by ian dobson on 2008-10-27
Hi,

When do you see the first output on your display?
The BIOS screen, Grub Menu, X server?

It could will be that the HDMI output is only enabled by the XServer graphic driver.

Regards
Ian Dobson

---

### Post by jape42 on 2008-10-27
> **ian dobson said:**
> Hi,

When do you see the first output on your display?
The BIOS screen, Grub Menu, X server?

It could will be that the HDMI output is only enabled by the XServer graphic driver.

Regards
Ian Dobson

Yes.  I can see the bios screen some initial messages.  It's only the mythbuntu graphical "progress bar" screens that result in a blank screen on my TV.

jp

---

### Post by jape42 on 2008-10-27
> **SiHa said:**
> You need to edit the boot menu file:**/boot/grub/menu.lst**

Scroll down to near the end, the first menu entry, after **## End Default Options##**, you should have a section that looks something like:```
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=ceef0edd-6b62-4601-b2aa-f21e3a86d29b ro quiet [COLOR="Red"]**splash**[/COLOR]
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

```

Just change the **splash** to **nosplash**

That will at least get rid of the Graphical startup screen. If You still can't see anything during boot, I think there is a way to change the default resolution used during boot, but I'm afraid I don't know what it is.

I didn't realize grub was responsible for displaying the progress screen, I assumed it was mythbuntu.  

As you suggested I changed to nosplash and now at least I can see some progress occurring.

Thanks

jp

---

### Post by ian dobson on 2008-10-28
Hi,

Or maybe this might help you [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)

Regards
Ian Dobson

---

