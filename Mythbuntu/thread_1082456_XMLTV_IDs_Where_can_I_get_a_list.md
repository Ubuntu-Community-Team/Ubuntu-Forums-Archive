---
title: "XMLTV IDs? Where can I get a list?"
date: 2009-02-27
forum: Mythbuntu
---

### Post by AKADAP on 2009-02-27
I have Comcast cable in San Jose CA. At almost exactly the same time as I signed up for Schedules direct, Comcast shuffled its channels around. The result is that most of my cable channels do not get any listings.

If I hit "e" in liveTV, the XMLTV ID shows the word "Loading..." forever.

I do not know how this is supposed to work as I have never seen this work correctly.

If I could get a list of KMLTV IDs, I believe that I could at least get correct listings for the important channels.

---

### Post by theophile on 2009-02-27
Just delete your lineup and let the grabber recreate it with the new channel numbers.

---

### Post by AKADAP on 2009-02-28
> **theophile said:**
> Just delete your lineup and let the grabber recreate it with the new channel numbers.

Delete my lineup? Which lineup? The only one I remember creating was on the schedules direct website, and I had to create that manually.

---

### Post by klc5555 on 2009-02-28
> **AKADAP said:**
> I have Comcast cable in San Jose CA. At almost exactly the same time as I signed up for Schedules direct, Comcast shuffled its channels around. The result is that most of my cable channels do not get any listings.

If I hit "e" in liveTV, the XMLTV ID shows the word "Loading..." forever.

I do not know how this is supposed to work as I have never seen this work correctly.

If I could get a list of KMLTV IDs, I believe that I could at least get correct listings for the important channels.

Log into SchedulesDirect manually over the web. Indicate that you wish to "add a new lineup" for your area code. Do not actually add any new lineup, instead, from the "Add a new lineup for *****" screen, "preview" your current lineup (which will otherwise appear grayed-out. It will then give you a complete list of channel numbers, XMLIDs, call signs, and names for that entire lineup. Print or otherwise save for future reference. Edit required information into frontend using "e" key from livetv, and the listings will begin straightening themselves out for "tomorrow" after the next regularly scheduled mythfilldatabase. (Or do a manual "mythfilldatabase --refresh-today" if you prefer.)

Cheers! :)

---

### Post by AKADAP on 2009-02-28
> **klc5555 said:**
> Log into SchedulesDirect manually over the web. Indicate that you wish to "add a new lineup" for your area code. Do not actually add any new lineup, instead, from the "Add a new lineup for *****" screen, "preview" your current lineup (which will otherwise appear grayed-out. It will then give you a complete list of channel numbers, XMLIDs, call signs, and names for that entire lineup. Print or otherwise save for future reference. Edit required information into frontend using "e" key from livetv, and the listings will begin straightening themselves out for "tomorrow" after the next regularly scheduled mythfilldatabase. (Or do a manual "mythfilldatabase --refresh-today" if you prefer.)

Cheers! :)

Thank you, that was exactly what I was looking for.

---

### Post by AKADAP on 2009-02-28
It took all day, but now I have listings (and icons) for most of my channels.

---

