---
title: "Tangerine media server Karmic"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by neojames on 2009-11-08
I want to share my songbird library with my desktop pc (also linux), so I installed Tangerine Media Server. When I click on the tangerine-properties icon nothing happens.

Here is the output I get when I run it from terminal

Unhandled Exception: System.DllNotFoundException: libgobject-2.0.dll
  at (wrapper managed-to-native) Tangerine.IconThemeUtils:g_type_class_peek (intptr)
  at Tangerine.IconThemeUtils.SetWindowIcon (Gtk.Window window, System.String iconName) [0x00000] 
  at Tangerine.IconThemeUtils.SetWindowIcon (Gtk.Window window) [0x00000] 
  at Tangerine.PropertiesWindow..ctor () [0x00000] 
  at Tangerine.EntryPoint.Main () [0x00000]

I'm not sure whether it's somthing i've done or whether its tangerine.

Also the share does appere in songbird but it's empty.

---

### Post by neojames on 2009-11-09
Bump

---

### Post by Dapilot1 on 2009-11-10
Yeah its not working for me neither.
```

Unhandled Exception: System.DllNotFoundException: libgobject-2.0.dll
  at (wrapper managed-to-native) Tangerine.IconThemeUtils:g_type_class_peek (intptr)
  at Tangerine.IconThemeUtils.SetWindowIcon (Gtk.Window window, System.String iconName) [0x00000] 
  at Tangerine.IconThemeUtils.SetWindowIcon (Gtk.Window window) [0x00000] 
  at Tangerine.PropertiesWindow..ctor () [0x00000] 
  at Tangerine.EntryPoint.Main () [0x00000]

```
Any way to fix?

---

### Post by neojames on 2009-11-11
It's anoying isn't it. It wouldn't matter to much if I can find out where the config files are.

---

### Post by Dapilot1 on 2009-11-12
Not sure how or why, but I can see a share that it made using my other computer. Sadly it doesn't have any songs in it.

---

### Post by neojames on 2009-11-13
I get the same, does anyone know whether this is a Karmic issue or a Tangerine issue? If it is a ubuntu issue i'll start a bug report.

---

### Post by neojames on 2009-11-14
If you launch it from control centre it works!

---

### Post by Dapilot1 on 2009-11-16
What control center? The mythbuntu one?

---

### Post by neojames on 2009-11-17
The gnome control centre you can enable it be right clicking on the ubuntu menu going to system and enabling control center. It apears to be working out of the preference menu now as well, so it might fix it for there as well!

---

### Post by jarcut on 2009-12-06
> **neojames said:**
> The gnome control centre you can enable it be right clicking on the ubuntu menu going to system and enabling control center. It apears to be working out of the preference menu now as well, so it might fix it for there as well!

this is not solved for me. starting it from shell gives same message and either preferences menu and control settings return nothing. regarthless, i can see the mahine's share in banshee.

can anyone provide help.

ps: i'm running it under a jaunty virtual box.

---

### Post by neojames on 2009-12-07
With me it was in karmic so it may be a different solution in jaunty? I'll mark as unsolved anyway.

---

### Post by jarcut on 2009-12-08
> **neojames said:**
> With me it was in karmic so it may be a different solution in jaunty? I'll mark as unsolved anyway.

i'm sorry, i didn't explain it right. this is a karmic koala issue. but since its a deal breaker for me i'm testing karmic inside a virtual box. and the virtual box is running on a jaunty machine

---

### Post by neojames on 2009-12-08
Ahh well i've marked it as unsolved and hopefully it will be fixed, it's still working with me it might be fixed by a reinstall I think I tried that last time and it might have been what fixed it!

---

### Post by jarcut on 2009-12-08
> **neojames said:**
> Ahh well i've marked it as unsolved and hopefully it will be fixed, it's still working with me it might be fixed by a reinstall I think I tried that last time and it might have been what fixed it!

I hope it does go away with a reinstall. I won't get my hopes up but let us know :)

BTW is there a thread already for the "unkown program is still running" on shutdown bug?

---

### Post by neojames on 2009-12-09
Thats a bug! I always asumed I had a program in the background like my backup script.

---

### Post by jarcut on 2009-12-10
> **neojames said:**
> Thats a bug! I always asumed I had a program in the background like my backup script.

I'm assuming it's a bug because it happened everytime -I've tried karmic out in a couple real machines and in the virtualbox i mentioned above. my guess is it's a gnome bug. i'll wait for it to get fixed in the vuirtual machine but in all honesty I suppose i'll only upgrade ubuntu when lucid comes out

---

