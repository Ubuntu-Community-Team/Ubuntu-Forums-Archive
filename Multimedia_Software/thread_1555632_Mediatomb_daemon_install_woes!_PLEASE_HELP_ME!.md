---
title: "Mediatomb daemon install woes! PLEASE HELP ME!"
date: 2010-08-18
forum: Multimedia Software
---

### Post by isaksdad on 2010-08-18
Hi,

I am new to completely new to this so please be patient. I am trying to install Mediatomb and keep getting this error message 

E: /var/cache/apt/archives/mediatomb-daemon_0.12.0~svn2018-4ubuntu1_all.deb: subprocess new pre-installation script returned error exit status 1

It appears that  mediatomb-daemon will not install due to an error.

Can anyone shed some light on what I might be doing wrong?


Thanks and sorry to be a complete noob

Isaksdad:p

---

### Post by aeiah on 2010-08-18
how are you trying to install it? what version of ubuntu are you running?

---

### Post by isaksdad on 2010-08-20
aeiah,

Thanks for the quick response, amazing that you are in my area too (Midlands, Uk).

Sorry for the late response!

I have now downloaded the mediatomb-0.12.1tar.gz and compiled and installed it that way. 
This was a really steep learning curve for me, but seems to have been a sucess ( no broken dependencies etc). Mediatomb is now detected on my network and streams audio and avi etc. 

Now I am having a real problem in streaming online content through the MT server from YouTube. I get this output in the Terminal window when doing so : -


MediaTomb UPnP Server version 0.12.1 - [http://mediatomb.cc/](http://mediatomb.cc/)

===============================================================================
Copyright 2005-2010 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2010-08-20 12:04:00    INFO: Loading configuration from: /home/christian/.mediatomb/config.xml
2010-08-20 12:04:00    INFO: Checking configuration...
2010-08-20 12:04:00    INFO: Setting filesystem import charset to UTF-8
2010-08-20 12:04:00    INFO: Setting metadata import charset to UTF-8
2010-08-20 12:04:00    INFO: Setting playlist charset to UTF-8
2010-08-20 12:04:00 WARNING: You enabled the YouTube feature, which allows you
                             to watch YouTube videos on your UPnP device!
                             Please check [http://www.youtube.com/t/terms](http://www.youtube.com/t/terms)
                             By using this feature you may be violating YouTube
                             service terms and conditions!

2010-08-20 12:04:00    INFO: Configuration check succeeded.
2010-08-20 12:04:00    INFO: Initialized port: 49152
2010-08-20 12:04:00    INFO: Server bound to: 192.168.1.xxx
2010-08-20 12:04:01    INFO: MediaTomb Web UI can be reached by following this link:
2010-08-20 12:04:01    INFO: [http://192.168.1.xxx:49152/](http://192.168.1.xxx:49152/)
2010-08-20 12:05:39   ERROR: Unexpected reply from YouTube: 404
2010-08-20 12:05:40   ERROR: Unexpected reply from YouTube: 404
2010-08-20 12:05:51   ERROR: Unexpected reply from YouTube: 404
2010-08-20 12:05:52   ERROR: Unexpected reply from YouTube: 404
2010-08-20 12:08:16   ERROR: Unexpected reply from YouTube: 404
2010-08-20 12:08:17   ERROR: Unexpected reply from YouTube: 404
2010-08-20 12:08:33   ERROR: Unexpected reply from YouTube: 404
2010-08-20 12:08:35   ERROR: Unexpected reply from YouTube: 404
[avi @ 0x8a80fd0]non-interleaved AVI
[NULL @ 0x8984d30]Invalid and inefficient vfw-avi packed B frames detected
[mpeg4 @ 0x8984d30]frame skip 8
[mpeg4 @ 0x8984d30]Invalid and inefficient vfw-avi packed B frames detected
[mpeg4 @ 0x8984d30]frame skip 8
    Last message repeated 2 times
[mpeg4 @ 0x8984d30]Invalid and inefficient vfw-avi packed B frames detected
[avi @ 0x8a80fd0]non-interleaved AVI
[NULL @ 0x8984d30]Invalid and inefficient vfw-avi packed B frames detected
[mpeg4 @ 0x8984d30]frame skip 8
[mpeg4 @ 0x8984d30]Invalid and inefficient vfw-avi packed B frames detected
[mpeg4 @ 0x8984d30]frame skip 8
    Last message repeated 2 times
[mpeg4 @ 0x8984d30]Invalid and inefficient vfw-avi packed B frames detected
[NULL @ 0x8984d30]Invalid and inefficient vfw-avi packed B frames detected
[mpeg4 @ 0x8984d30]Invalid and inefficient vfw-avi packed B frames detected
    Last message repeated 1 times
[NULL @ 0x8984d30]Invalid and inefficient vfw-avi packed B frames detected
[mpeg4 @ 0x8984d30]Invalid and inefficient vfw-avi packed B frames detected
^C2010-08-20 12:32:34    INFO: MediaTomb shutting down. Please wait...
2010-08-20 12:32:35    INFO: Server terminating
********@*********-laptop:~$ 

Do you have any ideas what is happening. The config.xml  has encoding enabled and should output to mp4 as the config.xml states!

Thanks for help and patience.

Cheers

isaksdad

---

### Post by justinlawrence on 2010-12-21
I get the same

```

2010-12-21 23:46:15   ERROR: Unexpected reply from YouTube: 404
2010-12-21 23:46:38   ERROR: Unexpected reply from YouTube: 404
2010-12-22 00:04:02   ERROR: Unexpected reply from YouTube: 404

```

running mediatomb Version: 0.12.1-0ubuntu1 on ubuntu maverick.

i suspect it's because something changed on Youtube itself.  is there any way for me to update whatever URL it's incorrectly calling?

if youtube change this regularly, may i suggest that the youtube_get setting get put into the /etc/mediatomb/config.xml

thanks

---

