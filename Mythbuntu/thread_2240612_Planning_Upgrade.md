---
title: "Planning Upgrade"
date: 2014-08-21
forum: Mythbuntu
---

### Post by mattshaw on 2014-08-21
Hi everybody

I am planning to upgrade my setup after the upcoming new series of Doctor Who. I have to do this
as my frontend running MythBuntu 12.10 is no longer receiving updates for XBMC/Kodi/Kernel etc.....

I also have a MythBuntu backend running 12.10 and MythTV0.25 fixes.

I would like to upgrade to the latest 0.27 on the backend, to get faster channel changes etc, but am
not too sure how to proceed. If I just upgrade the frontend and limit it to 0.25fixes, I won't need to
upgrade the backend. I have heard some bad stories about the 14.04 release.

Is there a release before 14.04 that will be LTS ???

The easiest way is I am sure is just to update the frontend, and leave the backend alone, but just
want some clarification

Regards
Matt

---

### Post by tgm4883 on 2014-08-21
> **mattshaw said:**
> Hi everybody

I am planning to upgrade my setup after the upcoming new series of Doctor Who. I have to do this
as my frontend running MythBuntu 12.10 is no longer receiving updates for XBMC/Kodi/Kernel etc.....

I also have a MythBuntu backend running 12.10 and MythTV0.25 fixes.

I would like to upgrade to the latest 0.27 on the backend, to get faster channel changes etc, but am
not too sure how to proceed. If I just upgrade the frontend and limit it to 0.25fixes, I won't need to
upgrade the backend. I have heard some bad stories about the 14.04 release.

Is there a release before 14.04 that will be LTS ???

The easiest way is I am sure is just to update the frontend, and leave the backend alone, but just
want some clarification

Regards
Matt

What bad stories?

---

### Post by topcat5 on 2014-08-22
I just did this upgrade.   I didn't have any issues with it but I do have the OS on a different physical  drive than that of the MythTV storage drives.   I followed the recommendation off the mythbuntu homepage.   i.e.  Backup your database using the mythtv tools.  Backup your home and mythtv home folders.  Backup any relevant files from /etc.   I'd also go to mythweb and print out your channel listing and possibly recording schedules.   Then do a clean install of mythbuntu and then restore the abov

It was pretty painless for me.  I upgraded my backend by this method.  One of my FEs got a full new install as well.  The other FE, I left at 12.04 so simply updated the version of mythbuntu (in the control center)  to match.  It works fine.

I did experience a Nvidia related video tearing problem which has since been fixed.  (turn off composting in both XFCE and in xorg.conf)


BTW, if you have a OTA antenna and RetroTV is available in your area, Classic Dr. Who is on in the afternoons.  They have started with the very rarely seen in the USA 1st Dr.  (assuming you are in the USA)

---

