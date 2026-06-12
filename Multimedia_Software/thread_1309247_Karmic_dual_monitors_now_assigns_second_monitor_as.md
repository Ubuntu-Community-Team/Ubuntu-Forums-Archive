---
title: "Karmic dual monitors now assigns second monitor as primary"
date: 2009-11-01
forum: Multimedia Software
---

### Post by shakeyB on 2009-11-01
Hi

Jaunty set up my dual monitors out of the box without me having to lift a finger.

In Karmic my second (vga) monitor is assigned as the primary with the launch bar and dock appearing there, which is a little annoying as i have to keep both monitors on even if I only need one.

Anyone know what has changed between releases to cause this and know how I can solve it?

I've seen similar problems listed for nvidia cards, the solution was to issue twinview specific commands in xorg.conf to assign the primary monitor to the dvi output. Anyone know if a way i can do this for ati?

I tried installing fglrx and the proprietry drivers from the ati site, both resulted in blank screens after login.

```

lspci | grep VGA

01:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
```

---

### Post by asimong on 2009-11-03
I am also disappointed. Jaunty worked just fine, but now having installed Karmic, not only has my dual screen setup been forgotten, but "Configure Display Settings" does not do what it should do. Not as if I'm using any different hardware -- nothing has changed on that front. I seem to be stuck with mirrored screens.

---

### Post by seventeener on 2009-11-09
Hi, I use Samsung NC10 and sometimes plug an external monitor for a dual-monitor setup. After an upgrade to Karmic my monitor switching scripts stopped working. Luckily, the fix was easy. First of all, correct names of outputs in the xrandr command, i.e. VGA to VGA1 and LVDS to LVDS1. Second, explicitly choose the external monitor as the primary one (see below). 
For dual-monitor with the external as the primary one:  
```
xrandr --output VGA1 --primary
xrandr --output VGA1 --auto --pos 0x0 --output LVDS1 --auto --below VGA1
```
For going back to the laptop screen only:
```
xrandr --output VGA1 --off --output LVDS1 --auto
```
For convenience I run these commands in scripts with assigned keyboard shortcuts (see how to assign shortcuts [here]("http://gsmblog.net/universal-shortcuts-in-gnome")).

---

### Post by edwardmccaughan on 2009-11-19
Thanks seventeener!

I was wondering how to do exactly that!

---

### Post by kdford on 2010-04-26
Thanks for the instructions.  This worked PERFECTLY for me.

---

### Post by frozenfyer on 2010-07-01
I had a similar problem with my dual monitor setup that I solved. One screen was connected to DVI and the other to VGA. Use the following to figure out what each screen is called:

```

xrandr --prop

```

You should see something like VGA-1 or DVI-D-1. Do the following to set the primary screen:

```

xrandr --output DVI-D-1 --primary

```

Replacing DVI-D-1 with whichever screen you want as the primary.

---

