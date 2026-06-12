---
title: "Why does VirtualBox automatically overlay offline SP2 onto my 1st edition XP?"
date: 2015-08-24
forum: Multimedia Software
---

### Post by Old_Printer on 2015-08-24
What's inside of VirtualBox? When I install a 1st edition of Windows XP, it finalizes and reaches the desktop, only to have balloon tips popping up from down by the clock. It's telling me about .Net and this and that. I'm pretty sure balloon tips didn't come about until SP2. Furthermore, upon further inspection, MS Messenger icons also appear in the system tray. This isn't so out of the ordinary, except that when I go to uninstall said Windows component, I don't have the option to uninstall it. It's not until I actually go through the motions of installing SP2, a full version upgrade that I have on CD, directly from MS, when I can finally uninstall Messenger.

So, is VirtualBox really an application composed of compressed versions of operating systems, which are simply re-hydrated when I go through the motions of spinning up my CD / DVDs and use my activation keys? A key still has to be valid, and match my disk, but the installation sure is surprising.

Old_Printer

---

### Post by QIII on 2015-08-24
No, VirtualBox is simply an empty virtual machine until you install your OS in it.

Your issue is quite interesting, but has nothing to do with VirtualBox.

---

### Post by Old_Printer on 2015-08-24
Hi QIII. Thanks for the reply. I appreciate it. I don't think MS .Net was even around yet when the 1st edition of XP was released. Yet, once you reach the desktop after the installation, there goes those SP2 balloon tips. I always go into the registry and disable them, so when I caught myself opening up the editor to do it, I thought, "Wait a minute. This isn't right. I'm getting balloon tips?"

Old_Printer

---

### Post by QIII on 2015-08-24
If VirtualBox were rehydrating freeze-dried Windows, Microsoft would own virtualbox.org by virtue of the gentle touch of their expensive lawyers.

---

### Post by Old_Printer on 2015-08-24
I'm going to do a clean install right now with my XP disk. I just have to find a SATA drive that doesn't have something on it. I want to be sure what I see. No Linux, no VirtualBox, just ASUS and XP -- 2001.

Old_Printer

---

### Post by Old_Printer on 2015-08-25
Well, I made a clean install of WinXP 2002 and then the video driver. No balloon tip whatsoever. Then, I installed Zorin 9. I had a download of VirtualBox 5.0_5.0.2-102096~Ubuntu~trusty_i386 from Oracle and performed a local .deb install. As you can see in the screenshots I was loading XP2, which is the 2002 version, even though the disk I used says 2001 on it.

There's no security shield badge in the system tray, indicative of SP2, but as you can see after the XP install in VB made it to the desktop, there's that .Net balloon tip. I first noticed this weird deal when using VB from the repository. That version is 4.3.10 Ubuntu r93012. Last week I used this same XP disk on my ASUS and installed all of the drivers, fulfilling the device manager. Never did I receive the .Net balloon tip.

Wouldn't MS's own operating system pop up that .Net balloon on its own when it's installed directly on a PC? If this .Net feature is part of the Windows install, what's going on in VB to bring it to the surface? This balloon will drive you nuts if you don't disable it. The only thing installed in VB is VBox Guest Additions 2.0.4 -- for display.

Old_Printer

[ATTACH=CONFIG]264038[/ATTACH][ATTACH=CONFIG]264039[/ATTACH][ATTACH=CONFIG]264040[/ATTACH]

---

