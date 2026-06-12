---
title: "channels.conf format for DVBstreamer anyone?"
date: 2009-05-31
forum: Multimedia Software
---

### Post by ebike on 2009-05-31
Hi, as the title states, I am wanting the format of channels.conf that is used in setupdvbstreamer, so that I can use dvbstreamer in Freevo.

It seems there is a lot of different formats of channels.conf, i.e for VDR and xine, mplayer TVTime etc ..

I have tried scan, dvbscan, w_scan but can't seem to get the right syntax that setupdvbstreamer will accept.. can't even get w_scan to tune the card. Scan will output in vdr,zap and pids format, by neither seem to work in setupdvb .. 

By the way is the only place that dvbstreamer saves it's database to the directory ~/.dvbstreamer ? If so, I should be able to start with a clean database by deleting this directory right?

My latest channels.conf is this, it seems to get accepted by setupdvbstreamer, as it reports 13 services on two multiplexes:
> TV ONE:12483:h:S160.0E:22500:515:653:579:0
TV2:12483:h:S160.0E:22500:516:654:580:0
TVNZ 7:12483:h:S160.0E:22500:518:656:582:0
TVNZ SPORT EXTRA:12483:h:S160.0E:22500:520:658:0:0
TVNZ 6:12483:h:S160.0E:22500:512:650:581:0
STRATOS:12483:h:0:22500:514:652:1922
Parliament TV:12483:h:0:22500:515:653:1923
CUE:12483:h:0:22500:516:654:1924
Te Reo:12483:h:0:22500:517:655:1925
TV3:12483:h:0:22500:512:650:1920
C4:12483:h:0:22500:513:651:1921
TV3 PLUS1:12483:h:0:22500:518:656:1926


When I run dvbstreamer I get this:
>  dvbstreamer 
New setup, performing initial scan to fill in missing details.
Scanning 1243741221
Segmentation fault


Thanks in advance.

---

### Post by soapBAR2 on 2009-05-31
Disclaimer: I'm not very familiar with dvbstreamer, I've used it for all of 5 minutes before giving up and switching to VLC.

After a quick google, it seems that dvbstreamer uses an sqlite database instead of channels.conf. Since you threw a segfault, I'm more inclined to suspect that dvbstreamer/dvbstreamer-setup is broken (it can't be that carefully coded if it's SUPPOSED to throw a segfault with no debug information from a malformed channels.conf!). At any rate, if you can get a dvbstreamer database (there's a chance the database is already made, just not populated), you can easily edit it with SQLite Database Browser (nice GUI for SQLite, next to no SQL/SQLite knowledge needed) and just pop your own information in. 

It's just a matter of getting the database format right (you could try going to a dvbstreamer IRC channel and asking for someone's dvbstreamer database), and after that, autopilot should take over. 

Your other options are switching from dvbstreamer to VLC (they'll do the same job, but the knack will be getting VLC to interface with Freevo), or switching from Freevo to MythTV. I personally think MythTV is a better choice because it's more supported (it even has it's own Ubuntu distro) and has Windows clients for networked TV (if that's what you want).

Good luck!

---

### Post by ebike on 2009-05-31
Thanks for that. Can you specify what the exact name of the sqlite GUI program is, so I can download it?

There was a .db file in the .dvbstreamer directory, I have found that removing this removes the database ..

I am annoyed that I can't get more debugging info out of dvbstreamer, even -vvv on the command line doesn't work. However I did find this in a log file:

> 2009-05-31 16:58:08 :  PluginManager   :  3 : Plugin Manager Initialised
2009-05-31 16:58:08 :  Main            :  4 : Initialised plugin manager.
2009-05-31 16:58:08 :  Object          :  4 : Registered class "ServiceFilter_t" size 2568 destructor? No
2009-05-31 16:58:08 :  Object          :  4 : (0x765110) Created object of class "ServiceFilter_t" app ptr 0x765128 (servicefilter.c:121)
2009-05-31 16:58:08 :  DeliveryMethod  :  3 : Created DeliveryMethodInstance(0x75e110) for null://
2009-05-31 16:58:08 :  SAP             :  3 : Annoucement thread starting
2009-05-31 16:58:08 :  Object          :  4 : (0x7544f0) Malloc'ed memory size 16 app ptr 0x754508 (commands/cmd_scanning.c:148)
2009-05-31 16:58:08 :  Object          :  4 : (0x765d70) Created object of class "Multiplex_t" app ptr 0x765d88 (multiplexes.c:185)
2009-05-31 16:58:08 :  Object          :  4 : (0x765db0) Created object of class "Multiplex_t" app ptr 0x765dc8 (multiplexes.c:185)
2009-05-31 16:58:08 :  tuning          :  3 : Writing changes back to database.
2009-05-31 16:58:08 :  tuning          :  4 : Disabling filters
2009-05-31 16:58:08 :  tuning          :  4 : Caching Services
2009-05-31 16:58:08 :  Cache           :  3 : Freeing services
2009-05-31 16:58:08 :  Cache           :  3 : Loading 1 services for 1243741221
2009-05-31 16:58:08 :  Object          :  4 : (0x766510) Created object of class "Service_t" app ptr 0x766528 (services.c:592)
2009-05-31 16:58:08 :  Cache           :  3 : Loaded 0x0000 Maori TV
2009-05-31 16:58:08 :  Object          :  4 : (0x765d70:Multiplex_t) Incrementing ref count, now 2 (cache.c:242)
2009-05-31 16:58:08 :  Object          :  4 : (0x765d70:Multiplex_t) Incrementing ref count, now 3 (tuning.c:226)
2009-05-31 16:58:08 :  tuning          :  4 : Getting Frondend parameters
2009-05-31 16:58:08 :  tuning          :  4 : Tuning
setfront front: Invalid argument
2009-05-31 16:58:09 :  DVBAdapter      :  0 : setfront front: Invalid argument
2009-05-31 16:58:19 :  DVBAdapter      :  0 : setfront front: Invalid argument
2009-05-31 16:58:32 :  DVBAdapter      :  0 : setfront front: Invalid argument


I don't know if that helps ..

> **soapBAR2 said:**
> 
 I personally think MythTV is a better choice because it's more supported (it even has it's own Ubuntu distro) and has Windows clients for networked TV (if that's what you want).

Good luck!

I have got sick of Mythtv (been running it 7 years), it is getting more and more flakey .. the WAF has dropped to an alltime low .. I like Freevo's simplicity and modularity.

Thanks.

---

### Post by ebike on 2009-06-02
Anyone?:p

---

### Post by soapBAR2 on 2009-06-03
SQLite Database Browser is in the [repositories]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=sqlitebrowser") under sqlitebrowser

```
sudo apt-get install sqlitebrowser
```

Or, the sourceforge page is [here]("http://sourceforge.net/project/showfiles.php?group_id=87946&package_id=91778&release_id=414746") (Source, OSX-PPC, Win, *nix-i386)

To me, the program looks like it's getting far enough to actually set up the database, so it should really just be a case of putting your own values in and crossing your fingers ;).

---