### Post by brycenesbitt on 2010-10-28
Thanks, the solution is great.  Putting this in the monitor control panel is a registered idea here: [http://brainstorm.ubuntu.com/idea/17526/](http://brainstorm.ubuntu.com/idea/17526/) and can be voted for.

---

### Post by oldmankit on 2011-01-02
> **seventeener said:**
> Hi, I use Samsung NC10 and sometimes plug an external monitor for a dual-monitor setup. After an upgrade to Karmic my monitor switching scripts stopped working. Luckily, the fix was easy. First of all, correct names of outputs in the xrandr command, i.e. VGA to VGA1 and LVDS to LVDS1. Second, explicitly choose the external monitor as the primary one (see below). 
For dual-monitor with the external as the primary one:  
```
xrandr --output VGA1 --primary
xrandr --output VGA1 --auto --pos 0x0 --output LVDS1 --auto --below VGA1
```For going back to the laptop screen only:
```
xrandr --output VGA1 --off --output LVDS1 --auto
```For convenience I run these commands in scripts with assigned keyboard shortcuts (see how to assign shortcuts [here]("http://gsmblog.net/universal-shortcuts-in-gnome")).

That worked fine for me in Maverick.  Thanks!

---

### Post by GT-Force on 2011-02-28
How can one make this permanent. After I execute this, it works, but after logging out and back in, it's back to how it was.

Until Ubuntu coders pull their heads out of their, ummm, ASCII terminals and see that at least 98% of computer users use GUI and put this into the monitor setup, we'll have to do it the hard way.

---

### Post by adduds on 2011-03-18
> **seventeener said:**
> Hi, I use Samsung NC10 and sometimes plug an external monitor for a dual-monitor setup. After an upgrade to Karmic my monitor switching scripts stopped working. Luckily, the fix was easy. First of all, correct names of outputs in the xrandr command, i.e. VGA to VGA1 and LVDS to LVDS1. Second, explicitly choose the external monitor as the primary one (see below). 
For dual-monitor with the external as the primary one:  
```
xrandr --output VGA1 --primary
xrandr --output VGA1 --auto --pos 0x0 --output LVDS1 --auto --below VGA1
```
For going back to the laptop screen only:
```
xrandr --output VGA1 --off --output LVDS1 --auto
```
For convenience I run these commands in scripts with assigned keyboard shortcuts (see how to assign shortcuts [here]("http://gsmblog.net/universal-shortcuts-in-gnome")).

good on ya mate wrote my scripts worked great

also promoted the solution to this problem on ubuntu brain storm

[http://brainstorm.ubuntu.com/idea/17526/](http://brainstorm.ubuntu.com/idea/17526/)

---

### Post by adduds on 2011-03-18
> **GT-Force said:**
> How can one make this permanent. After I execute this, it works, but after logging out and back in, it's back to how it was.

Until Ubuntu coders pull their heads out of their, ummm, ASCII terminals and see that at least 98% of computer users use GUI and put this into the monitor setup, we'll have to do it the hard way.

just notice this post

make the script run on boot using startup applications :)

---

### Post by petsoukos on 2011-04-30
> **adduds said:**
> just notice this post

make the script run on boot using startup applications :)

Thanks! Exactly what I was looking for. :)


System->Prefs->Startup Applications

Then Click Add

Name: Whatever
Command: xrandr --output NAMEOFTHEMONITOR --primary
Comment: Whatever

Click Add

DONE! :)

I guess I could set the same thing to run the python script I wrote to control the VGA fan speed. ;)

---

### Post by diddledan on 2011-05-03
set up your monitors using the monitors app and save. then edit the file it creates at ~/.settings/monitors.xml and change

```
<primary>no</primary>
```

for the monitor branch that you wish to be primary.

The system-wide file that this overrides is at /etc/gnome-settings-daemon/xrandr/monitors.xml. That file is created when you save as default in the monitors app.

---

### Post by SushiAddiction on 2011-08-31
> **diddledan said:**
> set up your monitors using the monitors app and save. then edit the file it creates at ~/.settings/monitors.xml and change

```
<primary>no</primary>
```

for the monitor branch that you wish to be primary.

The system-wide file that this overrides is at /etc/gnome-settings-daemon/xrandr/monitors.xml. That file is created when you save as default in the monitors app.

File ~/.settings/monitors.xml does not exist.
________________________
> **frozenfyer said:**
> I had a similar problem with my dual monitor setup that I solved. One screen was connected to DVI and the other to VGA. Use the following to figure out what each screen is called:

```

xrandr --prop

```

You should see something like VGA-1 or DVI-D-1. Do the following to set the primary screen:

```

xrandr --output DVI-D-1 --primary

```

Replacing DVI-D-1 with whichever screen you want as the primary.

> **petsoukos said:**
> Thanks! Exactly what I was looking for. :)


System->Prefs->Startup Applications

Then Click Add

Name: Whatever
Command: xrandr --output NAMEOFTHEMONITOR --primary
Comment: Whatever

Click Add

DONE! :)

I guess I could set the same thing to run the python script I wrote to control the VGA fan speed. ;)

I've got ATI card. Had problems setting primary monitor.
This works perfectly but you may have to swap the position of your monitors in the monitors app for unity menu to work properly.

My VGA monitors name was CRT1 just use xrandr --prop to find what your displays are called.

I'm surprised this problem still exists in 11.04

---

