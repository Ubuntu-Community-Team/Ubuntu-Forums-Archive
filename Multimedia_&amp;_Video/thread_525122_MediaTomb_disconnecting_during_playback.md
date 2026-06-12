---
title: "MediaTomb disconnecting during playback?"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by BKSea on 2007-08-14
I have installed and used mediatomb.  It disconnects me from the server a couple of minutes after starting a video using my DSM-520.  The server disconnects and then reappears almost immediately.  Does anyone have any idea why this is happening?

Thanks, 

Brian

---

### Post by BKSea on 2007-08-14
The server is losing connection with my DSM-520 every 2 1/2 minutes.  It immediately starts up, but then drops again.  I have tried different movie files, and it continues to happen.  Does anyone have any idea why this is happening, or a suggestion on how to repair it?

---

### Post by Roland of Gilead on 2007-11-26
I just installed Mediatomb for the first time, and noticed the same behavior from my DSM-520.

Sorry, no insights as of yet...hoping the bump will get someone more knowledgeable to notice!

---

### Post by engineuity on 2007-12-18
from: [http://mediatomb.cc/pages/devices](http://mediatomb.cc/pages/devices)

D-Link

    * DSM-320
    * DSM-320RD
    * DSM-510
    * DSM-520

Some additional settings in MediaTomb configuration are required to enable special features for the DSM renderers. If you have a DSM-320 and are experiencing problems during AVI playback, add the following to the <server> section of your config.xml:

<custom-http-headers>
    <add header="X-User-Agent: redsonic"/>
</custom-http-headers> 

We also support serving srt subtitles to the DSM players, add the following to the <server> section of your config.xml in order to enable this feature on the DSM:

<manufacturerURL>redsonic.com</manufacturerURL>
<modelNumber>105</modelNumber>

The DSM-510 (probably also valid for other models) will only play avi files if the mimetype is set to video/avi, you may want to add a mapping for that to the <extension-mimetype> section in your config.xml:

<map from="avi" to="video/avi"/>

---

### Post by mechgt on 2008-06-09
I've been having the same issues with my wireless DSM-520, mediatomb 0.11.0, and Hardy.  I'm wondering if I'm not having the TTL issue simply because I have 2 wireless access points in my house linked together on the same subnet (both WRT54Gs running DD-WRT).  How do I check/correct this?  Access point config, mediatomb config, server network card config?!?!

It's a strange problem because I have 2 DSM-520s, and it always (for at least a month or more) impacted one of them, but never the other.  Just last night the second one began disconnecting every ~3 minutes in the middle of viewing.

Everything was running fine before, and this recently popped up, but I can't pinpoint the update that it started, nor if it was at the Hardy upgrade a couple months ago... but it started somewhere in that broad time frame.

I collected a packet sniff using WireShark this morning, but haven't been able to track the problem, (I'm not exactly sure what I'm looking for...)

Any help?  or at least anyone else with this problem?

---

