---
title: "Flash objects choppy/broken/corrupted in Ubuntu 11.04 64-bit"
date: 2011-06-07
forum: Multimedia Software
---

### Post by pmorch on 2011-06-07
I was experiencing that flash elements looked weird when run under Firefox in Ubuntu 11.04 after a (two-step) upgrade from 10.04 where it worked fine. The exact same pages also looked properly for me in e.g. Chrome.

The problem looked like in [this youtube video]("http://www.youtube.com/watch?v=AAOLL2pUV08").

Also, the problem was only present when the flash object was run with "wmode transparent" as can be seen in this [jsfiddle]("http://jsfiddle.net/HX2tH/").

This posting is just to help out the next poor guy who runs into problems like I did. My personal problem was solved by using the [Firefox Flash-Aid plugin]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/"). It cleaned up my flash installation and now all is well.

---

### Post by lovinglinux on 2011-06-07
Glad to read that. Let me know if you have any suggestion to improve Flash-Aid.

Cheers

---

### Post by orlandocarguy on 2011-06-17
Wanted to say that it helped me too. YouTube videos especially would be very choppy, no matter whether they were fully buffered or not. But I installed Flash-Aid and the video is streaming smoothly.

---

### Post by ladydeth666 on 2011-06-19
Thank you for posting this!

---

### Post by thaDM on 2011-06-20
Thank-you very much! I was considering having to go back to 32bit but this is such an easy fix! :)

Will flash update if a new labs version is released?

---

### Post by lovinglinux on 2011-06-20
> **thaDM said:**
> Thank-you very much! I was considering having to go back to 32bit but this is such an easy fix! :)

Will flash update if a new labs version is released?

It will warn you. Then all you need is to run the Wizard again or any of the other installation methods.

---

### Post by thaDM on 2011-06-20
> **lovinglinux said:**
> It will warn you. Then all you need is to run the Wizard again or any of the other installation methods.

Brilliant! Never need to go back to 32bit then :)

---

### Post by lovinglinux on 2011-06-20
> **thaDM said:**
> Brilliant! Never need to go back to 32bit then :)

Unless Adobe stops releasing a 64bit version, which is not unlikely.

---

### Post by thaDM on 2011-06-21
> **lovinglinux said:**
> Unless Adobe stops releasing a 64bit version, which is not unlikely.

True. But surely everything will end up as 64bit: Macs are now fully 64 and new Windows7 machines are usually Win7 Premium 64. Anyway, going off topic. The main thing is, this works and works well: saving many headaches for Ubuntu64 users. Cheers :)

---

### Post by pmorch on 2011-06-21
> **lovinglinux said:**
> Unless Adobe stops releasing a 64bit version, which is not unlikely.

When I read that I was reminded of Adobe's missing love for linux. E.g. [Adobe scraps AIR for Linux, focuses on mobil](http://news.cnet.com/8301-30685_3-20071500-264/adobe-scraps-air-for-linux-focuses-on-mobile/) from June 14, 2011. 

Also, the support for flex builder for linux is horrible if even existent. 

They could scrap anything linux anytime.

---

### Post by h3ooo on 2011-06-28
Just wanted to say thanks for this - I hope you've solved my problem!

---

### Post by imchipbrown on 2011-07-19
I want to thank you, too.  Worked like a charm!

---

### Post by lovinglinux on 2011-07-19
> **pmorch said:**
> When I read that I was reminded of Adobe's missing love for linux. E.g. [Adobe scraps AIR for Linux, focuses on mobil](http://news.cnet.com/8301-30685_3-20071500-264/adobe-scraps-air-for-linux-focuses-on-mobile/) from June 14, 2011. 

Also, the support for flex builder for linux is horrible if even existent. 

They could scrap anything linux anytime.

You probably already know, but Adobe released Flash 11 Beta for 32bit and 64bit a couple of days ago. Flash-Aid is already updated, so all you need is to execute the Wizard to install the new version. Additionally, I have released a[ new version of Flash-Aid (2.2.0)]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/") that uses SSL authentication and file hash checking.

---

### Post by let on 2011-07-21
Thank you, it solved also for me.

---

### Post by Kenrro on 2011-08-05
The same here, thanks a lot :)

---

### Post by helpdeskdan on 2011-08-13
The plugin works, but puts files in strange places where other programs (boxee for instance) do not find them causing the user to have to ln -s them to other places.  

Also, it sets OverrideGPUValidation=true which is not something you want to do lightly.  The following should be considered required reading, more specifically the part that states "Another important note: Compiz and GPU-accelerated Flash on Linux do not mix."

