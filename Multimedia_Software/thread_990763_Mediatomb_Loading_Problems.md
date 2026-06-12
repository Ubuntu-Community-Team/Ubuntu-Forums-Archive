---
title: "Mediatomb Loading Problems"
date: 2008-11-23
forum: Multimedia Software
---

### Post by BartGunn on 2008-11-23
Every time I try to open Mediatomb, I get a 'failed to connect' message - Firefox can't establish a connection to the server at 192.168.1.33:49152. If I de-install Mediatomb and re-install, it connects but then I have to reconfigure it to access my media files, then when I close it down I'm back to square one when I want to use it again. Anyone know a fix or suggest a more stable UPnP platform? I use it to stream DivX movies through my PS3
Thanks

---

### Post by Pericles_vsd on 2008-12-08
Hi, I have the exact same problem. I just installed Mediatomb 0.11 on ubuntu 8.10 and it work perfectly. However, when I reboot my computer I get a "failed to connect" message in firefox when I try to start Mediatomb. I did a lot of research on google to fix this issue but there's not much help on this specific trouble.  

Actually, I need to de-install and re-install mediatomb everytime I need to stream some movies to my ps3. Please someone help us.
Thanks

---

### Post by gsanse on 2008-12-10
I have the same problem. For some reason mediatomb crashes after running for some time. I suspected it could be a problem with sqllite, but I tried mysql and the same problem happens. I am still trying to get more data to diagnose the problem, any help is welcome.

You don't need to restart the machine to get mediatomb started again, just restart the mediatomb service:

sudo /etc/init.d/mediatomb start

However, you may need to do it again and again as the server keeps crashing.

---

### Post by Aerospaztic on 2008-12-26
Thanks gsanse!  That worked perfectly for me!

---

### Post by strattonbrazil on 2008-12-29
Starting the daemon manually seems to solve the problem, but I don't think it's a crashing issue.  Once the daemon starts, it seems to stay running for quite a while.  It just doesn't start at all when the system reboots.  I don't know why since I changed the NO_START option to "no".

---

### Post by amak79 on 2009-01-12
> **BartGunn said:**
> Every time I try to open Mediatomb, I get a 'failed to connect' message - Firefox can't establish a connection to the server at 192.168.1.33:49152. If I de-install Mediatomb and re-install, it connects but then I have to reconfigure it to access my media files, then when I close it down I'm back to square one when I want to use it again. Anyone know a fix or suggest a more stable UPnP platform? I use it to stream DivX movies through my PS3
Thanks

I suspect that this issue is due to the fact that NetworkManager is starting after MediaTomb. The solution to this issue can be found in the MediaTomb [FAQ]("http://mediatomb.cc/dokuwiki/faq:faq#how_do_i_make_mediatomb_start_automatically").

---

### Post by miraceti52 on 2009-01-13
I have been trying for quite a while to get MediaTomb running properly in Intrepid 64 bit and failing.  I have tried every suggestion I could find in the forums and none worked.

I then found PMS  (Playstation Media Server) at 

[http://code.google.com/p/ps3mediaserver/downloads/detail?name=pms-linux-1.02.1.tgz&can=2&q=](http://code.google.com/p/ps3mediaserver/downloads/detail?name=pms-linux-1.02.1.tgz&can=2&q=) 

and it works perfectly straight "out of the box". 

In my opinion it is brilliant and very simple to use.

---

### Post by antiartist on 2011-02-21
Well, I am also having this issue and nothing in this thread has helped thus far.  Attempting to access Mediatomb's browser UI, the browser reports "Unable to connect - Firefox can't establish a connection to the server at 192.168.0.111:49152"

I cannot restart the service.  I have also tried killing the mediatomb service and starting it as well.  When I attempt to, the 'start' process never seems to finish (as seen below:)

```
MediaTomb UPnP Server version 0.12.0 - http://mediatomb.cc/

===============================================================================
Copyright 2005-2008 Gena Batsyan, Sergey Bostandzhyan, Leonhard Wimmer.
MediaTomb is free software, covered by the GNU General Public License version 2

2011-02-21 08:47:37    INFO: Loading configuration from: /etc/mediatomb/config.x                                                                                        ml
2011-02-21 08:47:37    INFO: Checking configuration...
2011-02-21 08:47:37    INFO: Setting filesystem import charset to UTF-8
2011-02-21 08:47:37    INFO: Setting metadata import charset to UTF-8
2011-02-21 08:47:37    INFO: Setting playlist charset to UTF-8
2011-02-21 08:47:37    INFO: Configuration check succeeded.
2011-02-21 08:47:37    INFO: Initialized port: 49152
2011-02-21 08:47:37    INFO: Server bound to: 192.168.0.111
2011-02-21 08:47:38    INFO: MediaTomb Web UI can be reached by following this l                                                                                        ink:
2011-02-21 08:47:38    INFO: http://192.168.0.111:49152/
```And when I press control-C to be able to make use of the terminal once again, I see the following and am returned to the prompt:
```
^C2011-02-21 08:53:42    INFO: MediaTomb shutting down. Please wait...
2011-02-21 08:53:43    INFO: Server terminating

```I have also  changed the run order (as mentioned in this thread, using:
```
sudo update-rc.d -f mediatomb remove
sudo update-rc.d mediatomb defaults 99
```It should be noted that sometimes when I attempt to start the service, it tries set the URL using port 49153, not 49152, but I am not sure why.  Either way, using either of the URL's in the browser returns the UI.

---

