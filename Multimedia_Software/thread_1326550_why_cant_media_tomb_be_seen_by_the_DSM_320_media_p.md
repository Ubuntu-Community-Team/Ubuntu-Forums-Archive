---
title: "why cant media tomb be seen by the DSM 320 media player?"
date: 2009-11-14
forum: Multimedia Software
---

### Post by sdowney717 on 2009-11-14
ok the network interface has to be set since i am running 2 nics
[https://help.ubuntu.com/community/MediaTomb](https://help.ubuntu.com/community/MediaTomb) does not mention this!
[http://mediatomb.cc/dokuwiki/faq:faq](http://mediatomb.cc/dokuwiki/faq:faq)
[http://en.gentoo-wiki.com/wiki/MediaTomb#Network_Interface](http://en.gentoo-wiki.com/wiki/MediaTomb#Network_Interface)

edit the file in etc/default/mediatomb

it is now working, sort of.
the server is running but no content is displayed as a directory listing

i found out it is not working on the network. A separate pc running xbmc cant see it as an available media server


scott@scott-desktop:~$ mediatomb

MediaTomb UPnP Server version 0.12.0 - [http://mediatomb.cc/](http://mediatomb.cc/)

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2
other servers such as ushare and minidlna are visible
interestingly, mediatomb is visible on the same machine it is installed by XBMC media player
just not showing up in the list, is there a configuration to turn on upnp broadcasting?


2009-11-14 14:20:23    INFO: Loading configuration from: /home/scott/.mediatomb/config.xml
2009-11-14 14:20:23    INFO: Checking configuration...
2009-11-14 14:20:23    INFO: Setting filesystem import charset to UTF-8
2009-11-14 14:20:23    INFO: Setting metadata import charset to UTF-8
2009-11-14 14:20:23    INFO: Setting playlist charset to UTF-8
2009-11-14 14:20:23    INFO: Configuration check succeeded.
2009-11-14 14:20:23    INFO: Initialized port: 49153
2009-11-14 14:20:23    INFO: Server bound to: 192.168.110.1
2009-11-14 14:20:23    INFO: Adding HTTP header "X-User-Agent: redsonic"
2009-11-14 14:20:24    INFO: MediaTomb Web UI can be reached by following this link:
2009-11-14 14:20:24    INFO: [http://192.168.110.1:49153/](http://192.168.110.1:49153/)

---

### Post by BuzzBunny on 2011-06-24
I know this is an old thread. But I am new and this thread solved my ( very simple it turned out ). I had got so bogged down in so much detail I missed the obvious two network cards issue.

Thanks ! Awesome. The [solved] label also helped draw me in. Great to see a thread properly completed.

---

