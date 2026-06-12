---
title: "another flash 9 solution.."
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by gilligan_ on 2007-01-22
There have been tons of posts about how to get
flash9 + sound working. Nothing worked for me so i had
a look into the whole thing..

First of all run firefox from a terminal and have a look at the
output ..

> 
ALSA lib pcm_direct.c:1123:(snd_pcm_direct_open_secondary_client) unable to open hardware


If you get something like the above it is likely that you are having the same
problem that I had. In this case edit your ~/.asoundrc file and paste the
following:

> 
 pcm.!default {
      type hw
      card 0
  }
  
  ctl.!default {
      type hw
      card 0
  }     


Make sure to remove or uncomment the line that includes .asoundrc.asoundconf.
I hope this will help some ppl ..

regards,
gilligan

---

