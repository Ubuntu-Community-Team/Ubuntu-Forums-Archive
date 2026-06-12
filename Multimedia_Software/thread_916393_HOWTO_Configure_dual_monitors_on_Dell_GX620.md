---
title: "HOWTO: Configure dual monitors on Dell GX620"
date: 2008-09-10
forum: Multimedia Software
---

### Post by draxbear on 2008-09-10
Use this information to setup your Dell GX620 Desktop computer with dual monitors in Ubuntu Hardy 8.04 (Linux 2.6.24-19-generic) with Gnome.

Posting as a new thread as I'm unable to add to an archived post:
  [dual monitor (VGA + DVI) support Dell d620 and D/Port replicator]("http://ubuntuforums.org/showthread.php?t=253936")
While very helpful the above post didn't resolve my problems despite the near match in my hardware. I can only assume some version differences (maybe that was a KDE install?).

Very helpful commands that may help you understand and modify this to suit you:
-Documentation on the i810 driver (shows DFP/CRT etc options):
 [INDENT][FONT="Courier New"]man i810[/FONT][/INDENT]
-Documentation on the xorg.conf file itself
 [INDENT][FONT="Courier New"]man xorg.conf[/FONT][/INDENT]
-Location of xorg.conf file
 [FONT="Courier New"][INDENT]/etc/X11/xorg.conf[/INDENT][/FONT]

Hardware: 
[LIST]
[*]Dell GX620 + DVI Add-on card
[*]Dell 1907FP monitor (connected to built in analog port)
[*]Dell 2001FP monitor (connected to digital DVI port add on card)
[/LIST]

Attached files: 
 xorg.conf_dual_ok.txt
[INDENT]  - Working xorg.conf file - Xinerama enabled
  - Shows resolution settings for each monitor.[/INDENT]

:) **[SIZE="3"]Xinerama is optional[/SIZE]**
You can also just disable xinerama by changing this line. 
 [INDENT]Option "Xinerama" "on"[/INDENT]
to
 [INDENT]Option "Xinerama" "off"[/INDENT]

At the login prompt, your second screen appears blank until you login, at which point an additional Xserver is kicked off for it, allowing you to use start applications on each screen individually. Unfortunately you can't drag running apps between these, but may be useful to you.

:) **[SIZE="3"]MonitorLayout Option notes[/SIZE]**
[INDENT]After trying several combinations it seems the best way to use this setting is only once, in your initial device entry (eg device0 in attached).[/INDENT]

In this case:
[INDENT]Option "MonitorLayout" "CRT,DFP"[/INDENT]

Seems to translate to:
[INDENT]  CRT = Motherboard built in Analog (15pin D-connector) port
  DFP = Digital DVI port add on card[/INDENT]

Good luck!

---

