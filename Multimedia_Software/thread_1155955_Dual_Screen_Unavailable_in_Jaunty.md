---
title: "Dual Screen Unavailable in Jaunty"
date: 2009-05-11
forum: Multimedia Software
---

### Post by chrisbliss18 on 2009-05-11
I have a Dell Studio 17 laptop with an external 24" LCD. The laptop has an ATI/AMD graphics chipset (Mobility Radeon HD 3650). The external monitor is connected using the HDMI connection with a HDMI/DVI cable.

Using both screens in a dual screen (non-mirror) setup worked extremely well in Intrepid. I updated to Jaunty, and dual screens no longer worked (more details on that in a moment). To ensure that it wasn't an upgrade issue, I also did a fresh install in a new partition. The new install has the same problem.

Here is a quick summary of the problems I have:
[LIST]
[*]The Display Preferences dialog doesn't always work
[list]
[*]When Display Preferences works (rare), I can deactivate the Mirror Screens option and get dual screens after logging out and logging back in. However, I can no longer get the Display Preferences to load back up at this point to make any modifications and rebooting the system resets the monitors back to a mirrored configuration.
[*]When Display Preferences does not work (most of the time), the window pops up, but it is a blank dialog with a green horizontal bar halfway down the window. Getting rid of this dead window requires killing it from the command line. While this dead window is present, one of my CPU cores is maxed, none of the panel menus function, and hotkeys are sluggish to respond.[/list]
[*]In Intrepid, I always used the ATI Catalyst Control Center to manage the dual screen setup. I have never been able to use CCC to successfully manage my dual screens in Jaunty.
[list]
[*]Xinerama is not available. Even when I can remove the Mirror Screens option in Display Preferences, the Xinerama options are all grayed out.
[*]The Display Manager recognizes and correctly identifies both screens, but the drop down under Multi-Display is grayed out/deactivated and only Unknown is shown in the drop down box.[/list]
[/LIST]

Additional notes that may be pertinent:
[list]
[*]I am using the proprietary FGLRX ATI driver. Interestingly, before activating the proprietary driver, I could get dual screens to work, but my external monitor would flicker to black randomly (anywhere from every few seconds to around once a minute). The proprietary driver fixed this issue yet broke the dual screen ability.
[*]I am using Compiz and Emerald. Disabling Compiz and/or switching to Metacity has no effect on the functionality of the dual screens.[/list]

I'd love to get any advice about things to try to remedy this situation.

---

### Post by Xinkill on 2009-05-17
First i would like to say i have the same problem. I have an ati HD3870. I am using the 9.4 driver since earlier drivers don't install on the new jaunty. But i must state that all drivers after 9.1 on intrepid have the same issue.

I did however managed to activate the multi-display but with any luck to configure it so that it was stable and usable. I have to look further into it but if my memory serves me correctly, some application that is installed on jaunty is blocking the driver to work correctly. Only thing i can say is try it from commandline and watch the errors that are given.

---

### Post by strycore on 2009-05-26
I installed Jaunty on a friend's laptop this weekend and the same problem occurs (the GPU is a ATI Technologies Inc Mobility Radeon HD 3400 Series )

The problem is that he lives 300kilometers away from me and now that he's back home, it's very hard to debug his problem.

This is his first experience with Linux so I made up a system that would automatically download and execute scripts that I write (such as gathering info, modifying xorg.conf, etc...) but the problem is still not solved.

I'd rather not risk heavy modifications such as changing drivers because I don't want to crash the machine and not being able to restore it.

So maybe you guys are more familiar with Ubuntu than him and can try out some stuff that my friend couldn't do on his own. 

1) Is there a launchpad bug reporting this problem, I'll have a look later but if you find something post it here please.
2) Maybe someone could test the latest version of xorg, published in the xorg-edgers PPA ( [https://launchpad.net/~xorg-edgers](https://launchpad.net/~xorg-edgers) )
3) I've heard that ATI released a new driver, maybe you should try it out
4) If all that fails and dual head works in Intrepid, then we should find a way to downgrade to whatever version of xorg or fglrx that works fine.

---

### Post by JeevesBond on 2009-06-12
I'm getting a similar issue with an ATi Radeon X600 dual-monitor setup. After using Preferences -> Display and logging out/in again, both monitors are 'zoomed-in' on the desktop, while the newer monitor shows a 'signal out of range' error.

Also, and weirdly, I can sometimes restart GDM (sudo /etc/init.d/gdm restart) and it will *almost* work. One monitor will work, while the wallpaper on the second will only extend half way across the screen.

In my case restarting does nothing, it just returns to the 'zoomed-in' state. I then have to Ctrl-F1 to get to a console, then sudo vim /etc/X11/xorg.conf and delete this:
```

	SubSection "Display"
		Virtual	3200 1200
	EndSubSection

```

That gets me back to a mirrored display. Am off to try the latest version of Xorg, see if that makes any difference. :)

*** EDIT ***

Just tried adding Radeon drivers from [Tormod Volden's PPA](https://launchpad.net/~tormodvolden/+archive/ppa?field.name_filter=&field.status_filter=published&field.series_filter=jaunty), which did nothing: didn't break anything, but didn't fix anything either. :)

---

### Post by JeevesBond on 2009-06-12
It's possible to use a 9.04 live cd to test whether the latest Xorg works for you, see the section: 'Testing with a live CD/media' on [https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge)

Unfortunately this did nothing to fix my dual-screen problem, but it might help someone else. Give it a try if you want to test the latest Xorg without hosing your system. :)

---

### Post by humphreybc on 2009-09-23
Any luck on this? I just started a new thread that has this same problem and if anyone has any info that'd be great....

This is the thread: [http://ubuntuforums.org/showthread.php?t=1273242](http://ubuntuforums.org/showthread.php?t=1273242)

---

