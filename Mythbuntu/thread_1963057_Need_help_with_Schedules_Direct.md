---
title: "Need help with Schedules Direct"
date: 2012-04-21
forum: Mythbuntu
---

### Post by robocrop on 2012-04-21
Ok, I have been using Mythbuntu for a few months. I started out with scanning for channels. Today I signed up with Schedules Direct. I have tried everything I can find to incorporate this into Myth with no success. I deleted all cards and channels from the backend and setup all up again. 

When I setup the capture cards I selected Schedules Direct and was able to gwt my lineup. When I try to Fetch channels I get nothing. Jumping out and back in doesnt improve anything. I cant find any posts out there either.

If you can post a how to, or a link to a how to I would appreciate it.

---

### Post by klc5555 on 2012-04-22
Fetching channels may only work when the database is being set up for the very first time, or it may not work at all. Experiences vary.

SchedulesDirect is only concerned with providing scheduling information for Video Sources. The wiki recommends you set up Schedules Direct to work with Video Sources as described here: [http://www.mythtv.org/wiki/User_Manual:MythTV_structure#Video_sources](http://www.mythtv.org/wiki/User_Manual:MythTV_structure#Video_sources)

The key that links the guide information Schedules Direct supplies with the actual physical channels you have found while scanning in Input Connections is the xmltvid number. These numbers can be found by logging into your SchedulesDirect account, clicking "add a new lineup" and then clicking "preview lineup" for the lineup you have already added. Each channel in the list will have its 5-digit xmlid number associated with it. You might want to print out the list.

When you scanned for channels in Input Connections in the backend setup, the scan may have pulled in from your provider the callsign, name, and xmltvid number for each of the scanned channels, or it may not have pulled in any of this information. Assuming it did not pull the information in, you will have to enter this information into your scanned channels yourself. You can do this in at least two ways: in the frontend by watching a particular channel in live tv and when you decide you know what channel it is, pulling up the "edit" menu with the "e" key, and entering in xmltvid number, callsign, name, and if you wish, the channel number mythtv should give this channel in the schedule. Then exit the menu and move on to another channel.

Or if the channel scan has given you the name/callsign of the station, but not the xmltvid number (or you have already determined the identities of your scanned stations), you may add the xmltvids one after another in the Channel Editor in the backend setup.


In any event, when all of your scanned channels have been edited with their correct xmltvid number and a unique callsign (these can be made up, as long as they are unique), you can run mythfilldatabase to populate the schedule with program information. By default mythfilldatabase will start the supplied information at midnight following the time the command was run. So if you want the entire schedule filled in including today, you should run the command as:
```

mythfilldatabase --refresh-today --refresh-all

```
and once the command has finished, you should be in business.

---

