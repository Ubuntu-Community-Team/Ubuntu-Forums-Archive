---
title: "Rythmbox cannot find application/x-gst_ff-vc1test decoder"
date: 2009-06-25
forum: Multimedia Software
---

### Post by bswilson on 2009-06-25
Friends,

About a week ago, I began noticing that when I plug in my iPod Shuffle (2G), a dialog box appears asking me to search for a suitable plugin.  Granted, I did switch about 2 weeks ago from using Amarok back to Rhythmbox after upgrading to Jaunty because the newest Amarok just sucks (IMHO).

Anywhoo, I see the following dialog boxes but I can never seem to get a suitable plugin.  All operations of my iPod and of Rhythmbox are fine.  Does anyone know what I should do here?  Thanks.

---

### Post by Screatch on 2009-07-25
I have the same problem, but in addition to x-gst_ff-vs1test decoder, system cant find also x-mswinurl and Windows media audio decoder. Its kinda annoying as he tells me this everytime i start RhytmBox

---

### Post by lucasgz on 2009-08-24
i have the same problem anyone any idea?:confused:

---

### Post by mc4man on 2009-08-24
What's somewhat unclear is if the warning itself that's the issue or something else functional
> 
All operations of my iPod and of Rhythmbox are fine
> 
have the same problem 


If just the pop up warning. what might be going on in rhythmbox is this or similar

> Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355
no application found
Rhythmbox-Message: No installation candidate for missing plugins found.
**
ERROR:gsttagdemux.c:418:gst_tag_demux_trim_buffer: assertion failed: (out_size > 0)
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|application/smil decoder|decoder-application/smil
no application found
Rhythmbox-Message: No installation candidate for missing plugins found.
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|application/smil decoder|decoder-application/smil (ignoring)
Rhythmbox-Message: All missing plugins are blacklisted, doing nothing
**
ERROR:gsttagdemux.c:418:gst_tag_demux_trim_buffer: assertion failed: (out_size > 0)
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|application[COLOR="Blue"]/x-gst_ff-vc1test decoder|decoder-application/x-gst_ff-vc1test[/COLOR]
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 (ignoring)
Rhythmbox-Message: All missing plugins are blacklisted, doing nothing
Rhythmbox-Message: Missing plugin: gstreamer|0.10|rhythmbox-metadata|audio/x-asf-unknown decoder|decoder-audio/x-asf-unknown, codec_id=(int)355 ([COLOR="Blue"]ignoring[/COLOR])
Rhythmbox-Message: All missing plugins are **blacklisted**, [COLOR="Blue"]doing nothing[/COLOR]

A couple of possible causes would be having one or more i-tunes purchased tracks on the ipod, and or using a ipod set up orig. on a mac.

For the former. maybe try turning off auto-detect new files in rhythmbox

---

### Post by lordmorgoth on 2009-09-19
:( getting the same problem, any luck fixing it ?

---

### Post by Screatch on 2009-09-22
Actually, disabling auto detect seems to be working good.
Thanks.

---

