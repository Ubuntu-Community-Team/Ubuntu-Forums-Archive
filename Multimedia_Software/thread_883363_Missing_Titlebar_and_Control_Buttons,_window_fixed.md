---
title: "Missing Titlebar and Control Buttons, window fixed"
date: 2008-08-07
forum: Multimedia Software
---

### Post by trebllaw on 2008-08-07
I finally got my NVIDIA GeForce 5500 working with ubuntu after installing the right drivers. Got the visual effects working (cube, switching, avant windows navigator, and the likes).

As I was toying with the software installed, to see what each software would do, i clicked on the compiz fusion icon on Applications > System Tools. Suddenly, the visual effects where turned off. I turned it on again by going to System > Preferences > Appearance, click on the Visual Effects and click on the Normal RAdio Button. But after i turned turned it to normal, the title bar and control buttons of all windows i open is gone along with the window borders. It is also fixed, i cant even resize them. Sure i got the avant window navigator back (the only thing i got when turning on the visual effect again) but now i cant move any window i open.

I tried shutting down fusion icon from the system monitor and doing a reboot but the problem persist. When I turn off the Visual Effects, the title bar, control buttons, window border will magically appear again but i have no avant window navigator and visual effects.

Does anybody know how to fix this problem? Any ideas?

---

### Post by overdrank on 2008-08-07
> **trebllaw said:**
> I finally got my NVIDIA GeForce 5500 working with ubuntu after installing the right drivers. Got the visual effects working (cube, switching, avant windows navigator, and the likes).

As I was toying with the software installed, to see what each software would do, i clicked on the compiz fusion icon on Applications > System Tools. Suddenly, the visual effects where turned off. I turned it on again by going to System > Preferences > Appearance, click on the Visual Effects and click on the Normal RAdio Button. But after i turned turned it to normal, the title bar and control buttons of all windows i open is gone along with the window borders. It is also fixed, i cant even resize them. Sure i got the avant window navigator back (the only thing i got when turning on the visual effect again) but now i cant move any window i open.

I tried shutting down fusion icon from the system monitor and doing a reboot but the problem persist. When I turn off the Visual Effects, the title bar, control buttons, window border will magically appear again but i have no avant window navigator and visual effects.

Does anybody know how to fix this problem? Any ideas?

HI and I am assuming you are using Hardy. If you are using emerald then you may try the command ```
emerald --replace
```
If not then you may look at the advance desktop effects settings (ccsm) under system, preference and ensure that window decorations is checked.

---

### Post by trebllaw on 2008-08-08
i think im not using emerald.. is metacity a composting manager? because i installed a theme via System > Preferences > Appearance.. if that's what it means to use emerald, then i am using emerald..

but i will your suggestio anyway.. thanks..

will post if it does not solve the problem..

---

### Post by Oldsoldier2003 on 2008-08-08
> **trebllaw said:**
> i think im not using emerald.. is metacity a composting manager? because i installed a theme via System > Preferences > Appearance.. if that's what it means to use emerald, then i am using emerald..

but i will your suggestio anyway.. thanks..

will post if it does not solve the problem..

if you are using metacity then

```
metacity --replace
``` should sort you out.

---

### Post by trebllaw on 2008-08-08
what does metacity --replace or emeralde --replace do if i may ask?

---

### Post by Oldsoldier2003 on 2008-08-08
> **trebllaw said:**
> what does metacity --replace or emeralde --replace do if i may ask?

It replaces the currently running window manager with metacity. In effect its a reload of your window manager.

---

### Post by trebllaw on 2008-08-08
oh ok.. now i know what it does. will try it later when i get home..

---

### Post by KentonS on 2008-10-15
I'm having a similar problem, but only with new accounts I create with my primary user account. Once they're created and I log in, there is no Title Bar on any windows. I brought up a terminal session and ran "metacity --replace". The Title Bar appeared, but I never got a command prompt back. I had to use <Ctrl-C>. Of course, at that point the Title Bar disappeared. Should I have run the command some other way and/or somewhere else?

Moreover, when I'm logged in to a newly-created account, when I click on the red icon in the upper right corner - the one that allows me to log off, shut down, etc. - nothing happens, sometimes for several minutes. Occasionally nothing ever happens, and I have to manually power down.

I'm running Gnome 2.20.1 on Ubuntu 7.10.

I remember being prompted to install some compiz components just after I got my laptop. Looking at the Synaptics History file, I see that I installed compizconfig-settings-manager (0.5.2+git20070912-0ubuntu1) and
python-compizconfig (0.5.2+git20070912-0ubuntu1). A few days later I decided I didn't like what was happening - among other things, a shaky screen when viewing images - and I removed compiz, compiz-core, compiz-fusion-plugins-extra, compiz-fusion-plugins-main, compiz-gnome, compiz-plugins, and
compizconfig-settings-manager. Some time later I reinstalled compizconfig-settings-manager. I don't remember why. Whatever the reason, it was probably wrong headed. (Hey... I'm new to all this! ;)).

I notice that other compiz components are installed as well - mostly libcompiz... packages and libdecoration0. (That last one raises a yellow flag; it has to do with "drawing the window borders and title bar of windows managed by Compiz".)

So that's the agonizingly-long description of my situation. I know it's probably TMI, but I'm trying to anticipate questions from responders.

(BTW: All this installing and uninstalling happened after I created my primary user account and before I created the accounts that are having the Title Bar problem. Coincidence? I think not! LOL)

Thanks very much for your patience in reading this, and thanks in advance for any help anyone can provide.

---

### Post by KentonS on 2008-11-06
Well, it took some digging, but I found the problem. Everything works fine now. Thanks for all the help!

---

