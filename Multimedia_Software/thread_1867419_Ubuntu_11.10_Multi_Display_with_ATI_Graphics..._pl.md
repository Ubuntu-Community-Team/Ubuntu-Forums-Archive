---
title: "Ubuntu 11.10 Multi Display with ATI Graphics... please help!"
date: 2011-10-22
forum: Multimedia Software
---

### Post by Eberbachl on 2011-10-22
I have two displays that I would like to use with Ubuntu 11.10, as a multi display configuration, and I'm having difficulty.

I have an ATI HD5800 series graphics card, one display's native resolution is 1680x1050 (20" Display), and the other display's native resolution is 1920x1080 (22" Display).

When I boot the machine with both displays connected it clones the displays and runs them both at 1690x1050. Cloning is useless for me in this environment... I want a multi display with my desktop extended onto the second monitor.

When I try to configure the multi display with the ATI Catalyst control centre, it just closes with no warning when I try to apply the settings. When I try to make the changes using the built in Displays control panel it returns the error:

```
"required virtual size does not fit available size: requested=(3600, 1080), minimum=(320, 200), maximum=(1920, 1920)"
```

Can anyone provide me with some useful suggestions on how to fix this please?

The same monitor configuration was working beautifully in 10.04 and 10.10. I've got to say multi display seems to be something Linux just can't seem to get right. It works in one release and then it's broken in the next. Windows and OS X don't seem to have this trouble... it's not like it's an obscure requirement... lots of people like to work with multiple monitors. Very frustrating.

Please help!

:D

---

### Post by masgeeks on 2011-10-22
I just wanted to say I "feel your pain" - I have had the same problems on and off with ATI and dual monitors and Ubuntu.  It was really unhappy in 11.04 when I last tried it.  I have a clean install of 11.10 now but am not inclined to bother giving it a go.  Multiple desktops work just as well... at least for me, and easy to switch between them, especially in gnome shell...  :)

---

### Post by 4Orbs on 2011-10-22
[ATTACH]205200[/ATTACH][ATTACH]205203[/ATTACH]

This isn't really a solution, but after trying to set up dual monitors the past four days... I've discovered that Kubuntu 11.10 is the only one that has been successful. I tried it with L/X/K/Ubuntu and Gnome Shell. Painless with Kubuntu, hopeless with the others.

---

### Post by Eberbachl on 2011-10-22
Moving to Kubuntu would be a bit of a deal breaker for me ATM, and whilst I like multiple desktops for day to day stuff and enjoy keep different apps running on each one - for this particular task (some photography study where I want some text resources in one display whilst I work in GIMP on another) I really need to see what's happening on all screens at the same time.

;)

Why does it need to be so hard? I've been having this trouble in Ubuntu (and other Linux variants) for years.

---

### Post by 4Orbs on 2011-10-22
Maybe I'm misunderstanding your reply. With Kubuntu I am using one extended display. I can drag an app from left screen to right, stretch a movie across both screens. Clicking maximize on an app will maximize it to just one screen or the other. I believe that is exactly what you are looking for (except that it is KDE rather than Unity or Gnome). Those pics I posted are two separate screenshots, each shot showing both monitors.

---

### Post by Eberbachl on 2011-10-23
Yes, that's exactly what I'm looking for, but I would prefer not to use Kubuntu. I know it's great... It's just that I really prefer the Unity interface of Ubuntu.

;)

I could switch to Kubuntu if I just couldn't make it work in Ubuntu, but I refuse to believe it should be impossible!

:D

I wish I was a programmer, then I could offer to work on a solution myself :D

---

### Post by osarusan on 2011-10-23
There are a number of threads already answering this question.
[http://ubuntuforums.org/showthread.php?t=1862451](http://ubuntuforums.org/showthread.php?t=1862451)

Run sudo aticonfig --initial -f

Then reboot.

Run gksu amdcccle

Set up your displays the way you like them and hit apply.

You may have to reboot once more.

You now have a working desktop! :)

---

### Post by Eberbachl on 2011-10-23
Thanks for that info... before I try it, do I have to do it every time I want to use multiple displays?

I don't use multiple displays all the time... not even most of the time. Most of the time I'm happy with only one display turned on, and I need a system that can cope with dynamically recognising and going into multi display mode when I turn the second screen on to do some specific tasks requiring that functionality.

;)

---

### Post by Eberbachl on 2011-10-23
Thanks - I have now tried it, and it works... somewhat.

