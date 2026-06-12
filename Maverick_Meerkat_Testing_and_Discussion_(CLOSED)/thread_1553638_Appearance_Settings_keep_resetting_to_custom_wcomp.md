---
title: "Appearance Settings keep resetting to custom w/compiz on reboot"
date: 2010-08-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by crjackson on 2010-08-15
I have a notebook that I generally like to use without desktop effects (it's an old beater).  I always turn off the desktop effects, but with Maverick...  Well it resets to custom on every reboot.

Is this just me or is anyone else getting this too?  Does anyone know how (without removing compiz) to fix this?

---

### Post by mc4man on 2010-08-15
Well then remove the simple-ccsm package and it will stay on "none"
Whether there is any difference between the 'minimal' or default profile and 'none' haven't a clue - never used or will use simple-ccsm

---

### Post by crjackson on 2010-08-15
> **mc4man said:**
> Well then remove the simple-ccsm package and it will stay on "none"
Whether there is any difference between the 'minimal' or default profile and 'none' haven't a clue - never used or will use simple-ccsm

Amazing, I didn't even realize I had installed it.

---

### Post by crjackson on 2010-08-16
I should have guessed it was too good to be true.  I still have to disable desktop effects on every reboot.  Removing simple-ccsm changed nothing.

Any other things to try?

---

### Post by ranch hand on 2010-08-16
Remove compiz?  I do not know if you can without removing other things.

I never use it but have never tried to remove it either.

You might want to look at your /.gconf/desktop/gnome/session and see if it is like this;
```

<?xml version="1.0"?>
<gconf>
    <entry name="windowmanager" mtime="1275855362" type="string">
        <stringvalue>metacity</stringvalue>
    </entry>
</gconf>

```

---

### Post by mc4man on 2010-08-16
> You might want to look at your /.gconf/desktop/gnome/session and see if it is like this;.....
That's what I have here and it's never moved off of 'none'

---

### Post by crjackson on 2010-08-17
> **ranch hand said:**
> Remove compiz?  I do not know if you can without removing other things.

I never use it but have never tried to remove it either.

You might want to look at your /.gconf/desktop/gnome/session and see if it is like this;
```

<?xml version="1.0"?>
<gconf>
    <entry name="windowmanager" mtime="1275855362" type="string">
        <stringvalue>metacity</stringvalue>
    </entry>
</gconf>

```

I've got the same.  Still trying to figure this out.

---

### Post by ranch hand on 2010-08-17
In /.config/compiz/compizconfig I have;
```

[gnome_session]
profile = 
plugin_list_autosort = true

```
You probably do too.  I would try changing "true" to "false".

You probably haven't broken your system for a while anyway.  Might as well try it.  There is always a chance that you can change it back.

---

### Post by ranch hand on 2010-08-17
There is also in /.gconf/desktop/gnome/applications/window_manager;
```

<gconf>
    <entry name="current" mtime="1262039455" type="string">
        <stringvalue>/usr/bin/compiz</stringvalue>
    </entry>
    <entry name="default" mtime="1240479228" type="string">
        <stringvalue>/usr/bin/compiz</stringvalue>
    </entry>
</gconf>

```
I would be tempted by that too.

I wonder what, if anything, would break if you changed that to metacity.

---

### Post by mc4man on 2010-08-17
open gconf-editor -  apps - metacity - general,  enable it as the compositing manager and see..

---

### Post by crjackson on 2010-08-17
> **mc4man said:**
> open gconf-editor -  apps - metacity - general,  enable it as the compositing manager and see..

Okay, I'm going to run the gamut and report back.  This being the last as I really don't want any compositing on this lappy.

---

### Post by crjackson on 2010-08-17
Okay so I've tried them all, still no good. SOMEHOW even with Metacity's compositing turned on, it also loads compiz and I have to turn it off by hand.

I think it's about time to reinstall Maverick from scratch.  This install started as Lucid and Pre-Alpha Maverick, so I guess it's just about that time now.

---

### Post by Starks on 2010-08-21
I have this problem too. Comes back during every single development cycle.

---

### Post by crjackson on 2010-08-21
> **Starks said:**
> I have this problem too. Comes back during every single development cycle.

Glad to know I'm not alone on this.  It's actually the first time I've ever noticed it.

---

### Post by Starks on 2010-08-21
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/621991](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/621991)

Enjoy.

---

### Post by crjackson on 2010-08-21
> **Starks said:**
> [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/621991](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/621991)

Enjoy.

Cool, I threw my hat into the ring too...

---

### Post by Jonners59 on 2010-08-27
I have this on my wife's Viao (and it's pink - agh).  I just upgraded from 9.10 to 10.4 earlier this week.  The difference is it defaults to None and She wants Extra, she needs it too as it auto opens Firefox on start, which has no title bar and will not move, so I have to Ctr+Q to close it, then go in to System, etc. to rest the Appearance, then all is fine.

I shall keep an eye on this thread for resolution or bug fix notification.

---

### Post by crjackson on 2010-08-27
> **Jonners59 said:**
> I have this on my wife's Viao (and it's pink - agh).  I just upgraded from 9.10 to 10.4 earlier this week.  The difference is it defaults to None and She wants Extra, she needs it too as it auto opens Firefox on start, which has no title bar and will not move, so I have to Ctr+Q to close it, then go in to System, etc. to rest the Appearance, then all is fine.

I shall keep an eye on this thread for resolution or bug fix notification.

Mine was defaulting to custom, but now it shows nothing selected BUT compiz is still running.  I'm sure it will all be sorted out soon.

It's my understanding that there is only ONE active DEV who works on compiz and the project is in danger.  I really wish canonical would take the ropes and adopt compiz on it's own.

---

### Post by mc4man on 2010-08-27
I normally use compiz (nvidia drivers) and never use Appearances -> effects, instead just installing ccsm and enabling/disabling from there, so nothing is checked in 'effects'

Atm, for various reasons,  am not using compiz on this laptop, (nvidia drivers), so simply checked "none" in effects and set metacity as compositing manager in gconf.
As screen shows compiz doesn't run.
I guess it may, as it often does, come down to the hardware..?

---

