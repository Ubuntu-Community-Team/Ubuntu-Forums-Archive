---
title: "my eyes hurt"
date: 2006-07-06
forum: Multimedia &amp; Video
---

### Post by amakiell on 2006-07-06
Im using an nvidia 5200 card with an IBM G97 19" crt monitor. The screen resolution settings claim to be running at 1280 x 1024 at 86Hz. Except that my monitor is clearly at 60Hz because it is so painful to look at. How do I change the refresh rate to a genuine 85Hz?

---

### Post by ajgreeny on 2006-07-06
It may be possible to edit the /etc/X11/xorg.conf file manually or using
"sudo dpkg-reconfigure xserver-xorg"
and entering your monitors horizontal and vertical sync rates.  In my older system the monitor section looked like this:-

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
[I] 	HorizSync	30-70
	VertRefresh	50-160[/I]

The horiz and vert sync figures should be available from the monitor manual or manufacturers info somewhere, so add those two lines shown in italics (figures changes for your monitor, of course) into the section and see what happens; it may give you better options in the desktop setup configuration.

---

### Post by TOPPEL on 2006-07-06
i changed my HorizSync and VertRefresh and saw no Hz change and my fonts were still blurry in terminal and a little shabby in xorg.  

am using latest nvidia driver for FX5200.  quite disappointing.  i dont know if there is a fix.  its running at 80Hz when it should be running at 76Hz or so.. not too much of a difference but another thing -- missing resolutions.  these things make me sad.  

:(

---

### Post by amakiell on 2006-07-08
damn. I modified the /etc/X11/xorg.conf file to include the horizsync and vertrefresh from the manual from the ibm website, and I still dont believe the monitor is doing more than 60Hz. bugger.

---

### Post by jabberwocky on 2006-07-08
> **amakiell said:**
> damn. I modified the /etc/X11/xorg.conf file to include the horizsync and vertrefresh from the manual from the ibm website, and I still dont believe the monitor is doing more than 60Hz. bugger.

my advice to you -- the only way i got it to work, if you have a seperate /home partition, or can back it up.. reinstall from a non-alternate cd..  the one that loads the GUI first.  thats how i got my antiquated 21" CRT to work with more options.  

good luck.

---

