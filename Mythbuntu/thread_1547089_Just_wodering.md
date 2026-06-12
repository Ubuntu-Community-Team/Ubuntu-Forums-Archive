---
title: "Just wodering"
date: 2010-08-06
forum: Mythbuntu
---

### Post by jrhartley on 2010-08-06
Ive used myth tv... different flavors in the past,mythbuntu,mythdora,ect..i have a set-up that incldes 2 networked media adapters(buffalo linktheater and pinnacle showcenter 200)I use the upnp media server built in to myth tv and it worked very well.then I started downloading shows from bittorrent sites and that has worked well too.problem is when I do the downloading Im using a windows based pc then I serve it to my media adapters using Wizdxp...Is there a way i can just do everthing with mythbuntu?my knowlege of linux is average...thanx

---

### Post by LowSky on 2010-08-06
Please put space between a sentence's period and the first word of the next sentence, thanks.


bittorrent is including in Ubuntu and can be added easily to Mythbuntu if it not included by default.

Downloading shows off bittorrent may be illegal so be careful.

---

### Post by jrhartley on 2010-08-06
OK thanks for the reply. I didn't know that downloading TV shows that have already aired was considered illegal.I guess I no longer need to integrate that function into my myth box.The quality wasn't bad but it wasn't HD. The really killer feature was no commercials. Is this grammar better?

---

### Post by newlinux on 2010-08-06
legal ramifications aside (different laws in different countries, I won't pretend to know them all). You can add the videos to mythvideo, which I think is now served via myth's UPnP server. So you could add a mythvideo storage group that has the files you are downloading in it, rescan in mythvideo, and then they should be available via mythtv' UPnP server.

Alternatively, as suggested earlier, you can just use a Linux bittorent client (there are many) and download them to a directory mythvideo is already using.

---

### Post by jrhartley on 2010-08-06
Hi newlinux thanx for the reply
would I have to shut down mythtv to do what you suggest. Im a little confused on the whole mythtv operation. I never cared before because I was just recording the shows and serving them out and it did it well with no issues. now do i have to go back into the desktop or run a cron or script????

---

### Post by newlinux on 2010-08-06
Where do you plan on storing the files you download? IF you put them in a directory mythvideo is already configured to use all you have to do is go into the mythvideo directory (in mythfrontend) and scan for changes and the files should show up. No shutdown of the frontend or backend needed. Or you could mount the files locally and add that directory to mythvideo storage groups or mythvideo directories.

[http://www.mythtv.org/wiki/MythVideo#Setting_up_Video_and_Image_Folders](http://www.mythtv.org/wiki/MythVideo#Setting_up_Video_and_Image_Folders)

for more info...

---

