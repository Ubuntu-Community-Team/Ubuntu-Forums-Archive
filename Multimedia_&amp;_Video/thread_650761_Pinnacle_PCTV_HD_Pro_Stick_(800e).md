---
title: "Pinnacle PCTV HD Pro Stick (800e)"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by fearpi on 2007-12-26
I have the [aforementioned device]("http://linuxtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_Stick_%28800e%29"), and using [this walkthrough]("http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices") I have been able to view analog signals just fine with tvtime. However, I have two issues:

1. I get no sound. Incidentally, Gutsy has been nothing but problems in that department anyway; in Feisty, it worked just fine; in Dapper, it worked like it does now. But I digress; I do have sound from the rest of my system.

2. I have no idea how to set up the device to use HD channels, nor how to view them. I'd rather not touch MythTV, but use something leaner like tvtime or mplayer. Most of the guides I've seen that might otherwise be helpful to me focus on DVB-T and DVB-S and other standards that are not used in the United States and are not ATSC.

Has anyone had success on either counts with this device?

---

Edit 1: Though I was hesitant to deal with MythTV, one of its [wiki pages]("http://www.mythtv.org/wiki/index.php/Pinnacle_PCTV_HD_Pro_USB_Stick") has proven valuable. Using the command at the bottom of the page (but modified for Ubuntu), I was able to generate a channels.conf file:

 scan /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.mplayer/channels.conf

Now, it seems I can view HD channels using "mplayer dvb://<channel>". Still working on sound.

---

### Post by RC Howe on 2007-12-29
The audio problem is just MythTV trying to manage its own audio.

To disable it, go to Setup > General, and press next until you get to the audio section (second or third one, I think). Uncheck the box that says "Use internal volume controls". This will let you manage the volume with the default Ubuntu volume manager.

---

### Post by fearpi on 2007-12-29
I never used MythTV. For analog signals, I am using tvtime.

---

