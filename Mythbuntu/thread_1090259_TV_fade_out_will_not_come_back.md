---
title: "TV fade out will not come back"
date: 2009-03-08
forum: Mythbuntu
---

### Post by menny on 2009-03-08
Hi,
I encountered a very annoying bug.
My Myth machine is connected exclusively to a TV monitor. When the screensaver comes on, it will do a fade out effect and blank the screen. If I press any key, the GUI will come back, and everything is fine.

BUT, if I press a key while the screensaver is FAD**ING** out, then it will not come back!
It is the weirdest thing, if I connect to the computer with VNC, I can see the GUI, and it works, and all is fine, but the TV monitor stays blank, no matter what. The only thing I can do, is reboot....

Help

---

### Post by utar on 2009-03-08
I'm guessing you have a Nvidia card.  This has been a long running problem.

The work around is not to press a key while the screen is dimming!  Otherwise if you press Ctrl+Alt+Backspace this should restart the window manager without a reboot.

---

### Post by menny on 2009-03-08
WOW, you kidding me....
Nobody want to fix that?

Thanks for the workaround, I'll do that next time

---

### Post by oldhack on 2009-03-09
I have found that once this fade-lock has occurred. I am able to walk away and if I don't disturb it for the amount of time it would have taken the screen saver to kick in again, then when I move the mouse, the screen will come back normally.

---

### Post by newlinux on 2009-03-09
> **menny said:**
> WOW, you kidding me....
Nobody want to fix that?

Thanks for the workaround, I'll do that next time

welcome to the club :). It is VERY annoying... Sometimes I don't realize it is fading, so I accidently push a button... But gotta have the screensaver on my plasma - Just something gotta live with for now...

---

### Post by 4dognight on 2009-03-09
> **newlinux said:**
> welcome to the club :).  But gotta have the screensaver on my plasma - Just something gotta live with for now...

Have ever considered using suspend or hibernate? My  LCD TV will turn itself off when there is no signal, as what will happen on a suspend/hibernate.

---

### Post by newlinux on 2009-03-09
> **4dognight said:**
> Have ever considered using suspend or hibernate? My  LCD TV will turn itself off when there is no signal, as what will happen on a suspend/hibernate.

Yes, but that won't address my problem. I still need the screensaver for when I have to chase my 2 year old around because he has gotten into something and I just want to pause the video (or I get a phone call :). My signal does get turned off after the screensaver has been on a certain number of minutes.

---

### Post by menny on 2009-03-10
> **newlinux said:**
> But gotta have the screensaver on my plasma - Just something gotta live with for now...

Your plasma is connected via a TV-out thingy? Not VGA/DVI?

---

### Post by newlinux on 2009-03-10
> **menny said:**
> Your plasma is connected via a TV-out thingy? Not VGA/DVI?

What makes you think that? My PCs connected to my Plasma is via an DVI->HDMI connection.

---

### Post by menny on 2009-03-11
I was sure that the fade-out problem exists only in TV-out connected monitors!
It exists in DVI also? If so, how come it is not a major bug?

---

### Post by newlinux on 2009-03-11
> **menny said:**
> I was sure that the fade-out problem exists only in TV-out connected monitors!
It exists in DVI also? If so, how come it is not a major bug?

It exists for VGA too...

---

### Post by menny on 2009-03-11
That's really weird... If I use VNC to remotely take over the faded computer, it isn't blanked - but the monitor stays blanked.

I don't understand, can this blank issue be fixed?

---

### Post by newlinux on 2009-03-11
> **menny said:**
> That's really weird... If I use VNC to remotely take over the faded computer, it isn't blanked - but the monitor stays blanked.

I don't understand, can this blank issue be fixed?

It would be nice. I've asked this question on a couple of different forums and get a lot of "that's just the way it is." I don't know about anyone fixing it, but hopefully it will happen.

Yes, I noticed that about VNC to - everything is there, for some reason the screen is just blanked out on the connected monitor... You just have to be careful not to hit a key while it is fading... I try to be careful, but I still do it every now and again.

---

