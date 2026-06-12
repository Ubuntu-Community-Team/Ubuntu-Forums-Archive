---
title: "Ubuntu 10.04 LTS upgrade breaks visual effects and sleep mode"
date: 2010-04-30
forum: Multimedia Software
---

### Post by Spartan-196 on 2010-04-30
After upgrading to 10.04 and rebooting I found that I no longer have the title bar on any of my windows so this means no minimize, maximize, or close buttons also. After some finagling I found that if I disable the Visual Effects under the appearance menu by setting it to none i get those button back. I did have it set to Extra at the time of the upgrade. Now changing the setting to either normal or extra removes the title bar. Also it seems to have lost its ability to enter sleep mode.

---

### Post by LeBurt on 2010-04-30
I have the exact same problem. I'm guessing there is some file in our home directory that breaks something, as I did a clean install but preserved /home.

---

### Post by Spartan-196 on 2010-04-30
I am unsure if is in the Home folder or not, when logged in a s root it does the same thing when setting visual effects to normal or extra. I have also removed xorg and reinstalled it

---

### Post by therealro on 2010-04-30
Same problem here on fresh install.

---

### Post by therealro on 2010-04-30
Just found something on another forum:

"Ubuntu 10.04 beta 1 places libGL.so* to /usr/lib/mesa/ and configures  dynamic loader so that it takes precedence over more conventional  /usr/lib/libGL.so*.
The simplest solution is to edit /etc/ld.so.conf putting /usr/lib on the  first line, and then run ldconfig to rebuild loader cache. 		 		 		  	"

I have to check if this works.. in the morning :-$

---

### Post by dannyauble on 2010-05-01
This did work for me.

My /etc/ld.so.conf now reads...

