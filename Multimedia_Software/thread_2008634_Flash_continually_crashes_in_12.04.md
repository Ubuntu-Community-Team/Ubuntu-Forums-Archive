---
title: "Flash continually crashes in 12.04"
date: 2012-06-23
forum: Multimedia Software
---

### Post by 98cwitr on 2012-06-23
Didn't have this issue in 10.04, but it seems that all flash content will crash w/ the exception of youtube. No idea where to start.

---

### Post by TenPlus1 on 2012-06-23
If you are using nvidia graphics then you could try and right-click on a youtube video, go to settings and disable hardware-acceleration for flash...  This may help...

---

### Post by 98cwitr on 2012-06-23
Yes, I am actually! But it wont let me uncheck the box under Settings...or even close it once it's open for that matter.

---

### Post by firekage on 2012-06-23
> **98cwitr said:**
> Yes, I am actually! But it wont let me uncheck the box under Settings...or even close it once it's open for that matter.

Same here. On Windows there is no sucha problem. It occured to me after updating firefox to a newer version. It updates flash, and i saw on forum that with latest update form Adobe there is no hardware acceleration support more for nVidia, while the old had it. I'm using icedtea web plugin now cause with adobe flash i had problems with firefox but it is still present cause i unpacked it and copied to a location where it should be.

---

### Post by 98cwitr on 2012-06-23
Well I unintalled the nvidia driver completely and deleted the mms.cfg (/etc/adobe) file. While I'm back to getting the screen tearing I was accustomed to in 10.04, flash actually works now. Catch 22 it seems :/

---

### Post by 98cwitr on 2012-06-24
nm, still crashing :(

---

### Post by firekage on 2012-06-24
> **98cwitr said:**
> nm, still crashing :(

Try to install for firefox icedtea webplugin. I have it in firefox.

---

### Post by Sigma1 on 2012-06-24
The solution which worked for me was to uninstall the adobe flashplayer plugin and replace it with the "Google, from Chrome" flashplayer, using the Flash-Aid tool for Firefox, available here: [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by TenPlus1 on 2012-06-25
if you run the youtube video in full screen it shoudl let you go into properties and untick the hardware acceleration box...  Had to do that for a friends system to get flash to behave...

---

### Post by Sigma1 on 2012-06-27
I spoke too soon. Flash is back working in youtube, but not in some other sites... This is particularly annoying when sites use flash technology for authentication: copying numbers and words.
No combination of plugins and browsers seems to fix it...

---

### Post by 98cwitr on 2012-06-27
> **TenPlus1 said:**
> if you run the youtube video in full screen it shoudl let you go into properties and untick the hardware acceleration box...  Had to do that for a friends system to get flash to behave...

While that worked and I was able to uncheck it...still didn't fix flash from breaking :( Seems to break less now though :)

---

