---
title: "mythfilldatabase stopped working - tv_grab_uk_rt"
date: 2009-01-20
forum: Mythbuntu
---

### Post by wizgnome on 2009-01-20
Hi,

I have been running my mythtv system (0.21 with mythbuntu 8.10) since November without any problems. Last weekend I saw that mythfilldatabase was failing with error 6400 when started by mythtv running as the mythtv user.

If I ran it from my own user it worked fine, so I changed the settings to use a crontab to run it. All was fine untill today when it stopped running with the same error again.

Looking at the log it fails with the line:
Use of uninitialized value $num_good_channels in numeric lt (<) at /usr/bin/tv_grab_uk_rt line 709.
Error: No usable XMLTV channel definitions seen in channel_ids, exiting at /usr/bin/tv_grab_uk_rt line 709.

I also use the tv_grab_nl_py script to fetch NL listings and that works without any problem. Its only the tv_grab_uk_rt script that fails.

I have just tried running it as root and it works fine, so I assume its a permissions problem - but what? 

Could something in a mythbuntu update have changed something?

Has anyone got any suggestions as to what had changed?

Mike.

---

### Post by wizgnome on 2009-01-20
Whilst running mythfilldatabase as root my internet connection went down (I wish XS4ALL/KPN would sort out the problem with the line).

I then got the same problem running as root. I noticed that a .xmltv/supplement/ directory had been created for each user. 

I removed the supplement directory and all the files there and now it works again. :D

---

