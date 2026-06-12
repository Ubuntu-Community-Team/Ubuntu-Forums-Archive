---
title: "Installing old WinTV card"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by Tatty on 2007-03-19
Hi all,

Im pretty new to linux, ive been using ubuntu for about 2 months now, and ive hit my first real brick wall with it.

Im trying to get my old Hauppauge WinTV card to work on it.  I tried following some guides to install IVTV, but my TV card doesnt show up with "dmesg |grep Initialized"

Ive finally figured that my card must be pretty old, cos it doesn't seem to follow any of the naming conventions used in the list of Supported Hardware for ivtv, (it just says WinTV "with SoftPVR") so im pinning my hopes on this: [http://pvr.sourceforge.net/]("http://pvr.sourceforge.net/")

However, whenever i try to build that driver i get the following:

> tatty@Ubuntu-PC:~/Desktop/fr-XXhwUe$ sudo make
Makefile:68: /lib/modules/2.6.17-11-386/build/Rules.make: No such file or directory
make: *** No rule to make target `/lib/modules/2.6.17-11-386/build/Rules.make'. Stop.

And thats about the end of it... Any ideas anyone?

Also should i / how do i uninstall ivtv now?

Thanks very much!
Tatty.

---

### Post by Placenta Juan on 2007-03-19
It looks like that link is for an MPEG2 (or hardware PVR), where as yours is software (softPVR). You woudn't happen to have a WinTV Go card, would you? That uses the bt848 drivers, and not IVTV. I'm not too sure how you would go about finding out short of looking at the label on the actual card...

---

### Post by tagra123 on 2007-03-19
The older wintv card "bt878" cards are plug and play.  To test them install tvtime -- its in the universe repositories.

---

### Post by Tatty on 2007-03-19
Thanks for the replies!

Ive just tried tvtime, did a complete scan for channels and nothing came up.

Im really not sure exactly what model my card is, as it has no obvious model name on it or the box... it has several things which could be the model... ill list them:

WinTV with Soft PVR
WinTV-PCI-FM
model 647  (tried the website, couldnt find any way of searching for the name of that model number)


The ubuntu Device Manager sees the card and under info.product it says "cx88 IR (Hauppauge WinTV 34xxx"

Apologies if im doing something stupid!

---

### Post by Placenta Juan on 2007-03-19
This page: [http://linuxtv.org/v4lwiki/index.php/WinTV_Go]("http://linuxtv.org/v4lwiki/index.php/WinTV_Go")
looks like it has some info that may be helpful.

---

### Post by Tatty on 2007-03-19
Got it working!

Thanks so much for that link...  i just did this:

```
modprobe cx88xx tuner=56 && modprobe cx8800
```

And it worked!

:) thanks

---

### Post by tagra123 on 2007-03-19
> **Tatty said:**
> Got it working!

Thanks so much for that link...  i just did this:

```
modprobe cx88xx tuner=56 && modprobe cx8800
```

And it worked!

:) thanks

Was it a win tv card or something like Generic Periphials?  I didn't remember having to do that for the regular card but I have one that didn't work .  I'll have to try it now.

---

