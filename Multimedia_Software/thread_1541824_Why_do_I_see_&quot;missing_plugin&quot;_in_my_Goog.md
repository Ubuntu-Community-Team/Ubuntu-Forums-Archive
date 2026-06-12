---
title: "Why do I see &quot;missing plugin&quot; in my Google Chrome?!!"
date: 2010-07-29
forum: Multimedia Software
---

### Post by lokutus25 on 2010-07-29
This thing is driving me crazy. I have Ubuntu Lucid 10.04 installed. I downloaded Google Chrome and installed it. It works. But when I trey to play in streaming something like a Web Radio, in WMA, I see "Missing Plugin" on the page. I removed/purged/installed a lot of things and now I'm lost.
Moreover I can see the Plugin in "about:plugin". 
Can someone to point me in the right direction?! Before I start on prozac?!!! :D:D:D Thanx!

```
Windows Media Player Plug-in 10 (compatible; Totem)
Description:	The Totem 2.30.2 plugin handles video and audio streams.
Location:	/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so
MIME types:	
MIME type	Description	File extensions
application/x-mplayer2	AVI video	
.avi	.wma	.wmv
video/x-ms-asf-plugin	ASF video	
.asf	.wmv
video/x-msvideo	AVI video	
.asf	.wmv
video/x-ms-asf	ASF video	
.asf
video/x-ms-wmv	Windows Media video	
.wmv
video/x-wmv	Windows Media video	
.wmv
video/x-ms-wvx	Windows Media video	
.wmv
video/x-ms-wm	Windows Media video	
.wmv
video/x-ms-wmp	Windows Media video	
.wmv
application/x-ms-wms	Windows Media video	
.wms
application/x-ms-wmp	Windows Media video	
.wmp
application/asx	Microsoft ASX playlist	
.asx
audio/x-ms-wma	Windows Media audio	
.wma

```

---

### Post by leseman on 2010-08-25
Disabling the VLC Multimedia Plug-in in about: plugins, worked for me! So, try to disable some of your plugins on a trial-and-error basis.

---

### Post by crowfield on 2010-08-25
join the club... it's driving me crazy as well.

Chrome recognizes my VLC plugin (in about:plugins), but I still get the "missing plugin" error when trying to stream.

Anybody have any ideas?

---

### Post by fiesta on 2010-09-30
ok man thanks a lot!!!!!!! just work perfect!:guitar:

---

### Post by joepz on 2010-10-16
What worked for you Fiesta?
Try to disable on trial & error basis?:confused:
Does not sound very robuust.
Any proper solution available?

---

### Post by spybee on 2011-11-30
You have to go here: 

```
chrome://plugins/
```

and disable both "VLC Multimedia Plug-in" and "VLC Multimedia Plugin" if they exist. That should fix the problem.

---

### Post by DapperDrakeNewbieDR on 2012-01-28
> **spybee said:**
> You have to go here: 

```
chrome://plugins/
```

and disable both "VLC Multimedia Plug-in" and "VLC Multimedia Plugin" if they exist. That should fix the problem.

That worked perfectly fine, I only disabled "VLC Multimedia Plug-in" and left "VLC Multimedia Plugin (compatible Totem 3.0.1)" enabled, and worked for me.

Thank you very much!

---

