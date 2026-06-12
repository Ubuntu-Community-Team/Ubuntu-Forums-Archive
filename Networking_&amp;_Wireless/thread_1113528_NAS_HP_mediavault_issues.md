---
title: "NAS HP mediavault issues"
date: 2009-04-01
forum: Networking &amp; Wireless
---

### Post by markosha on 2009-04-01
Hi,

I'm having a strange issue with my NAS drive. To be specific torrent and playing video from the drive. 

The drive is HP mediavault 5140. My laptop is dell e1505 with broadcom wireless card. The issue is the torrents would start downloading and then error out in about a minute. Same for video, it would start then shutter. It happens no matter what torrent client i use - deluged, transmittion, utorrent or what player i use to play video.

The strange part is that i get no issues copying files to/from the drive, in fact it get about 1 -1.5MBs rate. Both the torrent client and video player uses about 1/5 of that rate, so why would i get the issues then?

There are no obvious errors in the logs except these when issues start: 
__ratelimit: XXX callbacks suppressed

I'm using xubuntu 9.04 beta, my drive is mapped as follows:

 //marksvault/Videos /media/vaultvideo cifs credentials=/root/.credentials,nounix,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Anyone has any ideas on what would be the issue?

Thanks,
Mark

---

### Post by sdsmall on 2009-12-08
Mark, I just installed Ubuntu today and am totally ignorant how I can make the appearance of my mediavault drives persistent.

You may or may not have solved your problems by now but you are certainly way ahead of me.  I don't have any idea how to do the equivalent of windows "assign drive letter blah blah to mediavault reconnect at logon".

---