/usr/lib
include /etc/ld.so.conf.d/*.conf

---

### Post by terrybooth on 2010-05-02
I have this problem and tried this fix. Unfortunately, it did not work for me.

---

### Post by abelletti on 2010-05-02
I have this problem as well (upgrade from 9.10), and this didn't fix it for me.

Allen

---

### Post by cursief on 2010-05-02
Sounds to me like a driver issue. What video card do you have?

---

### Post by lyks on 2010-05-02
I have a Dell Vostro 1520, the chipset is Intel GM45. 
I had the same problem. After upgrading to Lucid, visual effects simply  gone. I tried to re-activate them but it didn't work. 
I remove, using synaptic, all nvidia files (nvidia-****). I Restarted,  and now visual effects are working fine.

---

### Post by Spartan-196 on 2010-05-02
Needless to say I broke down and did a fresh install of 10.04 last night formatted the partition and all :/ 
My visual effects seem to be doin ok now, however I still have the problem of no longer being able to enter sleep or hibernate

---

### Post by totalhealth on 2010-05-03
I had the same problem when I upgraded from 8.04 to 10.04.  I uninstalled compiz and emerald and then reinstalled both and it fixed the problem for me.

---

### Post by Spliff85555 on 2010-05-04
Missing window decorations here too, no title bar, no resize handles, just one difference: it starts with "no visual effects" and I have to turn it on to get the title bars (after waiting almost an eternity while it's searching for drivers which are already installed).

NVIDIA Geforce 9600M GT, Driver version 195.36.15
Upgraded from 9.10

I have to switch the visual effects EVERY TIME I LOGIN.

Reinstalling compiz didn't help, emerald wasn't and isn't installed.

Any help?
- Spliff

---

### Post by VipX1 on 2010-05-04
> **dannyauble said:**
> This did work for me.

My /etc/ld.so.conf now reads...

/usr/lib
include /etc/ld.so.conf.d/*.conf

Unfortunately this did not work for me. As a temporary solution I have the compiz fusion icon mentioned in my start-up applications and when the the compiz fusion icon starts the windows manager starts or reloads (I don't know which) and I get the windows decorations. My windows manager is set to Compiz in the Compiz Fusion Icon and in gconf-editor.
This is a solution but there's a delay between the desktop starting and the windows decorations being added and it looks crap. Anyway it's not right..

---

### Post by eric_son on 2010-05-04
Hey!  The same thing happens to me as well.

I just finished upgrading this morning.

At first boot, I have no title bar.  But if I logoff and logon again, the title bar problem is fixed.

Kinda annoying.

---

### Post by wekebu on 2010-05-04
I got it fixed.  Another thread recommended going into System> Appearances> Visual Effects Tab.  Change the setting from None to either Normal or Extra.  This fixed all my visual problems from no borders, to docking over the main panel.

However, it didn't save after a reboot.  I went into System> Startup Applications> Startup Programs and unchecked my graphic card, in my case nVidia.  I'm not sure if this next step is required, but there's another tab in Startup Programs, Remember current session" (or something to this effect, I'm not at that machine right now.

Hope this helps.

---

### Post by blz84 on 2010-05-05
Same problem in my case, everytime I have to enable the effects manually :/ By default it is set to 'none' and only after changing to 'normal' or 'extra' I can see the window borders. 

Might be that compiz does not autostart?

---

### Post by amoeba801 on 2010-05-05
It looks as though you are correct: compiz does not seem to start on boot. 

A work around for me was to add compiz as a new item in System->Preferences->Startup Applications.

---

### Post by Andres1967 on 2010-05-05
> **wekebu said:**
> I got it fixed.  Another thread recommended going into System> Appearances> Visual Effects Tab.  Change the setting from None to either Normal or Extra.  This fixed all my visual problems from no borders, to docking over the main panel.

However, it didn't save after a reboot.  I went into System> Startup Applications> Startup Programs and unchecked my graphic card, in my case nVidia.  I'm not sure if this next step is required, but there's another tab in Startup Programs, Remember current session" (or something to this effect, I'm not at that machine right now.

Hope this helps.



This did it for me. But somewhere I think it's not the right solution... Even though I'm new.

---

### Post by shihkster1015 on 2010-05-05
i would just go for a clean install. it's the best way to have a stable machine.

---

### Post by Spliff85555 on 2010-05-05
> **shihkster1015 said:**
> i would just go for a clean install. it's the best way to have a stable machine.
Thanks for your comment. This

a) really helps
b) prevents other users from posting more constructive suggestions
c) sound and feels like Windoze

So any help anyone?
- Spliff

---

### Post by .gr.c. on 2010-05-05
Hey Guys,
I have just upgraded from 9.10 to 10.04. I had the same effect:
No visual effects after login, missing borders, etc. Every time I logged on I had to turn visual effects on manually.
In one of the previous posts in this thread someone said that compiz doesn't get started at logon. I checked this out and that's true. So my simple workaround is:


[LIST=1]
[*]Go to System > Preferences > Startup applications
[*]Click "Add" (or whatever it is in English version, I use Polish)
[*]In "name" inputbox type "Compiz"; in "command" input box type "/usr/bin/compiz --replace"
[*]Click "Add"
[*]Click "Close"
[*]Logoff and log on back
[/LIST]

Worked for me.

Thanks for the hint.
I have no clue why compiz refuses to start automatically at logon. But really have no time form investigation.

Greg

---

### Post by Mr_Lazy on 2010-05-06
Thanks .gr.c. worked for me a treat, much appreciate you sharing this.

---

### Post by bluntknife on 2010-05-06
> **.gr.c. said:**
> Hey Guys,
I have just upgraded from 9.10 to 10.04. I had the same effect:
No visual effects after login, missing borders, etc. Every time I logged on I had to turn visual effects on manually.
In one of the previous posts in this thread someone said that compiz doesn't get started at logon. I checked this out and that's true. So my simple workaround is:


[LIST=1]
[*]Go to System > Preferences > Startup applications
[*]Click "Add" (or whatever it is in English version, I use Polish)
[*]In "name" inputbox type "Compiz"; in "command" input box type "/usr/bin/compiz --replace"
[*]Click "Add"
[*]Click "Close"
[*]Logoff and log on back
[/LIST]

Worked for me.

Thanks for the hint.
I have no clue why compiz refuses to start automatically at logon. But really have no time form investigation.

Greg

Thanks.  This worked for me too.

---

### Post by derekweber on 2010-05-07
Ditto for me. Thanks to .g.rc.

Running [FONT="Courier New"]/usr/bin/compiz --replace[/FONT] as a Startup item worked for me after logout/login and reboot. Still can't turn on desktop effects but it's a work machine so I'm not fussed.

Some more details if useful to anyone:

[LIST]
[*]amd64 version of Ubuntu
[*]nVidia Quadro FX1800 768Mb graphics card
[*]Installing downloaded nvidia binaries failed, even when attempting to compile against the new kernel
[*]logged in in low-graphics mode and installed via the Hardware Drivers UI - took a while but it did work, though without any window decorations
[*]running metacity --replace gave me window decorations but only while it was a foreground process (ie. no &). Whut?!
[*]System->Appearance->Visual Effects is set to None.
[*]When I tried to set it to Normal or Extra it bombed claiming desktop effects couldn't be enabled (whut?!)
[*]However, despite telling me I couldn't have nice graphics and setting itself back to None, it did give me window decorations. Yay!
[*]Tried the compiz --replace as a startup item, logged out and logged back in and all seems good.
[/LIST]

---

### Post by utkarsh009 on 2010-05-12
> **Spartan-196 said:**
> Needless to say I broke down and did a fresh install of 10.04 last night formatted the partition and all :/ 
My visual effects seem to be doin ok now, however I still have the problem of no longer being able to enter sleep or hibernate

found simplest solution.
just go to synaptic package manager and type "compiz" in search box. then install all packages which contain compiz in their name. (you will be asked to mark some extra packages which contain "mesa" in their name which i think solved problem.) then add "fusion-icon" to startup apps (click on add and type        "fusion-icon" in the command box without inverted commas.)
update: now you don't have to add "fusion-icon" to startup apps. instead add "compiz --replace" (without inverted commas)

---

### Post by triple.eh on 2010-06-16
I had the same situation where visual effects disappeared after reboot or logout.

This was a fresh install of the Ubuntu 10.04LTS Desktop using the Nvidia restricted driver v195.

Adding Compiz to the Startup Applications fixed it for me.  Now I can reboot and logout with visual effect settings intact.

---

### Post by Mr_Lazy on 2010-07-07
> **triple.eh said:**
> Adding Compiz to the Startup Applications fixed it for me.

It worked for me too for a couple of reboots... but now every time I boot I have to enable the effects. It is a little disappointing that when you upgrade so many things stop working.... :(

Any other ideas?

Thanks,
Stephen

---

### Post by robc02 on 2010-07-13
Same problem here. Fresh install of 10.04. Nvidia GeForce3 Ti200 using proprietary driver (nvidia-glx-96). 
Tried to start compiz from terminal using:

> /usr/bin/compiz --replace



but got the message:
> /usr/bin/compiz (core) - Warn: No GLXFBConfig for depth 32

Launching fallback window manager


Visual effects worked OK in Hardy Heron.

---

### Post by robc02 on 2010-07-13
Solved it! I added these lines to the Screen section of xorg.conf:

> Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"

I found this in a couple of places, this being one of them:

[http://organicveggie.wordpress.com/2007/06/02/no-glxfbconfig-for-depth-32/]("http://organicveggie.wordpress.com/2007/06/02/no-glxfbconfig-for-depth-32/")

---

