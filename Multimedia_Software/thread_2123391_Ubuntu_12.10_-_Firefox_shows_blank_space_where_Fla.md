---
title: "Ubuntu 12.10 - Firefox shows blank space where Flash content should be."
date: 2013-03-07
forum: Multimedia Software
---

### Post by Terry of Astoria on 2013-03-07
I did the following to try to fix; no dice. Any ideas?
```
me@a620n:~$ sudo apt-get --reinstall install flashplugin-installer 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfs6 libmtdev1 libx264-120 libxcb-dri2-0 printer-driver-min12xxw printer-driver-pnm2ppa x11-apps x11-session-utils x11-xfs-utils xfonts-base
  xfonts-scalable xinit xserver-common xserver-common-lts-quantal xserver-xorg-core-lts-quantal xserver-xorg-input-evdev-lts-quantal
  xserver-xorg-video-openchrome-lts-quantal
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/7,046 B of archives.
After this operation, 0 B of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 171236 files and directories currently installed.)
Preparing to replace flashplugin-installer 11.2.202.273ubuntu0.12.10.1 (using .../flashplugin-installer_11.2.202.273ubuntu0.12.10.1_i386.deb) ...
Unpacking replacement flashplugin-installer ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.273.orig.tar.gz
Installing from local file /tmp/tmpVdARnI.gz
Flash Plugin installed.
Setting up flashplugin-installer (11.2.202.273ubuntu0.12.10.1) ...
me@a620n:~$
```
I just get a blank space where the content would be . . .WUWD...??
I'm going to go sudo apt-get autoremove, reboot and come back and check for replies.
THX!

---

### Post by cetag on 2013-03-13
Yes, I've got the same problem. I'm on Oneiric Ocelot. Flash under Firefox has been working fine until several days ago, when a black screen only would appear in Flash in the Youtube box.
  
I 1st reinstalled from Firefox Preferences, no luck. Then reinstalled via Flash-Aid, and no luck.    

Then following this post:  
[http://ubuntuforums.org/showthread.php?t=1951166&p=11811776#post11811776](http://ubuntuforums.org/showthread.php?t=1951166&p=11811776#post11811776) 
Flash runs, but not on all Youtube material. Firefox then gives the notice; "Additional Plugins are required to view all the media on this page", and then pops up the Firefox "Plugin Finder Service" which when run, runs endlessly with "Firefox is now checking for available plugins", (after 10 minutes I've cancelled this). 
 
So presently I have a half-working Flash plugin, in my Firefox.  It plays some (Youtube) media and not others. 
Am looking now at removing Firefox and reinstalling. 

Any suggestions, gratefully received.

---

### Post by cetag on 2013-03-13
Any luck, Terry?     The article which I referred to worked for me in the past. However there have been revisions to Firefox since then, and perhaps revisions to Flash too. 
 
So it remains an open question:  How is it recommened to get Flash working (install, or upgrade, or deinstall/reinstall) in recent Unbuntu and recent Firefox. 
 
Presently, it is tempting to remove Firefox, and Flash-Aid, and then re-install.

---

### Post by cetag on 2013-03-14
Flash is back working again, on my Oneiric Ubuntu Firefox. 

I re-ran this method,     
[http://ubuntuforums.org/showthread.php?t=1951166&p=11813269#post11813269](http://ubuntuforums.org/showthread.php?t=1951166&p=11813269#post11813269) 

and used an older version  libflashplayer.so 

I can only guess that; this older version library, and that location ( /usr/lib/mozilla/plugins/ ), somehow did the trick. 
Unlike before (in the earlier post above), there was no  .so  library in that location.  

Thanks. 



-----Please disregard this following. ------
Further to,  I tried uninstalling then re-installing Flash-Aid, (after removing Flash). 
And here's the Flash-Aid version of events; 


*************************Starting install commands*************************
***************************************************************************
***************************************************************************
--2013-03-14 20:15:42--  [http://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.238/install_flash_player_11_linux.i386.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.238/install_flash_player_11_linux.i386.tar.gz)
Resolving fpdownload.macromedia.com... 96.7.130.70
Connecting to fpdownload.macromedia.com|96.7.130.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2013-03-14 20:15:43 ERROR 404: Not Found.

md5sum: *flash*: No such file or directory
Flash 32bit installation aborted, due to md5 checksum mismatch!
***************************************************************************
*************************Starting tweaking commands************************
***************************************************************************
***************************************************************************
***************************************************************************
******FINISHED! You can close this terminal and restart Firefox now.*******
***************************************************************************
***************************************************************************

---

### Post by paulvbrown on 2013-07-08
> **cetag said:**
> Flash is back working again, on my Oneiric Ubuntu Firefox. 

I re-ran this method,     
[http://ubuntuforums.org/showthread.php?t=1951166&p=11813269#post11813269](http://ubuntuforums.org/showthread.php?t=1951166&p=11813269#post11813269) 


Thx for this -- I used the same method and got it working on 12.04 (with warning msgs about using an old flash), but the link to the old flash linked to the current version that is causing all the problems, which of course I didn't realize until after I'd downloaded, unpacked, "installed", and restarted Firefox to test.  SO, to save others some time, here's a summary of the instructions as well as a link to archived flash-player versions: [http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html](http://helpx.adobe.com/flash-player/kb/archived-flash-player-versions.html)  

...and the link to the latest archived version of 11.1 (Released 3/05/2012) Flash Player 11.1.102.63 (174 MB):
[http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip](http://fpdownload.macromedia.com/get/flashplayer/installers/archive/fp_11.1.102.63_archive.zip)

It includes linux versions.  Just "drill down" into the zip file til you find "flashplayer11_1r102_63_linux.i386.tar.gz" (for 32-bit version), 
1) unpack libflashplayer.so to the directory of your choice,
2) use about:plugins in address bar of firefox to determine location of current libflashplayer.so
3) make backup copy of current libflashplayer.so
4) replace current libflashplayer.so with the one you just unpacked

I presume a restart of firefox is necessary, but didn't test.  Anyone have any idea if there are actual security risks in using this older version?

---

