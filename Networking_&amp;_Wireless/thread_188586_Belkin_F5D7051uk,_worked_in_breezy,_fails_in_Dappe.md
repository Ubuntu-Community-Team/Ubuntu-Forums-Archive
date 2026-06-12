---
title: "Belkin F5D7051uk, worked in breezy, fails in Dapper"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by andy101 on 2006-06-04
I have a Belkin USB wifi Adapter, model: F5D7051uk.

I had managed to get this working in Breezy using ndiswrapper version 11.

After upgrading to dapper went horribly wrong, (X broke, after fixing that gnome would crash) I did a clean install, erasing my old copy.

For some reason the ndiswrapper version with dapper is very old (v1.8 ). I upgraded to v1.16 by compilling it myself. ndiswrapper installed fine, installed driver, got driver present, hardware present. modprobed it, all works fine. But the wireless adapter won't even speak to my router. It has a little light on the front of it that indicates when a packets been sent and it doesn't seem to be even trying to send anything.

I don't remember doing anything differant when I did the same thing on breezy.

I have also tried using an older version of ndiswrapper that used to work (v1.11) but still no joy.

I am kind of confused why Breezy worked but Dapper does not. So far my experiance of Dapper is that its a step backwords and works less well than Breezy, but then I haven't actually used it much as I can't even get a network connection open so its hell to install anything.

The Nelson Mandella videos good though.

Anyone got any idea whats wrong, or any idea on how I can debug it, I doubt its a problem with ndiswrapper as it worked before, which leads me to think that something in Dapper is interfering with it. But as the kernel changed and Gnome then not much hasn't been changed!

Thanks.

(darn thoose sodding hardware vendors hiding there specs, had I been usig Ubuntu prior to buying a wireless card I would have definantly NOT bought a belkin, btw anyone know of a list of nativly supported wireless cards/adapters? I might shell out and buy a new adapter just to avoid this hassle, but would rater use what I have).

---

### Post by andy101 on 2006-06-04
OK this is wierd.

I setup the card via iwconfig and it appears that i I set essid BEFORE the key it works, but if key is set first or at the same time as essid then it fails.

The error message I get is:
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

Dapper also fails to complete the "configuring networks" step, it requires ctrl-c to get any further.

Any ideas how to fix this problem, or should I just remove autoloading of ndiswrapper and create a script to set things correctly? (if so how do I get it to run at startup). Or is there some way of making iwconfig or nidswrapper or network tools do things in the correct order?

Thanks.

---

