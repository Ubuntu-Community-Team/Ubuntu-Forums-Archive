---
title: "ushare and xbox video streaming problem"
date: 2011-12-26
forum: Multimedia Software
---

### Post by wujj123456 on 2011-12-26
Hi everyone,

I recently tried to stream video from Ubuntu to my XBOX360. After some searches, I found ushare. Once I start ushare, my XBOX360 can successfully detect my Ubuntu machine, and pull the folder/video list. However, all videos are not playable. If I copy the videos to a flash drive and plug into my XBOX360, it plays well. Streaming same videos from WMP12 also works. 

Anyone is having this problem or knows its solutions? I search the forum, but didn't find any answer. I am also open to alternative package/software (as long as it's free). 

Btw, I used the ushare in Ubuntu 11.04 repository, started the service with -x. My XBOX360 also has the latest update. My config is pasted below: 
USHARE_NAME=Ubuntu
USHARE_IFACE=eth2
USHARE_PORT=
USHARE_TELNET_PORT=
USHARE_DIR=/media/All/Videos
USHARE_OVERRIDE_ICONV_ERR=
USHARE_ENABLE_WEB=no
USHARE_ENABLE_TELNET=no
USHARE_ENABLE_XBOX=yes
USHARE_ENABLE_DLNA=no

Thanks.

---

### Post by wujj123456 on 2011-12-27
Bump.

I tried XBMC just now, and it works for XBOX360 streaming. However, importing videos into XBMC is really painful with the mandatory scrapper. Would be nice if I can get ushare working.

---

