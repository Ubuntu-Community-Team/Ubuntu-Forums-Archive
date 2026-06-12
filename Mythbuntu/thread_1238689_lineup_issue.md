---
title: "lineup issue"
date: 2009-08-12
forum: Mythbuntu
---

### Post by xinix on 2009-08-12
Hi I live on a university campus and cable is provided for us.  This includes some digital channels in clear QAM (mainly local and a few premium).  The problem is that the channel numbers aren't the same as they are listed in the lineup.  This is because the lineup I use is for an almost identical package that the cable provider offers to the area.  Is there any way I can tell MythTV that channel number 555 in the listing is what the tuner sees as 84.1?

I'm adding a digital tuner soon and would like to resolve this so that programing info is correct.

Thanks!

---

### Post by agamotto on 2009-08-12
I haven't found an answer to this either.  I can't get my digital televisions to agree on where most of the 'digital' channels are either.  The only suggestion offered my Mediacom, my cable provider is of course, to get a digital tuner box for a television that already has a digital tuner built-in.  I am assembling my information for an appropriate complaint to the FCC...

---

### Post by novellahub on 2009-08-13
Go to the schedules direct website and find out the XMLTV ID value for the channel in question.  Then go into Mythweb's channel editor and enter that value to the appropriate channel (Make sure to click the update button as well after editing)

After that, run mythfilldatabase refreshing all channels:

```
mythfilldatabase --refresh-all
```

I had to do this manually for my QAM lineup.

---

### Post by klc5555 on 2009-08-13
> **novellahub said:**
> Go to the schedules direct website and find out the XMLTV ID value for the channel in question.  Then go into Mythweb's channel editor and enter that value to the appropriate channel (Make sure to click the update botton as well after editing)

After than, run mythfilldatabase refreshing all channels:

```
mythfilldatabase --refresh-all
```

I had to do this manually for my QAM lineup.

Note that when you do this, the data will only start being correct at midnight with tomorrow's listings.

For today's listings also to be corrected, you'll need both options specified:

mythfilldatabase --refresh-all  --refresh-today

---

### Post by xinix on 2009-08-13
klc5555 & novellahub,
Thanks a lot!  This is the kind of edit I thought would be possible, but I didn't know how.  I should be getting my digital tuner by the week end so I'll get this ready to go.

---

### Post by novellahub on 2009-08-13
xinix -

You may want to see this as well:

[http://www.mythtv.org/wiki/Comcast_Users_And_scte65scan](http://www.mythtv.org/wiki/Comcast_Users_And_scte65scan)

---

### Post by xinix on 2009-08-16
The edit worked perfectly.  Now my program listing is correct for all channels.  The hardest part was manually adding a few channels that were being scanned as the same channel.  Not sure why it was happening several channels were being detected as the same number during the scan and would overwrite the previous one.

---