### Post by neojames on 2009-12-11
I was going to but it works a lot better on my laptop then karmic, if you can dual boot it's worth seeing as karmic is brilliant on my laptop but nothing but intrepid works on my desktop!

---

### Post by Arcadian on 2009-12-12
Hi All,

I've found the same issue (love Tangerine!) and googled across this...
[[COLOR="Blue"]https://bugzilla.redhat.com/show_bug.cgi?id=517256[/COLOR]]("https://bugzilla.redhat.com/show_bug.cgi?id=517256")

If you follow the instructions there, and add the line mentioned to the mono config file, it works straight off...

All I did was
```
gksudo gedit /etc/mono/config
```
and paste the dllmap entry so now mine looks like this (just the start of it anyhow)
```
<configuration>
	**<dllmap dll="libgobject-2.0.dll" target="libgobject-2.0.so.0"/>**
	<dllmap dll="i:cygwin1.dll" target="libc.so.6" os="!windows" />
	<dllmap dll="libc" target="libc.so.6" os="!windows"/>
	<dllmap dll="intl" target="libc.so.6" os="!windows"/>
	<dllmap dll="intl" name="bind_textdomain_codeset" target="libc.so.6" os="solaris"/>

```

No doubt this will be fixed in an update at some point. I hope that sorts it out for you :popcorn:

---

### Post by neojames on 2009-12-12
Mine just fixed itself but thx for the solution!

---

### Post by jarcut on 2009-12-13
mine too. just tried out clicking on the prefs link and it just popped like it was always there.

and the unknown program running just vanished too.

thank goodness! now i just need to try out if bashee alarm works and if it does i'm giving karmic a spot in my heart.

thank you all

---

### Post by neojames on 2009-12-13
I love karmic as well, how can you dissagre with a 30sec karmic boot time compered to a 1min 30sec boot on jaunty!

---

### Post by deathbyswiftwind on 2009-12-13
What about enabling the share using samba and mounting the folders you want? Pretty simple to do and it works great.

---

### Post by neojames on 2009-12-14
No use if you want to share to other DAPP compatible software which doesn't have samba (such as external devices) or if samba wont work like me!

---

### Post by woodsnake420 on 2010-01-05
I know this is marked as solved, but are you guys still having issues?  I ran into problems, like you guys in karmic.  I removed tangering, did a quick sudo apt-get build-dep tangerine, then downloaded, and compiled it from source.  So far so good. I'm adding songs from an esata drive right now.

Hope this helps.

---

### Post by neojames on 2010-01-06
I think the mono fix is working  i'vbe tried it on two pc's all fine.

---

### Post by Endolith on 2010-08-24
Don't look fixed to me.

```
~> tangerine-properties
 Unhandled Exception: System.DllNotFoundException: libgobject-2.0.dll
  at (wrapper managed-to-native) Tangerine.IconThemeUtils:g_type_class_peek (intptr)
  at Tangerine.IconThemeUtils.SetWindowIcon (Gtk.Window window, System.String iconName) [0x00000]
  at Tangerine.IconThemeUtils.SetWindowIcon (Gtk.Window window) [0x00000]
  at Tangerine.PropertiesWindow..ctor () [0x00000]
  at Tangerine.EntryPoint.Main () [0x00000]

        

```

---

### Post by midwesterndirt on 2010-09-22
Tangerine still isn't working for me in Lucid. The previous fix allows to tangerine-properties window to appear, but the shared music library is still empty.

---

### Post by warjowuch on 2010-10-13
Mine too.
I applied the mono-fix, then at first the library worked, but now it is empty again... Can't get it filled. Sucks!

---

### Post by paintonhisface on 2010-12-13
To those of you with the following error:

```
ERROR Failed to start server: org.freedesktop.Avahi.CollisionError: Local name collision
```

I found that immediately after performing the fix here--[http://ubuntuforums.org/showthread.php?t=1319098&p=8484358](http://ubuntuforums.org/showthread.php?t=1319098&p=8484358)--I still got the error.

BUT, after I ran ```
killall tangerine
``` and then restarted tangerine, everything worked.

---

### Post by rade95 on 2011-01-01
> **paintonhisface said:**
> To those of you with the following error:

```
ERROR Failed to start server: org.freedesktop.Avahi.CollisionError: Local name collision
```I found that immediately after performing the fix here--[http://ubuntuforums.org/showthread.php?t=1319098&p=8484358](http://ubuntuforums.org/showthread.php?t=1319098&p=8484358)--I still got the error.

BUT, after I ran ```
killall tangerine
``` and then restarted tangerine, everything worked.

This error drove me nuts on maverick, but killall tangerine followed by a tangerine restart fixed it. Thank you so much.

---

