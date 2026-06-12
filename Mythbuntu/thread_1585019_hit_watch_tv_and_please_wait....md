---
title: "hit watch tv and please wait..."
date: 2010-09-29
forum: Mythbuntu
---

### Post by moseleyb on 2010-09-29
Hi Folks,

I am trying to set up 10.04 and when I try to watch tv it says "please wait" and then just bounces me back to the main menu. I am using a homerun HD that has scanned and found channels when setting up the back end but I still can't watch tv with the front end. Any suggestions?

Thanks!

---

### Post by tgm4883 on 2010-09-29
> **moseleyb said:**
> Hi Folks,

I am trying to set up 10.04 and when I try to watch tv it says "please wait" and then just bounces me back to the main menu. I am using a homerun HD that has scanned and found channels when setting up the back end but I still can't watch tv with the front end. Any suggestions?

Thanks!

post your backend logs
/var/log/mythtv/mythbackend.log

---

### Post by ian dobson on 2010-09-30
Hi,

Can you first try recording something and then watching it, just to see if the whole record/playback loop works.

When you try and watch liveTV the frontend says to the backend, start recording this channel, and after a short delay the frontend looks to see if the recording is already on the harddisk and if yes it opens it and starts playing. How long the frontend waits can be configured in Myth-setup under Capture Cards (there are 2 delays that you can change).

Regards
Ian Dobson

---

### Post by goofnrox on 2010-09-30
Are you sure the tuner is set to start on a valid channel? My HDHR got stuck on a channel that no longer existed, and it wouldn't allow me to change channels to a good one. I had to go into the backend setup and change the starting channel to a known good one.

---