[http://blogs.adobe.com/penguinswf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguinswf/2008/05/flash_uses_the_gpu.html)

If you are fine with that, and you only use flash in Firefox, then flash-aid is indeed a good solution.

---

### Post by tredsyn on 2011-10-31
I've had some problems with youtube videos and flash games on facebook. I've had problems on ubuntu 10.04 but thought it was something else, then I replaced it with ubuntu 11.04 but still got the problem. I always see "flash-aid" as a must-have after install but disregarded it; after installing flash-aid I was able to watch a complete 5 minute "funny cats" video continously. Great Add-On!! If only there's something for Chrome and Chromium since I also use those with Firefox at the same time :)

---

### Post by lovinglinux on 2011-10-31
> **tredsyn said:**
> I've had some problems with youtube videos and flash games on facebook. I've had problems on ubuntu 10.04 but thought it was something else, then I replaced it with ubuntu 11.04 but still got the problem. I always see "flash-aid" as a must-have after install but disregarded it; after installing flash-aid I was able to watch a complete 5 minute "funny cats" video continously. Great Add-On!! If only there's something for Chrome and Chromium since I also use those with Firefox at the same time :)

Although Flash-Aid only runs through Firefox, it does nothing when idle and the changes it makes when you run the Wizard are used by any browser. For Chrome instructions:

[http://support.webgapps.org/forum/flash-aid/13-does-this-extension-work-with-chromechromium](http://support.webgapps.org/forum/flash-aid/13-does-this-extension-work-with-chromechromium)

---

### Post by tredsyn on 2011-10-31
> Although Flash-Aid is designed to run from Firefox only, the changes it  makes and the plugins installed will also be recognized by any browser.  However, if you are using Chrome 32bit, you might need to disable the  plugin that is shipped with Chrome. To do that, type *about:plugins* in the address bar and click the *Details* menu. Then disable the plugin located at **/opt/google/chrome/libgcflashplayer.so**[COLOR=#000000][FONT=Arial]I disabled this one: "/usr/lib/flashplugin-installer/libflashplayer.so" in google chrome.
There's nothing in chromium. 

Thanks for the tip :)

edit: command on address is "about: plugins" no space
command is not a smiley LOL it's colon then letter P, then L, so on...
[/FONT][/COLOR]

---

### Post by lovinglinux on 2011-10-31
> **tredsyn said:**
> [COLOR=#000000][FONT=Arial]I disabled this one: "/usr/lib/flashplugin-installer/libflashplayer.so" in google chrome.
There's nothing in chromium. 

Thanks for the tip :)

edit: command on address is "about: plugins" no space
command is not a smiley LOL it's colon then letter P, then L, so on...
[/FONT][/COLOR]

Chromium doesn't ship with a bundled plugin, only Chrome. So don't disable "/usr/lib/flashplugin-installer/libflashplayer.so", otherwise flash won't work.

So, any changes you make with Flash-Aid will also affect Chromium. Keep in mind that each browser behaves differently in regard to performance and plugins.

---

### Post by wonderingwhy on 2012-05-16
Didn't work for me - I'll keep looking

---

### Post by brokndodge on 2012-06-01
I've been looking thru solutions to this issue for months.  Even tried the flash-aid fix in this thread.  Unfortunately it just removed and reinstalled the beta version of flash that I had installed months ago.  

Finaly found a fix - at least on my machine with kubuntu 10.04 and nvidia proprietary driver:

Using the nvidia xserver interface I switched from 24 bit color to 16 bit color.  problem is fixed for the moment.  Everything is running smoother and flash is clean.  Full screen functions correctly now.  Also, switching from full screen back to windowed doesn't require any tricks or reboots.  

Worked for me anyway.

---

### Post by finny388 on 2012-06-04
> **brokndodge said:**
> I've been looking thru solutions to this issue for months.  Even tried the flash-aid fix in this thread.  Unfortunately it just removed and reinstalled the beta version of flash that I had installed months ago.  

Finaly found a fix - at least on my machine with kubuntu 10.04 and nvidia proprietary driver:

Using the nvidia xserver interface I switched from 24 bit color to 16 bit color.  problem is fixed for the moment.  Everything is running smoother and flash is clean.  Full screen functions correctly now.  Also, switching from full screen back to windowed doesn't require any tricks or reboots.  

Worked for me anyway.

Not long after I fresh installed Ubuntu 12.04 64bit Flash continues to crash ("The Adobe Flash plugin has crashed. Send Crash Report") (I continue to send the reports, hoping Adobe gets the message that linux users want to use Flash (or have it abolished I guess))
I've used the Flash-Aid wizard and the only option with 64bit is the beta version. It didn't help.

I've looked through nVidia's x server settings and can't find that color setting. My version is 295.40
a) would you please tell me where it is?
b)is that going to change the entire desktop to 16bit colors? :(

Thanks

---

