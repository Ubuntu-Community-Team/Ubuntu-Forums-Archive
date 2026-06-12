---
title: "flash player crashes"
date: 2010-04-12
forum: Multimedia Software
---

### Post by kartabosh on 2010-04-12
**lately** my flash player started crashing when i full screen it in youtube, it seams to work fine on any other site but youtube but not only does it crash on youtube fullscreen, it crashes whenever i find any webpage that has a youtube video embedded in it
i tried manually downloading and moving it myself in /usr/lib/flash...  and still nothing 

chromium can play youtube videos in normal mode but not full screen and firefox cannot even open a youtube page, it just crashes

---

### Post by kartabosh on 2010-04-12
also tried this 
[http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/fix_flash_problems_on_ubuntu/)
this
[http://kubuntuforums.net/forums/index.php?topic=3108697.0](http://kubuntuforums.net/forums/index.php?topic=3108697.0)
and others i cant find right now

i think one of the updates ruined the flash player since it worked perfectly until a couple of days ago

---

### Post by oxf on 2010-04-12
For starters I'd be inclined to completely remove it and then reinstall it.

---

### Post by kartabosh on 2010-04-12
i already did that several times, over 10 times

---

### Post by WinterRain on 2010-04-12
> **kartabosh said:**
> i already did that several times, over 10 times

Reinstalling won't do much unless you clear your cache first. Completely remove flash, then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then reinstall flash.

Btw, are you running 32 or 64bit ubuntu?

---

### Post by lovinglinux on 2010-04-12
If you are NOT using *ubuntu-mozilla-daily pp*a, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) and the [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#General-Troubleshooting-Steps-2) sections of the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

If you ARE using *ubuntu-mozilla-dail*y ppa, then see the quote below:

> **lovinglinux said:**
> **[SIZE="4"]Attention Firefox 3.6.4 [Namoroka] ubuntu-mozilla-daily users![/SIZE]**

It seems this is a bug affecting only Firefox 3.6.4 [Namoroka] installed using the *ubuntu-mozilla-daily* ppa. The browser crashes when viewing pages with flash content or content for other plugins.

This problem is due to a bad/old implementation of the new Lorentz technology that should prevent flash from crashing the browser. When opening a page with flash content using Namoroka 3.6.4, there is a new *firefox-bin* process loaded and the browser crashes. 

[Firefox 3.6.4 Lorentz from Mozilla](http://www.mozilla.com/en-US/firefox/lorentz/) doesn't behave like this and instead of loading a new *firefox-bin* process, it loads a *mozilla-runtime* process, which takes care of the flash content. It works like a charm and the browser doesn't crash or lock, even if you are viewing a messed up flash video.

So you have 3 options to fix your problem:

[LIST]
[*]disable *ubuntu-mozilla-daily* and reinstall Firefox to downgrade it to the default browser version
[*]temporarily turn off the flash process isolation following [these instructions](http://ubuntuforums.org/showpost.php?p=9104945&postcount=19)
[*]download [Firefox 3.6.4 Lorentz from Mozilla](http://www.mozilla.com/en-US/firefox/lorentz/) and follow [these instructions](http://lovinglinux.megabyet.net/?page_id=220##1---Manual-installation-of-fresh-final-releases-from-Mozilla-3) to install it.
[/LIST]

There are some considerations about using a ppa repository for Firefox that I would like to highlight:
[LIST]
[*]some ppa repositories like *ubuntu-mozilla-daily* update not only Firefox, but also other Mozilla applications, like Thunderbird.
[*]some ppa repositories like ubuntu-mozilla-daily install development versions of Firefox which does not have the official branding (logo and name). Although they use essentially the same source code, the browser could be called Shiretoko, Namoroka or something else.
[*] some repositories like *mozillateam/firefox-stable* doesn’t seem to be updated frequently, thus missing important security patches.
[*]some repositories like *ubuntu-mozilla-daily* upgrade Firefox with unstable releases, sometimes causing issues, like crashing the browser in specific conditions or preventing it from starting.
[/LIST]

Please Before adding a ppa repository for Firefox, please make sure you understand how the repository works, which version it will install and how often it will provide updates.[color="Sienna"][list]

[*]**Source:** [[color="DarkSlateGray"] Re: Firefox optimization and troubleshooting thread[/color]]("http://ubuntuforums.org/showpost.php?p=9112875")

[*]**Tags:** [[color="DarkSlateGray"]Firefox optimization and troubleshooting thread[/color]]("http://www.google.com/search?q=Firefox+optimization+and+troubleshooting+thread+site:ubuntuforums.org")

[*]**Powered by: **[[color="DarkSlateGray"]QuoteMarks[/color]]("http://lovinglinux.megabyet.net/?page_id=555")[/list][/color]

---

### Post by kartabosh on 2010-04-13
> **WinterRain said:**
> Reinstalling won't do much unless you clear your cache first. Completely remove flash, then do:
```
sudo apt-get clean && sudo apt-get autoremove
```
Then reinstall flash.

Btw, are you running 32 or 64bit ubuntu?

32bit ubuntu on a amd64 processor 
those commands didnt do much its exactly the same

> **lovinglinux said:**
> If you are NOT using *ubuntu-mozilla-daily pp*a, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) and the [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#General-Troubleshooting-Steps-2) sections of the [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

If you ARE using *ubuntu-mozilla-dail*y ppa, then see the quote below:


thanks for all your trouble but i dont really use firefox, i use google-chrome-beta and chromium-browser, firefox was way too much pain in the gas for me so i removed it

---

