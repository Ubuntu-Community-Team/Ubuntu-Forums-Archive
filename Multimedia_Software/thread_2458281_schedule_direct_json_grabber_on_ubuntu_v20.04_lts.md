---
title: "schedule direct json grabber on ubuntu v20.04 lts"
date: 2021-02-20
forum: Multimedia Software
---

### Post by majb63 on 2021-02-20
/*
 i am posting the following on this board, as i suspect my problem might be due to some particularities of ubuntu's packaging of tvheadend, when you get it through the "software store".
i have posted this on tvheadend's xmltv board, but because this was not an old-fashioned "apt-get install", i suspect the ubuntu people might know more what's happening.
and, the more eyes on my issue, the better.
cheers.
*/

 hello all --


 i've been trying to get my epg grabber to work under tvhe 4.2.8 in ubuntu 20.04 lts without much success.


 i've downloaded tvheadend from the ubuntu software "store"; it was not an old-fashioned apt-get install.
after i got all my channels configured, mapped and everything in tvheadend, i went to configure the epg grabber.
since i have a schedule direct account, might as well use that.

 
so i ran the script "tv_grab_zz_sdjson --configure" in  /snap/tvheadend/152/usr/bin: it generated a config file in  /root/.xmltv/. 
the file name is "tv_grab_zz_sdjson.conf".
I then ran the script from the command-line (again, in /snap/tvheadend/152/usr/bin) to make sure everything was ok;
it ran successfully and generated a cache file in /root/.xmltv/.
that file name is "tv_grab_zz_sdjson.cache".
both files are owned by root, with rw,r,r permissions.

 
before choosing the epg grabber, i got the tvheadend log pane to show up (at the bottom of the window).

 
so i selected the schedules direct grabber (json interface, no sql lite), enabled it and clicked on "save".
tvheadend then tried to run "/snap/tvheadend/152/usr/bin/tv_grab_zz_sdjson", only to tell me i had to configure
the grabber by running it with --configure. (huh, i did it already?)
it also complained with "no output detected" and "grab returned no data".

 
thinking it might need a reboot for the new config (i disabled the over-the-air epg and enabled the scheduledirect
one) to kick in, i rebooted the box. that didn't help, same result.

 
i've tried to point it to the configuration file by specifying "--config-file ~/.xmltv/tvgrab_zz-sdjson.conf" in the
"extra arguments" field, to no avail.

/* btw, i did try both "~/.xmltv/tvgrab_zz-sdjson.conf" and "/root/.xmltv/tvgrab_zz-sdjson.conf". saw no difference. */ 

 
am not sure what to do next, though i'm convinced the problem is staring me in the face and i can't see it.

 
anyone else run into this?

 
thanks in advance.

---

