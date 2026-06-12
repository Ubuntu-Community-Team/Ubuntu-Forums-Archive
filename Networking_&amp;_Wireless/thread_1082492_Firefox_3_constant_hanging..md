---
title: "Firefox 3 constant hanging."
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by mjoolnir on 2009-02-27
I've been having issues with Firefox 3.0.4pre hanging. It seems to begin about fifteen minutes after starting, then every 30s or so it locks up. During these lockups I can't scroll, switch tabs, click anything, or close FF without using ```
kill -9
``` These lockups make FF unusable. How can I diagnose what is causing these lockups? Is this a known problem and if so is there a fix?

---

### Post by lidex on 2009-02-27
You could try opening your system monitor before starting Firefox to see what processes are involved. Firefox freezing up for me usually means Flash Player or Adobe Reader. 

Have you tried re-installing or running with a fresh profile? Version 3.0.6 is available through Synaptic from Intrepid updates. I am currently
using that on AMD64 with no problems.

---

### Post by mjoolnir on 2009-02-27
I don't have Adobe Reader or Flash installed, I've tried creating a new profile and the freezing went away for a few days but they just come back. To be specific I am running Swiftfox Athlon XP, but the problem appears in both Swiftfox and Firefox. Top doesn't reveal any processes using alot of CPU when I start Swiftfox. Is there a program to see what processes start after Swiftfox starts?

---

### Post by lidex on 2009-02-27
I'm not familiar with Swiftfox. There may be an issue using two browsers with one installed in a non-standard location using plug-ins/profiles of the other. Just a guess. Seems to be some kind of conflict. Did you have any issues b4 Swiftfox?

I would try completely removing both - including profile directories and the .mozilla folder in your home directory. Then do a clean install of only one browser.

---

### Post by mjoolnir on 2009-02-27
Swiftfox is just FF compiled with optimizations for specific architectures. FF had these exact same problems before I installed Swiftfox, in fact I installed Swiftfox in hope that it would not be affected by this issue. I'll uninstall them both and reinstall Swiftfox. Does FF store file in any directories besides ~.mozilla?

---

### Post by lidex on 2009-02-27
usr/share/firefox
usr/share/mozilla
may be something in opt/ from Swiftfox

You were using Firefox 3.0.4 pre originally - when you first had problems?
What version of Ubuntu?

---

### Post by mjoolnir on 2009-02-27
Xubuntu 8.10 2.6.27-11-generic i686. I've reinstalled Swiftfox, /usr/share/mozilla and /usr/share/firefox are both just defaults now, /opt/ is emtpy. I was using the latest Ubuntu package for FF before I installed Swiftfox. The current Swiftfox package is at 3.0.4pre.

---

### Post by mjoolnir on 2009-02-28
bump

---

### Post by lidex on 2009-03-01
What's your Swiftfox status - still hanging? Did you delete old profiles?

---

### Post by mjoolnir on 2009-03-02
Its not hanging yet, probably because it hasn't built up enough profile data.

---

### Post by mjoolnir on 2009-03-05
> **Exilim said:**
> May be its coz of RAM memoary mismatch. Just a wild guess. Try increasing it.

I have 3GB of RAM and all the sticks pass Memtest86+, I will try increasing the heap size. Swiftfox is now hanging for about 5s every 15s. I have Fasterfox Lite, Adblock Plus, Adblock Element Hiding Helper, and Greasemonkey installed. Greasemonkey is only running the script "Disable Text Ads". Top lists this ```
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
31044 mike      20   0  938m 782m  29m R 51.3 27.0 284:17.83 swiftfox-bin
31027 mike      20   0  1844  528  456 S  0.0  0.0   0:00.00 swiftfox
```

---

