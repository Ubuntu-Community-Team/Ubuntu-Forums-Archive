---
title: "Graphics driver problem"
date: 2012-12-17
forum: Multimedia Software
---

### Post by iamtommo on 2012-12-17
Hi, I recently upgraded from the Nvidia GT520 to ATI Radeon 6570.
I expected that I would be able to simple install the new card on my linux installation, but I ran into some complications.

Note: I'm running Ubuntu 12.04

First off, with no drivers installed on my part (I expect it uses some open source drivers) as soon as I get to the login screen the whole screen is the same colour (green, since my background was green). I can hear all the login sounds and I can even login, and once logged in the screen turns fully white and almost seems to flash bright grey/white, you get the point.

So I dropped to a root shell prompt and installed the latest catalyst drivers (12.10) from a binary I downloaded onto a a separate hard drive from my Windows partition. Note: This card works perfectly on Windows with the same catalyst drivers (12.10). Upon logging in, I have no display whatsoever, I'm just in a full screen terminal where I can go about my stuff without a display.

I have tried many fixes many times, most notably the full remove/purge of fglrx, reconfiguring xserver, reinstalling xserver/open source drivers/catalyst drivers... everything I can possibly think of I have tried.

Is there a possibility that the open source drivers and/or catalyst drivers don't support/are broken for my new card?

---

### Post by QIII on 2012-12-17
Did you previously have the nVIDIA driver installed and did you uninstall it prior to installing the ATI driver?

---

### Post by Portaro on 2012-12-17
I dont have a certain answer to you but:

Try this- on boot press -e key and 

add this line to the end of kernel boot parmeter option =

radeon.modeset=0

See if the image works, if works you have a misconfigured xorg or you dont have remove completely the drivers for blob of ATI.

---

### Post by iamtommo on 2012-12-17
> **QIII said:**
> Did you previously have the nVIDIA driver installed and did you uninstall it prior to installing the ATI driver?

Sadly not, I'll try yours and Portaro's solutions now, thanks.

---

### Post by QIII on 2012-12-17
If you had the nVIDIA driver installed and did not uninstall it first, uninstall both and reboot.

nomodeset is rarely needed for ATI cards.

---

### Post by iamtommo on 2012-12-17
Good news, I uninstalled all nvidia drivers and its working with the default open-source drivers. Cannot believe I was so stupid. Thankyou.

Not solved yet though, I'm going to install the proprietary drivers and see how it goes...

---

### Post by QIII on 2012-12-17
Not stupid at all.  How do you think I learned to ask that question?  ;)

It is not supposed to be necessary any longer, but I still recommend doing

```
sudo aticonfig --initial
```

after installing the driver and before rebooting.

---

