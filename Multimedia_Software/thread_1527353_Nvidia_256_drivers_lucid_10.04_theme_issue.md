---
title: "Nvidia 256 drivers lucid 10.04 theme issue"
date: 2010-07-09
forum: Multimedia Software
---

### Post by david_1989 on 2010-07-09
OK, I'm using Ubuntu 10.04 and since upgrading to the 256.35 drivers from the ubuntu-x-swat/x-updates ppa the ambiance and radiance themes have gone funny. For example the scroll bars and buttons are now very white and when hovering over the time it goes a very bright colour. If I return to the 195 drivers the problem goes, but the 256 drivers have better video vdpau performance.

The problem occurs regardless of whether compiz is enabled. The login screen is also affected.

My gfx card is an 8600m gs.

The attached screenshot illustrates the problem.

---

### Post by Linuxforall on 2010-07-09
I was on Ubuntu till yesterday using the very same drivers and didn't face this issue, I have a 8400GS card, now I am on Kubuntu using the same and no issues.

---

### Post by luisromangz on 2010-07-09
I have exactly the same problem!

---

### Post by david_1989 on 2010-07-09
> **luisromangz said:**
> I have exactly the same problem!
What graphics card do you have?

---

### Post by david_1989 on 2010-07-11
I guess it must just be a Nvidia driver bug.

---

### Post by sarim on 2010-07-14
I'm having the same problem in 10.10 alpha 2. Here in from ubuntu repositary i installed nvidia-current driver. which version is 256.
In ambiance and radiance  theme button and scroll bar become solid white. :(

Have anyone tried nvidia.com's driver  ? 
I have Geforce 8400.

I have previously downloaded 196 version of nvidia-current driver but it does not install, when dpkg configuring it breaks saying a problem with xorg. the version mismatches with xorg version.
How can now I swiftly back to 196 nvidia-current.
is there any deb package for ubuntu 10.10 ?

---

### Post by 1jackjack on 2010-07-27
I confirm this issue - when you mouse over an item in the window selector, it highlights to pure white so you cant read the writing!

Also funny issues with gnome-do: weird square shadows and delays when typing.

It's annoying because if I revert back to the ubuntu repo version (195.36.24), I get a random black flickering at random intervals.

Also if I switch back to the open source driver (as described here: [https://wiki.ubuntu.com/X/Drivers](https://wiki.ubuntu.com/X/Drivers)), I don't get any desktop effects at all (the old "desktop effects could not be enabled").

---

### Post by david_1989 on 2010-09-01
Just done a kernel update and nvidia driver update and still this issue is not resolved. It's really rather irritating as all round the 256 drivers seem much better particularly with vdpau but for me they cause this annoying bug in the themes.

---

### Post by realzippy on 2010-09-01
Have you run all updates that are available?
I had this issue also,but was gone after updating everything...

---

### Post by david_1989 on 2010-09-01
Do you have any particular repositories? What updates were updated specifically?

---

### Post by realzippy on 2010-09-01
Yes...lucid-proposed-updates.
And a bunch off ppa's like xswat/vdpau/xorgedgers...

---

### Post by david_1989 on 2010-09-01
> **realzippy said:**
> Yes...lucid-proposed-updates.
And a bunch off ppa's like xswat/vdpau/xorgedgers...

Yup done that, and still not fixed!

What gfx card you got?

---

### Post by realzippy on 2010-09-01
9800 GTX,but that won't help you.

I had your issue on 2 machines (2 weeks ago?);was not amused,tried reinstalling
nvidia-driver and desktop-theme without luck.Decided to wait a few days for common updates....and problems solved.Can give you my *sources.list or other info*?

---

### Post by david_1989 on 2010-09-01
> **realzippy said:**
> 9800 GTX,but that won't help you.

I had your issue on 2 machines (2 weeks ago?);was not amused,tried reinstalling
nvidia-driver and desktop-theme without luck.Decided to wait a few days for common updates....and problems solved.Can give you my *sources.list or other info*?

OK, might as well send me your sources.list so I can have look. What version of nvidia 256 drivers you got, 256.52?

Cheers.

---

### Post by realzippy on 2010-09-01
256.52 from xorg-edgers/Lucid.

Just wondering where the ppa`s in the sources list have gone which
I can see in synaptic...??!!

---

### Post by david_1989 on 2010-09-04
OK, did some updates before I switched off on Wednesday evening and haven't used my laptop since this morning when I switched on and this problem is solved!

Annoying thing is is that I do not know what update(s) actually fixed the problem! Basically, I would just recommend installing the updates recommended by realzippy.

---

