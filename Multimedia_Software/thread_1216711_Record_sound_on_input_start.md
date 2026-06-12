---
title: "Record sound on input start"
date: 2009-07-18
forum: Multimedia Software
---

### Post by nuekleer on 2009-07-18
Hi guys!  First post but really need some help.  

I'm looking for software or how to in any language to record from sound card microphone when talking or sound starts.  

I'm trying to build a machine to listen to a police scanner and record after it hears a certain tone.  

So I guess I need code or software to detect tones as well.  I'm not a newb - been programming a while but never worked with hardware like talking to a sound card.  Any help would me much appreciated.  

Thanks guys!

---

### Post by samichx on 2011-11-09
There is no application that performs all of these functions automatically with a GUI but there is a script that you can use that'll record intervals of your choosing.

Here: [http://linuxmoc.wordpress.com/2009/12/04/linux-scanner-recorder-rev-3/](http://linuxmoc.wordpress.com/2009/12/04/linux-scanner-recorder-rev-3/)

Combine that with a cron task ('sudo crontab -e' or 'crontab -e') and you can have each hour, day or week output to a file.

Stuck with the second script on that page with hourly recording on days known to be busy and used the first script for weekend monitoring on the HAM bands.

---

