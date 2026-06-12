---
title: "Google Chrome Browser - 1st impression"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by KaYnemO on 2009-12-12
Just downloaded and installed on my 9.10 Ubuntu a new Google Chrome browser. First thought are: very fast startup, low memory consumption, good flash plugin handling and memory allocation. Very fast webpage load up and nice content visualization. So far so good - I am liking it. Any thoughts/reviews ? I would've liked to know other people's associations.

---

### Post by Marlonsm on 2009-12-12
IMO, Chrome is ***fast*** but that's pretty much it.
You won't find most of the fancy features of other browsers there. Although it seems their add-on library is growing fast.
Until Chrome gets add-ons like Qtl (quick translator/dictionary), All-in-one sidebar, dictionary auto-switcher, FireGestures and DownThemAll, I'll stay with Firefox.

---

### Post by serstickman on 2009-12-12
> **KaYnemO said:**
> Just downloaded and installed on my 9.10 Ubuntu a new Google Chrome browser. First thought are: very fast startup, low memory consumption, good flash plugin handling and memory allocation. Very fast webpage load up and nice content visualization. So far so good - I am liking it. Any thoughts/reviews ? I would've liked to know other people's associations.

It's screaming fast, I agree.  Not being able to change the font settings (under the hood change does not work for me) is a major downer for me.

---

### Post by KaYnemO on 2009-12-12
it is true the whole thing is raw right now, not too many add-ons and themes, but give them a little time - considering it is Google behind all that, it will not take to long for them to make more addons and stuff.

---

### Post by A_T on 2009-12-12
More addons means slower so I hope they keep it light.

---

### Post by gradinaruvasile on 2009-12-12
> **KaYnemO said:**
> Just downloaded and installed on my 9.10 Ubuntu a new Google Chrome browser. First thought are: very fast startup, low memory consumption, good flash plugin handling and memory allocation. Very fast webpage load up and nice content visualization. So far so good - I am liking it. Any thoughts/reviews ? I would've liked to know other people's associations.

About the memory consumption - IT IS NOT LOW. 
Chromium spawns separate processes (named chrome) for EACH TAB. Beside those it has a "master" thread (the biggest in memory usually) and a process (named "exe") that is the flash plugins thread. Count them all in and you will be surprised how much memory is used. This threading means it is much more stable than other browsers (one tab content crashes, the others are unaffected).
But despite these it manages to run fast on lower memory (512 MB in my case) and slower CPU hardware.

I see the difference on a P4 Mobile powered old laptop with 512 mb RAM - firefox (both 3.0 and 3.5.5) takes ages to load and lags badly if there are a few tabs opened. In contrast Chromium launches fast and i saw even 30-40 tabs opened and it was working well.

And yes, its the fastest browser around. It has its rough edges (some of them like the java plugin incompatibility come from webkit) but its damn stable and fast for a beta browser.

Also some addons like adblocker already exist.
Its named AdBlock+:

[http://www.chromeextensions.org/appearance-functioning/adblock/](http://www.chromeextensions.org/appearance-functioning/adblock/)

It needs a bit of mouse handling profficiency in some cases - the rule of thumb is that always select the frame drawn by the plugin when in block mode (sometimes with pixel precision) of the object (and wait for the yellow label with the object id to appear)you want to block to avoid opening of the ad. But once mastered, you can block just about any frame/object visible on the page - that in many cases wont work in the firefox adblocker unless you manually select it from the list of blockable items (which is sometimes tedious).


Edit: i meant flash plugin, not java. My mistake. Corrected.

---

### Post by thienhaxanh2405 on 2009-12-15
make chrome default browser =p~
so fast :D
[RIGHT][IMG]http://laptopviet.info/thienhaxanh2405/thx.gif[/IMG][/RIGHT]

---

### Post by gradinaruvasile on 2010-01-15
I found that you can enable the Java plug-in support. Some java builds  from the PPAs already make it so in 9.10, but in 9.04 i had to manually link a file to get it work (locate the libnpjp2.so file if it returns an error, this is done with the default jvm install):

```
sudo ln -s /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so /usr/lib/mozilla/plugins/
```

restart the browser, open java.com, click "Do i have java?" and see if the plugin is detected. This will enable the java applet-based stuff (like Runescape) to run in Chromium/Chrome. Note that i use the latest Chromium dev build ( 4.0.299.0 (36335) ), i dont know what version introduced this feature.

---

### Post by KaYnemO on 2010-04-04
ok, now! It has been quite a few months that I've been automatically using chrome and I got to say I've got extremely used to it... It runs well (so far), fast and furious. Nothing else to report - just got used to it :)

---

### Post by alexdelprogramador on 2010-04-04
ive just installed it

its really quick
 
also I used Seamonkey, but chrome its better ;)

---

