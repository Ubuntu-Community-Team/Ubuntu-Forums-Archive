---
title: "Another Nova-T DVB-T MythTv/Feisty question"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by lemmyc on 2007-04-29
Hi all,
When i run through the MythTV capture card settings, none of the options appear to work. I try to add a capture card, but nothing seems to happen. Should the card appear in the menu once it's been added?
The card appears to be detected in the first two options for capture card types, but not in the third. Could it be that the third option is the one I want? :confused: 
I've seen other posts where users have entered the following at a terminal: sudo modprobe cx88-dvb
This seems to have no effect in my case.
Anyone out there can walk me through this?
Thanks!

---

### Post by lemmyc on 2007-04-30
bump?

---

### Post by daverave999 on 2007-04-30
I found [this site]("http://parker1.co.uk/mythtv_ubuntu.php") very useful. I believe you need to add ```
cx88_dvb
``` into the /etc/modules file. Reboot.

See if you have any success then?

HTH

---

### Post by lemmyc on 2007-05-02
Thanks. I already had that in my modules file though.
My card seems to be detected OK. But when I choose the appropriate capture card, nothing happens. I'm just taken back to the capture card menu again.
If I then try to "delete all capture cards" I get an error message saying the operation failed. It seems no card was selected.

Not really sure how to troubleshoot this one.

---

### Post by superm1 on 2007-05-03
> **lemmyc said:**
> Thanks. I already had that in my modules file though.
My card seems to be detected OK. But when I choose the appropriate capture card, nothing happens. I'm just taken back to the capture card menu again.
If I then try to "delete all capture cards" I get an error message saying the operation failed. It seems no card was selected.

Not really sure how to troubleshoot this one.
It's sounding like possibly you have a corrupt database?  If so your the third one in the past few days I've seen.  Two options you can try:
- Either remove mythtv-database, drop your database, and reinstall mythtv-database.
- *Purge mysql-server-5.0 and mythtv-database, then reinstall both.

---

### Post by lemmyc on 2007-05-03
That got things working, thanks! 
Now I just need to sort out the audio and the channel listings. :/

---