Your advice has got my multi display working nicely, but sadly when I want to revert to a single display I have to physically unplug the second screen - ATI CCC will enable me to disable it, but even if I reboot with it connected but turned off it automatically goes back into multi display mode.

Pretty lame, but I do have my multi display with a bit of plucking around so thanks for the help.

;)

---

### Post by osarusan on 2011-10-24
Ones your xorg.conf has been correctly set up by amdcccle you should be able to use Ubuntu's built-in Displays setting to turn the monitors on or off with no issues. Try using that and see what happens.

---

### Post by cmavr8 on 2011-10-26
> **osarusan said:**
> There are a number of threads already answering this question.
[http://ubuntuforums.org/showthread.php?t=1862451](http://ubuntuforums.org/showthread.php?t=1862451)

Run sudo aticonfig --initial -f

Then reboot.

Run gksu amdcccle

Set up your displays the way you like them and hit apply.

You may have to reboot once more.

You now have a working desktop! :)

Unfortunately it still crashes... (amdcccle).
If I try Ubuntu's display manager I still get the error about virtual size.

Too bad... :(

---

### Post by osarusan on 2011-10-27
Are you running it from a terminal? What is the error message you get when it crashes?

---

### Post by cmavr8 on 2011-10-27
I tried running it using the launcher and a terminal. No error I think... I can't test it now as I'm using the opensource drivers and don't want to fiddle around any more..

---

### Post by sashahtkk on 2011-10-27
I had the same problem with ATI Mobility Radeon HD 4500 Series. I am new to ubuntu, so i dont really know many things but In my case the "Displays" setting and AMD control center settings were conflicting. That is why on reboot it preferred the settings from "Displays". It was displaying the clone of desktop 1 on desktop 2 on every reboot. I used the similar settings in both cases and it worked.

---

### Post by jaws222 on 2011-11-02
I had the same issue in Lubuntu.  I read on another forum about a quick fix that worked for me.  I added the KDE desktop environment, restarted and used that desktop to set up multiple screens.  When I hit apply it ask me if I wanted to save and I said yes and restarted to save my settings.  I then logged back in under my LXDE desktop and had dual screens.

---

### Post by msffsm on 2011-11-28
> **osarusan said:**
> There are a number of threads already answering this question.
[http://ubuntuforums.org/showthread.php?t=1862451](http://ubuntuforums.org/showthread.php?t=1862451)

Run sudo aticonfig --initial -f

Then reboot.

Run gksu amdcccle

Set up your displays the way you like them and hit apply.

You may have to reboot once more.

You now have a working desktop! :)


I am new to Ubuntu and want to thank you very much for your post. This got me 90% there. I actually had to run 'sudo gksu amdcccle' in order for the changes to take affect in version 11.10.

---

### Post by rafaelbeckel on 2012-03-09
For me it shows the following error in terminal when I try to apply dual screen:

(process:2703): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.30.0/./gobject/gtype.c:2708: You forgot to call g_type_init()

(process:2703): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:2703): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.30.0/./gobject/gtype.c:2708: You forgot to call g_type_init()

(process:2703): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:2703): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

---

### Post by yippy on 2012-05-14
> **rafaelbeckel said:**
> For me it shows the following error in terminal when I try to apply dual screen:

(process:2703): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.30.0/./gobject/gtype.c:2708: You forgot to call g_type_init()

(process:2703): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:2703): GLib-GObject-CRITICAL **: /build/buildd/glib2.0-2.30.0/./gobject/gtype.c:2708: You forgot to call g_type_init()

(process:2703): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(process:2703): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed

This is what I'm seeing also.

---

### Post by zigac on 2012-06-12
I have a problem with configuring Multi-Display. I want to have multi-display on my monitor and TV. I configure in amdcccle. I had no problem with previous version of Kubuntu 11.10, now i am using 12.04. It's working, the only problem is that the TV is always the primary and monitor secondary, even if i switch monitors in the amdcccle. The login and desktop is always on the tv. If i don't use amd additional drivers, there is no problem, i can have multi desktop, but i need amd driver to adjust the fan speed. Can anyone help?

---

### Post by stphnwallace on 2012-11-06
This worked a treat on Precise 12.04 as well.
Step by step. I moved /etc/X11/xorg.conf out the way before I started as well.
All good.

---

### Post by stphnwallace on 2012-11-06
I played with this for hours before following this process  for Ubuntu 12.04 which works :)

I moved /etc/X11/xorg.conf out the way before I started.

sudo aticonfig --initial -f

Then reboot.

Run gksu amdcccle

Set up your displays the way you like them and hit apply.

You may have to reboot once more.

All good.

---

