---
title: "Flash Player Update needed - Flash-Aid not working"
date: 2011-11-26
forum: Multimedia Software
---

### Post by Odense on 2011-11-26
Yesterday when I entered a site that worked OK previously I got this message:

"We have detected that you do not have the newest version of Flash Player installed.  Therefore, your connection has been switched to the Java connection mode.  For a better experience, please click here to upgrade to the latest Flash Player for free.  View current connection mode."

After logging in to these pages I decided that the Flash-Aid Add-On to my firefox was the way to go. So I installed that and used it with the following results:

"***************************************************************************
*****************PLEASE WAIT...DON'T CLOSE THIS TERMINAL!******************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting removal commands*************************
***************************************************************************
***************************************************************************
[sudo] password for mnj: 
***************************************************************************
*************************Starting update commands**************************
***************************************************************************
***************************************************************************
***************************************************************************
*************************Starting install commands*************************
***************************************************************************
***************************************************************************
--2011-11-27 00:09:08--  [http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11-2/flashplayer11-2_p2_install_lin_32_112211.tar.gz](http://download.macromedia.com/pub/labs/flashplatformruntimes/flashplayer11-2/flashplayer11-2_p2_install_lin_32_112211.tar.gz)
Resolving download.macromedia.com... 2.21.67.191
Connecting to download.macromedia.com|2.21.67.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 6887485 (6.6M) [application/x-gzip]
Saving to: `flashplayer11-2_p2_install_lin_32_112211.tar.gz'

100%[======================================>] 6,887,485   1.04M/s   in 6.4s    

2011-11-27 00:09:25 (1.03 MB/s) - `flashplayer11-2_p2_install_lin_32_112211.tar.gz' saved [6887485/6887485]

libflashplayer.so
***************************************************************************
*************************Starting tweaking commands************************
***************************************************************************
***************************************************************************
OverrideGPUValidation=true
***************************************************************************
******FINISHED! You can close this terminal and restart Firefox now.*******
***************************************************************************
***************************************************************************
"

So I restarted the firefox and tried the site again - but still with this result:

"We have detected that you do not have the newest version of Flash Player installed.  Therefore, your connection has been switched to the Java connection mode.  For a better experience, please click here to upgrade to the latest Flash Player for free.  View current connection mode."

So how DO I get my the flsh player upated and how do I get rid of the Flash-Aid Add-On that does not work for me ?

---

### Post by ajgreeny on 2011-11-26
See [[ubuntu] ubuntu 10.10, firefox 8 64bit - flash not working]("http://ubuntuforums.org/showthread.php?t=1887314&goto=newpost")  

There have been problems with flash-aid just recently.  Or perhaps generally with flash, I'm not sure, but the stable version (Shockwave Flash 11.1 r102) works OK for me; the beta not at all.

---

### Post by Odense on 2011-11-27
Thank you - that did the trick for me :)

---

