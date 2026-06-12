---
title: "Disney+ (Disneyplus) stopped playing videos, workaround: Windows user agent"
date: 2022-10-28
forum: Multimedia Software
---

### Post by teemu-3 on 2022-10-28
I've been using Disney+ on Kubuntu 20.04/Firefox for a while without any special configuration (except for allowing playing DRM content in Firefox settings). Videos suddenly stopped playing at some point during the last few days. When clicking on the play icon, an icon might spin for a second and then nothing. Same issue on Kubuntu/Chromium and Fedora 36/Chrome.

The following issue is shown on the Chrome Developer tools Console output (and a similar one in Firefox):

> vendor.fcc3d378e3f325b62130.js:2 Possible Unhandled Promise Rejection: TypeError: Cannot read properties of undefined (reading 'deviceProfile')

DeviceProfile sounds like they're trying to get some info from the client, so I tried switching the browser user agent to a WIndows one. That seems to fix the issue (on FIrefox install a user agent switcher add-on like "User-Agent Switcher and Manager", change the user agent to e.g. latest Firefox on Windows).

Just a FYI + is anyone else experiencing this?

---

### Post by webaake on 2022-10-28
Same here on Chrome: 
> Possible Unhandled Promise Rejection: TypeError: Cannot read properties of undefined (reading 'deviceProfile')
Ahh, typical! 

I'll try that addon and see.

---

### Post by webaake on 2022-10-28
"User-Agent Switcher and Manager" from Chrome addons fixed it for me too. In it you can set user-agent switch for one site, several or all. Nice and flexible. 

(I guess some noob at Disneyplus just forgot about Linux)

---

### Post by chubbant on 2022-10-28
I have the same problem with Ubuntu 22.04 using Chrome.

---

### Post by FernandoSidders on 2022-10-29
Same issue with StarPlusLA (Disney owned streaming Service for Latin America), solved with User Agent change too.

---

### Post by __jcubic__ on 2022-10-31
I'm on Fedora 37 that use Chrome 107 and extension no longer works, it doesn't change the User-Agent. It keep throwing the same error. The only way to fix it in Chrome 107 was to pause the code in debugger and patch the variable that was holding user agent string.

---

### Post by jamescze on 2023-01-10
Disney+ officially do not support Linux, only Windows. It would be interesting to test, if Disney+ is working on Windows in FF...

[https://help.disneyplus.com/csp?id=csp_article_content&article=computer-browser-requirements](https://help.disneyplus.com/csp?id=csp_article_content&article=computer-browser-requirements)

Anyway, I dont have any issue with Disney+ on MS Edge or Chromium on Ubuntu 22.04. And I am watching something there almost on daily basis.

---

### Post by TheFu on 2023-01-10
I gave up dealing with little issues like this just to watch videos using Linux.  $30 for a Roku stick, knowing they are tracking everything, every click, every skip, every audio search, every video played, but for DRM content, it always works.  It is a trade-off.  Heck, anyone using Chrome as their browser has already decided that privacy doesn't matter, so may as well use a Roku. ;}

Be certain to put it (and every IoT device) on a private subnet, like the FBI recommends. 
[https://www.fbi.gov/contact-us/field-offices/portland/news/press-releases/tech-tuesday-internet-of-things-iot](https://www.fbi.gov/contact-us/field-offices/portland/news/press-releases/tech-tuesday-internet-of-things-iot)
When the FBI says to do something related to network and computer security, I'm going to listen.

---

### Post by SeijiSensei on 2023-01-10
I've been a happy Roku user for a few years now. It has apps for even obscure services like the Crunchyroll and HIDIVE anime channels.

---

### Post by webaake on 2023-01-11
Still works here on Google Chrome version 108.0.5359.124. Don't know the version of the addon.

---

