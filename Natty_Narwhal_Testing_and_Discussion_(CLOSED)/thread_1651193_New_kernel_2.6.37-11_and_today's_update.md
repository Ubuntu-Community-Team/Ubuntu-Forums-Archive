---
title: "New kernel 2.6.37-11 and today's update"
date: 2010-12-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by nm_geo on 2010-12-22
Things seem to be improving well after todays update.  I enjoy moving a window into the left panel and watching it hide. Now I am sure some ccsm changes will break everything, but so far so good.

---

### Post by Arla on 2010-12-23
Lucky you, for some reason .11 doesn't even boot for me, I have to go back to .10 to even get into my system.

Ahh the joy of testing!

---

### Post by Quackers on 2010-12-23
It seems that since this mornings updates I can copy text from a file but I can't paste that text into a terminal window or a firefox window. The paste option is greyed out from the right-click context window.

---

### Post by jmmL on 2010-12-23
> **Quackers said:**
> It seems that since this mornings updates I can copy text from a file but I can't paste that text into a terminal window or a firefox window. The paste option is greyed out from the right-click context window.

I experience the same behaviour.

---

### Post by Harry33 on 2010-12-23
> **Quackers said:**
> It seems that since this mornings updates I can copy text from a file but I can't paste that text into a terminal window or a firefox window. The paste option is greyed out from the right-click context window.

Could that paste problem also have its origin on buggy GTK+2.0.
See the bug #693758.
Does gnome-classic work OK with you? Do you see clock, notification-area and Trashbox?

---

### Post by Quackers on 2010-12-23
> **Harry33 said:**
> Could that paste problem also have its origin on buggy GTK+2.0.
See the bug #693758.
Does gnome-classic work OK with you? Do you see clock, notification-area and Trashbox?

After my last episode when logging out of desktop edition and logging in to classic desktop I try not to do that any more :-)
In fact, I've still got a bottom panel in Unity that won't go away!

---

### Post by Harry33 on 2010-12-24
> **Quackers said:**
> After my last episode when logging out of desktop edition and logging in to classic desktop I try not to do that any more :-)
In fact, I've still got a bottom panel in Unity that won't go away!

Right :p

Anyway, a new GTK+2.0 build (a roll back version) has been uploaded into repos:
GTK+2.0_2.23.3.is.2.23.2-0ubuntu1, which just works.

---

### Post by Quackers on 2010-12-24
My problems are fixed with the new updates, thanks.

---

### Post by mc4man on 2010-12-24
> **Quackers said:**
> After my last episode when logging out of desktop edition and logging in to classic desktop I try not to do that any more :-)
In fact, I've still got a bottom panel in Unity that won't go away!

Possibly you're running unity with gnome-panel which should only be available from the Classic login though anythings possible I guess depending on what you've done previously.
Atm it may be the best choice for some setups , to check, if curious, run

```
ps -A |grep panel
```

---

### Post by Quackers on 2010-12-24
> **mc4man said:**
> Possibly you're running unity with gnome-panel which should only be available from the Classic login though anythings possible I guess depending on what you've done previously.
Atm it may be the best choice for some setups , to check, if curious, run

```
ps -A |grep panel
```

And the output is
```
nattyalpha@nattyalpha-VGN-AR51SU:~$ ps -A |grep panel
 1462 ?        00:00:00 gnome-panel
 1586 ?        00:00:01 unity-panel-ser

```

What does that mean?  :-)

All that happened previously is that I was logged in using Unity with no bottom panel and I logged out and then in to Classic. I then logged out of Classic and back in to desktop and Unity didn't start.So I enabled Unity plugin and the bottom panel appeared with Unity. And it's still there.

---

### Post by mc4man on 2010-12-24
> What does that mean?
It just means you're using unity thru the Classic login so gnome-panel is also running which is fine.
You actually will also have a top panel hidden under the unity menu bar.
and stuff like Alt+F2 probably works, ect.

If you did wish to remove the unused bottom panel you can try r. clicking on it > remove.
If no go then you'd need to disable the unity plugin in the Classic login, remove the panel and then re-enable the unity plugin. (in the Classic login.

Or leave as is.

---

### Post by Quackers on 2010-12-24
Well that'll be the difference then. Alt + F2 didn't work for a week or so but now it does :-)
Rt-clicking and remove doesn't work - greyed out. I'll try your other suggestion and hope not too much goes wrong :-)
Thanks

Edit My autologin is set to Desktop edition by default.

---

### Post by Reiger on 2010-12-25
ps lists process information, ranging from what commands are running (exact commandline args) to what user started them, and how many threads a process uses...

In this case the ps|grep output informs you that there are two processes running with the word “panel” in the name. You could for instance use this information to kill gnome-panel by typing: kill `pidof gnome-panel`; and if it is a badly behaved gnome-panel then you can be more forceful using kill -9 `pidof gnome-panel`.

---

### Post by Quackers on 2010-12-25
Thank you Reiger. A little more learned :-)

---

### Post by jerrylamos on 2010-12-26
> **Arla said:**
> Lucky you, for some reason .11 doesn't even boot for me, I have to go back to .10 to even get into my system.
Arla, what video graphics do you have?
lspci | grep VGA
My IBM Thinkpad T40 with ati radeon mobility 7500 won't boot without adding:
radeon.modeset=0 single
to the linux boot line, then when it boots to the recovery menu, select root prompt and enter:
sudo nano /etc/X11/xorg.conf
Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection
Ctrl-o
Ctrl-x
sudo service gdm start

