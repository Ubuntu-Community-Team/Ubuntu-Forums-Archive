---
title: "Facebook video not working but youtube and vimeo does."
date: 2014-04-27
forum: Multimedia Software
---

### Post by danielzazen on 2014-04-27
Hi friends. 
Although I can open my videos on my HP mini 210 when downloaded, I can't watch them on my chrome webbrowser.Many of yhen work fine on firefox, but I am a Chrome/chromium user and I can't do that anymore on 14.04. It's just Facebook video not working but youtube and vimeo does.
Any Ideas?

---

### Post by monkeybrain20122 on 2014-04-28
Because fb is flash, vimeo is html5, youtube is mostly html5. That means you don't have flash and that is because you use Chromium. You said Chrome/Chromium as if they are interchangeable but the distinction is important when it comes to flash. Chrome bundles its own flash so no problem there. But Chromium has always used system flash (same as Firefox), Chrome can use either system flash or its own. Google has decided to drop support for all Mozilla plugins (not just flash, but all other media plugins as well)on Chrome and Chromium, effective April for Chromium and May for Chrome. So Chromium has mo bult in flash and it cannot use system flash hence your problem.

Fortunately someone has been able to get pepper flash from Chrome and put it in the repo so you can install it in Chromium. [http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html](http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html)

---

### Post by danielzazen on 2014-05-04
Followed that, and got it running, but problem remains the same.
[COLOR=#000000][FONT=Arial]**Adobe Flash Player** - Versión: 13.0.0.206Shockwave Flash 13.0 r0
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial][TABLE]
[TR]
[TD="class: plugin-details-label"]Nombre:[/TD]
[TD]Shockwave Flash[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Descripción:[/TD]
[TD]Shockwave Flash 13.0 r0[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Versión:[/TD]
[TD]13.0.0.206[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Ubicación:[/TD]
[TD]/usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Tipo:[/TD]
[TD]PPAPI (fuera de proceso)[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"] [/TD]
[TD][Inhabilitar]("chrome://plugins/#")[/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD="class: plugin-details-label"]Tipos MIME:[/TD]
[TD][TABLE="class: mime-types, width: 100%"]
[TR="class: header"]
[TD]Tipo MIME[/TD]
[TD]Descripción[/TD]
[TD]Extensiones de archivo[/TD]
[/TR]
[TR]
[TD]application/x-shockwave-flash[/TD]
[TD]Shockwave Flash[/TD]
[TD][TABLE="class: hlisting"]
[TR]
[TD].swf[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD]application/futuresplash[/TD]
[TD]FutureSplash Player[/TD]
[TD][TABLE="class: hlisting"]
[TR]
[TD].spl

[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]


[/FONT][/COLOR]
Tryed enabling acceleration, but still too slow... it seems like powerpoint slides...

---

