---
title: "Netflix Roku via Mythbuntu"
date: 2009-01-25
forum: Mythbuntu
---

### Post by williammanda on 2009-01-25
Has anyone been able to integrate the Netflix Roku box into Mythbuntu? I was thinking that it could be done using a pvr-150?
Thanks

---

### Post by williammanda on 2009-01-31
Bump

---

### Post by theophile on 2009-01-31
Yes it can. Use S-Video. Though you have to realize that if you use it this way, all the Roku button presses and menus will be time shifted too. That means if you press a button on the Roku remote, it will take several seconds before you see the effect in Myth. 

In short, using the Roku on MythTV via s-video is the same as using any STB that way.

---

### Post by linuxhippy on 2010-01-26
> **theophile said:**
> In short, using the Roku on MythTV via s-video is the same as using any STB that way.


How would you set the Roku up with an s-video cable in mythbuntu?

---

### Post by mathewDD on 2010-01-26
Maybe not at all what you are looking to do, especially if you already have a Roku...but what I'm doing for Netflix is launching XBMC from Myth.

I created a menu entry on the main menu and added in the logo for the watermark, works out great.

Of course I don't get the HD stream...but with an old TV, that just does not matter.

---

### Post by williammanda on 2010-01-27
> **mathewDD said:**
> Maybe not at all what you are looking to do, especially if you already have a Roku...but what I'm doing for Netflix is launching XBMC from Myth.

I created a menu entry on the main menu and added in the logo for the watermark, works out great.

Of course I don't get the HD stream...but with an old TV, that just does not matter.

You are being very vague. Are you suggesting that you are viewing videos via netflix on linux without a roku box? If so please be more specific about your setup. There are thousands of linux people that would want your setup.

---

### Post by linuxhippy on 2010-01-27
> **williammanda said:**
> You are being very vague. Are you suggesting that you are viewing videos via netflix on linux without a roku box? If so please be more specific about your setup. There are thousands of linux people that would want your setup.

I've done that with virtual box.  Unfortnately when I put Virtual Box on my mythbuntu box my video capture card stopped working and I had to re-install mythbuntu.  I made a 5 GB WinXP Virtual Box session and installed WinXP on it...then surf to netflix in IE and download the software for netflix watching.

---

### Post by mathewDD on 2010-01-27
> **williammanda said:**
> You are being very vague. Are you suggesting that you are viewing videos via netflix on linux without a roku box? If so please be more specific about your setup. There are thousands of linux people that would want your setup.

Oh ya, I forgot the magic that is bringing it into XBMC

I have a copy of XP SP3 running PlayOn Server in VMware Workstation 7 on my desktop (desktop is Jaunty X86_64) 

I configure XBMC as a UPNP client and it grabs the Netflix stream from the PlayOn server

It's pretty convoluted, but in the end it's even wife friendly

If my Myth backend were more powerful (it's only a P4 1.8 with 512MB) I'd just run VMware or Virtualbox or somethin on it and keep my desktop out of the equation. My desktop has plenty of power to spare, it's a dual socket Opteron with 8GB

---

### Post by williammanda on 2010-01-27
> **mathewDD said:**
> Oh ya, I forgot the magic that is bringing it into XBMC

I have a copy of XP SP3 running PlayOn Server in VMware Workstation 7 on my desktop (desktop is Jaunty X86_64) 

I configure XBMC as a UPNP client and it grabs the Netflix stream from the PlayOn server

It's pretty convoluted, but in the end it's even wife friendly

If my Myth backend were more powerful (it's only a P4 1.8 with 512MB) I'd just run VMware or Virtualbox or somethin on it and keep my desktop out of the equation. My desktop has plenty of power to spare, it's a dual socket Opteron with 8GB
 Thanks for your reply. Netflix will not be usable until silverlight is available in linux. Also this topic was roku not adhoc setups that may or not work.

---

### Post by LowSky on 2010-01-28
> **williammanda said:**
> Thanks for your reply. Netflix will not be usable until silverlight is available in linux. Also this topic was roku not adhoc setups that may or not work.

Silverlight is available
[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

unfortunately Netflix still doesn't work on Linux. Blame Netflix

---

