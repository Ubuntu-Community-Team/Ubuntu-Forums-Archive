---
title: "WinFast TV2000 XP &amp; TVtime"
date: 2006-11-24
forum: Multimedia &amp; Video
---

### Post by rvickers on 2006-11-24
I have a WinFast TV2000 XP Expert Tv card using TVTime. Everything seems to be working fine except the picture quality isn't up to Window$ XP quality. Is there a way to improve this?
Thanks

---

### Post by theorem_hunter on 2007-02-10
please could you put the steps u took to get your winfast tv2000 xp card working. im having no luck... i get his error...

dimitri@programming:~$ tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/dimitri/.tvtime/tvtime.xml"
I/O error : Permission denied
Cannot change owner of /home/dimitri/.tvtime/tvtime.xml: Permission denied.
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

dimitri@programming:~$ sudo tvtime
Password:
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/dimitri/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.
----------------------------------------------------------------

sorry for all that, just not sure whats wrong, i have a ATI Radeon X700 & i think im using the drivers from the repos...

dont know if thats a problem?

---

### Post by rjcroy on 2007-03-06
> **theorem_hunter said:**
> please could you put the steps u took to get your winfast tv2000 xp card working. im having no luck... i get his error...
...
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
,,,
----------------------------------------------------------------

sorry for all that, just not sure whats wrong, i have a ATI Radeon X700 & i think im using the drivers from the repos...

dont know if thats a problem?

[SIZE="2"]Yes, this problem is caused by the poor ATI video drivers. fglrx gave me all sorts of troubles. I could not find a solution to this... Other than changing my video card to Nvidia--much better driver support for linux. My ATI card had other color problems in Linux too. I have never had problems with nvidia cards in Linux. The binary drivers work fine.[/SIZE]

---

### Post by nikoPSK on 2007-09-27
I need to find my card+channel number... :( 

(Winfast TV2000 XP series) :confused:

---

