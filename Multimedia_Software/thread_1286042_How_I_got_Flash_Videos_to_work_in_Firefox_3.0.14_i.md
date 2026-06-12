---
title: "How I got Flash Videos to work in Firefox 3.0.14 in Ubuntu 9.04"
date: 2009-10-08
forum: Multimedia Software
---

### Post by natrone on 2009-10-08
Make sure you have the latest Adobe Flash Player, you can download the deb. from the following website: 

[COLOR="Blue"] [http://get.adobe.com/flashplayer/?promoid=DXLUJ]("http://get.adobe.com/flashplayer/?promoid=DXLUJ")
[/COLOR]

Run the Gdebi package installer that you downloaded from Adobe.  If the latest Flash Player version is installed on your system you will be notified.  Otherwise let the install complete.

Go to FireFox and in the address bar enter:  

**about:config**

search for shockwave you should get the following **Preference Name**:

**modules.plugins.mimetype.application/x-shockwave-flash**

select this Preference delete the current **Value** entry and add:

**libflashplayer.so**

also in Firefox Go to >**Tools** >**Add-Ons** >**Plugins** and make sure you have Shockwave Flash 10.0 r32 enabled and any other related Shockwave Flash Plugins disabled.  For example:  Gnash or swfdec

[SIZE="5"][COLOR="Red"]
**NOW!  This operation worked for me please do so at your own risk to your FF installation.  **[/COLOR][/SIZE]

---

