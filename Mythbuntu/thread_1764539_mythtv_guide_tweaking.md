---
title: "mythtv guide tweaking"
date: 2011-05-21
forum: Mythbuntu
---

### Post by davidstoll on 2011-05-21
If I want a particular video source to use guide info from some particular channel, how do I do that?

So, let's say that /dev/video0 is a source that has guide info (from schedules direct) and also from OTA data.  Let's say that /dev/video1 is another source where there is no guide info available, but I want it to use something from a known source...like what /dev/video0 uses on a particular channel.

How do I do this?

When i edit the channel info on the backend, there is a place to edit a particular channel and even has a spot for a 5 digit XMLTV ID.  I tried to put an XMLTV ID in there from a known source/channel, but it didn't seem to populate...it just says "unknown" when I look at the channel guide for that "channel".

Does this make sense?

---

### Post by davidstoll on 2011-05-26
bump

---

### Post by klc5555 on 2011-05-26
If the XMLTV ID corresponds to a channel that actually exists on a provider listed in your zipcode according to Schedules Direct; and if you have actually subscribed to that particular Schedules Direct lineup in your account, and have the channel corresponding to that particular XMLTV ID enabled in that lineup, then the data should get downloaded and put into the guide (starting with midnight the following day) whenever mythfilldatabase runs.

I've used exactly the same technique myself over the past couple of years when Comcast has added this or that channel in my area, but the only XMLTV listings for these new channels on Schedules Direct was to be found among the local FIOS listings. So I had to add the FIOS listings to my Schedules Direct account, enabled only the needed FIOS channels missing from the Comcast channels, added the XMLTV ID to the appropriate box in mythtv's channel editor and ran mythfilldatabase --refresh-today --refresh-all  ...It works.

---

### Post by davidstoll on 2011-05-27
> **klc5555 said:**
> If the XMLTV ID corresponds to a channel that actually exists on a provider listed in your zipcode according to Schedules Direct; and if you have actually subscribed to that particular Schedules Direct lineup in your account, and have the channel corresponding to that particular XMLTV ID enabled in that lineup, then the data should get downloaded and put into the guide (starting with midnight the following day) whenever mythfilldatabase runs.

I've used exactly the same technique myself over the past couple of years when Comcast has added this or that channel in my area, but the only XMLTV listings for these new channels on Schedules Direct was to be found among the local FIOS listings. So I had to add the FIOS listings to my Schedules Direct account, enabled only the needed FIOS channels missing from the Comcast channels, added the XMLTV ID to the appropriate box in mythtv's channel editor and ran mythfilldatabase --refresh-today --refresh-all  ...It works.

I think it's the command that did it for me.  Must be my database was filled with a bunch of nothing.  I even tried entering/exiting the backend to trigger the mythfilldatabase, but it didn't help.  Manually running it did...I think.  I did change the channel to the extra lineup (with the xml id I wanted to assign to it) also.  This is the same screen where you manually enter the xml id...so, I'm not sure if that helped too, but in either case, it's working.

Thank you.

---

### Post by davidstoll on 2011-06-01
Well, it reverted to no guide info again.  I didn't run the backend setup at all, but after just a few days, I lost guide info.  I tried to go through the process again, but it isn't working.

Any suggestions?

:(

---

### Post by davidstoll on 2011-06-07
It looks like it only downloads/updates about 24 hours (a little less) out from the last mythfilldatabase.  It runs out of channel data before it runs again and I can't schedule anything more than 24 hours out.  Why is it updating my normal channels 2 weeks out, but the extra channel number that I am trying to link to a particular xmlid, only gets 24 hours of data at a time?

hmmm

:(

---

