---
title: "Browsing problems"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by jbwagjr on 2010-01-04
I successfully installed Ubuntu 9.1 on my brand new Compaq Presario desktop (also running Windows 7).  Everything is working except for what I wanted most:  web browsing.  Using Mozzila 3.5 everthing starts out ok but invariably I do someithing like moving from one site to another or a search on EBay, etc. and the browser either slows down horribly or simply stops browsing.  I exit and relaunch and the problem generally persists unless I wait 5 minutes or so.  Other network functions like system updates, email and networked printing seem to work fine.
 
Any ideas?

---

### Post by johnson.d on 2010-01-05
You can try out the following

1) start the firefox in safe mode for testing purpose using this command at the terminal- "firefox -safe-mode" and browse the same websites in safe mode. This can find if any add-on is responsible for the slow speed of the browsing.
2) If the internet connection is direct try checking whether firefox is using any proxy server for connecting to internet.
3) Try updating Firefox if the update is available with Ubuntu repository.
4) For testing purpose try loading the same websites using other browsers like opera, Google chrome.

---

### Post by cocopuffz on 2010-01-05
I used to have this problem until I installed the proprietary nvidia drivers instead of  the ones that came with the distro... not sure what gpu you've got... but if you've got an nvidia or ati card on it you may try that. You're probably thinking "what does this have to do with web browsing?" ... I thought the same thing until I just tried it. For me.. it turned out it wasn't actually a slow browser, but a crappy gpu driver that was struggling with displaying the browser contents..

You might also try going from IPv6 to IPv4 in the firefox config menu... "about:config" in the address bar. That helps a little.

---

