---
title: "ATI 4770 - Catalyst 9.5 - Logout / Switch Users"
date: 2009-06-06
forum: Multimedia Software
---

### Post by randyklein99 on 2009-06-06
I have a newly built desktop with an ATI 4770 graphics card.  I am having issues with regards to logging out and switching users.  Here's how it breaks down:

**Catalyst 9.5:**
- Able to switch to a non-logged in user
- Switching back to the first logged in user - black screen, unresponsive to all magic key combos, must power cycle to reboot
- Logging out with 1 or more users logged in - same results as above


**Using the default install driver:**
- Able to switch to non-logged in user
- Able to switch back, but graphics are real ugly.  As if there was only 8 colors to choose from.  However, a screen capture doesn't capture the ugliness - once I get the graphics back, the screen capture didn't show the problem.
- Able to logout and log back in without hanging.  This also solves the ugly graphics problem.


Evidently, to me at least, this is related to the graphics card driver.  Is there anything I can do to fix either of these driver configurations?  I would rather have an ugly screen than power cycling, so is there an easy fix for that?

Also, the proprietary drivers offered by Ubuntu inform me I have unsupported hardware.

---

### Post by randyklein99 on 2009-06-07
I have also tried the RadeonHD drivers following the guide [here]("https://help.ubuntu.com/community/RadeonHD").

They seem to have none of the above problems.  However, they have some awfully slow scrolling in Firefox.  So slowly its unusable.

---

### Post by randyklein99 on 2009-06-07
I had to take real pictures of my screen since the software screen capture wasn't capturing the problem.
Entire screen:
[ATTACH]116731[/ATTACH]

Close up:
[ATTACH]116732[/ATTACH]


Also, since this is occurring with the default drivers, is this a bug I should report?  Or is it because the 4770 may be unsupported hardware right now?

---

### Post by pandasonic on 2009-06-08
I have got the same exact problems.  I was told that it is perhaps because Catalyst 9.5 came out at almost the same time as our card (4770), we'll probably have these problems until Catalyst 9.6 comes out.

I tried reinstalling Ubuntu because the last attempt at fixing this problem crippled my PC and now I'm back at the same place.  All I get after GRUB and the loading screen is a black screen.  Not even the login screen.   I am going to try using my backup xorg.conf file and if that doesn't work that's it with Ubuntu on this system, until 9.10 comes out in October.

Let me know if you have success.  I really don't have the time to fiddle around with my computer just to get the video working, my Win7 RC1 works just fine so I'll stick with that in the meantime.

Thanks.

---

### Post by randyklein99 on 2009-06-09
My solution now is to use the default install driver and wait for 9.6 or until someone smarter figures out how to configure 9.5 or radeonhd.

Also thanks for replying and confirming this was an issue for someone else.  It helps to know that I'm not the only one.

---

### Post by randyklein99 on 2009-06-10
Some success.  

I have the RadeonHD drivers installed and no longer have choppy scrolling in Firefox, am able to switch users without corrupting graphics, can suspend and logout with no issues.

The only change I had to do from the install instructions was to remove the EXA and DRI option.

So here is my xorg.conf:

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver   	"radeonhd"
EndSection

Section "ServerFlags"
	Option	"DontZap"	"False"
EndSection

```

The only issue I can't seem to resolve yet is that I can't drop to a terminal (Ctrl-Alt-F1). I get a floating window that says:

```

Not optimum mode 
Recommend mode:
1280x1024 60 Hz

```

But that is what I have my resolution set at.  Any ideas?  Further xorg.conf tweaking?

---

