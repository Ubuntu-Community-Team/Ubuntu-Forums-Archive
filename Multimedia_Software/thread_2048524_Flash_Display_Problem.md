---
title: "Flash Display Problem"
date: 2012-08-26
forum: Multimedia Software
---

### Post by dgharmon on 2012-08-26
I have two Windows open in the browser, a Youtube video playing on one, displaying any image on the second and the video from the flash video partly breaks through, [this]("http://coding.scribd.com/2010/11/13/flashheed-fixing-the-flash-z-index-problem-for-ads/") seems to relate to the cause, what's the fix?

The video even stays on screen when the screensaver kicks in ...
--
Lubuntu 12.04 Nvidia GeForce 210

---

### Post by siddharthshetty on 2012-08-27
> **dgharmon said:**
> I have two Windows open in the browser, a Youtube video playing on one, displaying any image on the second and the video from the flash video partly breaks through, [this]("http://coding.scribd.com/2010/11/13/flashheed-fixing-the-flash-z-index-problem-for-ads/") seems to relate to the cause, what's the fix?
 
The video even stays on screen when the screensaver kicks in ...
--
Lubuntu 12.04 Nvidia GeForce 210
  

Make sure you have goto the additional drivers option (Dash> type additional drivers)
and check if it can find an opensrouce driver for your card,  Also try what resolution are you using?
 
and I know answers like this don't help much, but all the info you give will be helfpul to the much advanced users who might answer your question!

---

### Post by dgharmon on 2012-08-27
> **siddharthshetty said:**
> Make sure you have goto the additional drivers option (Dash> type additional drivers)
and check if it can find an opensrouce driver for your card,  Also try what resolution are you using?
 
and I know answers like this don't help much, but all the info you give will be helfpul to the much advanced users who might answer your question!

I installed the drivers as per the [these]("http://us.download.nvidia.com/XFree86/Linux-x86_64/304.37/README/installdriver.html") instructions. I now get a "NVIDIA X Server Settings" menu item, which reports a Dell Ultrascan P990 at 2048x1536. I tried recording the desktop but the effect didn't show on the recording. As I said, what's curious is the video shows even when the screensaver kicks-in and the screen goes blank. I  don't see any options "NVIDIA X Server Settings" to fix this. It does appear to be the 'Flash Z-index Problem', doesn't happen when playing VLC etc. Disable hardware acceleration seems to cure it. See the [Z-index]("http://www.wikiencyclopedia.net/free/output-file.avi") problem in action ..

---

