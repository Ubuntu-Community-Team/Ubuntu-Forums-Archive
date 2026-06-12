---
title: "DVD troubles"
date: 2009-02-01
forum: Multimedia Software
---

### Post by techmarks on 2009-02-01
When I put a DVD in it puts a DVD icon on the desktop and the directory contents pop up.

However when I want to change to another DVD I press the eject button on the drive and it pops out and then in again real quick, so I can't take it out.

So basically I can't use DVD's in XFCE.

So then I chose Gnome as the desktop, but it's almost equally bad.

I tried right clicking on the DVD icon and it says 'eject', if I press eject the same things happens it pops out and back in real quick.

So I have to click 'unmount' and it pops in and out, then I have to click 'eject' and only then can I take it out.

Is this normal? I think I need a new DVD drive.

---

### Post by mc4man on 2009-02-01
I'm assuming your using 8.10, if so there was a bug about this which was fixed with an updaye of udev to version 124-9.
So check and see if your updated. If so, sometimes the update doesn't work the first time.

Go to System -> Admin.. -> Synaptic package .. and search udev. If it shows ver. 124-9 then you can do 2 things. First try highlighting udev and in upper panel go package -> force version and choose 124-8, click force version and then apply. When it's done search udev again, mark for upgrade, and apply.

If there's no version to force back to then mark udev for reinstallation and apply

---

