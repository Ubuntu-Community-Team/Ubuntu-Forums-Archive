---
title: "Zoneminder upgrade - 1.26 to 1.32"
date: 2019-09-19
forum: Multimedia Software
---

### Post by juanboy2k on 2019-09-19
Unable to get images to show and various errors in the logs  Here's the primary issue I'm guessing ... i have a zmdc.sock=  in the /tmp/zm  folder and that's it..  

I updated on an ubuntu 14.04 workstation, from 1.26 of ZM to 1.32. ... the install when fine... DB got updated with no issues.    But had various config issues with apache that got sorted out when i re-enabled the cgi, write, and such.  

Any suggestions other than starting with a fresh install?  Are the camera properties i used under 1.26 compatible with 1.32 as is? 
[TABLE="class: major table-sortable, width: 1244"]
[TR="class: log-err"]
[TD="bgcolor: #FFCCCC, align: left"]2019-09-19 17:23:52[/TD]
[TD="bgcolor: #FFCCCC, align: left"]web_js[/TD]
[TD="bgcolor: #FFCCCC, align: left"]12388[/TD]
[TD="bgcolor: #FFCCCC, align: left"]ERR[/TD]
[TD="bgcolor: #FFCCCC, align: left"]getStreamCmdResponse stream error: Socket /tmp/zm/zms-832658s.sock does not exist. This file is created by zms, and since it does not exist, either zms did not run, or zms exited early. Please check your zms logs and ensure that CGI is enabled in apache and check that the PATH_ZMS is set correctly. Make sure that ZM is actually recording. If you are trying to view a live stream and the capture process (zmc) is not running then zms will exit. Please go to [http://zoneminder.readthedocs.io/en/latest/faq.html#why-can-t-i-see-streamed-images-when-i-can-see-stills-in-the-zone-window-etc](http://zoneminder.readthedocs.io/en/latest/faq.html#why-can-t-i-see-streamed-images-when-i-can-see-stills-in-the-zone-window-etc) for more information. - checkStreamForErrors()[/TD]
[TD="bgcolor: #FFCCCC, align: left"]?view=watch[/TD]
[TD="bgcolor: #FFCCCC, align: left"][/TD]
[/TR]
[TR="class: table-tr-odd log-err, bgcolor: #EEEEEE"]
[TD="bgcolor: #FFCCCC, align: left"]2019-09-19 17:23:52[/TD]
[TD="bgcolor: #FFCCCC, align: left"]web_php[/TD]
[TD="bgcolor: #FFCCCC, align: left"]12388[/TD]
[TD="bgcolor: #FFCCCC, align: left"]ERR[/TD]
[TD="bgcolor: #FFCCCC, align: left"]Socket /tmp/zm/zms-832658s.sock does not exist. This file is created by zms, and since it does not exist, either zms did not run, or zms exited early. Please check your zms logs and ensure that CGI is enabled in apache and check that the PATH_ZMS is set correctly. Make sure that ZM is actually recording. If you are trying to view a live stream and the capture process (zmc) is not running then zms will exit. Please go to [http://zoneminder.readthedocs.io/en/latest/faq.html#why-can-t-i-see-streamed-images-when-i-can-see-stills-in-the-zone-window-etc](http://zoneminder.readthedocs.io/en/latest/faq.html#why-can-t-i-see-streamed-images-when-i-can-see-stills-in-the-zone-window-etc) for more information.[/TD]
[TD="bgcolor: #FFCCCC, align: left"]/usr/share/zoneminder/www/includes/functions.php[/TD]
[TD="bgcolor: #FFCCCC, align: left"]2048[/TD]
[/TR]
[/TABLE]

---

### Post by yancek on 2019-09-20
Have you verified that zoneminder is running as suggested in the output you posted?
Have you checked that the PATH_ZMS is set correctly?
You might want to do a new install of Ubuntu as 14.04 has not been supported since April of this year.

---

### Post by juanboy2k on 2019-09-20
Thanks!  as it turns out, I did indeed install 16.04 of ubuntu ... however, I ended up right back where I was.  I actually ended up removing ZM and totally reinstalling (dropping the database etc).   As it turns out, the whole problem was the typical path issue.  Unfortunately, EVERY REFERENCE I COULD FIND re: how to ensure that the script alias and PATH_ZMS variable was set correctly, referred to a console OPTIONS ==> PATH setting that is NO LONGER present on 1.32 of ZM.  which brings up a curious problem as to how to ensure folks new to this level of support can possibly find the correct answers online without having to actually make a post.  When the actual functionality of the product changes like this, and the old docs are still readily accessible.. it makes it difficult to keep from pulling out your hair.    I was unable to figure this out until I actually SEARCHED GOOGLE for "ZONEMINDER MISSING PATH_ZMS"    at which point, i found the handy site that explained as how these path variables are now in zmcustom.conf as noted here (if this is allowed:)   [https://forums.zoneminder.com/viewtopic.php?t=27722#p108059](https://forums.zoneminder.com/viewtopic.php?t=27722#p108059)

Once I realized that the path variables are now in [COLOR=#333333][FONT=&amp]zmcustom.conf in /etc/zm/conf.d  the world was a much better place, and immediately the camera i had defined started working. I simply had to insert "/zm" in front of the default setting there.  Getting a few other cameras to work was very difficult due to odd FOSCAM HD camera settings, but I finally got there.   We're back in business - though i do have to re map my zone on the motion detection camera.[/FONT][/COLOR]

---

### Post by juanboy2k on 2020-06-09
So one more item here ... i'm now looking at the situation of 18.04.4.  So is it the case that when updating the OS like this, that you end up having to *reinstall* ZM  as opposed to doing an upgrade?  and if that's the case, does it mean i have to uninstall ZM ? Not sure how to actually go about any of that).  thanks!

---

