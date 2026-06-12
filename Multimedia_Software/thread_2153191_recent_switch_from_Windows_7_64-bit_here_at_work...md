---
title: "recent switch from Windows 7 64-bit here at work.."
date: 2013-06-10
forum: Multimedia Software
---

### Post by Roccor on 2013-06-10
Ok so last friday I switched... been running Win7 64 for the past couple years now simply because we are a Windows shop.  Anyway after not rebooting for literally three months (yes I know.. shame, shame!) I bounced it and all hell broke loose.  To make a long story short it floundered like a shot duck.

So I am now running 12.04 on an HP Z400 Xeon, 12gb ram, 750gb hdd and an ATI Radeon HD 6850.  I've have a few tiny issues with the graphics being ATI but all in all I think it'll do ok.  My question right now is for graphical performance.  I am in IT here so I'm not trying to run CAD applications but I am using a triple monitor setup.  Obviously there's some lag when dragging windows between screens.  I am running Catalyst 12.10.17

Glxgears gives @2600fps and I am running Gnome3 on lightdm.

---

### Post by Bucky Ball on 2013-06-10
*Thread moved to **Multimedia & Video**.*

Welcome to the forums. You might have more luck here.

---

### Post by Mark Phelps on 2013-06-10
You should check the AMD site, since I believe that Catalyst 13.4 (at least) is available for your chipset:  [http://support.amd.com/us/gpudownload/Pages/index.aspx]("http://support.amd.com/us/gpudownload/Pages/index.aspx")

---

### Post by Roccor on 2013-06-10
Actually I was reading the version earlier from within AMDCCC.. the version I had downloaded and installed was 13.4 straight from the website.

Is that what you'd recommend though, the one from them or via Restricted Drivers?  I know performance is usually in teh eye of teh beholder but there's gotta be some hard numbers on which 'should' perform better.

---

### Post by Mark Phelps on 2013-06-10
It's generally better to install using the Additional Drivers option  because if you do that, when you later do updates that affect the kernel version, the drivers get updated automatically.  Otherwise, you have to remove and reinstall the drivers with every kernel update.  Just don't select the "post upgrade" version if that is offered.  Those seem to fail most of the time.

---

