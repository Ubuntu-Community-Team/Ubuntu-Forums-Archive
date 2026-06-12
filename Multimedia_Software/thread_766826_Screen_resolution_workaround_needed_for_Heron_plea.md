---
title: "Screen resolution workaround needed for Heron please."
date: 2008-04-25
forum: Multimedia Software
---

### Post by trubshac on 2008-04-25
Hi

Please forgive me if this information is already somewhere on the forum - I have spent sometime searching.  If it is, just point me to it and accept my apologies.

I should also say that I am just in the process of kicking the microsoft habit so am a bit of a Linux newbie.

I have a Dell Latitude C800 laptop.  It has a "ATI Technologies Inc Rage Mobility M4 AGP" (according to lspci) and a 1600x1200 display.  Gutsy didn't recognise my video card/monitor and only offered me 800x600 resolution.  My work around for Gutsy was to go into "Administration -> Screens and Graphics" and insist that I had a 1600x1200 monitor.  When I then went into "Preferences -> Screen Resolution" it would allow me to select 1600x1200 there too.  If I missed the first step (change monitor size), then I would only be offered 800x600 in "Screen Resolution".

On Hardy, the "Administration -> Screens and Graphics" program is no longer present.  I cannot therefore tell the system that I have a high res monitor, so "Screen Resolution" does not offer me anything higher than 800x600.

Can anyone suggest a work around for me please?   I am quite happy to use shells and edit config files, I just need to know which to adjust.

Thanks in anticipation
Colin

---

### Post by hurtstotalktoyou on 2008-04-25
It's still there, just in a different place.  Go to System > Preferences > Main Menu, then choose the Applications > Other.  Then you'll see the "Screens and Graphics" checkbox, which you must check.  Finally, go to Applications > Other > Screens and Graphics to set up your display.

Whoever dreamed that up made a pretty serious mistake, I believe.

---

### Post by kebabdylan on 2008-04-25
> **hurtstotalktoyou said:**
> It's still there, just in a different place.  Go to System > Preferences > Main Menu, then choose the Applications > Other.  Then you'll see the "Screens and Graphics" checkbox, which you must check.  Finally, go to Applications > Other > Screens and Graphics to set up your display.

Whoever dreamed that up made a pretty serious mistake, I believe.

never mind. I am an idiot. Although the screens and graphics was unchecked so it didn't display in my menus until I edited it.

What actually fixed it was "enable display" check box in the ati catalyst.

like I said, I am an idiot.

---

### Post by dugonline on 2008-04-25
> **hurtstotalktoyou said:**
> It's still there, just in a different place.  Go to System > Preferences > Main Menu, then choose the Applications > Other.  Then you'll see the "Screens and Graphics" checkbox, which you must check.  Finally, go to Applications > Other > Screens and Graphics to set up your display.

Whoever dreamed that up made a pretty serious mistake, I believe.

THANK YOU SO MUCH!!!!  I am a very recent Linux convert and have dropped the dual boot safety blanket with the release of HH.  I was afraid I would have to go back to Dual boot to avoid dealing with lower screen resolution while I waited for a fix.


THANK YOU THANK YOU THANK YOU

---

### Post by athene8 on 2008-04-25
> **hurtstotalktoyou said:**
> It's still there, just in a different place.  Go to System > Preferences > Main Menu, then choose the Applications > Other.  Then you'll see the "Screens and Graphics" checkbox, which you must check.  Finally, go to Applications > Other > Screens and Graphics to set up your display.

Whoever dreamed that up made a pretty serious mistake, I believe.
Thank you *so* much for this. As another recent convert to Ubuntu minor video annoyances were no big deal for me (1 old desktop, 1 old laptop, and a eee pc). But where I was running the HH Release Candidate I wanted to do a clean install and suddenly the perfectly working Video was totally borked. After enabling the "hidden" Screens and Graphics preference and fiddling with some settings I am back to a happy 1024x768 with my Intel 82845G graphics and 10 year old Sony 200es CRT.

Thank you again!

---

### Post by AirRaven on 2008-04-25
Quick question- I assume that this *isn't* supposed to automatically resize the "Login" dialog to the maxiumum possible resolution?

