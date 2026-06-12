---
title: "EIT Not Working (Nextek AF9015 DVB-T Tuner) in South Africa"
date: 2010-04-18
forum: Mythbuntu
---

### Post by Grakul on 2010-04-18
Hi, All

I'm running Mythbuntu 9.10 on an old notebook. I have a Nextek AF9015 DVB-T Tuner stick (USB). I can watch LiveTV fine, but I cannot get it to show me EIT listings data! I set up the source in the backend to use EIT listings only, and went into Settings -> Channel Info under Mythweb, and ticked "useonairguide" for all channels, but none of my channels have program data (Neither in Mythweb nor in the Program Guide in the front-end).

It's worth noting that Mythtv doesn't have a setting for South Africa under "Scan Channels", so I had to use UK. However, UK gives me all my channels just fine (I think SA uses the same transponder ranges as the UK).

On Windows, I use the stick under BlazeDTV. It doesn't have a "South Africa" option either, but it has a "Universal" one, which also finds all my channels, and all my program data is there.

Cheers
Grakul

---

### Post by Altino on 2011-05-31
> **Grakul said:**
> Hi, All

I'm running Mythbuntu 9.10 on an old notebook. I have a Nextek AF9015 DVB-T Tuner stick (USB). I can watch LiveTV fine, but I cannot get it to show me EIT listings data! I set up the source in the backend to use EIT listings only, and went into Settings -> Channel Info under Mythweb, and ticked "useonairguide" for all channels, but none of my channels have program data (Neither in Mythweb nor in the Program Guide in the front-end).

It's worth noting that Mythtv doesn't have a setting for South Africa under "Scan Channels", so I had to use UK. However, UK gives me all my channels just fine (I think SA uses the same transponder ranges as the UK).

On Windows, I use the stick under BlazeDTV. It doesn't have a "South Africa" option either, but it has a "Universal" one, which also finds all my channels, and all my program data is there.

Cheers
Grakul


Dear Grakul,

unfortunately, you're experimenting the same issue I had before. Since linuxtv moved drivers from linuxtv.org/~anttip to new linuxtv.org/mchehab/new_build.git, EIT stop working with.

I'm in Portugal and having exactly the same issue. Until yesterday, there was no solution, since I updated the drivers but still no success. 

Kind regards,
Altino

---

### Post by Altino on 2011-05-31
> **Grakul said:**
> Hi, All

I'm running Mythbuntu 9.10 on an old notebook. I have a Nextek AF9015 DVB-T Tuner stick (USB). I can watch LiveTV fine, but I cannot get it to show me EIT listings data! I set up the source in the backend to use EIT listings only, and went into Settings -> Channel Info under Mythweb, and ticked "useonairguide" for all channels, but none of my channels have program data (Neither in Mythweb nor in the Program Guide in the front-end).

It's worth noting that Mythtv doesn't have a setting for South Africa under "Scan Channels", so I had to use UK. However, UK gives me all my channels just fine (I think SA uses the same transponder ranges as the UK).

On Windows, I use the stick under BlazeDTV. It doesn't have a "South Africa" option either, but it has a "Universal" one, which also finds all my channels, and all my program data is there.

Cheers
Grakul





Dear Grakul,

unfortunately, you're experimenting the same issue I had before. Since  linuxtv moved drivers from linuxtv.org/~anttip to new  linuxtv.org/mchehab/new_build.git, EIT stop working with.

I'm in Portugal and having exactly the same issue. Until yesterday,  there was no solution, since I updated the drivers but still no success.  

Kind regards,
Altino

---

