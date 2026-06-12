---
title: "Add Capture Card screen doesnt load"
date: 2008-07-30
forum: Mythbuntu
---

### Post by Ohs0Ahxi on 2008-07-30
After running updates today my mythbuntu machine started acting up. The frontend would complain it couldnt connect to the master backend although no addresses had been changed. When i opened the backend setup it would tell me that the backend was running so some changes might not work.

Then i decided to stop mythbacked with /etc/init.d/mythbackend stop
and ran it again from the terminal the output was about not being able to open the DVB devices.
I went into backend setup and removed the capture cards and sources and mythbackend started correctly and the frontends could connect.

Now when i try and add the capture cards i am stuck with a blank (themed) screen. If i ALT + TAB the output is roughly (couldn't figure out how to copy it)

```
Loading from : /usr/share/mythtv/themes/ProjectGrayhem-wide/base.xml
Loading from : /usr/share/mythtv/themes/default/base.xml
Couldn't get handle
eno: No Such file or directory (2)

GetSTBListPrivate --begin
GetSTBListPrivate --got lock
GetSTBListPrivate -- end
```

can anyone offer any suggestions?

---

### Post by ian dobson on 2008-07-30
Hi,

Can you try setting your theme back to default then try adding your capture cards.

It sounds as if the ProjectGrayhem-wide theme has afew bugs in it or your copie is corrupt.

You could also try deleting the theme cache.

Regards
Ian Dobson

---

### Post by Ohs0Ahxi on 2008-07-31
> **ian dobson said:**
> Hi,

Can you try setting your theme back to default then try adding your capture cards.

It sounds as if the ProjectGrayhem-wide theme has afew bugs in it or your copie is corrupt.

You could also try deleting the theme cache.

Regards
Ian Dobson

Thanks for the help, i managed to get rid of the theme related errors by changing to another theme. But i was still getting an empty page and still had the ```
GetSTBListPrivate --begin
GetSTBListPrivate --got lock
GetSTBListPrivate -- end
``` in the output when it stopped.
Seeing as some of the previous errors mentioned my DVB tuners, i recompiled the v4l-dvb source, and it all started working again. 

I've just scanned for channels and its all working, changed back to my original theme and its all back to normal.

---

