---
title: "Unity will be better? How to disable it?"
date: 2011-01-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by sartic on 2011-01-02
From what I see in alpha. It is useless for me.
Have to ctrl+alt+T to reach terminal.
Have no categoriazed access to applications (main menu).
Panel on left should be hideable (automatic if u do not use touch access).
Second key on mouse should be used for more options on empty space of panel.
Some kind of gadgets should be implemented or better use old gnome (i miss my gnome weather :)
etc.

And question what is cleanest way to disable it?

---

### Post by zika on 2011-01-02
Log-in into Classic Desktop... I do...
Veliki pozdrav za sve pod Marjanom!

---

### Post by dino99 on 2011-01-02
from synaptic:
- uninstall ubuntu-desktop (only a meta-package)
- uninstall everything about unity

that it :)

---

### Post by 098799 on 2011-01-02
When the terminal (or any other application) is open click RMB on it's icon and "keep in launcher".

Main menu is still in developement.

Panel is hideable. Open compiz config => unity plugin.

---

### Post by sartic on 2011-01-02
> **zika said:**
> Log-in into Classic Desktop... I do...
Veliki pozdrav za sve pod Marjanom!

Thx for tip :)

ps: fala i pozdrav

---

### Post by sartic on 2011-01-02
> **098799 said:**
> When the terminal (or any other application) is open click RMB on it's icon and "keep in launcher".

Main menu is still in developement.

Panel is hideable. Open compiz config => unity plugin.

I was talking about empty space.
Nice idea will be second key on empty and configure Unity.

---

### Post by sartic on 2011-01-02
> **dino99 said:**
> from synaptic:
- uninstall ubuntu-desktop (only a meta-package)
- uninstall everything about unity

that it :)

How do you uninstall only meta-package?
Give me cmd line ....

---

### Post by amano on 2011-01-02
Do you know that it is not ready?

Do you understand the sense of alpha-testing, that things are uncomplete and you have to file bugs to make the software better and complete?

Uninstalling it will not help this mission.

If you uninstall everything that is currently broken or not useful, you will have to uninstall probably everything within natty at some point of the development circle.

---

### Post by ronacc on 2011-01-02
has unity now becone the sine qua non of Ubuntu ? are there not many other things that can be tested and filed upon or is unity the only thing that matters ? If so perhaps we should just change the name to Unity OS and be done with it .

---