It sets itself to display in 1600x1200, I believe- a resolution my monitor doesn't support, meaning that the bottom-right area of the login window gets cut out.

Any solutions? =\

---

### Post by trubshac on 2008-04-25
Many thanks hurtstotalktoyou.   I now have full resolution :)  
My wireless card (WPC54GS) is also working 'out of the box' - my laptop and I am happy, and happy to be rid of microsoft.

Thanks again.

---

### Post by jeffs0413 on 2008-05-07
hurtstotalktoyou:
Thanks for the solution. A well hidden screen
jeff

---

### Post by trubshac on 2008-08-06
Hi

If I'm posting in the wrong place, please redirect me.

I have now decide to move from ubuntu to xubuntu on this particular laptop, and I one again have the same problem that I had in my original post at the start of this thread:  I need to force xubuntu to believing that my monitor is 1200x1600, then I can use the "Display" icon within "Xfce Settings Manager" to select the same resolution (currently it only offers me 800x600 or 640x480 as ubuntu did).

Does anyone know how I can do this please?

---

### Post by trubshac on 2008-08-06
OK - I've got it sorted.
I simply booted ubuntu, copied /etc/X11/xorg.conf onto a USB stick, then booted xubuntu, made a backup safe copy of the same file (just in case), then copied the ubuntu one from the stick.  Hey presto, I can now set 1600x1200 from the menu.

---

### Post by XPuntu on 2008-09-28
This looks like a promising solution. When I try to run the program though, nothing happens. The taskbar shows the application starting then it disappears so I'm still stuck at 800x600. Is there something I should re-install?

Thanks.

---

### Post by ZxEfR on 2008-09-29
> **athene8 said:**
> Thank you *so* much for this. As another recent convert to Ubuntu minor video annoyances were no big deal for me (1 old desktop, 1 old laptop, and a eee pc). But where I was running the HH Release Candidate I wanted to do a clean install and suddenly the perfectly working Video was totally borked. After enabling the "hidden" Screens and Graphics preference and fiddling with some settings I am back to a happy 1024x768 with my Intel 82845G graphics and 10 year old Sony 200es CRT.

Thank you again!

Whatever you do don't share with the rest of us how to enable the "hidden" Screens and Graphics preferences :confused:

---

### Post by athene8 on 2008-09-29
I'm so sorry ZxEfR, it was the settings talked about earlier in this thread.
:arrow:> **hurtstotalktoyou said:**
> It's still there, just in a different place.  Go to System > Preferences > Main Menu, then choose the Applications > Other.  Then you'll see the "Screens and Graphics" checkbox, which you must check.  Finally, go to Applications > Other > Screens and Graphics to set up your display.

Whoever dreamed that up made a pretty serious mistake, I believe.

---

### Post by ZxEfR on 2008-09-29
> **athene8 said:**
> I'm so sorry ZxEfR, it was the settings talked about earlier in this thread.
:arrow:

Actually I'm the one that's sorry....I was having a bad day and took it out on you....so...sorry about that.

I read in the earlier thread how to find it. And I looked and looked and just flat out kept missing the "main menu" aspect of it. So I thought it was some secret when actually it was my stupidity.

Once again.......sorry....and thanks for your reply. As you helped me to find it after all!

---

### Post by athene8 on 2008-09-30
No problem at all.

---

### Post by SomethingFishy on 2008-10-17
> **hurtstotalktoyou said:**
> It's still there, just in a different place.  Go to System > Preferences > Main Menu, then choose the Applications > Other.  Then you'll see the "Screens and Graphics" checkbox, which you must check.  Finally, go to Applications > Other > Screens and Graphics to set up your display.

Whoever dreamed that up made a pretty serious mistake, I believe.

Hi.  I'm also having a problem getting a higher resolution but following the advice above doesn't work cos I can't select Applications>Other.  "Other" is italicised and when I click on the checkbox a check mark appears for a moment then disappears again.  Any suggestions please anybody?  I'm feeling like the Heron's ready to spear me with it's nasty beak, hence my choice of username!

---

