---
title: "Mythtv program data not showing up correctly."
date: 2018-12-19
forum: Multimedia Software
---

### Post by Tadaen_Sylvermane on 2018-12-19
My issue is odd. Never noticed it before as I barely watch TV. My wife watches the spanish channels here in Tucson, AZ. I am running Mythtv .28 backend through Kodi 17.6 as my front end. I'm quite certain this is a mythtv issue though. TV is OTA, no cable or satellite. It's only the Spanish channels that have this issue.

In my case I have 2 channels that show nothing for program data. The bar is just grey in the guide display. However when selecting those channels they play tv from another couple channels. When I goto those channels as listed in the guide, it simply says channel unavailable. So somehow, or why I don't know my data isn't showing on the proper channel under the guide. As such it makes recording impossible. How can I straighten this out?

---

### Post by #&amp;thj^% on 2018-12-20
_Total stab in the dark here_ but sometimes it gets confused because its already cached the programs. Might be worth clearing the cache

```

mythutil --cleareit
```

Perform EIT scan >> If enabled, program guide data for channels on this source will be updated with data provided by the channels themselves 'Over-the-Air'.

---

### Post by Tadaen_Sylvermane on 2018-12-27
Sorry to take so long to reply. I did clear the cache but had the same problem. I decided on a random idea to check my lineup on Schedules Direct. I deleted my old lineup and changed to my current zip code. A few years ago my zip code was changed and was too new and Schedules Direct didn't recognize it so I had used my old zip code. I tried putting in my current zip code and everything works fine. The two 34.1, 34.2 channels showed up but I made them invisible in the channel editor. Also made a few others invisible. Restarted Kodi, reloaded database and all channels work as they should. No more "Channel Unavailable" messages where they previously showed that.

---