### Post by zika on 2011-01-02
Unity is new &#8222;plymouth&#8220;...
Nevertheless, even though I do not like Unity (and it doesn't, yet work properly on my install) I do not propose uninstalling it... I do enter through that door once in a while just to see the &#8222;future&#8220;... Yes, I do not have &#8222;splash&#8220; in kernel line, just not to look at plymouth...

---

### Post by zika on 2011-01-02
Unity is new &#8222;plymouth&#8220;...
Nevertheless, even though I do not like Unity (and it doesn't, yet, work properly on my install) I do not propose uninstalling it... I do enter through that door once in a while just to see the &#8222;future&#8220;... Yes, I do not have &#8222;splash&#8220; in kernel line, just not to look at plymouth...

---

### Post by zika on 2011-01-02
Unity is new „plymouth“...
Nevertheless, even though I do not like Unity (and it doesn't, yet work properly on my install) I do not propose uninstalling it... I do enter through that door once in a while just to see the „future“... Yes, I do not have „splash“ in kernel line, just not to look at plymouth...

---

### Post by zika on 2011-01-02
Unity is new „plymouth“...
Nevertheless, even though I do not like Unity (and it doesn't, yet work properly on my install) I do not propose uninstalling it... I do enter through that door once in a while just to see the „future“... Yes, I do not have „splash“ in kernel line, just not to look at plymouth...

---

### Post by dino99 on 2011-01-02
> **zika said:**
> Unity is new „plymouth“...
Nevertheless, even though I do not like Unity (and it doesn't, yet work properly on my install) I do not propose uninstalling it... I do enter through that door once in a while just to see the „future“... Yes, I do not have „splash“ in kernel line, just not to look at plymouth...

ah ah but plymouth is still new :( (was a kid, now a teen)

---

### Post by dino99 on 2011-01-02
> **sartic said:**
> How do you uninstall only meta-package?
Give me cmd line ....

goto : system admin synaptic (no cmd line here, its selectable with mouse, fust right click on the package & choose "complete remove")

---

### Post by sartic on 2011-01-02
> **dino99 said:**
> goto : system admin synaptic (no cmd line here, its selectable with mouse, fust right click on the package & choose "complete remove")

Last time I did that I get broken system :)

---

### Post by sartic on 2011-01-02
> **amano said:**
> Do you know that it is not ready?

Do you understand the sense of alpha-testing, that things are uncomplete and you have to file bugs to make the software better and complete?

Uninstalling it will not help this mission.

If you uninstall everything that is currently broken or not useful, you will have to uninstall probably everything within natty at some point of the development circle.

I understand your way of thinking. My way is freedom to choose what to do with OS installed on my computer. Linux is freedom to choose ;)

Another bad news for me is Compiz is now melted width ubuntu-desktop.

---

### Post by mc4man on 2011-01-02
> Unity will be better?
certainly

> How to disable it?
Just login to Classic Desktop. If the unity launcher shows up then open ccsm ( compizconfig-settings-manager) and disable the unity plugin

> Another bad news for me is Compiz is now melted width ubuntu-desktop
Seems quite unlikely unless you've done something not normal

(If you wanted to remove the unity libs this would do and should not touch compiz
sudo apt-get purge libunity*

---

### Post by Mr. Picklesworth on 2011-01-02
> **sartic said:**
> Another bad news for me is Compiz is now melted width ubuntu-desktop.

Unity is a Compiz plugin. You can just disable it as usual if you want.
(Compositing in Compiz is also its own plugin now).

The "classic desktop session", as far as I am aware, loads Metacity but you can throw whatever window manager you want in there.

---

### Post by Harry33 on 2011-01-02
> **sartic said:**
> I understand your way of thinking. My way is freedom to choose what to do with OS installed on my computer. Linux is freedom to choose ;)

Another bad news for me is Compiz is now melted width ubuntu-desktop.

No it is not.
Package ubuntu-desktop does not depend on compiz, it only recommends it.
But ubuntu-desktop depends on unity, which in turn, depends on compiz-core.
So if you really are not satisfied selecting gnome-classic session and insist on uninstalling unity, you will have to uninstall ubuntu-desktop first.
And after uninstalling unity you can very well keep compiz untouchable.

BTW ubuntu-desktop is only a meta package. It really does not harm your system to remove it. It is there to make it easy for noobies to keep their system the way Canonical has planned.

---

### Post by ronacc on 2011-01-02
you can uninstall unity with out consequences but you will loose the convenience of ubuntu destop for keeping up to date . log in to a "classic desktop" session open ccsm and uncheck unity plugin as described by others then open synaptic and search on unity and uninstall everything with the word unity in it , this worked for me , YMMV .

---

### Post by mc4man on 2011-01-02
nothing

---

### Post by Merk42 on 2011-01-02
I don't like X for the reasons a, b, c; rather than file bugs to fix those reasons in X, I refuse to use X at all.
Get off my lawn.

---

### Post by jerrylamos on 2011-01-02
> **amano said:**
> Do you know that it is not ready?

Do you understand the sense of alpha-testing, that things are uncomplete and you have to file bugs to make the software better and complete?

Uninstalling it will not help this mission.

If you uninstall everything that is currently broken or not useful, you will have to uninstall probably everything within natty at some point of the development circle.

Well, "Unity" is busted on my ati radeon mobility 7500.  I can get Natty "classic" up on it with some gymnastics.  Bug filed, no action (yet).  It appears "Unity" is asking compiz to do something that won't work, and nobody in "Unity" has had time to make it stop doing that.  Likely "Unity" folks are pretty busy.

As far as I can tell "Unity" will never run on my two intel integrated video graphics pc's, no matter how capable and useful these pc's are to me running real applications.

"Unity" will run on this ati radeon xpress 200.  I just haven't studied what to do with Unity.

So I'm batting 75% failure rate on Unity on my four test pc's.

Yes I do file launchpad bugs where feedback could be useful.

Jerry

---

### Post by ronacc on 2011-01-02
> **Merk42 said:**
> I don't like X for the reasons a, b, c; rather than file bugs to fix those reasons in X, I refuse to use X at all.
Get off my lawn.

It is not the bugs in unity nor that it is not yet finished that bothers me about unity , I am here to help find and fix bugs and help polish applications . What bothers me about unity is much deeper than bugs and "smoothness" , it is the very concept of unity that I find unacceptable .

---

### Post by VMC on 2011-01-02
> **Merk42 said:**
> I don't like X for the reasons a, b, c; rather than file bugs to fix those reasons in X, I refuse to use X at all.
Get off my lawn.

I didn't realize you had an option. What are you using in place of X?

---

### Post by Merk42 on 2011-01-02
> **ronacc said:**
> It is not the bugs in unity nor that it is not yet finished that bothers me about unity , I am here to help find and fix bugs and help polish applications . What bothers me about unity is much deeper than bugs and "smoothness" , it is the very concept of unity that I find unacceptable .It was referring to the OP
> **VMC said:**
> I didn't realize you had an option. What are you using in place of X?
Y, clearly.

I meant X as in {insert program here}, not X.org (which I guess eventually would have Wayland as an alternative)

---

### Post by sartic on 2011-01-03
> **Merk42 said:**
> I don't like X for the reasons a, b, c; rather than file bugs to fix those reasons in X, I refuse to use X at all.
Get off my lawn.

I ... lost u man :)
I have my reasons. Like always I seem to be bad man but I speak for many silent ;)

---

### Post by sartic on 2011-01-03
> **ronacc said:**
> It is not the bugs in unity nor that it is not yet finished that bothers me about unity , I am here to help find and fix bugs and help polish applications . What bothers me about unity is much deeper than bugs and "smoothness" , it is the very concept of unity that I find unacceptable .

That's my point also. They are trying to brand some kind of "dock" width (i hope) some kind of better way of managing your windows.
I wish them luck (also for waylandish stuff :)

OT: Meego(Moblin) has best GUI I saw until now for newbies and small screens. Lubuntu is easier for newcomers from Win but it miss many stuff from classic gnome desktop.

---

### Post by zika on 2011-01-03
> **Mr. Picklesworth said:**
> Unity is a Compiz plugin. You can just disable it as usual if you want.
(Compositing in Compiz is also its own plugin now).

The "classic desktop session", as far as I am aware, loads Metacity but you can throw whatever window manager you want in there.Such as FluxBox...

---