No fun.

Jerry

p.s. This is because Compiz is using some code path nobody else uses, and Compiz hasn't fixed it yet.  If ever.  'Way back on Intrepid when the same kind of Compiz trick occurred with intel integrated video graphics Ubuntu just blacklisted Compiz for those pc's.  I wish they'd do it for ati radeon mobility 7500 too.

---

### Post by Amaranth on 2010-12-29
Actually it's because **libnux** is apparently trying to run ARB fragment programs on your Radeon 7500 Mobility which would seem to imply either the driver is lying about supporting them or libnux isn't checking. Or it could be that the card supports them but the driver has issues with the particular program. We had issues like that in the compiz blur plugin.

In either case, compiz itself isn't killing your card, blame the Unity folks. ;)

---

### Post by lucazade on 2010-12-29
> **Amaranth said:**
> Actually it's because **libnux** is apparently trying to run ARB fragment programs on your Radeon 7500 Mobility which would seem to imply either the driver is lying about supporting them or libnux isn't checking. Or it could be that the card supports them but the driver has issues with the particular program. We had issues like that in the compiz blur plugin.

In either case, compiz itself isn't killing your card, blame the Unity folks. ;)

Compiz works quite well here with my Mobility 7500 (like in previous releases), it is the Unity part that doesn't work well.

---

### Post by jerrylamos on 2010-12-29
> **Amaranth said:**
> Actually it's because **libnux** is apparently trying to run ARB fragment programs on your Radeon 7500 Mobility which would seem to imply either the driver is lying about supporting them or libnux isn't checking. Or it could be that the card supports them but the driver has issues with the particular program. We had issues like that in the compiz blur plugin.

In either case, compiz itself isn't killing your card, blame the Unity folks. ;)

Amaranth, I said "Compiz" because that's what the automatically generated error program put in the title.  
compiz crashed with SIGSEGV in nux::IOpenGLAsmVertexShader::IOpenGLAsmVertexShader()
Launchpad bug #692017
I'm not a developer so I don't know what's going on under the covers.

Xorg on CD Live tries to use driver "fbdevhw" which doesn't work.  If I put in an xorg.conf specifying driver "radeon" CD Live can be made to work.  Driver "ati" just gets a non-functional purple splotch screen and cursor just like no xorg.conf at all.

On installed Natty, ati radeon mobility 7500 running fine after a lot (!) of thrashes to get a panel running long enough to log out and log back in specifying "classic" and "radeon" in xorg.conf.

I'd be happy if "Unity" and/or "Compiz" were black listed from the mobility 7500 so it would run classic right off like it does on my two intel video graphics test pc's.  "Compiz" died on those pc's back at Intrepid time so they've been black listed ever since.  Applications run just fine.  "Unity" will run on my Compaq Presario but I don't use it because it doesn't help my applications run any better than "Classic" and there's a whole lot of function reached in "Classic" with less keystrokes and less windows than "Unity", at least from my limited experience.  So "Unity" will run on one of my four test pc's.  Not a good enough batting average for me.

Jerry

---

### Post by Amaranth on 2010-12-30
Blacklisting probably isn't needed because, as lucazade said, compiz itself works fine. The bug in libnux just needs to be fixed and you may even be able to run unity.

---

### Post by lucazade on 2010-12-30
> **Amaranth said:**
> Blacklisting probably isn't needed because, as lucazade said, compiz itself works fine. The bug in libnux just needs to be fixed and you may even be able to run unity.

Yes, I don't think blacklisting is neeeded because compiz w/o unity plugin works fine (performance of ati drivers improved a lot during these years for this chipset).

So libnux/unity code should be fixed in my opinion. :)

---

### Post by Reiger on 2010-12-31
It could very well be the driver lying about ARB support: this issue is something the kwin developers ran into as well.

See:
[http://blog.martin-graesslin.com/blog/2010/09/driver-dilemma-in-kde-workspaces-4-5/](http://blog.martin-graesslin.com/blog/2010/09/driver-dilemma-in-kde-workspaces-4-5/)
And follow up:
[http://blog.martin-graesslin.com/blog/2010/09/demystifying-opengl-desktop-effects/](http://blog.martin-graesslin.com/blog/2010/09/demystifying-opengl-desktop-effects/)

---

### Post by jerrylamos on 2010-12-31
Here's another one on the main topic.  Lubuntu Natty was running (for an Alpha 1) with 2.6.37-7 which is their download.  Updated to 2.6.37-11 and boots to a kernel "panic".  This is integrated intel video graphics i845G.

O.K., boot with "i915.modeset=0" to turn that troublesome "kms" off, and boots O.K.  Shades of months and years of "compiz" trouble with many intel integrated video graphics.  Note with Lubuntu this is their "classic" mode which is fine since the only way gnome will run on this i845G is in "classic" mode anyway.

Something changed in the code from -7 to -11 to cause the "panic".

I'm running O.K. with the "i915.modeset=0".  Wonder what the next update will do.

Jerry

---

